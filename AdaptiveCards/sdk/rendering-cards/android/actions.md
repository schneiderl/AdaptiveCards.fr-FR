---
title: Actions – Kit de développement logiciel (SDK) Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 680aab595123ce35654d760f0e1dbbe406c8f29d
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145519"
---
# <a name="actions---android"></a><span data-ttu-id="05c9f-102">Actions – Android</span><span class="sxs-lookup"><span data-stu-id="05c9f-102">Actions - Android</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05c9f-103">**Liste des modifications avec rupture**</span><span class="sxs-lookup"><span data-stu-id="05c9f-103">**List of Breaking changes**</span></span>
> 
> [<span data-ttu-id="05c9f-104">Modifications avec rupture dans v 1.1</span><span class="sxs-lookup"><span data-stu-id="05c9f-104">Breaking changes in v1.1</span></span>](#breaking-changes-in-v11)
> 

<span data-ttu-id="05c9f-105">Lorsqu’une action de cartes est exécutée, la classe qui a été passée à l’appel de rendu qui implémente l’interface ```ICardActionHandler``` est appelée.</span><span class="sxs-lookup"><span data-stu-id="05c9f-105">When a cards action is executed, the class that was passed to the render call that implements the ```ICardActionHandler``` interface gets invoked.</span></span> <span data-ttu-id="05c9f-106">Voici comment définir votre gestionnaire d’actions :</span><span class="sxs-lookup"><span data-stu-id="05c9f-106">Here is how to define your action handler:</span></span>

```java
public class ActionHandler implements ICardActionHandler
{
    @Override
    public void onAction(BaseActionElement actionElement, RenderedAdaptiveCard renderedCard)
    {
        ActionType actionType = actionElement.GetElementType();
        if (actionType == ActionType.Submit)
        {
            onSubmit(actionElement, renderedCard);
        }
        else if (actionType == ActionType.ShowCard)
        {
            onShowCard(actionElement);
        }
        else if (actionType == ActionType.OpenUrl)
        {
            onOpenUrl(actionElement);
        }
        else if (actionType == ActionType.Custom)
        {
            //Handle activation of custom actions
            ...
        }
    }

    private void onSubmit(BaseActionElement actionElement, RenderedAdaptiveCard renderedAdaptiveCard)
    {
        SubmitAction submitAction = null;
        if (actionElement instanceof SubmitAction)
        {
            submitAction = (SubmitAction) actionElement;
        }
        else if ((submitAction = SubmitAction.dynamic_cast(actionElement)) == null)
        {
            throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
        }

        String data = submitAction.GetDataJson();
        Map<String, String> keyValueMap = renderedAdaptiveCard.getInputs();
        if (!data.isEmpty())
        {
            try
            {
                JSONObject object = new JSONObject(data);
                showToast("Submit data: " + object.toString() + "\nInput: " + keyValueMap.toString(), Toast.LENGTH_LONG);
            }
            catch (JSONException e)
            {
                showToast(e.toString(), Toast.LENGTH_LONG);
            }
        }
        else
        {
            showToast("Submit input: " + keyValueMap.toString(), Toast.LENGTH_LONG);
        }
    }

    private void onShowCard(BaseActionElement actionElement)
    {
        ShowCardAction showCardAction = null;
        if (actionElement instanceof ShowCardAction)
        {
            showCardAction = (ShowCardAction) actionElement;
        }
        else if ((showCardAction = ShowCardAction.dynamic_cast(actionElement)) == null)
        {
            throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
        }

        //Get the card from show card and create a view
        RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, showCardAction.GetCard(), cardActionHandler, hostConfig);

        ViewGroup viewGroup = (ViewGroup) renderedCard.getView();
        ...
    }

    private void onOpenUrl(BaseActionElement actionElement)
    {
        OpenUrlAction openUrlAction = null;
        if (actionElement instanceof ShowCardAction)
        {
            openUrlAction = (OpenUrlAction) actionElement;
        }
        else if ((openUrlAction = OpenUrlAction.dynamic_cast(actionElement)) == null)
        {
            throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
        }

        Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(openUrlAction.GetUrl()));
        this.startActivity(browserIntent);
    }
}
```

## <a name="breaking-changes-in-v11"></a><span data-ttu-id="05c9f-107">Modifications avec rupture dans v 1.1</span><span class="sxs-lookup"><span data-stu-id="05c9f-107">Breaking changes in v1.1</span></span>

<span data-ttu-id="05c9f-108">L’élément multimédia inclus dans cette version requiert que deux nouvelles méthodes soient implémentées par les classes qui implémentent ```ICardActionHandler```, ces méthodes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="05c9f-108">The media element included in this version requires two new methods to be implemented by the classes that implement ```ICardActionHandler```, these methods are:</span></span>

* <span data-ttu-id="05c9f-109">```onMediaPlay``` est appelée quand le bouton de lecture est enfoncé pour la première fois dans un élément multimédia</span><span class="sxs-lookup"><span data-stu-id="05c9f-109">```onMediaPlay``` is invoked when the play button is pressed for the first time in any media element</span></span>
* <span data-ttu-id="05c9f-110">```onMediaStop``` est appelé lorsque le support atteint son extrémité</span><span class="sxs-lookup"><span data-stu-id="05c9f-110">```onMediaStop``` is invoked when the media reaches it's end</span></span>

<span data-ttu-id="05c9f-111">Les signatures pour ces méthodes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="05c9f-111">The signatures for these methods are:</span></span>

```java
public void onMediaPlay(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
public void onMediaStop(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
```

<span data-ttu-id="05c9f-112">Et l’implémentation de ActionHandler de l’exemple précédent ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="05c9f-112">And the implementation for the ActionHandler from the previous example would now look similar to this:</span></span>

```java
public class ActionHandler implements ICardActionHandler
{
    @Override
    public void onAction(BaseActionElement actionElement, RenderedAdaptiveCard renderedCard)
    { }

    private void onSubmit(BaseActionElement actionElement, RenderedAdaptiveCard renderedAdaptiveCard) 
    { }

    private void onShowCard(BaseActionElement actionElement)
    { }

    private void onOpenUrl(BaseActionElement actionElement)
    { }

    @Override
    public void onMediaPlay(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
    {
        // Your logic here, i.e.
        showToast("Media started: " + mediaElement, Toast.LENGTH_LONG);
    }

    @Override
    public void onMediaStop(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
    {
        // Your logic here, i.e.
        showToast("Media ended playing: " + mediaElement, Toast.LENGTH_LONG);
    }
}
```
