---
title: Kit de développement logiciel (SDK) Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 378171186599dd8d103111da183b7fc2e6e01c42
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134258"
---
# <a name="extensibility---android"></a>Extensibilité – Android

## <a name="custom-parsing-of-card-elements"></a>Analyse personnalisée d’éléments de carte

Vous pouvez étendre l’analyseur pour prendre en charge les éléments de carte que vous avez définis. Par exemple, imaginons que nous ayons un nouveau type d’élément ressemblant à ceci :
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

Ensuite, les lignes suivantes montrent comment l’analyser dans un CardElement qui s’étend à partir de BaseCardElement :
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

Et voici comment inscrire l’analyseur et obtenir un objet AdaptiveCard contenant l’élément personnalisé :
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Vient ensuite le rendu de l’élément personnalisé

## <a name="custom-rendering-of-card-elements"></a>Rendu personnalisé d’éléments de carte

Pour définir notre propre convertisseur personnalisé pour notre type, nous devons commencer par créer une classe qui s’étend à partir de BaseCardElementParser :
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

Nous enregistrons ensuite ce convertisseur comme suit :
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

## <a name="custom-rendering-of-actions"></a>Rendu personnalisé d’actions

[!IMPORTANT]
> Des modifications du rendu personnalisé d’actions sont prévues pour la version v1.2 mais ne sont pas encore terminées

## <a name="custom-image-loading"></a>Chargement d’image personnalisée

### <a name="ionlineimageloader"></a>IOnlineImageLoader

> [!IMPORTANT]
> **Il n’est possible d’inscrire qu’un seul IOnlineImageLoader qui prévaut sur la méthode par défaut de récupération d’images**

L’IOnlineImageLoader a été ajouté pour permettre aux développeurs d’obtenir des images qui ne pourraient pas être simplement téléchargées ou récupérées à partir d’une source en ligne, ou dont la récupération nécessiterait des étapes préalables. Pour implémenter un OnlineImageLoader, vous devez uniquement implémenter la méthode : 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

Voici un exemple d’OnlineImageLoader qui modifie toutes les images d’un chat :

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Enfin, pour inscrire ce chargeur d’image, il vous suffit d’ajouter cette ligne à votre code.

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a>IResourceResolver (rend obsolète IOnlineImageLoader)

Pour la version v1.2, la prise en charge de ResourceResolvers complets a été ajoutée au convertisseur Android. L’implémentation d’un résolveur de ressources est très similaire à celle d’un IOnlineImageLoader, mais le fait de disposer de ResourceResolvers permet à un développeur d’ajouter plusieurs méthodes pour récupérer des images à partir de toutes sortes de sources dans une seule carte. Cela se fait en liant chaque ResourceResolver à un préfixe unique interrogeable lors d’une tentative de récupération d’image. 

Vous pouvez implémenter un ResourceResolver similaire à celui-ci :

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

Comme mentionné précédemment, vous pouvez inscrire plusieurs ResourceResolvers. Pour inscrire un ResourceResolver, vous pouvez faire ceci :

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a>Transformation d’un IOnlineImageLoader en IResourceResolver 

La transformation d’un IOnlineImageLoader en IResourceResolver est une tâche assez facile, car nous avons tenté de maintenir les méthodes pour ce dernier aussi similaires que possible à l’IOnlineImageLoader.

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

Comme vous pouvez le voir, plus grands changements sont les suivants :
* loadOnlineImage(String, GenericImageLoaderAsync) a été renommé en resolveImageResource(String, GenericImageLoaderAsync) ;
* une surcharge pour resolveImageResource (String, GenericImageLoaderAsync) a été ajoutée en tant que resolveImageResource (chaîne, GenericImageLoaderAsync, int) pour prendre en charge des scénarios où la largeur maximale est requise.

## <a name="custom-media-loading"></a>Chargement de média personnalisé

> [!IMPORTANT]
> **N’oubliez pas qu’IOnlineMediaLoader requiert que MediaDataSource ait été ajouté dans l’API niveau 23 ou Android M**

En même temps que l’élément multimédia, a également été incluse l’interface IOnlineMediaLoader qui permet aux développeurs de remplacer la [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) utilisée pour l’élément mediaPlayer sous-jacent. **(Nécessite Android M)**

La première chose à faire est de créer une classe qui implémente IOnlineImageLoader :

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

Une fois que cette classe a été implémentée, vous pouvez inscrire votre classe OnlineMediaLoader en ajoutant : 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
