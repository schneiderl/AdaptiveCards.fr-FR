---
title: Outils des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 35ce89653a6cf2a313518be0f221a166e1eb7711
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552501"
---
# <a name="card-designer"></a>Concepteur de carte 

Vous avez besoin d’un outil concevoir vos cartes ? Ne cherchez plus que le concepteur basée sur navigateur de carte adaptative à [https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![capture d’écran de concepteur](media/tools/designer.jpg)](https://adaptivecards.io/designer)

## <a name="embed-the-designer-into-your-app"></a>Incorporer le concepteur dans votre application

Mais pourquoi diriger vos utilisateurs il dès que possible **incorporer le Concepteur de carte directement dans votre site web** application à l’aide de notre bibliothèque JavaScript. 

Découvrez le [adaptivecards-concepteur](https://npmjs.com/adaptivecards-designer) package pour commencer.

# <a name="schema-validation"></a>Validation de schéma

Validation de schéma constitue un moyen efficace de faire plus simple de création et l’activation des outils.

## <a name="json-schema"></a>JSON Schema
Nous avons fourni un complète [fichier de schéma JSON](http://adaptivecards.io/schemas/adaptive-card.json) pour l’édition et la validation des cartes adaptatives dans json.

Dans Visual Studio et Visual Studio Code, vous pouvez obtenir Intellisense automatique en incluant un `$schema` référence.

![bad](media/tools/invalidjson1.png)

![Saisie semi-automatique](media/tools/autocomplete.png)

### <a name="example"></a>Exemple

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "0.5",
    "body": []
}
```

# <a name="tools-and-samples"></a>Outils et exemples
Il existe certains outils et des exemples dans l’arborescence source qui sont des références utiles, ainsi que des outils utiles.

## <a name="visual-studio-code-extension"></a>Extension de Visual Studio Code
Nous avons créé une extension de code de Visual Studio qui vous permet de visualiser la carte que vous modifiez en temps réel à l’intérieur de l’éditeur lui-même. 

![extension](media/tools/vscode-extension.png)

Pour installer, ouvrez Extensions Marketplace et recherchez **ADAPTATIF visionneuse carte**.

![marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Utilisation

Lorsque vous modifiez un fichier .json avec une carte adaptative `$schema` propriété que vous pouvez afficher à l’aide de `Ctrl+Shift+V A`.
```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Options

Le paramètre de Visual Studio Code suivant est disponible pour la visionneuse AdaptiveCards. Cela peut être défini dans les paramètres de l’utilisateur ou de paramètres de l’espace de travail.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Visualiseur WPF, exemple
Le [exemple de projet WPF visualiseur](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser les cartes à l’aide de WPF/Xaml sur un ordinateur Windows.  Un `hostconfig` éditeur est intégré pour la modification et l’affichage des paramètres de configuration d’hôte. Enregistrer ces paramètres en tant que JSON pour les utiliser dans un rendu dans votre application.

![visualiseur WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>WPF, exemple ImageRender
Le [ImageRender exemple de projet](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) transforme n’importe quelle carte en un fichier PNG à partir de la ligne de commande à l’aide de WPF. 