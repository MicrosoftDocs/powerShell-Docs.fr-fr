---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,installation
title: Boucles et instructions conditionnelles dans les configurations
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736894"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="e3e53-103">Boucles et instructions conditionnelles dans une configuration</span><span class="sxs-lookup"><span data-stu-id="e3e53-103">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="e3e53-104">Vous pouvez rendre votre [configuration](configurations.md) plus dynamique à l’aide de mots clés de contrôle de flux de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3e53-104">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="e3e53-105">Cet article vous explique comment utiliser des instructions et des boucles conditionnelles pour rendre vos `Configuration` plus dynamiques.</span><span class="sxs-lookup"><span data-stu-id="e3e53-105">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="e3e53-106">La combinaison d’instructions et de boucles conditionnelles avec des [paramètres](add-parameters-to-a-configuration.md) et des [Données de configuration](configData.md) vous offre plus de souplesse et de contrôle lors de la compilation de vos `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-106">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="e3e53-107">Comme pour une fonction ou un bloc de script, vous pouvez utiliser n’importe quelle fonctionnalité de langage PowerShell au sein d’une `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-107">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span>
<span data-ttu-id="e3e53-108">Les instructions que vous utilisez seront évaluées uniquement lorsque vous appelez votre `Configuration` pour compiler un fichier `.mof`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-108">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="e3e53-109">Les exemples ci-dessous montrent des scénarios pour illustrer des concepts.</span><span class="sxs-lookup"><span data-stu-id="e3e53-109">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="e3e53-110">Les instructions et les boucles conditionnelles sont plus souvent utilisées avec des paramètres et des Données de configuration.</span><span class="sxs-lookup"><span data-stu-id="e3e53-110">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="e3e53-111">Dans cet exemple simple, le bloc de ressources **Service** récupère l’état actuel d’un service au moment de la compilation pour générer un fichier `.mof` qui conserve son état actuel.</span><span class="sxs-lookup"><span data-stu-id="e3e53-111">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="e3e53-112">L’utilisation de blocs de ressources dynamiques sera plus efficace qu’IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e3e53-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="e3e53-113">L’analyseur PowerShell ne peut pas déterminer si les valeurs spécifiées sont acceptables tant que `Configuration` n’a pas été compilée.</span><span class="sxs-lookup"><span data-stu-id="e3e53-113">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="e3e53-114">En outre, vous pouvez créer un bloc de ressources **Service** pour chaque service sur l’ordinateur actuel à l’aide d’une boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-114">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="e3e53-115">Vous pouvez également créer un `Configuration` uniquement pour les ordinateurs qui sont en ligne à l’aide d’une instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-115">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="e3e53-116">Les blocs de ressources dynamiques des exemples ci-dessus font référence à l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e3e53-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="e3e53-117">Dans ce cas, il s’agit de l’ordinateur sur lequel vous créez `Configuration` et non pas le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="e3e53-117">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="e3e53-118">Résumé</span><span class="sxs-lookup"><span data-stu-id="e3e53-118">Summary</span></span>

<span data-ttu-id="e3e53-119">En résumé, vous pouvez utiliser n’importe quelle fonctionnalité de langage PowerShell au sein d’une `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-119">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="e3e53-120">Cela inclut des éléments tels que :</span><span class="sxs-lookup"><span data-stu-id="e3e53-120">This includes things like:</span></span>

- <span data-ttu-id="e3e53-121">Objets personnalisés</span><span class="sxs-lookup"><span data-stu-id="e3e53-121">Custom Objects</span></span>
- <span data-ttu-id="e3e53-122">Tables de hachage</span><span class="sxs-lookup"><span data-stu-id="e3e53-122">Hashtables</span></span>
- <span data-ttu-id="e3e53-123">Manipulation de chaîne</span><span class="sxs-lookup"><span data-stu-id="e3e53-123">String manipulation</span></span>
- <span data-ttu-id="e3e53-124">Communication à distance</span><span class="sxs-lookup"><span data-stu-id="e3e53-124">Remoting</span></span>
- <span data-ttu-id="e3e53-125">WMI et CIM</span><span class="sxs-lookup"><span data-stu-id="e3e53-125">WMI and CIM</span></span>
- <span data-ttu-id="e3e53-126">Objets ActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="e3e53-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="e3e53-127">et plus...</span><span class="sxs-lookup"><span data-stu-id="e3e53-127">and more...</span></span>

<span data-ttu-id="e3e53-128">Tout code PowerShell défini dans une `Configuration` sera évalué lors d’une compilation, mais vous pouvez également placer le code dans le script contenant votre `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-128">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="e3e53-129">Tout code en dehors du bloc `Configuration` est exécuté lorsque vous importez votre `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="e3e53-129">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3e53-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3e53-130">See also</span></span>

- [<span data-ttu-id="e3e53-131">Ajouter des paramètres à une configuration</span><span class="sxs-lookup"><span data-stu-id="e3e53-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="e3e53-132">Séparer des données de configuration des configurations</span><span class="sxs-lookup"><span data-stu-id="e3e53-132">Separate Configuration data from Configurations</span></span>](configData.md)
