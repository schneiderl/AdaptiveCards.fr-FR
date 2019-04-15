---
title: Kit de développement logiciel Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 735f0f8ed1f0d3fdc78f1c840a7aba1892faa5d4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553361"
---
# <a name="extensibility---android"></a><span data-ttu-id="50fa0-102">Extensibilité - Android</span><span class="sxs-lookup"><span data-stu-id="50fa0-102">Extensibility - Android</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="50fa0-103">L’analyse personnalisée des éléments de la carte</span><span class="sxs-lookup"><span data-stu-id="50fa0-103">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="50fa0-104">Vous pouvez étendre l’analyseur pour les éléments de carte de prise en charge que vous avez définies.</span><span class="sxs-lookup"><span data-stu-id="50fa0-104">You may extend the parser to suport card elements that you have defined.</span></span> <span data-ttu-id="50fa0-105">Par exemple, supposons que nous avons un nouveau type d’élément qui ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="50fa0-105">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="50fa0-106">Ensuite, les lignes suivantes montrent comment analyser dans un CardElement qui s’étend de la BaseCardElement :</span><span class="sxs-lookup"><span data-stu-id="50fa0-106">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="50fa0-107">Et Voici comment inscrire l’analyseur et obtenir un objet AdaptiveCard qui contient l’élément personnalisé :</span><span class="sxs-lookup"><span data-stu-id="50fa0-107">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="50fa0-108">Vient ensuite le rendu de l’élément personnalisé</span><span class="sxs-lookup"><span data-stu-id="50fa0-108">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="50fa0-109">Rendu personnalisé d’éléments de la carte</span><span class="sxs-lookup"><span data-stu-id="50fa0-109">Custom Rendering of Card Elements</span></span>

<span data-ttu-id="50fa0-110">Pour définir notre propre convertisseur personnalisé pour notre type, nous devons tout d’abord créer une classe qui s’étend de BaseCardElementParser :</span><span class="sxs-lookup"><span data-stu-id="50fa0-110">To define our own custom renderer for our type, we must first create a class that extends from BaseCardElementParser:</span></span>
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instace we returned at parse. We can then cast that object to our type
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

<span data-ttu-id="50fa0-111">Nous enregistrons ensuite ce convertisseur comme suit :</span><span class="sxs-lookup"><span data-stu-id="50fa0-111">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

