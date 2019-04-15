---
title: HostConfig pour des cartes adaptatives
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 46ba9987cf162e95ab86dcdafa55e10df29b1121
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552591"
---
# <a name="what-is-hostconfig"></a>Qu’est HostConfig ?
`HostConfig` est un **objet inter-plateformes configuration** qui spécifie comment un convertisseur de carte adaptative génère une interface utilisateur.

Ainsi, les propriétés qui sont indépendante de la plateforme à partager entre les convertisseurs sur différentes plateformes et appareils. Il permet également à créer des outils qui vous donne une idée de l’apparence que la carte aurait pour un environnement donné.

Voir un exemple [HostConfig.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) pour obtenir un sentiment pour son contenu.

---

   * [`AdaptiveCardConfig`](#schema-adaptivecardconfig) -Options Toplevel pour `AdaptiveCards`
   * [`ActionsConfig`](#schema-actionsconfig) -Options pour `Action`s
   * [`ContainerStylesConfig`](#schema-containerstylesconfig) -Application d’un style par défaut et une accentuation conteneurs de contrôles
   * [`FactSetConfig`](#schema-factsetconfig) -Contrôle l’affichage de `FactSet`s
   * [`FontSizesConfig`](#schema-fontsizesconfig) : Contrôle les métriques de taille de police pour les styles de texte différente
   * [`FontWeightsConfig`](#schema-fontweightsconfig) : Contrôle les métriques d’épaisseur de police
   * [`ForegroundColorsConfig`](#schema-foregroundcolorsconfig) : Contrôle de différentes couleurs de police
   * [`ImageSetConfig`](#schema-imagesetconfig) : Contrôle la façon dont `ImageSet`s sont affichés.
   * [`ImageSizesConfig`](#schema-imagesizesconfig) : Contrôle `Image` tailles
   * [`MediaConfig`](#schema-mediaconfig) : Contrôle l’affichage et le comportement de `Media` éléments
   * [`SeparatorConfig`](#schema-separatorconfig) : Contrôle l’affichent des séparateurs
   * [`ShowCardConfig`](#schema-showcardconfig) : Contrôle le comportement et les styles de `Action.ShowCard`
   * [`SpacingsConfig`](#schema-spacingsconfig) : Contrôle la façon dont les éléments doivent être disposé
   * [`TextBlockConfig`](#schema-textblockconfig) -Paramètres de contrôle de l’affichage de texte

# <a name="card-configuration"></a>Configuration de la carte

<a name="schema-adaptivecardconfig"></a>
## <a name="adaptivecardconfig"></a>AdaptiveCardConfig

Options de niveau supérieur pour `AdaptiveCards`

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**allowCustomStyle**|`boolean`| Non, par défaut : `true`|Détermine si l’application d’un style personnalisée est autorisée|1.0
|**supportsInteractivity**|`boolean`| Non, par défaut : `true`|Contrôler si interactive `Action`sont autorisés à être appeler|1.0
|**imageBaseUrl**|`string`| Non|URL de base à utiliser lors du chargement des ressources|1.0
|**fontFamily**|`string`| Non, par défaut : `"Calibri"`|Type de police à utiliser lors du rendu de texte|1.0
|**actions**|`object`| Non|Options pour `Action`s|1.0
|**adaptiveCard**|`object`| Non|Options de niveau supérieur pour `AdaptiveCards`|1.0
|**containerStyles**|`object`| Non|Application d’un style par défaut et une accentuation conteneurs de contrôles|1.0
|**imageSizes**|`object`| Non|Contrôles `Image` tailles|1.0
|**imageSet**|`object`| Non|Contrôles comment `ImageSet`s sont affichés.|1.0
|**factSet**|`object`| Non|Contrôle l’affichage de `FactSet`s|1.0
|**fontSizes**|`object`| Non|Métriques de taille de police de contrôles pour les styles de texte différente|1.0
|**fontWeights**|`object`| Non|Mesures de poids de police de contrôles|1.0
|**spacing**|`object`| Non|Contrôle la façon dont les éléments doivent être disposé|1.0
|**separator**|`object`| Non|Contrôle l’affichent des séparateurs|1.0
|**Média**|`object`| Non|Contrôle l’affichage et le comportement de `Media` éléments|1.1


<a name="schema-actionsconfig"></a>
## <a name="actionsconfig"></a>ActionsConfig

Options pour `Action`s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**actionsOrientation**|`string`| Non, par défaut : `"horizontal"`|Contrôle la disposition des boutons|1.0
|**actionAlignment**|`string`| Non, par défaut : `"stretch"`|Disposition des contrôles de boutons|1.0
|**buttonSpacing**|`integer`| Non, par défaut : `10`|Contrôle la quantité espacement à utiliser entre les boutons|1.0
|**maxActions**|`integer`| Non, par défaut : `5`|Détermine combien de valeurs autorisées au total|1.0
|**spacing**|`string`| Non, par défaut : `"default"`|Contrôles espacement globale de l’élément d’action|1.0
|**showCard**|`object`| Non|Comportement des contrôles et styles de `Action.ShowCard`|1.0
|**iconPlacement**|`string`| Non, par défaut : `"aboveTitle"`|Contrôle où placer l’icône d’action|1.0
|**iconSize**|`integer`| Non, par défaut : `30`|Taille des contrôles de l’icône d’action|1.0


<a name="schema-containerstylesconfig"></a>
## <a name="containerstylesconfig"></a>ContainerStylesConfig

Application d’un style par défaut et une accentuation conteneurs de contrôles

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Non|Style de conteneur par défaut|1.0
|**emphasis**|`object`| Non|Style de conteneur à utiliser pour mettre en évidence|1.0


<a name="schema-factsetconfig"></a>
## <a name="factsetconfig"></a>FactSetConfig

Contrôle l’affichage de `FactSet`s

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**title**|`object`| Non, par défaut : `{"weight":"bolder","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":150}`|Paramètres de contrôle de l’affichage de texte|1.0
|**value**|`object`| Non, par défaut : `{"weight":"default","size":"default","color":"default","isSubtle":false,"wrap":true,"maxWidth":0}`|Paramètres de contrôle de l’affichage de texte|1.0
|**spacing**|`integer`| Non, par défaut : `10`|&nbsp;|1.0


<a name="schema-fontsizesconfig"></a>
## <a name="fontsizesconfig"></a>FontSizesConfig

Métriques de taille de police de contrôles pour les styles de texte différente

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, par défaut : `10`|Petite taille de police|1.0
|**default**|`integer`| Non, par défaut : `12`|Taille de police par défaut|1.0
|**medium**|`integer`| Non, par défaut : `14`|Taille de police moyenne|1.0
|**large**|`integer`| Non, par défaut : `17`|Taille de grande taille de police|1.0
|**extraLarge**|`integer`| Non, par défaut : `20`|Taille de police de très grande taille|1.0


<a name="schema-fontweightsconfig"></a>
## <a name="fontweightsconfig"></a>FontWeightsConfig

Mesures de poids de police de contrôles

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**lighter**|`integer`| Non, par défaut : `200`|&nbsp;|1.0
|**default**|`integer`| Non, par défaut : `400`|&nbsp;|1.0
|**bolder**|`integer`| Non, par défaut : `800`|&nbsp;|1.0


<a name="schema-foregroundcolorsconfig"></a>
## <a name="foregroundcolorsconfig"></a>ForegroundColorsConfig

Contrôle de différentes couleurs de police

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**default**|`object`| Non, par défaut : `{"default":"#FF000000","subtle":"#B2000000"}`|&nbsp;|1.0
|**accent**|`object`| Non, par défaut : `{"default":"#FF0000FF","subtle":"#B20000FF"}`|&nbsp;|1.0
|**dark**|`object`| Non, par défaut : `{"default":"#FF101010","subtle":"#B2101010"}`|&nbsp;|1.0
|**light**|`object`| Non, par défaut : `{"default":"#FFFFFFFF","subtle":"#B2FFFFFF"}`|&nbsp;|1.0
|**good**|`object`| Non, par défaut : `{"default":"#FF008000","subtle":"#B2008000"}`|&nbsp;|1.0
|**warning**|`object`| Non, par défaut : `{"default":"#FFFFD700","subtle":"#B2FFD700"}`|&nbsp;|1.0
|**attention**|`object`| Non, par défaut : `{"default":"#FF8B0000","subtle":"#B28B0000"}`|&nbsp;|1.0


<a name="schema-imagesetconfig"></a>
## <a name="imagesetconfig"></a>ImageSetConfig

Contrôles comment `ImageSet`s sont affichés.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**imageSize**|`string`| Non, par défaut : `"auto"`|Dimensionnement des images individuelles de contrôles|1.0
|**maxImageHeight**|`integer`| Non, par défaut : `100`|Limiter la hauteur de l’image à cette valeur|1.0


<a name="schema-imagesizesconfig"></a>
## <a name="imagesizesconfig"></a>ImageSizesConfig

Contrôles `Image` tailles

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, par défaut : `80`|Valeur de taille petite image|1.0
|**medium**|`integer`| Non, par défaut : `120`|Valeur de taille moyenne d’image|1.0
|**large**|`integer`| Non, par défaut : `180`|Valeur de taille d’image de grande taille|1.0


<a name="schema-mediaconfig"></a>
## <a name="mediaconfig"></a>MediaConfig

Contrôle l’affichage et le comportement de `Media` éléments

#### <a name="introduced-in-version-11"></a>Introduite dans la version 1.1

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**defaultPoster**|`string`| Non|URI d’image à afficher lorsque le bouton de lecture n’a pas été appelée.|1.1
|**playButton**|`string`| Non|Image à afficher comme bouton lecture|1.1
|**allowInlinePlayback**|`boolean`| Non, par défaut : `true`|S’il faut s’affichent en ligne du support ou appeler en externe|1.1


<a name="schema-separatorconfig"></a>
## <a name="separatorconfig"></a>SeparatorConfig

Contrôle l’affichent des séparateurs

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**lineThickness**|`integer`| Non, par défaut : `1`|Épaisseur de ligne de séparation|1.0
|**lineColor**|`string,null`| Non, par défaut : `#B2000000`|Couleur à utiliser lors du dessin de ligne de séparation|1.0


<a name="schema-showcardconfig"></a>
## <a name="showcardconfig"></a>ShowCardConfig

Comportement des contrôles et styles de `Action.ShowCard`

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**actionMode**|`string`| Non, par défaut : `"inline"`|Contrôle l’affichage de la carte|1.0
|**style**|`object`| Non, par défaut : `emphasis`|Style des contrôles d’un conteneur|1.0
|**inlineTopMargin**|`integer`| Non, par défaut : `16`|Taille de marge à utiliser lors de l’affichage de la carte|1.0


<a name="schema-spacingsconfig"></a>
## <a name="spacingsconfig"></a>SpacingsConfig

Contrôle la façon dont les éléments doivent être disposé

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**small**|`integer`| Non, par défaut : `3`|Valeur d’interligne petite|1.0
|**default**|`integer`| Non, par défaut : `8`|Valeur de l’espacement par défaut|1.0
|**medium**|`integer`| Non, par défaut : `20`|Valeur de l’espacement de taille moyenne|1.0
|**large**|`integer`| Non, par défaut : `30`|Valeur d’interligne volumineux|1.0
|**extraLarge**|`integer`| Non, par défaut : `40`|Valeur de l’espacement de très grande taille|1.0
|**padding**|`integer`| Non, par défaut : `20`|La valeur de remplissage|1.0


<a name="schema-textblockconfig"></a>
## <a name="textblockconfig"></a>TextBlockConfig

Paramètres de contrôle de l’affichage de texte

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**size**|`string`| Non, par défaut : `"default"`|Taille de police à utiliser lors de la ne spécifie pas une carte|1.0
|**weight**|`string`| Non, par défaut : `"normal"`|Épaisseur de police à utiliser lors d’une carte ne spécifie pas|1.0
|**color**|`string`| Non, par défaut : `"default"`|Couleur de police à utiliser lorsque ne spécifie pas une carte|1.0
|**isSubtle**|`boolean`| Non, par défaut : `false`|Texte doit être délicat si ne spécifie pas une carte|1.0
|**wrap**|`boolean`| Non, par défaut : `true`|Texte doit habiller si ne spécifie pas une carte|1.0
|**maxWidth**|`integer`| Non, par défaut : `0`|Largeur maximale à utiliser si vous ne spécifie pas une carte|1.0
