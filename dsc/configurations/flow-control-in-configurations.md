---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Boucles et instructions conditionnelles dans les configurations
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401251"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="fcbad-103">Boucles et instructions conditionnelles dans les configurations</span><span class="sxs-lookup"><span data-stu-id="fcbad-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="fcbad-104">Vous pouvez rendre votre [Configurations](configurations.md) plus dynamique à l’aide de mots clés de contrôle de flux de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcbad-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="fcbad-105">Cet article vous explique comment vous pouvez utiliser des instructions conditionnelles et des boucles pour rendre vos Configurations plus dynamique.</span><span class="sxs-lookup"><span data-stu-id="fcbad-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="fcbad-106">Combinaison conditionnelle et des boucles avec [paramètres](add-parameters-to-a-configuration.md) et [les données de Configuration](configData.md) vous permet de plus de souplesse et de contrôle lors de la compilation de vos Configurations.</span><span class="sxs-lookup"><span data-stu-id="fcbad-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="fcbad-107">Tout comme une fonction ou un bloc de Script, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une Configuration.</span><span class="sxs-lookup"><span data-stu-id="fcbad-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="fcbad-108">Les instructions que vous utilisez seront évaluées uniquement lorsque vous appelez votre Configuration pour compiler un fichier « .mof ».</span><span class="sxs-lookup"><span data-stu-id="fcbad-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="fcbad-109">Les exemples ci-dessous illustrent des scénarios simples pour illustrer les concepts.</span><span class="sxs-lookup"><span data-stu-id="fcbad-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="fcbad-110">Instructions conditionnelles sont boucles sont plus souvent utilisés avec des paramètres et données de Configuration.</span><span class="sxs-lookup"><span data-stu-id="fcbad-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="fcbad-111">Dans cet exemple simple, le **Service** bloc de ressources récupère l’état actuel d’un service au moment de la compilation pour générer un fichier « .mof » qui conserve son état actuel.</span><span class="sxs-lookup"><span data-stu-id="fcbad-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="fcbad-112">À l’aide de blocs de ressources dynamiques sera préempter l’efficacité d’Intellisense.</span><span class="sxs-lookup"><span data-stu-id="fcbad-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="fcbad-113">L’Analyseur de PowerShell ne peut pas déterminer si les valeurs spécifiées sont acceptables jusqu'à ce que la Configuration est compilée.</span><span class="sxs-lookup"><span data-stu-id="fcbad-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="fcbad-114">En outre, vous pouvez créer un **Service** bloquer les ressources pour chaque service sur l’ordinateur actuel, à l’aide un `foreach` boucle.</span><span class="sxs-lookup"><span data-stu-id="fcbad-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
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

<span data-ttu-id="fcbad-115">Vous pouvez créer également uniquement des configurations pour les ordinateurs qui sont en ligne, à l’aide d’une simple `if` instruction.</span><span class="sxs-lookup"><span data-stu-id="fcbad-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="fcbad-116">La ressource dynamique bloque, dans la référence d’exemples ci-dessus, l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="fcbad-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="fcbad-117">Dans ce cas, ce qui serait l’ordinateur que vous créez la Configuration sur, pas la nœud cible.</span><span class="sxs-lookup"><span data-stu-id="fcbad-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="fcbad-118">Résumé</span><span class="sxs-lookup"><span data-stu-id="fcbad-118">Summary</span></span>

<span data-ttu-id="fcbad-119">En résumé, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une Configuration.</span><span class="sxs-lookup"><span data-stu-id="fcbad-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="fcbad-120">Cela inclut des éléments tels que :</span><span class="sxs-lookup"><span data-stu-id="fcbad-120">This includes things like:</span></span>

- <span data-ttu-id="fcbad-121">Objets personnalisés</span><span class="sxs-lookup"><span data-stu-id="fcbad-121">Custom Objects</span></span>
- <span data-ttu-id="fcbad-122">Tables de hachage</span><span class="sxs-lookup"><span data-stu-id="fcbad-122">Hashtables</span></span>
- <span data-ttu-id="fcbad-123">Manipulation de chaînes</span><span class="sxs-lookup"><span data-stu-id="fcbad-123">String manipulation</span></span>
- <span data-ttu-id="fcbad-124">Communication à distance</span><span class="sxs-lookup"><span data-stu-id="fcbad-124">Remoting</span></span>
- <span data-ttu-id="fcbad-125">WMI et CIM</span><span class="sxs-lookup"><span data-stu-id="fcbad-125">WMI and CIM</span></span>
- <span data-ttu-id="fcbad-126">Objets Active Directory</span><span class="sxs-lookup"><span data-stu-id="fcbad-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="fcbad-127">et plus...</span><span class="sxs-lookup"><span data-stu-id="fcbad-127">and more...</span></span>

<span data-ttu-id="fcbad-128">N’importe quel code PowerShell défini dans une Configuration sera évaluée à un moment de la compilation, mais vous pouvez également placer le code dans le script qui contient votre Configuration.</span><span class="sxs-lookup"><span data-stu-id="fcbad-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="fcbad-129">N’importe quel code en dehors du bloc de Configuration sera exécuté lorsque vous importez votre Configuration.</span><span class="sxs-lookup"><span data-stu-id="fcbad-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcbad-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcbad-130">See also</span></span>

- [<span data-ttu-id="fcbad-131">Ajouter des paramètres à une configuration</span><span class="sxs-lookup"><span data-stu-id="fcbad-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="fcbad-132">Séparer des données de configuration des configurations</span><span class="sxs-lookup"><span data-stu-id="fcbad-132">Separate Configuration data from Configurations</span></span>](configData.md)
