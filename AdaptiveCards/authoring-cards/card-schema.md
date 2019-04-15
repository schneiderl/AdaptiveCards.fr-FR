---
title: Schéma de la carte
author: paulcam206
ms.author: paulcam
ms.date: 09/18/2018
ms.topic: reference
ms.openlocfilehash: 76a21affcd26798acb52e2bcf1168121838ed00a
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553721"
---
# <a name="card-schema"></a>Schéma de la carte

Cartes
   * [`AdaptiveCard`](#schema-adaptivecard) -Élément racine dans une carte adaptative.

Éléments de carte
   * [`TextBlock`](#schema-textblock) -Affiche le texte, ce qui permet de contrôler les tailles de police, le poids et couleur.
   * [`Image`](#schema-image) -Affiche une image.
   * [`Media`](#schema-media) -Affiche un lecteur multimédia pour le contenu audio ou vidéo.
   * [`MediaSource`](#schema-mediasource) -Définit une source d’un élément multimédia

Conteneurs
   * [`Container`](#schema-container) -Conteneurs regroupent les éléments.
   * [`ColumnSet`](#schema-columnset) -Le jeu de colonnes divise une région en colonnes, ce qui permet des éléments rester assis côte à côte.
   * [`Column`](#schema-column) -Définit un conteneur qui fait partie d’un jeu de colonnes.
   * [`FactSet`](#schema-factset) -L’élément FactSet affiche une série de faits (autrement dit, les paires nom/valeur) dans une forme tabulaire.
   * [`Fact`](#schema-fact) -Décrit un fait dans un FactSet comme une paire clé/valeur.
   * [`ImageSet`](#schema-imageset) -Le ImageSet affiche une collection d’Images similaires à une galerie.

Actions
   * [`Action.OpenUrl`](#schema-action.openurl) -En cas d’appel, afficher l’url donnée soit en lançant dans un navigateur web externe ou un affichage in situ avec un navigateur web incorporé.
   * [`Action.Submit`](#schema-action.submit) -Rassemble les champs d’entrée, fusionne avec le champ de données facultatif et envoie un événement au client. Il incombe au client d’identifier le mode de traitement de ces données. Exemple : Avec des robots de BotFramework, le client envoie une activité par l’intermédiaire de messagerie au robot.
   * [`Action.ShowCard`](#schema-action.showcard) -Définit un AdaptiveCard qui est affichée à l’utilisateur lorsque l’utilisateur clique sur le bouton ou un lien.

Entrées
   * [`Input.Text`](#schema-input.text) -Permet un utilisateur d’entrer du texte.
   * [`Input.Number`](#schema-input.number) -Permet à un utilisateur à entrer un numéro.
   * [`Input.Date`](#schema-input.date) -Permet à un utilisateur choisir une date.
   * [`Input.Time`](#schema-input.time) -Autorise un utilisateur de sélectionner une heure.
   * [`Input.Toggle`](#schema-input.toggle) -Permet à un utilisateur le choix entre deux options.
   * [`Input.ChoiceSet`](#schema-input.choiceset) -Permet à un utilisateur à entrer un choix.
   * [`Input.Choice`](#schema-input.choice) -Décrit un choix pour une utilisation dans un ChoiceSet.

# <a name="cards"></a>Cartes

<a name="schema-adaptivecard"></a>
## <a name="adaptivecard"></a>AdaptiveCard

Élément racine dans une carte adaptative.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"AdaptiveCard"`|Oui|Doit être `"AdaptiveCard"`.|1.0
|**actions**|`Action[]`| Non|Les Actions à afficher dans la barre d’action de la carte.|1.0
|**body**|`array[]`| Non|Les éléments de la carte à afficher dans la région de la carte principale.|1.0
|**selectAction**|`object`| Non|Une Action qui sera appelée lorsque la carte est activé par un clic ou sélectionnée. `Action.ShowCard` n’est pas pris en charge.|1.0
|**version**|`string`|Oui|Version du schéma nécessitant cette carte. Si un client est **inférieure** que cette version, le `fallbackText` sera restitué.|1.0
|**fallbackText**|`string`| Non|Texte affiché lorsque le client ne prend en charge la version spécifiée (peut contenir le markdown).|1.0
|**backgroundImage**|`string`| Non|Une image à utiliser comme arrière-plan de la carte.|1.0
|**speak**|`string`| Non|Spécifie ce qui doit être prononcé pour cette carte entière. Il s’agit texte simple ou un fragment SSML.|1.0
|**lang**|`string`| Non|La langue ISO-639-1 de 2 lettres utilisée dans la carte. Utilisé pour localiser les fonctions de date/heure.|1.0


# <a name="card-elements"></a>Éléments de carte

<a name="schema-textblock"></a>
## <a name="textblock"></a>TextBlock

Affiche le texte, ce qui permet de contrôler les tailles de police, le poids et couleur.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**color**|`string`| Non|Contrôle la couleur des `TextBlock` éléments.|1.0
|**horizontalAlignment**|`string`| Non, par défaut : `"left"`|Contrôle la façon dont les éléments sont positionnés horizontalement au sein de leur conteneur.|1.0
|**isSubtle**|`boolean`| Non, par défaut : `false`|Si `true`, affiche le texte légèrement atténuez apparaissent moins importante.|1.0
|**maxLines**|`number`| Non|Spécifie le nombre maximal de lignes à afficher.|1.0
|**size**|`string`| Non|Contrôle la taille du texte.|1.0
|**text**|`string`|Oui|Texte à afficher.|1.0
|**type**|`"TextBlock"`|Oui|Doit être `"TextBlock"`.|1.0
|**weight**|`string`| Non|Contrôle le poids de `TextBlock` éléments.|1.0
|**wrap**|`boolean`| Non, par défaut : `false`|Si `true`, autoriser le texte à inclure dans un wrapper. Sinon, le texte est coupé.|1.0
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-image"></a>
## <a name="image"></a>Image

Affiche une image.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**altText**|`string`| Non|Texte de remplacement décrivant l’image.|1.0
|**horizontalAlignment**|`string`| Non, par défaut : `"left"`|Contrôle la façon dont les éléments sont positionnés horizontalement au sein de leur conteneur.|1.0
|**selectAction**|`object`| Non|Une Action qui sera appelé lorsque le `Image` est activé par un clic ou sélectionnée. `Action.ShowCard` n’est pas pris en charge.|1.0
|**size**|`string`| Non, par défaut : `"auto"`|Contrôle la taille approximative de l’image. Les dimensions physiques varie par hôte. Spécifiez `"auto"` pour la dimension de l’image true, ou `"stretch"` pour le forcer à remplir le conteneur.|1.0
|**style**|`string`| Non|Contrôles comment ce `Image` s’affiche.|1.0
|**type**|`"Image"`|Oui|Doit être `"Image"`.|1.0
|**url**|`string`|Oui|URL de l’image.|1.0
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-media"></a>
## <a name="media"></a>Support

Affiche un lecteur multimédia pour le contenu audio ou vidéo.

#### <a name="introduced-in-version-11"></a>Introduite dans la version 1.1

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Media"`|Oui|Doit être `"Media"`.|1.1
|**sources**|`object` `[]`| Non|Tableau de sources de médias pour tenter de lire.|1.1
|**poster**|`string`| Non|URL d’une image à afficher avant la lecture.|1.1
|**altText**|`string`| Non|Texte de remplacement décrivant le contenu audio ou vidéo.|1.1
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.1
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.1
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.1


<a name="schema-mediasource"></a>
## <a name="mediasource"></a>MediaSource

Définit une source d’un élément multimédia

#### <a name="introduced-in-version-11"></a>Introduite dans la version 1.1

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**mimeType**|`string`|Oui|Type de média associé MIME (par exemple, `"video/mp4"`).|1.1
|**url**|`string`|Oui|URL de média.|1.1


# <a name="containers"></a>Conteneurs

<a name="schema-container"></a>
## <a name="container"></a>Conteneur

Conteneurs de regroupent les éléments.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Container"`|Oui|Doit être `"Container"`.|1.0
|**items**|`array[]`|Oui|Les éléments de la carte pour afficher à l’intérieur de la `Container`.|1.0
|**selectAction**|`object`| Non|Une Action qui sera appelé lorsque le `Container` est activé par un clic ou sélectionnée. `Action.ShowCard` n’est pas pris en charge.|1.0
|**style**|`string`| Non|Indicateur de style pour `Container`.|1.0
|**verticalContentAlignment**|`string`| Non, par défaut : `"top"`|Définit comment le contenu doit être aligné verticalement au sein du conteneur.|1.1
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-columnset"></a>
## <a name="columnset"></a>ColumnSet

Jeu de colonnes divise une région en colonnes, ce qui permet des éléments rester assis côte à côte.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**columns**|`Column[]`| Non|Le tableau de `Columns` pour diviser la région dans.|1.0
|**selectAction**|`object`| Non|Une Action qui sera appelé lorsque le `ColumnSet` est activé par un clic ou sélectionnée. `Action.ShowCard` n’est pas pris en charge.|1.0
|**type**|`"ColumnSet"`|Oui|Doit être `"ColumnSet"`.|1.0
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-column"></a>
## <a name="column"></a>colonne

Définit un conteneur qui fait partie d’un jeu de colonnes.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**items**|`array[]`|Oui|Les éléments de carte à inclure dans le `Column`.|1.0
|**selectAction**|`object`| Non|Une Action qui sera appelé lorsque le `Column` est activé par un clic ou sélectionnée. `Action.ShowCard` n’est pas pris en charge.|1.0
|**style**|`string`| Non|Indicateur de style pour `Column`.|1.0
|**width**|`string,number`| Non|`"auto"`, `"stretch"`, ou un nombre qui représente la largeur relative de la colonne dans le groupe de colonnes.|1.0
|**type**|`"Column"`| Non|Doit être `"Column"`.|1.0
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-factset"></a>
## <a name="factset"></a>FactSet

L’élément FactSet affiche une série de faits (autrement dit, les paires nom/valeur) dans une forme tabulaire.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**facts**|`Fact[]`|Oui|Le tableau de `Fact`s.|1.0
|**type**|`"FactSet"`|Oui|Doit être `"FactSet"`.|1.0
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-fact"></a>
## <a name="fact"></a>Faits

Décrit un fait dans un FactSet comme une paire clé/valeur.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Fact"`| Non|&nbsp;|1.0
|**title**|`string`|Oui|Le titre du fait.|1.0
|**value**|`string`|Oui|La valeur du fait.|1.0


<a name="schema-imageset"></a>
## <a name="imageset"></a>ImageSet

Le ImageSet affiche une collection d’Images similaires à une galerie.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**images**|`Image[]`|Oui|Le tableau de `Image` éléments à afficher.|1.0
|**imageSize**|`string`| Non, par défaut : `"auto"`|Contrôle la taille approximative de l’image. Les dimensions physiques varie par hôte. Spécifiez `"auto"` pour la dimension de l’image true, ou `"stretch"` pour le forcer à remplir le conteneur.|1.0
|**type**|`"ImageSet"`|Oui|Doit être `"ImageSet"`.|1.0
|**id**|`string`| Non|Un identificateur unique associé à l’élément.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


# <a name="actions"></a>Actions

<a name="schema-action.openurl"></a>
## <a name="actionopenurl"></a>Action.OpenUrl

Lorsqu’elle est appelée, afficher l’url donnée soit en lançant dans un navigateur web externe ou un affichage in situ avec un navigateur web incorporé.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.OpenUrl"`|Oui|Doit être `"Action.OpenUrl"`.|1.0
|**title**|`string`|Oui|Étiquette de bouton ou un lien qui représente cette action.|1.0
|**iconUrl**|`string`| Non|Icône facultatif à afficher sur l’action conjointement avec le titre|1.1
|**url**|`string`|Oui|L’URL à ouvrir.|1.0


<a name="schema-action.submit"></a>
## <a name="actionsubmit"></a>Action.Submit

Rassemble les champs d’entrée, fusionne avec le champ de données facultatif et envoie un événement au client. Il incombe au client d’identifier le mode de traitement de ces données. Exemple : Avec des robots de BotFramework, le client envoie une activité par l’intermédiaire de messagerie au robot.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.Submit"`|Oui|Doit être `"Action.Submit"`.|1.0
|**title**|`string`|Oui|Étiquette de bouton ou un lien qui représente cette action.|1.0
|**iconUrl**|`string`| Non|Icône facultatif à afficher sur l’action conjointement avec le titre|1.1
|**data**|`string,object`| Non|Données initiales à combiner avec des champs d’entrée. Il s’agit essentiellement des propriétés « masquées ».|1.0


<a name="schema-action.showcard"></a>
## <a name="actionshowcard"></a>Action.ShowCard

Définit un AdaptiveCard qui est affichée à l’utilisateur lorsque l’utilisateur clique sur le bouton ou un lien.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Action.ShowCard"`|Oui|Doit être `"Action.ShowCard"`.|1.0
|**title**|`string`|Oui|Étiquette de bouton ou un lien qui représente cette action.|1.0
|**iconUrl**|`string`| Non|Icône facultatif à afficher sur l’action conjointement avec le titre|1.1
|**card**|`object`|Oui|Élément racine dans une carte adaptative.|1.0


# <a name="inputs"></a>Entrées

<a name="schema-input.text"></a>
## <a name="inputtext"></a>Input.Text

Permet à un utilisateur de saisir du texte.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Oui|Identificateur unique pour la valeur. Utilisé pour identifier l’entrée collectée lors de l’action d’envoi est effectuée.|1.0
|**isMultiline**|`boolean`| Non, par défaut : `false`|Si `true`, autoriser plusieurs lignes d’entrée.|1.0
|**maxLength**|`number`| Non|Indicateur de caractères de longueur maximale à collecter (peut être ignorée par certains clients).|1.0
|**placeholder**|`string`| Non|Description de l’entrée que vous le souhaitez. Affichée quand aucun texte n’a été entrée.|1.0
|**style**|`string`| Non, par défaut : `"text"`|Indicateur de style pour `Input.Text`.|1.0
|**type**|`"Input.Text"`|Oui|Doit être `"Input.Text"`.|1.0
|**value**|`string`| Non|La valeur initiale pour ce champ.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-input.number"></a>
## <a name="inputnumber"></a>Input.Number

Permet à un utilisateur à entrer un numéro.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Oui|Identificateur unique pour la valeur. Utilisé pour identifier l’entrée collectée lors de l’action d’envoi est effectuée.|1.0
|**max**|`number`| Non|Indicateur de valeur maximale (peut être ignorée par certains clients).|1.0
|**min**|`number`| Non|Indicateur de valeur minimale (peut être ignorée par certains clients).|1.0
|**placeholder**|`string`| Non|Description de l’entrée que vous le souhaitez. Affichée quand aucune sélection n’a été effectuée.|1.0
|**type**|`"Input.Number"`|Oui|Doit être `"Input.Number"`.|1.0
|**value**|`number`| Non|Valeur initiale pour ce champ.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-input.date"></a>
## <a name="inputdate"></a>Input.Date

Permet à un utilisateur de choisir une date.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Oui|Identificateur unique pour la valeur. Utilisé pour identifier l’entrée collectée lors de l’action d’envoi est effectuée.|1.0
|**max**|`string`| Non|Indicateur de valeur maximale exprimée au format ISO 8601 (peut être ignorée par certains clients).|1.0
|**min**|`string`| Non|Indicateur de valeur minimale exprimée au format ISO 8601 (peut être ignorée par certains clients).|1.0
|**placeholder**|`string`| Non|Description de l’entrée que vous le souhaitez. Affichée quand aucune sélection n’a été effectuée.|1.0
|**type**|`"Input.Date"`|Oui|Doit être `"Input.Date"`.|1.0
|**value**|`string`| Non|La valeur initiale pour ce champ exprimée au format ISO 8601.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-input.time"></a>
## <a name="inputtime"></a>Input.Time

Permet à un utilisateur de sélectionner une heure.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Oui|Identificateur unique pour la valeur. Utilisé pour identifier l’entrée collectée lors de l’action d’envoi est effectuée.|1.0
|**max**|`string`| Non|Indicateur de valeur maximale (peut être ignorée par certains clients).|1.0
|**min**|`string`| Non|Indicateur de valeur minimale (peut être ignorée par certains clients).|1.0
|**placeholder**|`string`| Non|Description de l’entrée que vous le souhaitez. Affichée quand aucun temps n’a été sélectionné.|1.0
|**type**|`"Input.Time"`|Oui|Doit être `"Input.Time"`.|1.0
|**value**|`string`| Non|La valeur initiale pour ce champ exprimée au format ISO 8601.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-input.toggle"></a>
## <a name="inputtoggle"></a>Input.Toggle

Permet à un utilisateur de choisir entre deux options.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**id**|`string`|Oui|Identificateur unique pour la valeur. Utilisé pour identifier l’entrée collectée lors de l’action d’envoi est effectuée.|1.0
|**title**|`string`|Oui|Titre pour le bouton bascule|1.0
|**type**|`"Input.Toggle"`|Oui|Input.Toggle|1.0
|**value**|`string`| Non, par défaut : `"false"`|La valeur sélectionnée en cours. Si l’élément est sélectionné, que « valueOn » sera utilisé, sinon « valueOff »|1.0
|**valueOff**|`string`| Non, par défaut : `"false"`|La valeur lorsque le bouton bascule est désactivé|1.0
|**valueOn**|`string`| Non, par défaut : `"true"`|La valeur lorsque le bouton bascule est activé|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-input.choiceset"></a>
## <a name="inputchoiceset"></a>Input.ChoiceSet

Permet à un utilisateur à entrer un choix.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**choices**|`Input.Choice[]`|Oui|`Choice` Options.|1.0
|**id**|`string`|Oui|Identificateur unique pour la valeur. Utilisé pour identifier l’entrée collectée lors de l’action d’envoi est effectuée.|1.0
|**isMultiSelect**|`boolean`| Non, par défaut : `false`|Autoriser plusieurs options à sélectionner.|1.0
|**style**|`string`| Non, par défaut : `"compact"`|Indicateur de style pour `Input.ChoiceSet`.|1.0
|**type**|`"Input.ChoiceSet"`|Oui|Doit être `"Input.ChoiceInput"`.|1.0
|**value**|`string`| Non|Le choix initial (ou un ensemble de choix) qui doit être sélectionné. Pour une sélection multiple, spécifiez une chaîne séparée par des virgules de valeurs.|1.0
|**spacing**|`string`| Non|Contrôle la quantité d’espace entre cet élément et l’élément qui précède.|1.0
|**separator**|`boolean`| Non, par défaut : `false`|Lorsque `true`, dessinez une ligne de séparation en haut de l’élément.|1.0


<a name="schema-input.choice"></a>
## <a name="inputchoice"></a>Input.Choice

Décrit un choix pour une utilisation dans un ChoiceSet.

|Propriété|Type|Obligatoire|Description|Version|
|--------|----|--------|-----------|-------|
|**type**|`"Input.Choice"`| Non|&nbsp;|1.0
|**title**|`string`|Oui|Texte à afficher.|1.0
|**value**|`string`|Oui|La valeur brute pour le choix. **Remarque :** n’utilisez pas un `,` dans la valeur, dans la mesure où un `ChoiceSet` avec `isMultiSelect` la valeur `true` retourne une chaîne délimitée par des virgules des valeurs de choix.|1.0
