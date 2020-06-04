---
title: HostConfig pour cartes adaptatives
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: d7fda209e6c470659d2fb2b66ac982e9c7183367
ms.sourcegitcommit: eb71aebe40a592649461e468a87993a10cbe6187
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84318199"
---
# <a name="what-is-hostconfig"></a>Qu’est-ce que HostConfig ?
`HostConfig` est un **objet de configuration partagé multiplateforme** qui spécifie comment un renderer de carte adaptative génère l’interface utilisateur.

Cela permet aux propriétés qui sont indépendantes de la plateforme d’être partagées par les renderers sur différents appareils et plateformes. Cela permet également de créer des outils qui vous donnent une idée de l’apparence de la carte pour un environnement donné.

Pour voir un aperçu de son contenu, consultez un exemple de fichier [HostConfig.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json).

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig) : options de niveau supérieur pour `AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig) : options pour les `Action`s
   * [`ContainerStylesConfig`](#schema-containerstylesconfig) : contrôle le style des conteneurs par défaut et d’accentuation
   * [`FactSetConfig`](#schema-factsetconfig) : contrôle l’affichage des `FactSet`s
   * [`FontSizesConfig`](#schema-fontsizesconfig) : contrôle les métriques de taille de police pour différents styles de texte
   * [`FontWeightsConfig`](#schema-fontweightsconfig) : contrôle les métriques d’épaisseur de police
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig) : contrôle diverses couleurs de police
   * [`ImageSetConfig`](#schema-imagesetconfig) : contrôle le mode d’affichage des `ImageSet`s
   * [`ImageSizesConfig`](#schema-imagesizesconfig) : contrôle les tailles des objets `Image`
   * [`MediaConfig`](#schema-mediaconfig) : contrôle l’affichage et le comportement des éléments `Media`
   * [`SeparatorConfig`](#schema-separatorconfig) : contrôle l’affichage des séparateurs
   * [`ShowCardConfig`](#schema-showcardconfig) : contrôle le comportement et le style de `Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig) : contrôle la disposition des éléments
   * [`TextBlockConfig`](#schema-textblockconfig) : paramètres contrôlant l’affichage du texte

## <a name="card-configuration"></a>Configuration de carte

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

Options de niveau supérieur pour `AdaptiveCards`

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| Non, valeur par défaut : `true`|Contrôle si le style personnalisé est autorisé|1.0
|**supportsInteractivity**|`boolean`| Non, valeur par défaut : `true`|Contrôle si l’appel des `Action`s interactives est autorisé|1.0
|**imageBaseUrl**|`string`| Non|URL de base à utiliser lors du chargement des ressources|1.0
|**fontFamily**|`string`| Non, valeur par défaut : `"Calibri"`|Type de police à utiliser lors du rendu du texte|1.0
|**actions**|`object`| Non|Options pour les `Action`s|1.0
|**adaptiveCard**|`object`| Non|Options de niveau supérieur pour `AdaptiveCards`|1.0
|**containerStyles**|`object`| Non|Contrôle le style des conteneurs par défaut et d’accentuation|1.0
|**imageSizes**|`object`| Non|Contrôle la tailles des objets `Image`|1.0
|**imageSet**|`object`| Non|Contrôle le mode d’affichage des `ImageSet`s|1.0
|**factSet**|`object`| Non|Contrôle l’affichage des `FactSet`s|1.0
|**fontSizes**|`object`| Non|Contrôle les métriques de taille de police pour différents styles de texte|1.0
|**fontWeights**|`object`| Non|Contrôle les métriques d’épaisseur de police|1.0
|**spacing**|`object`| Non|Contrôle la disposition des éléments|1.0
|**separator**|`object`| Non|Contrôle l’affichage des séparateurs|1.0
|**media**|`object`| Non|Contrôle l’affichage et le comportement des éléments `Media`|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

Options pour les `Action`s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| Non, valeur par défaut : `"horizontal"`|Contrôle la disposition des boutons|1.0
|**actionAlignment**|`string`| Non, valeur par défaut : `"stretch"`|Contrôle la disposition des boutons|1.0
|**buttonSpacing**|`integer`| Non, valeur par défaut : `10`|Contrôle la quantité d’espacement à utiliser entre les boutons|1.0
|**maxActions**|`integer`| Non, valeur par défaut : `5`|Contrôle le nombre d’actions autorisées au total|1.0
|**spacing**|`string`| Non, valeur par défaut : `"default"`|Contrôle l’espacement global de l’élément action|1.0
|**showCard**|`object`| Non|Contrôle le comportement et le style de `Action.ShowCard`|1.0
|**iconPlacement**|`string`| Non, valeur par défaut : `"aboveTitle"`|Contrôle où placer l’icône d’action|1.0
|**iconSize**|`integer`| Non, valeur par défaut : `30`|Contrôle la taille de l’icône d’action|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

Contrôle le style des conteneurs par défaut et d’accentuation

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Non|Style de conteneur par défaut|1.0
|**emphasis**|`object`| Non|Style de conteneur à utiliser pour l’accentuation|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

Contrôle l’affichage des `FactSet`s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**title**|`object`| Non, valeur par défaut : `{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|Paramètres contrôlant l’affichage du texte|1.0
|**value**|`object`| Non, valeur par défaut : `{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|Paramètres contrôlant l’affichage du texte|1.0
|**spacing**|`integer`| Non, valeur par défaut : `10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

Contrôle les métriques de taille de police pour différents styles de texte

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, valeur par défaut : `10`|Petite taille de police|1.0
|**default**|`integer`| Non, valeur par défaut : `12`|Taille de police par défaut|1.0
|**medium**|`integer`| Non, valeur par défaut : `14`|Taille de police moyenne|1.0
|**large**|`integer`| Non, valeur par défaut : `17`|Grande taille de police|1.0
|**extraLarge**|`integer`| Non, valeur par défaut : `20`|Très grande taille de police|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

Contrôle les métriques d’épaisseur de police

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| Non, valeur par défaut : `200`|&nbsp;|1.0
|**default**|`integer`| Non, valeur par défaut : `400`|&nbsp;|1.0
|**bolder**|`integer`| Non, valeur par défaut : `800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

Contrôle diverses couleurs de police

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Non, valeur par défaut : `{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| Non, valeur par défaut : `{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| Non, valeur par défaut : `{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| Non, valeur par défaut : `{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| Non, valeur par défaut : `{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| Non, valeur par défaut : `{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| Non, valeur par défaut : `{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

Contrôle le mode d’affichage des `ImageSet`s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| Non, valeur par défaut : `"auto"`|Contrôle le dimensionnement d’une image spécifique|1.0
|**maxImageHeight**|`integer`| Non, valeur par défaut : `100`|Contraint la hauteur de l’image à cette valeur|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

Contrôle la tailles des objets `Image`

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, valeur par défaut : `80`|Valeur de taille de petite image|1.0
|**medium**|`integer`| Non, valeur par défaut : `120`|Valeur de taille d’image moyenne|1.0
|**large**|`integer`| Non, valeur par défaut : `180`|Valeur de taille de grande image|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

Contrôle l’affichage et le comportement des éléments `Media`

#### <a name="introduced-in-version-11"></a>Introduit dans la version 1.1

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| Non|URI de l’image à afficher quand le bouton de lecture n’a pas été appelé|1.1
|**playButton**|`string`| Non|Image à afficher comme bouton de lecture|1.1
|**allowInlinePlayback**|`boolean`| Non, valeur par défaut : `true`|Indique s’il faut afficher le média inline ou l’appeler en externe|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

Contrôle l’affichage des séparateurs

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| Non, valeur par défaut : `1`|Épaisseur de la ligne de séparation|1.0
|**lineColor**|`string,null`| Non, valeur par défaut : `#B2000000`|Couleur à utiliser lors du dessin de la ligne de séparation|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

Contrôle le comportement et le style de `Action.ShowCard`

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| Non, valeur par défaut : `"inline"`|Contrôle l’affichage de la carte|1.0
|**style**|`object`| Non, valeur par défaut : `emphasis`|Contrôle le style d’un conteneur|1.0
|**inlineTopMargin**|`integer`| Non, valeur par défaut : `16`|Quantité de marge à utiliser lors de l’affichage de la carte|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

Contrôle la disposition des éléments

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, valeur par défaut : `3`|Valeur de faible espacement|1.0
|**default**|`integer`| Non, valeur par défaut : `8`|Valeur d’espacement par défaut|1.0
|**medium**|`integer`| Non, valeur par défaut : `20`|Valeur d’espacement moyen|1.0
|**large**|`integer`| Non, valeur par défaut : `30`|Valeur de grand espacement|1.0
|**extraLarge**|`integer`| Non, valeur par défaut : `40`|Valeur de très grand espacement|1.0
|**padding**|`integer`| Non, valeur par défaut : `20`|Valeur de remplissage|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

Paramètres contrôlant l’affichage du texte

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**size**|`string`| Non, valeur par défaut : `"default"`|Taille de police à utiliser quand une carte ne la spécifie pas|1.0
|**weight**|`string`| Non, valeur par défaut : `"normal"`|Épaisseur de police à utiliser quand une carte ne la spécifie pas|1.0
|**color**|`string`| Non, valeur par défaut : `"default"`|Couleur de police à utiliser quand une carte ne la spécifie pas|1.0
|**isSubtle**|`boolean`| Non, valeur par défaut : `false`|Indique si le texte doit être discret si une carte ne le spécifie pas|1.0
|**wrap**|`boolean`| Non, valeur par défaut : `true`|Indique si le texte doit être renvoyé à la ligne si une carte ne le spécifie pas|1.0
|**maxWidth**|`integer`| Non, valeur par défaut : `0`|Largeur maximale à utiliser si une carte ne la spécifie pas|1.0
