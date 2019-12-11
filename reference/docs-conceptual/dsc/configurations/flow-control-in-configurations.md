---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Boucles et instructions conditionnelles dans les configurations
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954076"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="367d5-103">Boucles et instructions conditionnelles dans les configurations</span><span class="sxs-lookup"><span data-stu-id="367d5-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="367d5-104">Vous pouvez rendre vos [configurations](configurations.md) plus dynamiques à l’aide de mots clés de contrôle de flux de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="367d5-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="367d5-105">Cet article vous explique comment utiliser des instructions conditionnelles et des boucles pour rendre vos configurations plus dynamiques.</span><span class="sxs-lookup"><span data-stu-id="367d5-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="367d5-106">La combinaison d’instructions conditionnelles et de boucles avec des [paramètres](add-parameters-to-a-configuration.md) et des [données de configuration](configData.md) vous offre plus de souplesse et de contrôle lors de la compilation de vos configurations.</span><span class="sxs-lookup"><span data-stu-id="367d5-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="367d5-107">Comme pour une fonction ou un bloc de script, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="367d5-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="367d5-108">Les instructions que vous utilisez seront évaluées uniquement lorsque vous appelez votre configuration pour compiler un fichier « .mof ».</span><span class="sxs-lookup"><span data-stu-id="367d5-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="367d5-109">Les exemples ci-dessous montrent des scénarios simples pour illustrer des concepts.</span><span class="sxs-lookup"><span data-stu-id="367d5-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="367d5-110">Les instructions conditionnelles représentent des boucles plus souvent utilisées avec des paramètres et des données de configuration.</span><span class="sxs-lookup"><span data-stu-id="367d5-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="367d5-111">Dans cet exemple simple, le bloc de ressources **Service** récupère l’état actuel d’un service au moment de la compilation pour générer un fichier « .mof » qui conserve son état actuel.</span><span class="sxs-lookup"><span data-stu-id="367d5-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="367d5-112">L’utilisation de blocs de ressources dynamiques sera plus efficace qu’IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="367d5-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="367d5-113">L’analyseur PowerShell ne peut pas déterminer si les valeurs spécifiées sont acceptables tant que la configuration n’a pas été compilée.</span><span class="sxs-lookup"><span data-stu-id="367d5-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="367d5-114">En outre, vous pouvez créer un bloc de ressources **Service** pour chaque service sur l’ordinateur actuel à l’aide d’une boucle `foreach`.</span><span class="sxs-lookup"><span data-stu-id="367d5-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="367d5-115">Vous pouvez également créer uniquement des configurations pour les ordinateurs en ligne à l’aide d’une simple instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="367d5-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="367d5-116">Les blocs de ressources dynamiques des exemples ci-dessus font référence à l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="367d5-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="367d5-117">Dans ce cas, il s’agit de l’ordinateur sur lequel vous créez la configuration, et non pas le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="367d5-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="367d5-118">Résumé</span><span class="sxs-lookup"><span data-stu-id="367d5-118">Summary</span></span>

<span data-ttu-id="367d5-119">En résumé, vous pouvez utiliser n’importe quel langage PowerShell au sein d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="367d5-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="367d5-120">Cela inclut des éléments tels que :</span><span class="sxs-lookup"><span data-stu-id="367d5-120">This includes things like:</span></span>

- <span data-ttu-id="367d5-121">Objets personnalisés</span><span class="sxs-lookup"><span data-stu-id="367d5-121">Custom Objects</span></span>
- <span data-ttu-id="367d5-122">Tables de hachage</span><span class="sxs-lookup"><span data-stu-id="367d5-122">Hashtables</span></span>
- <span data-ttu-id="367d5-123">Manipulation de chaîne</span><span class="sxs-lookup"><span data-stu-id="367d5-123">String manipulation</span></span>
- <span data-ttu-id="367d5-124">Communication à distance</span><span class="sxs-lookup"><span data-stu-id="367d5-124">Remoting</span></span>
- <span data-ttu-id="367d5-125">WMI et CIM</span><span class="sxs-lookup"><span data-stu-id="367d5-125">WMI and CIM</span></span>
- <span data-ttu-id="367d5-126">Objets ActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="367d5-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="367d5-127">et plus...</span><span class="sxs-lookup"><span data-stu-id="367d5-127">and more...</span></span>

<span data-ttu-id="367d5-128">Tout code PowerShell défini dans une configuration sera évalué lors d’une compilation, mais vous pouvez également placer le code dans le script contenant votre configuration.</span><span class="sxs-lookup"><span data-stu-id="367d5-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="367d5-129">Tout code en dehors du bloc de configuration sera exécuté lorsque vous importez votre configuration.</span><span class="sxs-lookup"><span data-stu-id="367d5-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="367d5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="367d5-130">See also</span></span>

- [<span data-ttu-id="367d5-131">Ajouter des paramètres à une configuration</span><span class="sxs-lookup"><span data-stu-id="367d5-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="367d5-132">Séparer des données de configuration des configurations</span><span class="sxs-lookup"><span data-stu-id="367d5-132">Separate Configuration data from Configurations</span></span>](configData.md)
