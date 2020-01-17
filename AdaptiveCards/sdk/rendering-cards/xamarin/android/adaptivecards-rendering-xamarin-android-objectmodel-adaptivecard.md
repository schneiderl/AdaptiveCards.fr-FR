---
title: AdaptiveCard, classe-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 0f64bf635023271d8b40bf55fce079300aae7652
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146083"
---
# <a name="adaptivecard"></a>AdaptiveCard

```csharp
public class AdaptiveCard : Java.Lang.Object 
```

**Namespace**

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a>Récapitulatif

| Attributes | |
| ---- | --- |
| Actions | Actions à afficher dans la barre d’action de la carte. |
| BackgroundImage | Spécifie l’image d’arrière-plan de la carte. |
| Body | Éléments de carte à afficher dans la région de carte principale. |
| type_élément | Doit être « AdaptiveCard ». |
| FallbackText | Texte affiché lorsque le client ne prend pas en charge la version spécifiée (peut contenir la démarque). |
| Hauteur | |
| InputNecessityIndicators | |
| Langue | Le langage ISO-639-1 à 2 lettres utilisé dans la carte. Utilisé pour localiser des fonctions de date/heure. |
| MinHeight | Spécifie la hauteur minimale de la carte. |
| SelectAction | Action qui est appelée lorsque la carte est activée ou sélectionnée. Action. ShowCard n’est pas pris en charge. |
| Speak | Spécifie ce qui doit être parlé pour cette carte entière. Il s’agit de texte simple ou de fragment SSML. |
| Style | |
| Version | Version de schéma requise par cette carte. Si un client est inférieur à cette version, le fallbackText sera rendu. Remarque : la version n’est pas requise pour les cartes dans une action. ShowCard. Toutefois, il est requis pour la carte de niveau supérieur. |
| VerticalContentAlignment | Définit la façon dont le contenu doit être aligné verticalement dans le conteneur. Concerne uniquement les cartes à hauteur fixe ou les cartes avec un minHeight spécifié. |

&nbsp;

**Constructeurs publics**

---

<a href="#ctor0"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor1"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

<a href="#ctor2"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor3"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

&nbsp;
| Méthodes publiques | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](#deserializefromstring0) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```](#deserializefromstring1) |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```](#makefallbacktextcard) |
| ```string``` | [```Serialize()```](#serialize) |
| ```JsonValue``` | [```SerializeToJsonValue()```](#serializetojsonvalue) |

&nbsp;
## <a name="public-constructors"></a>Constructeurs publics
---

### <a id="ctor0"></a>AdaptiveCard
<p style='text-align:right'>Ajouté dans la version 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight) 
```

| Paramètres | |
| --- | --- |
| Version de | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| hauteur | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor1"></a>AdaptiveCard
<p style='text-align:right'>Ajouté dans la version 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body, 
                    BaseActionElementVector actions)
```

| Paramètres | |
| --- | --- |
| Version de | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| hauteur | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| corps | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| actions | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;&nbsp;

### <a id="ctor2"></a>AdaptiveCard
<p style='text-align:right'>Ajouté dans la version 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight) 
```

| Paramètres | |
| --- | --- |
| Version de | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```string``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| hauteur | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor3"></a>AdaptiveCard
<p style='text-align:right'>Ajouté dans la version 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body,
                    BaseActionElementVector actions)

```

| Paramètres | |
| --- | --- |
| Version de | ```string``` |
| fallbackText | ```string``` |
| backgroundImage | ```string``` |
| style | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| hauteur | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| corps | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| actions | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;

## <a name="public-methods"></a>Méthodes publiques
---
### <a id="deserializefromstring0"></a>DeserializeFromString
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

Désérialise la carte adaptative donnée en tant que chaîne JSON pour la version de convertisseur spécifiée.

| Paramètres | |
| --- | --- |
| jsonString | ```string``` |
| rendererVersion | ```string``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a>Exemple

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
```

--- 
### <a id="deserializefromstring1"></a>DeserializeFromString
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

Désérialise la carte adaptative donnée en tant que chaîne JSON pour la version du convertisseur spécifiée à l’aide d’un objet [ParseContext]() pour gérer l’analyse des éléments personnalisés.

| Paramètres | |
| --- | --- |
| jsonString | ```string``` |
| rendererVersion | ```string``` |
| context | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a>Exemple

```csharp
ParseContext parseContext = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, parseContext);
```

---

### <a id="makefallbacktextcard"></a>MakeFallbackTextCard
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

Désérialise la carte adaptative donnée en tant que chaîne JSON pour la version de convertisseur spécifiée.

| Paramètres | |
| --- | --- |
| fallbackText | ```string``` |
| language | ```string``` |
| speak | ```string``` |

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` | Carte adaptative qui contient le texte de secours pour une carte unrendereable |

#### <a name="sample"></a>Exemple

```csharp
AdaptiveCard adaptiveCard = AdaptiveCard.MakeFallbackTextCard("This card failed to render", "es", "Unrendereable card");
```

---

### <a id="serialize"></a>Sérialiser
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public string Serialize ()
```

Sérialise la carte adaptative sous sa forme de chaîne JSON.

| Returns | |
| --- | --- |
| ```string``` | Carte adaptative comme chaîne JSON |

#### <a name="sample"></a>Exemple

```csharp
string jsonString = parseResult.AdaptiveCard.Serialize();
```

---

### <a id="serializetojsonvalue"></a>SerializeToJsonValue
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public JsonValue SerializeToJsonValue ()
```

Sérialise la carte adaptative dans un objet de valeur JSON.

| Returns | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue``` | |

#### <a name="sample"></a>Exemple

```csharp
JsonValue value = parseResult.AdaptiveCard.SerializeToJsonValue();
```