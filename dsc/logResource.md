---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Log dans DSC
ms.openlocfilehash: 50fd6cd31ba426108830fcf124a767318060a95d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268430"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="2ceb2-103">Ressource Log dans DSC</span><span class="sxs-lookup"><span data-stu-id="2ceb2-103">DSC Log Resource</span></span>

<span data-ttu-id="2ceb2-104">_S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="2ceb2-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="2ceb2-105">La ressource __Log__ dans DSC (Desired State Configuration) Windows PowerShell fournit un mécanisme permettant d’écrire des messages dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="2ceb2-106">Par défaut, seuls les journaux des opérations relatifs à DSC sont activés.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="2ceb2-107">Pour que le journal d’analyse soit disponible ou visible, il doit être activé.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="2ceb2-108">Pour plus d’informations, consultez [Où se trouvent les journaux des événements DSC ?](troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="2ceb2-108">For more information, see [Where are DSC Event Logs?](troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="2ceb2-109">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2ceb2-109">Properties</span></span>

| <span data-ttu-id="2ceb2-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="2ceb2-110">Property</span></span> | <span data-ttu-id="2ceb2-111">Description</span><span class="sxs-lookup"><span data-stu-id="2ceb2-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2ceb2-112">Message</span><span class="sxs-lookup"><span data-stu-id="2ceb2-112">Message</span></span>| <span data-ttu-id="2ceb2-113">Indique le message à écrire dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="2ceb2-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2ceb2-114">DependsOn</span></span> | <span data-ttu-id="2ceb2-115">Indique que la configuration d’une autre ressource doit être exécutée avant l’écriture de ce message dans le journal.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="2ceb2-116">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="2ceb2-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ceb2-117">Example</span></span>

<span data-ttu-id="2ceb2-118">L’exemple suivant écrit un message dans le journal des événements Microsoft-Windows-Desired State Configuration/Analytic.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="2ceb2-119">Si vous exécutez [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) avec cette ressource configurée, elle retourne toujours la valeur **$false**.</span><span class="sxs-lookup"><span data-stu-id="2ceb2-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```