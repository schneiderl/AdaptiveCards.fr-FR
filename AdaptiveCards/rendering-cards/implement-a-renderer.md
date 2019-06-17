---
title: Implémentation d’un Renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: b39493f82f3378e5a554abc6df890d6821869671
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138022"
---
# <a name="adaptive-card-renderer-specification"></a>Spécification de convertisseur de carte adaptative

La spécification suivante décrit comment implémenter un convertisseur de carte adaptative sur n’importe quelle plateforme de l’interface utilisateur.

> [!IMPORTANT]
> 
> Ce contenu n’est pas encore terminé. Revenez plus tard.

## <a name="sdk-versioning"></a>Kit de développement logiciel de contrôle de version

1. La version majeure et mineure de kit de développement logiciel **SHOULD** correspond à la `schema` version. 
1. Correctif/build **SHOULD** être utilisé pour les mises à jour de convertisseur qui n’ont pas les modifications de schéma.

## <a name="parsing-json"></a>L’analyse JSON

### <a name="error-conditions"></a>Conditions d’erreur
1. Un analyseur **doit** vérifier qu’il s’agit d’un contenu JSON valid
1. Un analyseur **doit** valider par rapport au schéma (propriétés requises, etc.)
1. Les erreurs ci-dessus **doit** être signalées à l’application hôte (exception ou équivalent)

### <a name="unknown-types"></a>Types inconnus
1. Si vous rencontrez des types « inconnus » ils **doivent être supprimés** à partir du résultat
1. Toutes les modifications de la charge utile (comme ci-dessus) **SHOULD** soient signalés comme avertissements à l’application hôte

### <a name="unknown-properties"></a>Propriétés inconnues
1. Un analyseur **doit** incluent **supplémentaires** propriétés sur les éléments

### <a name="additional-considerations"></a>Considérations supplémentaires
1. Le `speak` propriété peut contenir un balisage SSML et **doit** être renvoyé à l’application de l’hôte spécifié en tant que

## <a name="parsing-host-config"></a>L’analyse de configuration de l’hôte
1. TODO

## <a name="versioning"></a>Contrôle de version

1. Un convertisseur **doit** implémenter une version particulière du schéma. 
1. Le `AdaptiveCard` constructeur **doit** donner le `version` propriété une valeur par défaut en fonction de la version actuelle du schéma 
1. Si un convertisseur rencontre un `version` propriété dans le `AdaptiveCard` qui est supérieure à la version prise en charge, il **doit** retourner le `fallbackText` à la place.

## <a name="rendering"></a>Rendu

Un `AdaptiveCard` se compose d’un `body` et `actions`. Le `body` est une collection de `CardElement`s qui sera un convertisseur d’énumérer et de restituer dans l’ordre. 

1. Chaque élément **doit** stretch de la largeur de son parent (pensez `display: block` au format HTML).
1. Un convertisseur **doit** ignorer les types d’élément inconnu et continuer le reste de la charge utile de rendu.

### <a name="spacing-and-separators"></a>L’espacement et les séparateurs

1. Le `spacing` propriété sur chaque élément a un impact sur la quantité d’espace entre le **actuel** élément et celui **BEFORE** il.
1. Espacement **doit uniquement** s’appliquent lorsqu’il est en fait un élément qui précède. (Par exemple, ne s’appliquent pas au premier élément dans un tableau)
1. Un convertisseur **doit** rechercher la quantité d’espace à utiliser à partir de la `hostConfig` espacement pour la valeur enum appliquée à l’élément actuel.
1. Si l’élément a un `separator` valeur `true`, puis une ligne visible **doit** être tracée entre l’élément actuel et celle qui précède.
1. La ligne de séparation **doit** être dessiné en utilisant le `container.style.default.foregroundColor`.
1. Un séparateur **doit uniquement** être dessiné Si l’élément **IS NOT** le premier dans le tableau.

### <a name="columns"></a>Colonnes

1. `Column` `width` **DOIT** être interprétées par « auto », « stretch » ou un ratio pondéré.

### <a name="textblock"></a>TextBlock

1. Un TextBlock **doit** occupe une seule ligne, sauf si le `wrap` propriété est `true`. 
1. Le bloc de texte **SHOULD** trim n’importe quel texte excessive des points de suspension (...)

#### <a name="markdown"></a>Markdown

1. Des cartes adaptatives autorisant pour un sous-ensemble de Markdown et **SHOULD** pris en charge dans `TextBlock`. 
1. Consultez complète [les exigences de markdown](../authoring-cards/text-features.md)

#### <a name="formatting-functions"></a>Fonctions de mise en forme

1. `TextBlock` permet de [mise en forme de fonctions DATE/heure](../authoring-cards/text-features.md) qui **doit** pris en charge par chaque convertisseur.
1. **DOIT de tous les échecs de** afficher la chaîne brute dans la carte. Aucun message convivial tentée. (En cours pour que le développeur soit conscient immédiatement il vise un problème)

1. TODO : Inclure des expressions régulières

### <a name="images"></a>Images

1. Un convertisseur **SHOULD** permettent d’héberger des applications de savoir lorsque toutes les images HTTP ont été téléchargées et la carte est « entièrement restituée »
1. Un convertisseur **doit** inspecter la configuration de l’hôte `maxImageSize` param lors du téléchargement des images HTTP
1. Un convertisseur **doit** prennent en charge `.png` et `.jpeg`
1. Un convertisseur **SHOULD** prennent en charge `.gif` images

### <a name="host-config"></a>Configuration de l’hôte

* TODO : Que doivent contenir les valeurs par défaut ? Doivent tous partager ? Devons-nous incorporer un fichier hostConfig.json commun dans les fichiers binaires ?
* TODO : Je pense que HostConfig a besoin de gérer les versions ainsi qu’à l’analyse ?

[`HostConfig`](host-config.md) est un objet de configuration partagée qui spécifie comment un convertisseur de carte adaptative génère l’interface utilisateur.  

Ainsi, les propriétés qui sont indépendante de la plateforme à partager entre les convertisseurs sur différentes plateformes et appareils. Il permet également à créer des outils qui vous donne une idée de l’apparence que la carte aurait pour un environnement donné.

1. Convertisseurs **doit** exposer un **configuration de l’hôte** paramètre pour héberger des applications
1. Tous les éléments **doit** un style en fonction de leurs paramètres respectifs de la configuration de l’hôte

### <a name="native-platform-styling"></a>Style de la plateforme native

1. Chaque type d’élément **SHOULD** attacher un style de la plateforme native avec l’élément d’interface généré. Par exemple, au format HTML, nous avons ajouté une classe CSS pour les types d’élément, et dans XAML, nous attribuons un Style spécifique.

## <a name="extensibility"></a>Extensibilité 

1. Un convertisseur **doit** permettent d’héberger des applications remplacer les convertisseurs d’élément par défaut. Par exemple, remplacez `TextBlock` avec leur propre logique de rendu.
1. Un convertisseur **doit** permettent d’héberger des applications inscrire les types d’élément personnalisés. Par exemple, ajouter la prise en charge pour un personnalisé `Rating` élément
1. Un convertisseur **doit** permettent d’héberger des applications supprimer la prise en charge pour un élément par défaut. Par exemple, supprimez `Action.Submit` s’ils ne veulent plus prise en charge.

## <a name="actions"></a>Actions

1. Si HostConfig `supportsInteractivity` est `false`, un convertisseur **ne doit pas** afficher toutes les actions.
1. Le `actions` propriété **doit** être restitué sous forme de boutons dans une sorte de barre d’action, généralement en bas de la carte. 
1. Lorsque l’utilisateur appuie sur un bouton il **doit** permettent à l’application hôte gérer l’événement. 
1. L’événement **doit** passe le long de toutes les propriétés associées avec l’action
1. L’événement **doit** transmettent le `AdaptiveCard` qui a été exécuté

Action | Comportement
--- | ---
**Action.OpenUrl** | Ouvrir une URL externe pour l’affichage
**Action.ShowCard** | Demande une entrée secondaire à afficher à l’utilisateur.
**Action.Submit** | Demandez à tous les éléments d’entrée à collecter dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte pour vous.

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl` **DOIT** ouvrir une URL en utilisant le mécanisme de plateforme native
1. Si ce n’est pas possible il **doit** déclencher un événement à l’application hôte pour gérer l’ouverture de l’URL. Cet événement **doit** permettent à l’application hôte de substituer le comportement par défaut. Par exemple, leur permettent d’ouvrir l’URL dans leur propre application.

### <a name="actionshowcard"></a>Action.ShowCard

1. `Action.ShowCard` **DOIT** pris en charge d’une certaine façon, en fonction du paramètre hostConfig. Il existe deux modes : inline et la fenêtre contextuelle. Les cartes inline **SHOULD** activer/désactiver la visibilité de la carte automatiquement. En mode de menu contextuel, un événement **SHOULD** être déclenché à l’application hôte pour afficher la carte d’une certaine façon.

### <a name="actionsubmit"></a>Action.Submit

L’Action Envoyer se comporte comme un envoi de formulaire HTML, à ceci près qu’où HTML déclenche généralement une requête HTTP post, des cartes adaptatives laisse jusqu'à chaque application hôte pour déterminer ce que « soumettre » signifie que leur. 

1. Lorsque cela **doit** déclencher un événement que l’utilisateur appuie sur l’action appelée.  
1. Le `data` propriété **doit** être inclus dans la charge utile de rappel.
1. Pour `Action.Submit`, un convertisseur **doit** rassembler toutes les entrées sur la carte et de récupérer les valeurs. 

### <a name="selectaction"></a>selectAction

1. Si configuration de l’hôte `supportedInteractivity` est `false` un `selectAction` **ne doit pas** restituées en tant qu’une cible tactile.
1. `Image`, `ColumnSet`, et `Column` offrent un `selectAction` propriété, laquelle **SHOULD** à exécuter lorsque l’utilisateur l’appelle, par exemple, en appuyant sur l’élément.

## <a name="inputs"></a>Entrées

1. Si HostConfig `supportsInteractivity` est `false` un convertisseur **ne doit pas** afficher toutes les entrées.
2. Entrées **SHOULD** afficher avec la plus haute fidélité possible. Par exemple, un `Input.Date` offrirait dans l’idéal, un sélecteur de dates à un utilisateur, mais si ce n’est pas possible sur votre pile de l’interface utilisateur, puis le convertisseur **doit** revenir au rendu d’une zone de texte standard.
3. Un convertisseur **SHOULD** afficher le `placeholderText` si possible
4. Un convertisseur **ne** obligé d’implémenter la validation de l’entrée. Les utilisateurs de cartes adaptatives doivent planifier valider toutes les données reçues de leur côté.
5. Liaison de la valeur d’entrée **doit** être correctement échappés

6. L’objet **doit** renvoyés à l’application hôte comme suit :

   Nous ne faites pas les promesses de validation d’entrée dans des cartes adaptatives, il est donc à la partie réception à analyser correctement la réponse. Par exemple, un Input.Number peut renvoyer « hello » et ils doivent être préparées pour ce faire.


## <a name="events"></a>Events

1. Un convertisseur **SHOULD** déclencher un événement lorsqu’une visibilité d’un élément a changé, ce qui permet l’application hôte faire défiler la carte dans sa position.
