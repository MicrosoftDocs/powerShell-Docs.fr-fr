---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085352"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="286af-102">Extraire et analyser des objets structurés hors de contenu String</span><span class="sxs-lookup"><span data-stu-id="286af-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="286af-103">Cet article présente également certaines fonctionnalités supplémentaires pour l’applet de commande `ConvertFrom-String` :</span><span class="sxs-lookup"><span data-stu-id="286af-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="286af-104">Suppression de la propriété de texte d’étendue par défaut.</span><span class="sxs-lookup"><span data-stu-id="286af-104">Removes the extent text property by default.</span></span> <span data-ttu-id="286af-105">Vous pouvez l’inclure avec le paramètre -IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="286af-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="286af-106">Nombreux correctifs de bogues d’algorithmes d’apprentissage résolus suite aux commentaires fournis par les MVP et la Communauté.</span><span class="sxs-lookup"><span data-stu-id="286af-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="286af-107">Nouveau paramètre -UpdateTemplate pour enregistrer les résultats de l’algorithme d’apprentissage dans un commentaire dans le fichier de modèle.</span><span class="sxs-lookup"><span data-stu-id="286af-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="286af-108">Ainsi, le processus d’apprentissage (l’étape la plus lente) a un coût unique.</span><span class="sxs-lookup"><span data-stu-id="286af-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="286af-109">L’exécution de Convert-String avec un modèle qui contient l’algorithme d’apprentissage encodé est désormais presque instantanée.</span><span class="sxs-lookup"><span data-stu-id="286af-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="286af-110">Extraire et analyser des objets structurés hors de contenu String</span><span class="sxs-lookup"><span data-stu-id="286af-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="286af-111">En collaboration avec [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), une nouvelle applet de commande `ConvertFrom-String` a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="286af-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="286af-112">Cette applet de commande prend en charge deux modes : l’analyse délimitée de base et l’analyse pilotée par un exemple généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="286af-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="286af-113">Par défaut, l’analyse délimitée fractionne l’entrée au niveau de l’espace blanc et elle affecte des noms de propriétés aux groupes résultants.</span><span class="sxs-lookup"><span data-stu-id="286af-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="286af-114">Vous pouvez personnaliser le délimiteur :</span><span class="sxs-lookup"><span data-stu-id="286af-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="286af-115">L’applet de commande prend également en charge l’analyse pilotée par un exemple généré automatiquement basée sur le travail de recherche [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) mené par [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="286af-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="286af-116">Pour commencer, prenez un carnet d’adresses basé sur du texte :</span><span class="sxs-lookup"><span data-stu-id="286af-116">To get started, consider a text-based address book:</span></span>

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

<span data-ttu-id="286af-117">Copiez quelques exemples dans un fichier, que vous utiliserez comme modèle :</span><span class="sxs-lookup"><span data-stu-id="286af-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="286af-118">Placez des accolades autour des données que vous souhaitez extraire, en leur donnant un nom.</span><span class="sxs-lookup"><span data-stu-id="286af-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="286af-119">La propriété **Name** (et ses autres propriétés associées) pouvant apparaître plusieurs fois, vous devez utiliser un astérisque (\*) pour indiquer que cela génère plusieurs enregistrements (plutôt que l’extraction d’un ensemble de propriétés dans un enregistrement unique) :</span><span class="sxs-lookup"><span data-stu-id="286af-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="286af-120">À partir de cet ensemble d’exemples, `ConvertFrom-String` peut maintenant extraire automatiquement la sortie basée sur des objets à partir des fichiers d’entrée ayant une structure similaire.</span><span class="sxs-lookup"><span data-stu-id="286af-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

<span data-ttu-id="286af-121">Pour effectuer des manipulations de données supplémentaires sur le texte extrait, la propriété **ExtentText** capture le texte brut à partir duquel l’enregistrement a été extrait.</span><span class="sxs-lookup"><span data-stu-id="286af-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="286af-122">Pour nous faire part de vos commentaires sur cette fonctionnalité ou pour partager du contenu pour lequel vous avez des difficultés à écrire des exemples, envoyez-nous un message à l’adresse <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="286af-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>