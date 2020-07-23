---
title: Outils de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: f26550a73610073000166357df5b70c1bd8ccdc8
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417592"
---
# <a name="tools-and-samples"></a>Outils et exemples

## <a name="card-designer"></a>Concepteur de cartes 

Vous avez besoin d’un outil pour concevoir vos cartes ? Ne cherchez pas plus loin. Sur [https://adaptivecards.io/designer](https://adaptivecards.io/designer), vous trouverez un concepteur de cartes adaptatives basé sur le navigateur.

[![capture d’écran du concepteur](media/tools/designer.jpg)](https://adaptivecards.io/designer)

### <a name="embed-the-designer-into-your-app"></a>Incorporer le concepteur dans votre application

Mais pourquoi y envoyer vos utilisateurs quand vous pouvez **incorporer le concepteur de cartes directement dans votre application web** à l’aide de notre bibliothèque JavaScript. 

Pour bien démarrer, consultez le [package adaptivecards-designer](https://npmjs.com/adaptivecards-designer).

## <a name="schema-validation"></a>Validation de schéma

La validation de schéma est un excellent moyen de simplifier la création d’outils.

Nous mettons à votre disposition un [fichier de schéma JSON](https://adaptivecards.io/schemas/1.2.0/adaptive-card.json) complet pour la modification et la validation des cartes adaptatives dans JSON. Notez que l’URL de schéma a une version spécifique. Les versions plus récentes des cartes adaptatives auront une URL correspondante.

Dans Visual Studio et Visual Studio Code, vous pouvez obtenir une fonctionnalité IntelliSense automatique en incluant une référence `$schema`.

![incorrect](media/tools/invalidjson1.png)

![complétion automatique](media/tools/autocomplete.png)

## <a name="example"></a>Exemple

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a>Extension Visual Studio Code

Nous avons créé une extension Visual Studio Code qui vous permet de visualiser la carte que vous modifiez en temps réel dans l’éditeur lui-même. 

![extension](media/tools/vscode-extension.png)

Pour l’installer, ouvrez la Place de marché des extensions et recherchez **Adaptive Card Viewer**.

![place de marché](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Utilisation

Quand vous modifiez un fichier .json avec une propriété `$schema` de carte adaptative, vous pouvez la voir à l’aide de `Ctrl+Shift+V A`.
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Options

Le paramètre Visual Studio Code suivant est disponible pour la visionneuse AdaptiveCards. Vous pouvez le définir dans les paramètres utilisateur ou dans les paramètres de l’espace de travail.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Exemple de visualiseur WPF

L’[exemple de projet de visualiseur WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser des cartes à l’aide de WPF/XAML sur un ordinateur Windows.  Un éditeur `hostconfig` est intégré pour modifier et voir les paramètres de configuration de l’hôte. Enregistrez ces paramètres au format JSON pour les utiliser dans le cadre du rendu de votre application.

![visualiseur WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>Exemple ImageRender WPF

L’[exemple de projet ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) convertit n’importe quelle carte au format PNG à partir de la ligne de commande à l’aide de WPF. 
