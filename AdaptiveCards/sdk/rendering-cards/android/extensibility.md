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
# <a name="extensibility---android"></a><span data-ttu-id="13c6b-102">Extensibilité – Android</span><span class="sxs-lookup"><span data-stu-id="13c6b-102">Extensibility - Android</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="13c6b-103">Analyse personnalisée d’éléments de carte</span><span class="sxs-lookup"><span data-stu-id="13c6b-103">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="13c6b-104">Vous pouvez étendre l’analyseur pour prendre en charge les éléments de carte que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="13c6b-104">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="13c6b-105">Par exemple, imaginons que nous ayons un nouveau type d’élément ressemblant à ceci :</span><span class="sxs-lookup"><span data-stu-id="13c6b-105">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="13c6b-106">Ensuite, les lignes suivantes montrent comment l’analyser dans un CardElement qui s’étend à partir de BaseCardElement :</span><span class="sxs-lookup"><span data-stu-id="13c6b-106">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="13c6b-107">Et voici comment inscrire l’analyseur et obtenir un objet AdaptiveCard contenant l’élément personnalisé :</span><span class="sxs-lookup"><span data-stu-id="13c6b-107">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="13c6b-108">Vient ensuite le rendu de l’élément personnalisé</span><span class="sxs-lookup"><span data-stu-id="13c6b-108">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="13c6b-109">Rendu personnalisé d’éléments de carte</span><span class="sxs-lookup"><span data-stu-id="13c6b-109">Custom Rendering of Card Elements</span></span>

<span data-ttu-id="13c6b-110">Pour définir notre propre convertisseur personnalisé pour notre type, nous devons commencer par créer une classe qui s’étend à partir de BaseCardElementParser :</span><span class="sxs-lookup"><span data-stu-id="13c6b-110">To define our own custom renderer for our type, we must first create a class that extends from BaseCardElementParser:</span></span>
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

<span data-ttu-id="13c6b-111">Nous enregistrons ensuite ce convertisseur comme suit :</span><span class="sxs-lookup"><span data-stu-id="13c6b-111">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="13c6b-112">Rendu personnalisé d’actions</span><span class="sxs-lookup"><span data-stu-id="13c6b-112">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="13c6b-113">Des modifications du rendu personnalisé d’actions sont prévues pour la version v1.2 mais ne sont pas encore terminées</span><span class="sxs-lookup"><span data-stu-id="13c6b-113">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="13c6b-114">Chargement d’image personnalisée</span><span class="sxs-lookup"><span data-stu-id="13c6b-114">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="13c6b-115">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="13c6b-115">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="13c6b-116">**Il n’est possible d’inscrire qu’un seul IOnlineImageLoader qui prévaut sur la méthode par défaut de récupération d’images**</span><span class="sxs-lookup"><span data-stu-id="13c6b-116">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="13c6b-117">L’IOnlineImageLoader a été ajouté pour permettre aux développeurs d’obtenir des images qui ne pourraient pas être simplement téléchargées ou récupérées à partir d’une source en ligne, ou dont la récupération nécessiterait des étapes préalables.</span><span class="sxs-lookup"><span data-stu-id="13c6b-117">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="13c6b-118">Pour implémenter un OnlineImageLoader, vous devez uniquement implémenter la méthode :</span><span class="sxs-lookup"><span data-stu-id="13c6b-118">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="13c6b-119">Voici un exemple d’OnlineImageLoader qui modifie toutes les images d’un chat :</span><span class="sxs-lookup"><span data-stu-id="13c6b-119">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

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

<span data-ttu-id="13c6b-120">Enfin, pour inscrire ce chargeur d’image, il vous suffit d’ajouter cette ligne à votre code.</span><span class="sxs-lookup"><span data-stu-id="13c6b-120">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="13c6b-121">IResourceResolver (rend obsolète IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="13c6b-121">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="13c6b-122">Pour la version v1.2, la prise en charge de ResourceResolvers complets a été ajoutée au convertisseur Android.</span><span class="sxs-lookup"><span data-stu-id="13c6b-122">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="13c6b-123">L’implémentation d’un résolveur de ressources est très similaire à celle d’un IOnlineImageLoader, mais le fait de disposer de ResourceResolvers permet à un développeur d’ajouter plusieurs méthodes pour récupérer des images à partir de toutes sortes de sources dans une seule carte. Cela se fait en liant chaque ResourceResolver à un préfixe unique interrogeable lors d’une tentative de récupération d’image.</span><span class="sxs-lookup"><span data-stu-id="13c6b-123">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="13c6b-124">Vous pouvez implémenter un ResourceResolver similaire à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="13c6b-124">You can implement a ResourceResolver similar to this</span></span>

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

<span data-ttu-id="13c6b-125">Comme mentionné précédemment, vous pouvez inscrire plusieurs ResourceResolvers. Pour inscrire un ResourceResolver, vous pouvez faire ceci :</span><span class="sxs-lookup"><span data-stu-id="13c6b-125">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="13c6b-126">Transformation d’un IOnlineImageLoader en IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="13c6b-126">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="13c6b-127">La transformation d’un IOnlineImageLoader en IResourceResolver est une tâche assez facile, car nous avons tenté de maintenir les méthodes pour ce dernier aussi similaires que possible à l’IOnlineImageLoader.</span><span class="sxs-lookup"><span data-stu-id="13c6b-127">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="13c6b-128">Comme vous pouvez le voir, plus grands changements sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="13c6b-128">As you can see, the biggest changes are</span></span>
* <span data-ttu-id="13c6b-129">loadOnlineImage(String, GenericImageLoaderAsync) a été renommé en resolveImageResource(String, GenericImageLoaderAsync) ;</span><span class="sxs-lookup"><span data-stu-id="13c6b-129">loadOnlineImage(String, GenericImageLoaderAsync) was renamed to resolveImageResource(String, GenericImageLoaderAsync)</span></span>
* <span data-ttu-id="13c6b-130">une surcharge pour resolveImageResource (String, GenericImageLoaderAsync) a été ajoutée en tant que resolveImageResource (chaîne, GenericImageLoaderAsync, int) pour prendre en charge des scénarios où la largeur maximale est requise.</span><span class="sxs-lookup"><span data-stu-id="13c6b-130">an overload for resolveImageResource(String, GenericImageLoaderAsync) was added as resolveImageResource(String, GenericImageLoaderAsync, int) in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="13c6b-131">Chargement de média personnalisé</span><span class="sxs-lookup"><span data-stu-id="13c6b-131">Custom media loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="13c6b-132">**N’oubliez pas qu’IOnlineMediaLoader requiert que MediaDataSource ait été ajouté dans l’API niveau 23 ou Android M**</span><span class="sxs-lookup"><span data-stu-id="13c6b-132">**Remember IOnlineMediaLoader requires MediaDataSource was added in API level 23 or Android M**</span></span>

<span data-ttu-id="13c6b-133">En même temps que l’élément multimédia, a également été incluse l’interface IOnlineMediaLoader qui permet aux développeurs de remplacer la [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) utilisée pour l’élément mediaPlayer sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="13c6b-133">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="13c6b-134">**(Nécessite Android M)**</span><span class="sxs-lookup"><span data-stu-id="13c6b-134">**(Requires android M)**</span></span>

<span data-ttu-id="13c6b-135">La première chose à faire est de créer une classe qui implémente IOnlineImageLoader :</span><span class="sxs-lookup"><span data-stu-id="13c6b-135">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

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

<span data-ttu-id="13c6b-136">Une fois que cette classe a été implémentée, vous pouvez inscrire votre classe OnlineMediaLoader en ajoutant :</span><span class="sxs-lookup"><span data-stu-id="13c6b-136">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
