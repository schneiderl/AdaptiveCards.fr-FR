---
title: Service de modèles de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 81d1e598b6157b6ba1fedbf458a7c624705afcd5
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878886"
---
# <a name="adaptive-cards-template-service"></a>Service de modèles de cartes adaptatives

Le service de modèles de cartes adaptatives est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.

Il est utile si vous voulez afficher des données sans avoir à écrire une carte adaptative personnalisée pour celles-ci.

> Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).

> [!IMPORTANT] 
> 
> *Termes et contrat* 
> 
> Ce service de **niveau alpha** est fourni « en l’état », avec tous ses défauts et sans aucun support. Toute collecte de données à partir du service est soumise à la [déclaration de confidentialité de Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).
> 
> Ces fonctionnalités sont **en préversion et sujettes à modification**. Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.

## <a name="how-does-the-service-help-me"></a>En quoi le service peut-il m’aider ?

Prenons un exemple : je viens de recevoir des données. Il peut s’agir de données financières, de données Microsoft Graph, de données schema.org ou de données personnalisées provenant de mon organisation. 

Je souhaite les présenter à un utilisateur. 

Pour cela, je dois normalement écrire un code d’interface utilisateur personnalisé dans toutes les piles front-end que je livre aux utilisateurs finaux.

Imaginons maintenant un monde dans lequel mon application pourrait « apprendre » de nouveaux modèles d’interface utilisateur en fonction du type de données. Un monde où quiconque pourrait participer à l’élaboration de modèles d’interface utilisateur communs, les améliorer et les partager au sein de leurs propres projets, au sein d’une organisation voire à l’échelle de l’Internet.

## <a name="what-is-the-card-template-service"></a>Qu’est-ce que le service de modèles de cartes ?

Le service de modèles de cartes est un point de terminaison REST simple qui vous aide à effectuer les tâches suivantes :

* **Rechercher** un modèle en analysant la structure de vos données
* **Obtenir** un modèle pour pouvoir le lier directement sur le client *sans envoyer vos données au serveur ni quitter l’appareil*
* **Remplir** un modèle sur le serveur quand la liaison de données côté client n’est pas appropriée ou possible

Derrière tout cela :

* Un dépôt de modèles open source et partagés, basé sur GitHub. *(Le dépôt est actuellement privé, mais il sera rendu public dès que nous aurons réglé quelques détails.)*
* Tous les modèles étant des fichiers JSON plats dans le dépôt, les opérations de modification, de contribution et de partage s’inscrivent naturellement dans un workflow de développeur.
* Vous aurez également accès au code du service pour pouvoir l’héberger là où vous le souhaitez. 

## <a name="using-the-service"></a>Utilisation du service

### <a name="get-all-templates"></a>Obtenir tous les modèles 

Ce point de terminaison retourne une liste de tous les modèles connus.

> `HTTP GET https://templates.adaptivecards.io/list`

**Extrait de la réponse**

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

### <a name="find-a-template"></a>Trouver un modèle

Ce point de terminaison tente de trouver un modèle en analysant la structure de vos données.

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a>Exemple

Prenons un exemple : je viens d’accéder à un point de terminaison [Microsoft Graph](https://graph.microsoft.com) pour obtenir des données organisationnelles me concernant.

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Capture d’écran de l’Afficheur Graph](content/2019-08-01-12-08-13.png)

Cette API retourne des **données JSON**, mais comment puis-je **les présenter** aux utilisateurs au moyen de cartes adaptatives ? 

Tout d’abord, je souhaite voir s’il existe un modèle pour ce type de données. J’envoie donc une requête HTTP au point de terminaison `/find` avec mes données dans `POST body`.

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

**Réponse :**

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

Le service retourne une liste de tous les modèles correspondants, ainsi qu’une valeur `confidence` indiquant le degré de correspondance. Je peux à présent utiliser l’URL de ce modèle pour **obtenir** le modèle ou le **remplir** côté serveur.

### <a name="get-a-template"></a>Obtenir un modèle

Un modèle récupéré à partir de ce point de terminaison peut être rempli avec des données au moment de l’exécution [à l’aide des kits SDK de création de modèles](sdk.md).

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

Vous pouvez également inclure un « exemple de données » avec le modèle, ce qui rend la modification dans le concepteur plus conviviale :

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a>Exemple

Nous obtenons le modèle de profil Microsoft Graph retourné par `/find` ci-dessus.

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

**Extrait de la réponse**

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

Utilisez maintenant ce modèle avec les [kits SDK de création de modèles](sdk.md) pour créer une carte adaptative prête pour l’affichage.

### <a name="populate-a-template-server-side"></a>Remplir un modèle côté serveur

Dans certains cas, il est inutile de remplir un modèle sur le client.  Vous pouvez alors faire en sorte que le service retourne une carte adaptative entièrement remplie, prête à être passée à n’importe quel renderer de carte adaptative.

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a>Exemple

Remplissons le modèle de profil Microsoft Graph retourné par `/find` à l’aide des données ci-dessus.

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

**Extrait de la réponse**

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

Notez que la réponse remplace le texte `"{name}"` du premier `TextBlock` par `"Megan Bowen"`, comme dans la requête `GET`. Cette carte adaptative peut désormais être passée à n’importe quel renderer de carte adaptative sans passer par la création de modèles côté client.

## <a name="contributing-templates"></a>Contribution aux modèles

Le service de modèles s’appuie sur un dépôt GitHub (actuellement **privé**), que nous mettrons à disposition en open source après avoir réglé quelques détails.

Nous espérons que l’utilisation de GitHub comme magasin de stockage pour les modèles nous permettra de « démocratiser » le processus de création, d’amélioration et de partage de modèles. N’importe qui peut envoyer une demande de tirage (pull request) incluant un modèle entièrement nouveau ou améliorer des modèles existants... le tout dans l’expérience de développement conviviale de GitHub.

## <a name="self-hosting-the-service"></a>Auto-hébergement du service

Tous les types de données ne sont pas appropriés pour le service de modèles de cartes adaptatives « central » hébergé sur `https://templates.adaptivecards.io`. 

Nous voulons faire en sorte que le service de modèles puisse être hébergé par toute personne au sein de votre organisation. Nous veillerons donc à mettre à disposition le code source et à faciliter le déploiement sur Azure ou votre propre back-end.

De plus amples informations seront annoncées à une date ultérieure.