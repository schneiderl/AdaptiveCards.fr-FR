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
# <a name="extensibility---android"></a>Extensibilité - Android

## <a name="custom-parsing-of-card-elements"></a>L’analyse personnalisée des éléments de la carte

Vous pouvez étendre l’analyseur pour les éléments de carte de prise en charge que vous avez définies. Par exemple, supposons que nous avons un nouveau type d’élément qui ressemble à ceci :
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

Ensuite, les lignes suivantes montrent comment analyser dans un CardElement qui s’étend de la BaseCardElement :
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

Et Voici comment inscrire l’analyseur et obtenir un objet AdaptiveCard qui contient l’élément personnalisé :
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Vient ensuite le rendu de l’élément personnalisé

## <a name="custom-rendering-of-card-elements"></a>Rendu personnalisé d’éléments de la carte

Pour définir notre propre convertisseur personnalisé pour notre type, nous devons tout d’abord créer une classe qui s’étend de BaseCardElementParser :
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

Nous enregistrons ensuite ce convertisseur comme suit :
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

