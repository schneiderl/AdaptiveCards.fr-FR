---
title: Actions - Kit de développement logiciel .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 9e96fd0ce6322e79f8717d8132857233f62f66f1
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553131"
---
# <a name="actions---net-wpf"></a>Actions - .NET WPF

N’importe quel `actions` au sein de la carte s’affiche en tant que WPF `Button`s, mais il du à votre application à gérer que se passe-t-il quand un utilisateur appuie dessus. 

Le `RenderedAdaptiveCard` objet fournit une `OnAction` événement à cet effet.

```csharp
// Event handler fires when a user clicks an action within the card
renderedCard.OnAction += MyActionHandler;

private void MyActionHandler(RenderedAdaptiveCard sender, ActionEventArgs e)
{
    if (e.Action is AdaptiveOpenUrlAction openUrlAction)
    {
        Process.Start(openUrlAction.Url);
    }
    else if (e.Action is AdaptiveShowCardAction showCardAction)
    {
        // Action.ShowCard can be rendered inline automatically
        // ... but if you want to handle show card as a "popup", you handle this event
        if (_myHostConfig.Actions.ShowCard.ActionMode == ShowCardActionMode.Popup)
        {
            var dialog = new ShowCardWindow(showCardAction.Title, showCardAction, Resources);
            dialog.Owner = this;
            dialog.ShowDialog();
        }
    }
    else if (e.Action is AdaptiveSubmitAction submitAction)
    {
        var inputs = sender.UserInputs.AsJson();
        inputs.Merge(submitAction.Data);
        MessageBox.Show(this, JsonConvert.SerializeObject(inputs, Formatting.Indented), "SubmitAction");
    }
}
```