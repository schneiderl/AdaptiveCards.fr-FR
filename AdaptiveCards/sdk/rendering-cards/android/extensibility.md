---
title: Kit de développement logiciel (SDK) Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: ca92f0a2b6ef8a36c5394e4dd9853df59fef22b2
ms.sourcegitcommit: 8c8067206f283d97a5aa4ec65ba23d3fe18962f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299556"
---
# <a name="extensibility---android"></a><span data-ttu-id="97048-102">Extensibilité – Android</span><span class="sxs-lookup"><span data-stu-id="97048-102">Extensibility - Android</span></span>

<span data-ttu-id="97048-103">Le convertisseur Android peut être étendu pour prendre en charge plusieurs scénarios, notamment:</span><span class="sxs-lookup"><span data-stu-id="97048-103">The Android renderer can be extended to support multiple scenarios including:</span></span>
* [<span data-ttu-id="97048-104">Analyse personnalisée des éléments de carte</span><span class="sxs-lookup"><span data-stu-id="97048-104">Custom Parsing of Card Elements</span></span>](#custom-parsing-of-card-elements)
* [<span data-ttu-id="97048-105">Rendu personnalisé d’éléments de carte</span><span class="sxs-lookup"><span data-stu-id="97048-105">Custom Rendering of Card Elements</span></span>](#custom-rendering-of-card-elements)
* <span data-ttu-id="97048-106">[Rendu personnalisé des actions](#custom-rendering-of-actions) (Depuis v 1.2)</span><span class="sxs-lookup"><span data-stu-id="97048-106">[Custom Rendering of Actions](#custom-rendering-of-actions) (Since v1.2)</span></span>
* <span data-ttu-id="97048-107">[Chargement d’images personnalisées](#custom-image-loading) (Depuis v 1.0.1)</span><span class="sxs-lookup"><span data-stu-id="97048-107">[Custom Image Loading](#custom-image-loading) (Since v1.0.1)</span></span>
* <span data-ttu-id="97048-108">[Chargement de support personnalisé](#custom-media-loading) (Depuis v 1.1)</span><span class="sxs-lookup"><span data-stu-id="97048-108">[Custom Media Loading](#custom-media-loading) (Since v1.1)</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="97048-109">Analyse personnalisée d’éléments de carte</span><span class="sxs-lookup"><span data-stu-id="97048-109">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="97048-110">Vous pouvez étendre l’analyseur pour prendre en charge les éléments de carte que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="97048-110">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="97048-111">Par exemple, imaginons que nous ayons un nouveau type d’élément ressemblant à ceci :</span><span class="sxs-lookup"><span data-stu-id="97048-111">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="97048-112">Ensuite, les lignes suivantes montrent comment l’analyser dans un CardElement qui s’étend à partir de BaseCardElement :</span><span class="sxs-lookup"><span data-stu-id="97048-112">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="97048-113">Et voici comment inscrire l’analyseur et obtenir un objet AdaptiveCard contenant l’élément personnalisé :</span><span class="sxs-lookup"><span data-stu-id="97048-113">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="97048-114">Vient ensuite le rendu de l’élément personnalisé</span><span class="sxs-lookup"><span data-stu-id="97048-114">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="97048-115">Rendu personnalisé d’éléments de carte</span><span class="sxs-lookup"><span data-stu-id="97048-115">Custom Rendering of Card Elements</span></span>

> [!IMPORTANT]
>
> <span data-ttu-id="97048-116">**Liste des modifications avec rupture**</span><span class="sxs-lookup"><span data-stu-id="97048-116">**List of Breaking Changes**</span></span>
>
> [<span data-ttu-id="97048-117">Changements importants pour la version v1.2</span><span class="sxs-lookup"><span data-stu-id="97048-117">Breaking changes for v1.2</span></span>](#breaking-changes-for-v12)

<span data-ttu-id="97048-118">Pour définir notre propre convertisseur personnalisé pour notre type, nous devons d’abord créer une classe qui s’étend ```BaseCardElementRenderer```de:</span><span class="sxs-lookup"><span data-stu-id="97048-118">To define our own custom renderer for our type, we must first create a class that extends from ```BaseCardElementRenderer```:</span></span>
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

<span data-ttu-id="97048-119">Nous enregistrons ensuite ce convertisseur comme suit :</span><span class="sxs-lookup"><span data-stu-id="97048-119">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a><span data-ttu-id="97048-120">Modifications avec rupture pour v 1.2</span><span class="sxs-lookup"><span data-stu-id="97048-120">Breaking changes for v1.2</span></span>

<span data-ttu-id="97048-121">La ```render``` méthode a été modifiée pour inclure ```RenderedAdaptiveCard``` le paramètre ```ContainerStyle``` et a été modifiée pour un RenderArgs où le ContainerStyle est maintenant contenu, de sorte qu’une classe qui étend BaseCardElementRenderer doit se présenter comme suit</span><span class="sxs-lookup"><span data-stu-id="97048-121">The ```render``` method was changed to include the ```RenderedAdaptiveCard``` parameter and ```ContainerStyle``` was changed for a RenderArgs where the ContainerStyle is now contained so a class that extends BaseCardElementRenderer should look like this</span></span>

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a><span data-ttu-id="97048-122">Analyse personnalisée des actions de carte</span><span class="sxs-lookup"><span data-stu-id="97048-122">Custom Parsing of Card Actions</span></span>

<span data-ttu-id="97048-123">De même que l’analyse d’éléments de carte personnalisés dans v 1.2, il est possible d’analyser des actions personnalisées.</span><span class="sxs-lookup"><span data-stu-id="97048-123">Similarly to parsing custom card elements in v1.2 the possibility to parse custom actions was introduced.</span></span> <span data-ttu-id="97048-124">Par exemple, imaginons que nous ayons un nouveau type d’action qui ressemble à ceci:</span><span class="sxs-lookup"><span data-stu-id="97048-124">For example, say we have a new action type that looks like this:</span></span>
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

<span data-ttu-id="97048-125">Les lignes suivantes montrent comment l’analyser dans un ActionElement qui s’étend à partir de ```BaseActionElement```:</span><span class="sxs-lookup"><span data-stu-id="97048-125">Then the following lines demonstrate how to parse it into a ActionElement that extends from the ```BaseActionElement```:</span></span>
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

<span data-ttu-id="97048-126">Et les lignes suivantes montrent comment inscrire l’analyseur et récupérer un objet AdaptiveCard qui contient l’élément d’action personnalisé:</span><span class="sxs-lookup"><span data-stu-id="97048-126">And the next lines demonstrate how to register the parser and get an AdaptiveCard object that contains the custom action element:</span></span>
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="97048-127">Le prochain rendu de l’action personnalisée</span><span class="sxs-lookup"><span data-stu-id="97048-127">Next comes rendering the custom action</span></span>

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="97048-128">Rendu personnalisé des actions</span><span class="sxs-lookup"><span data-stu-id="97048-128">Custom Rendering of Actions</span></span>

<span data-ttu-id="97048-129">Pour définir notre propre convertisseur d’action personnalisé pour notre type, nous devons d’abord créer une classe qui s' ```BaseActionElementRenderer```étend de:</span><span class="sxs-lookup"><span data-stu-id="97048-129">To define our own custom action renderer for our type, we must first create a class that extends from ```BaseActionElementRenderer```:</span></span>
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

<span data-ttu-id="97048-130">Nous enregistrons ensuite ce convertisseur comme suit :</span><span class="sxs-lookup"><span data-stu-id="97048-130">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="97048-131">Rendu personnalisé d’actions</span><span class="sxs-lookup"><span data-stu-id="97048-131">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="97048-132">Des modifications du rendu personnalisé d’actions sont prévues pour la version v1.2 mais ne sont pas encore terminées</span><span class="sxs-lookup"><span data-stu-id="97048-132">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="97048-133">Chargement d’image personnalisée</span><span class="sxs-lookup"><span data-stu-id="97048-133">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="97048-134">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="97048-134">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97048-135">**Il n’est possible d’inscrire qu’un seul IOnlineImageLoader qui prévaut sur la méthode par défaut de récupération d’images**</span><span class="sxs-lookup"><span data-stu-id="97048-135">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="97048-136">L’IOnlineImageLoader a été ajouté pour permettre aux développeurs d’obtenir des images qui ne pourraient pas être simplement téléchargées ou récupérées à partir d’une source en ligne, ou dont la récupération nécessiterait des étapes préalables.</span><span class="sxs-lookup"><span data-stu-id="97048-136">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="97048-137">Pour implémenter un OnlineImageLoader, vous devez uniquement implémenter la méthode :</span><span class="sxs-lookup"><span data-stu-id="97048-137">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="97048-138">Voici un exemple d’OnlineImageLoader qui modifie toutes les images d’un chat :</span><span class="sxs-lookup"><span data-stu-id="97048-138">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

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

<span data-ttu-id="97048-139">Enfin, pour inscrire ce chargeur d’image, il vous suffit d’ajouter cette ligne à votre code.</span><span class="sxs-lookup"><span data-stu-id="97048-139">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="97048-140">IResourceResolver (rend obsolète IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="97048-140">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="97048-141">Pour la version v1.2, la prise en charge de ResourceResolvers complets a été ajoutée au convertisseur Android.</span><span class="sxs-lookup"><span data-stu-id="97048-141">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="97048-142">L’implémentation d’un résolveur de ressources est très similaire à celle d’un IOnlineImageLoader, mais le fait de disposer de ResourceResolvers permet à un développeur d’ajouter plusieurs méthodes pour récupérer des images à partir de toutes sortes de sources dans une seule carte. Cela se fait en liant chaque ResourceResolver à un préfixe unique interrogeable lors d’une tentative de récupération d’image.</span><span class="sxs-lookup"><span data-stu-id="97048-142">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="97048-143">Vous pouvez implémenter un ResourceResolver similaire à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="97048-143">You can implement a ResourceResolver similar to this</span></span>

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

<span data-ttu-id="97048-144">Comme mentionné précédemment, vous pouvez inscrire plusieurs ResourceResolvers. Pour inscrire un ResourceResolver, vous pouvez faire ceci :</span><span class="sxs-lookup"><span data-stu-id="97048-144">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="97048-145">Transformation d’un IOnlineImageLoader en IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="97048-145">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="97048-146">La transformation d’un IOnlineImageLoader en IResourceResolver est une tâche assez facile, car nous avons tenté de maintenir les méthodes pour ce dernier aussi similaires que possible à l’IOnlineImageLoader.</span><span class="sxs-lookup"><span data-stu-id="97048-146">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="97048-147">Comme vous pouvez le voir, plus grands changements sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="97048-147">As you can see, the biggest changes are</span></span>

* <span data-ttu-id="97048-148">```loadOnlineImage(String, GenericImageLoaderAsync)```a été renommé en```resolveImageResource(String, GenericImageLoaderAsync)```</span><span class="sxs-lookup"><span data-stu-id="97048-148">```loadOnlineImage(String, GenericImageLoaderAsync)``` was renamed to ```resolveImageResource(String, GenericImageLoaderAsync)```</span></span>
* <span data-ttu-id="97048-149">une surcharge pour ```resolveImageResource(String, GenericImageLoaderAsync)``` a été ajoutée ```resolveImageResource(String, GenericImageLoaderAsync, int)``` comme afin de prendre en charge les scénarios où la largeur maximale est requise</span><span class="sxs-lookup"><span data-stu-id="97048-149">an overload for ```resolveImageResource(String, GenericImageLoaderAsync)``` was added as ```resolveImageResource(String, GenericImageLoaderAsync, int)``` in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="97048-150">Chargement de support personnalisé</span><span class="sxs-lookup"><span data-stu-id="97048-150">Custom Media Loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97048-151">**N’oubliez pas ```IOnlineMediaLoader``` queaétéajoutéauniveaudel’API23ouAndroidM```MediaDataSource```**</span><span class="sxs-lookup"><span data-stu-id="97048-151">**Remember ```IOnlineMediaLoader``` requires ```MediaDataSource``` which was added in API level 23 or Android M**</span></span>

<span data-ttu-id="97048-152">En même temps que l’élément multimédia, a également été incluse l’interface IOnlineMediaLoader qui permet aux développeurs de remplacer la [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) utilisée pour l’élément mediaPlayer sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="97048-152">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="97048-153">**(Nécessite Android M)**</span><span class="sxs-lookup"><span data-stu-id="97048-153">**(Requires android M)**</span></span>

<span data-ttu-id="97048-154">La première chose à faire est de créer une classe qui implémente IOnlineImageLoader :</span><span class="sxs-lookup"><span data-stu-id="97048-154">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

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

<span data-ttu-id="97048-155">Une fois que cette classe a été implémentée, vous pouvez inscrire votre classe OnlineMediaLoader en ajoutant :</span><span class="sxs-lookup"><span data-stu-id="97048-155">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
