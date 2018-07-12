---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892354"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Extraire et analyser des objets structurés hors de contenu String

Cet article présente également certaines fonctionnalités supplémentaires pour l’applet de commande `ConvertFrom-String` :

- Suppression de la propriété de texte d’étendue par défaut. Vous pouvez l’inclure avec le paramètre -IncludeExtent.

- Nombreux correctifs de bogues d’algorithmes d’apprentissage résolus suite aux commentaires fournis par les MVP et la Communauté.

- Nouveau paramètre -UpdateTemplate pour enregistrer les résultats de l’algorithme d’apprentissage dans un commentaire dans le fichier de modèle. Ainsi, le processus d’apprentissage (l’étape la plus lente) a un coût unique. L’exécution de Convert-String avec un modèle qui contient l’algorithme d’apprentissage encodé est désormais presque instantanée.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>Extraire et analyser des objets structurés hors de contenu String

En collaboration avec [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), une nouvelle applet de commande `ConvertFrom-String` a été ajoutée.

Cette applet de commande prend en charge deux modes : l’analyse délimitée de base et l’analyse pilotée par un exemple généré automatiquement.

Par défaut, l’analyse délimitée fractionne l’entrée au niveau de l’espace blanc et elle affecte des noms de propriétés aux groupes résultants. Vous pouvez personnaliser le délimiteur :

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

L’applet de commande prend également en charge l’analyse pilotée par un exemple généré automatiquement basée sur le travail de recherche [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) mené par [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).

Pour commencer, prenez un carnet d’adresses basé sur du texte :

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA
```

Copiez quelques exemples dans un fichier, que vous utiliserez comme modèle :

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

Placez des accolades autour des données que vous souhaitez extraire, en leur donnant un nom. La propriété **Name** (et ses autres propriétés associées) pouvant apparaître plusieurs fois, vous devez utiliser un astérisque (\*) pour indiquer que cela génère plusieurs enregistrements (plutôt que l’extraction d’un ensemble de propriétés dans un enregistrement unique) :

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

À partir de cet ensemble d’exemples, `ConvertFrom-String` peut maintenant extraire automatiquement la sortie basée sur des objets à partir des fichiers d’entrée ayant une structure similaire.

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

Pour effectuer des manipulations de données supplémentaires sur le texte extrait, la propriété **ExtentText** capture le texte brut à partir duquel l’enregistrement a été extrait. Pour nous faire part de vos commentaires sur cette fonctionnalité ou pour partager du contenu pour lequel vous avez des difficultés à écrire des exemples, envoyez-nous un message à l’adresse <psdmfb@microsoft.com>.