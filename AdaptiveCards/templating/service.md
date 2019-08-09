---
title: Service de modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 81d1e598b6157b6ba1fedbf458a7c624705afcd5
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878886"
---
# <a name="adaptive-cards-template-service"></a>Service de modèle de cartes adaptatives

Le service de modèle de cartes adaptatives est un service de preuve de concept qui permet à quiconque de rechercher, de contribuer et de partager un ensemble de modèles connus.

Elle est utile si vous souhaitez afficher des données, mais ne souhaitez pas avoir à écrire une carte adaptative personnalisée pour celle-ci.

> Pour obtenir une vue d' [ensemble de la création de modèles de cartes adaptatives](index.md) , consultez.

> [!IMPORTANT] 
> 
> *Termes et contrats* 
> 
> Ce service de **niveau alpha** est fourni «en l’État», avec toutes les erreurs et n’est en aucun cas pris en charge. Toute collecte de données à partir du service est soumise à la [déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).
> 
> Ces fonctionnalités sont **en version préliminaire et sujettes à modification**. Vos commentaires sont non seulement des bienvenues, mais essentiels pour garantir que nous fournissons les fonctionnalités dont **vous** avez besoin.

## <a name="how-does-the-service-help-me"></a>Comment le service m’aide-t-il?

Supposons que vous disposiez d’un élément de données, peut-être des données financières, des données Microsoft Graph, des données schema.org ou des données personnalisées à partir de mon organisation. 

Je souhaite à présent afficher les données à un utilisateur. 

Traditionnellement, cela signifie écrire du code d’interface utilisateur personnalisé dans toutes les piles frontales que je livre aux utilisateurs finaux.

Mais que se passe-t-il si mon application pouvait «apprendre» de nouveaux modèles d’interface utilisateur en fonction du type de données? Un monde où tout le monde peut contribuer, améliorer et partager des modèles d’interface utilisateur communs, au sein de leurs propres projets, au sein d’une organisation ou pour l’ensemble de l’Internet.

## <a name="what-is-the-card-template-service"></a>Qu’est-ce que le service de modèle de carte?

Le service de modèle de carte est un point de terminaison REST simple qui permet d’obtenir les éléments suivants:

* **Rechercher** un modèle en analysant la structure de vos données
* **Obtenir** un modèle pour pouvoir le lier directement sur le client, *sans envoyer vos données au serveur ou sans jamais quitter l’appareil*
* **Remplissage** d’un modèle sur le serveur, lorsque la liaison de données côté client n’est pas appropriée ou possible

En arrière-plan, est:

* Un référentiel de modèles Open source partagé, sauvegardé par GitHub. *(Le référentiel est actuellement privé, mais sera rendu public dès que nous mettrons des points faibles.)*
* Tous les modèles sont des fichiers JSON plats dans le référentiel, ce qui permet de modifier, de contribuer et de partager une partie naturelle d’un flux de travail de développement.
* Le code du service sera mis à disposition pour que vous puissiez l’héberger là où vous le souhaitez. 

## <a name="using-the-service"></a>Utilisation du service

### <a name="get-all-templates"></a>Récupération de tous les modèles 

Ce point de terminaison retourne une liste de tous les modèles connus.

> `HTTP GET https://templates.adaptivecards.io/list`

**Extrait de réponse**

```json
{
  "graph.microsoft.com": {
    "templates": [
      {
        "file": "Files.json",
        "fullPath": "graph.microsoft.com/Files.json"
      },
      {
        "file": "Profile.json",
        "fullPath": "graph.microsoft.com/Profile.json"
      }
   ]
}
```

### <a name="find-a-template"></a>Rechercher un modèle

Ce point de terminaison tente de trouver un modèle en analysant la structure de vos données.

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a>Exemple

Supposons que je clique juste sur un point de terminaison [Microsoft Graph](https://graph.microsoft.com) pour obtenir des données organisationnelles à mon sujet.

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Capture d’écran de l’Explorateur graphique](content/2019-08-01-12-08-13.png)

Cette API a renvoyé des **données JSON**, mais comment l' **Afficher** aux utilisateurs à l’aide de cartes adaptatives? 

Tout d’abord, je souhaite voir s’il existe un modèle pour ce type de données. je fais donc une requête `/find` http au point de terminaison avec `POST body`mes données dans le.

```
HTTP POST https://templates.adaptivecards.io/find

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

**Lutte**

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

Le service retourne une liste de tous les modèles correspondants, ainsi qu' `confidence` une indication de la fermeture de la correspondance. Je peux maintenant utiliser cette URL de modèle pour **récupérer** le modèle ou le **remplir** côté serveur.

### <a name="get-a-template"></a>Obtenir un modèle

Un modèle récupéré à partir de ce point de terminaison peut être rempli avec les données au moment de l’exécution [à l’aide des Kits SDK templatng](sdk.md).

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

Vous pouvez également inclure des «exemples de données» avec le modèle, ce qui rend la modification dans le concepteur plus conviviale:

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a>Exemple

Nous obtenons le modèle de `/find` profil Microsoft Graph qui a été retourné ci-dessus.

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

**Extrait de réponse**

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "{name}"
    },
    {
        // ...snip
    }
  ]
}
```

Utilisez maintenant ce modèle avec les [Kits de développement](sdk.md) logiciel (SDK) de création de modèles pour créer une carte adaptative prête à l’emploi.

### <a name="populate-a-template-server-side"></a>Remplir un modèle côté serveur

Dans certains cas, il peut s’avérer inutile de remplir un modèle sur le client.  Pour ces cas d’utilisation, vous pouvez faire en sorte que le service retourne une carte adaptative entièrement remplie, prête à être transmise à n’importe quel convertisseur de carte adaptative.

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a>Exemple

Nous allons remplir le modèle de profil Microsoft Graph qui a été `/find` retourné à l’aide des données ci-dessus.

```
HTTP POST https://templates.adaptivecards.io/graph.microsoft.com/Profile.json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

**Extrait de réponse**

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "Megan Bowen"
    },
    {
        // ...snip
    }
  ]
}
```

Notez que la réponse a remplacé le texte de la `TextBlock` première `"Megan Bowen"` par au `"{name}"`lieu de, comme `GET` dans la demande. Ce AdaptiveCard peut désormais être passé à n’importe quel convertisseur de carte adaptative sans passer par la création de modèles côté client.

## <a name="contributing-templates"></a>Modèles contributeurs

Le service de modèle est associé à un GitHub référentiel (qui est actuellement **privé**), mais nous allons ouvrir la source une fois que nous aurons des terminaisons libres.

Nous espérons qu’en utilisant GitHub comme magasin de stockage pour les modèles, nous pouvons «démocratiser» le processus de création, d’amélioration et de partage de modèles. Tout le monde peut soumettre une demande de tirage incluant un modèle entièrement nouveau ou apporter des améliorations à celles qui existent déjà... tout cela dans l’expérience conviviale du développeur de GitHub.

## <a name="self-hosting-the-service"></a>Hébergement automatique du service

Tous les types de données ne sont pas adaptés au service de modèle de cartes adaptatives «central `https://templates.adaptivecards.io`» hébergé à l’adresse. 

Nous voulons nous assurer que tout le monde peut héberger le service de modèle au sein de votre organisation. le code source sera donc mis à disposition et nous faciliterons le déploiement sur Azure ou votre propre serveur principal.

En savoir plus à ce jour ultérieurement.