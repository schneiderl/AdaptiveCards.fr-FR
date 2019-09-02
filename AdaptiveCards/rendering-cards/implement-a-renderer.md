---
title: Implémentation d’un renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: b39493f82f3378e5a554abc6df890d6821869671
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138022"
---
# <a name="adaptive-card-renderer-specification"></a>Spécification de renderer de carte adaptative

La spécification suivante décrit comment implémenter un renderer de carte adaptative sur une plateforme d’interface utilisateur.

> [!IMPORTANT]
> 
> Ce contenu n’est pas encore terminé. N’hésitez pas à y revenir sous peu.

## <a name="sdk-versioning"></a>Gestion des versions de l’API

1. La version principale et la version mineure du SDK **DOIVENT** correspondre à la version de `schema`. 
1. Un correctif/une build **DOIT** être utilisé(e) pour les mises à jour du renderer qui n’ont pas de modifications de schéma.

## <a name="parsing-json"></a>Analyse du JSON

### <a name="error-conditions"></a>Conditions d’erreur
1. Un analyseur **DOIT** vérifier qu’il s’agit de contenu JSON valide.
1. Un analyseur **DOIT** effectuer une validation par rapport au schéma (propriétés requises, etc.).
1. Les erreurs ci-dessus **DOIVENT** être signalées à l’application hôte (exception ou équivalent).

### <a name="unknown-types"></a>Types inconnus
1. Si des « types » inconnus sont détectés, ils **DOIVENT ÊTRE SUPPRIMÉS** du résultat.
1. Toute modification de la charge utile (comme ci-dessus) **DOIT** être signalée comme avertissement à l’application hôte.

### <a name="unknown-properties"></a>Propriétés inconnues
1. Un analyseur **DOIT** inclure des propriétés **supplémentaires** sur les éléments.

### <a name="additional-considerations"></a>Considérations supplémentaires
1. La propriété `speak` peut contenir du balisage SSML et **DOIT** être retournée à l’application hôte telle qu’elle est spécifiée.

## <a name="parsing-host-config"></a>Analyse de la configuration de l’hôte
1. TODO

## <a name="versioning"></a>Contrôle de version

1. Un renderer **DOIT** implémenter une version particulière du schéma. 
1. Le constructeur `AdaptiveCard` **DOIT** attribuer à la propriété `version` une valeur par défaut basée sur la version actuelle du schéma. 
1. Si un renderer rencontre une propriété `version` dans le `AdaptiveCard` qui est supérieure à la version prise en charge, il **DOIT** retourner le `fallbackText` à la place.

## <a name="rendering"></a>Rendu

Un `AdaptiveCard` est constitué d’un `body` et d’`actions`. Le `body` est une collection de `CardElement`s qu’un renderer énumère et affiche dans l’ordre. 

1. Chaque élément **DOIT** s’étendre à la largeur de son parent (pensez à `display: block` HTML).
1. Un renderer **DOIT** ignorer les types d’éléments inconnus et continuer le rendu du reste de la charge utile.

### <a name="spacing-and-separators"></a>Espacement et séparateurs

1. La propriété `spacing` sur chaque élément influence la quantité d’espace entre l’élément **ACTUEL** et celui qui le **PRÉCÈDE**.
1. L’espacement **DOIT UNIQUEMENT** s’appliquer quand il existe réellement un élément qui le précède. (Par exemple, il ne s’applique pas au premier élément d’un tableau.)
1. Un renderer **DOIT** rechercher la quantité d’espace à utiliser à partir de l’espacement `hostConfig` pour la valeur enum appliquée à l’élément actuel.
1. Si la valeur `separator` de l’élément est `true`, une ligne visible **DOIT** être dessinée entre l’élément actuel et celui qui le précède.
1. La ligne de séparation **DOIT** être dessinée à l’aide du `container.style.default.foregroundColor`.
1. Un séparateur **DOIT UNIQUEMENT** être dessiné si l’élément **N’EST PAS** le premier dans le tableau.

### <a name="columns"></a>Colonnes

1. `Column` `width` **DOIT** être interprété par « auto », « stretch » ou un rapport pondéré.

### <a name="textblock"></a>TextBlock

1. Un TextBlock **DOIT** occuper une seule ligne, sauf si la propriété `wrap` est `true`. 
1. Le bloc de texte **DOIT** supprimer tout texte excédentaire avec des points de suspension (...).

#### <a name="markdown"></a>Markdown

1. Les cartes adaptatives autorisent un sous-ensemble de Markdown et `TextBlock`DOIVENT**être prises en charge dans**. 
1. Voir les [conditions requises complètes pour le Markdown](../authoring-cards/text-features.md).

#### <a name="formatting-functions"></a>Fonctions de mise en forme

1. `TextBlock` autorise les [fonctions de mise en forme de DATE/HEURE](../authoring-cards/text-features.md) qui **DOIVENT** être prises en charge sur chaque renderer.
1. **TOUTES LES DÉFAILLANCES DOIVENT** afficher la chaîne brute dans la carte. Aucun message convivial n’est tenté. (L’objectif est de permettre au développeur de savoir immédiatement qu’il y a un problème.)

1. TODO: Inclure regex

### <a name="images"></a>Images

1. Un renderer **DOIT** permettre aux applications hôtes de savoir quand toutes les images HTTP ont été téléchargées et que la carte est « entièrement affichée ».
1. Un renderer **DOIT** inspecter le paramètre `maxImageSize` de configuration de l’hôte lors du téléchargement d’images HTTP
1. Un renderer **DOIT** prendre en charge `.png` et `.jpeg`.
1. Un renderer **DOIT** prendre en charge les images `.gif`.

### <a name="host-config"></a>Configuration de l’hôte

* TODO: Quelles doivent-être les valeurs par défaut ? Doivent-ils tous les partager ? Devons-nous incorporer un fichier hostConfig.json commun dans les fichiers binaires ?
* TODO: Je pense que HostConfig a également besoin d’une gestion des versions pour l’analyse.

[`HostConfig`](host-config.md) est un objet de configuration partagé qui spécifie comment un renderer de carte adaptative génère l’interface utilisateur.  

Cela permet aux propriétés qui sont indépendantes de la plateforme d’être partagées par les renderers sur différents appareils et plateformes. Cela permet également de créer des outils qui vous donnent une idée de l’apparence de la carte pour un environnement donné.

1. Les renderers **DOIVENT** exposer un paramètre de **Configuration d’hôte** pour héberger des applications.
1. Un style **DOIT** être appliqué à tous les éléments en fonction de leurs paramètres de configuration d’hôte respectifs.

### <a name="native-platform-styling"></a>Style de plateforme natif

1. Chaque type d’élément **DOIT** attacher un style de plateforme natif à l’élément d’interface utilisateur généré. Par exemple, dans le code HTML nous avons ajouté une classe CSS aux types d’éléments et, en XAML, nous affectons un style spécifique.

## <a name="extensibility"></a>Extensibilité 

1. Un renderer **DOIT** autoriser les applications hôtes à remplacer les renderers d’éléments par défaut (par exemple remplacer le rendu `TextBlock` par leur propre logique).
1. Un renderer **DOIT** autoriser les applications hôtes à inscrire des types d’éléments personnalisés (par exemple ajouter la prise en charge d’un élément personnalisé `Rating`).
1. Un renderer **DOIT** autoriser les applications hôtes à supprimer la prise en charge d’un élément par défaut (par exemple supprimer `Action.Submit` si elles ne souhaitent pas qu’il soit pris en charge).

## <a name="actions"></a>Actions

1. Si `supportsInteractivity` de configuration de l’hôte est `false`, un renderer **NE DOIT PAS** afficher d’action.
1. La propriété `actions` **DOIT** être rendue sous forme de boutons dans un type de barre d’action, généralement au bas de la carte. 
1. Quand un bouton est enfoncé, il **DOIT** permettre à l’application hôte de gérer l’événement. 
1. L’événement **DOIT** transmettre toutes les propriétés associées avec l’action.
1. L’événement **DOIT** transmettre le `AdaptiveCard` qui a été exécuté.

Action | Comportement
--- | ---
**Action.OpenUrl** | Ouvrir une URL externe pour l’affichage
**Action.ShowCard** | Demande de présenter une sous-carte à l’utilisateur
**Action.Submit** | Demande de regrouper tous les éléments d’entrée au sein d’un même objet, qui vous est ensuite envoyé par le biais d’une méthode définie par l’application hôte

### <a name="actionopenurl"></a>Action.OpenUrl
1. `Action.OpenUrl` **DOIT** ouvrir une URL à l’aide du mécanisme de plateforme natif.
1. Si ce n’est pas possible, il **DOIT** déclencher un événement sur l’application hôte pour gérer l’ouverture de l’URL. Cet événement **DOIT** permettre à l’application hôte de remplacer le comportement par défaut (par exemple, lui laisser ouvrir l’URL dans sa propre application).

### <a name="actionshowcard"></a>Action.ShowCard

1. `Action.ShowCard` **DOIT** être pris en charge d’une certaine manière, en fonction du paramètre hostConfig. Il existe deux modes : inline et popup. Les cartes inline **DOIVENT** basculer automatiquement la visibilité de la carte. En mode popup, un événement **DOIT** être déclenché sur l’application hôte pour afficher la carte d’une certaine façon.

### <a name="actionsubmit"></a>Action.Submit

L’action Submit se comporte comme un envoi de formulaire HTML, sauf que là où le code HTML déclenche généralement une requête HTTP, les cartes adaptatives laissent à chaque application hôte le soin de déterminer ce que signifie pour elles « envoi ». 

1. Quand cela **DOIT** déclencher un événement, l’utilisateur appuie sur l’action appelée.  
1. La propriété `data` **DOIT** être incluse dans la charge utile de rappel.
1. Pour `Action.Submit`, un renderer **DOIT** recueillir toutes les entrées sur la carte et récupérer leurs valeurs. 

### <a name="selectaction"></a>selectAction

1. Si `supportedInteractivity` de la configuration de l’hôte est `false`, un `selectAction` **NE DOIT PAS** être affiché en tant que cible tactile.
1. `Image`, `ColumnSet` et `Column` offrent une propriété `selectAction`, qui **DOIT** être exécutée quand l’utilisateur l’appelle, par exemple en appuyant sur l’élément.

## <a name="inputs"></a>Entrées

1. Si `supportsInteractivity` de configuration de l’hôte est `false`, un renderer **NE DOIT PAS** afficher d’entrée.
2. Les entrées **DOIVENT** être affichées avec la fidélité la plus élevée possible. Par exemple, dans l’idéal un `Input.Date` proposera un sélecteur de date à un utilisateur, mais si cela n’est pas possible sur votre pile d’interface utilisateur, le renderer **DOIT** revenir au rendu d’une zone de texte standard.
3. Un renderer **DOIT** afficher le `placeholderText` si possible.
4. Un renderer **N’EST PAS OBLIGÉ** d’implémenter la validation de l’entrée. Les utilisateurs de cartes adaptatives doivent prévoir de valider toutes les données reçues à leur extrémité.
5. La liaison de valeur d’entrée **DOIT** être correctement placée dans une séquence d’échappement.

6. L’objet **DOIT** être retourné à l’application hôte comme suit :

   Nous n’offrons aucune promesse de validation d’entrée dans les cartes adaptatives ; il incombe donc à la partie réceptrice d’analyser correctement la réponse. Par exemple, un Input.Number pourrait retourner « Hello », et vous devez être préparé à cela.


## <a name="events"></a>Événements

1. Un renderer **DOIT** déclencher un événement quand la visibilité d’un élément a changé, permettant à l’application hôte de faire défiler la carte vers la position.
