---
ms.topic: reference
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: Applets de commande d’Accès Web PowerShell
ms.openlocfilehash: 34a7a01f154b2e43416dfe8ea43d4d8e937816d9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188018"
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="8b0c1-103">Applets de commande d’accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b0c1-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="8b0c1-104">Cette rubrique d’informations de référence contient les descriptions et la syntaxe de toutes les applets de commande spécifiques à Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="8b0c1-105">Elle répertorie les applets de commande par ordre alphabétique en fonction du verbe situé au début de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="8b0c1-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b0c1-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="8b0c1-107">Ajoute une nouvelle règle d’autorisation à l’ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="8b0c1-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b0c1-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="8b0c1-109">Retourne un ensemble des règles d’autorisation d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="8b0c1-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8b0c1-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="8b0c1-111">Configure l’application web Accès Web Windows PowerShell dans IIS.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="8b0c1-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b0c1-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="8b0c1-113">Supprime une règle d’autorisation spécifiée d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="8b0c1-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b0c1-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="8b0c1-115">Teste les règles d’autorisation pour vérifier qu’une demande d’accès d’un utilisateur, d’un ordinateur ou d’un point de terminaison particulier est autorisée.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="8b0c1-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8b0c1-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="8b0c1-117">Désinstalle l’application Accès Web Windows PowerShell d’IIS.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="8b0c1-118">**Remarque** :</span><span class="sxs-lookup"><span data-stu-id="8b0c1-118">**Note**:</span></span>
>
><span data-ttu-id="8b0c1-119">Pour répertorier toutes les applets de commande disponibles, utilisez l’applet de commande :</span><span class="sxs-lookup"><span data-stu-id="8b0c1-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="8b0c1-120">`Get-Command –Module PowerShellWebAccess`.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="8b0c1-121">Pour plus d’informations sur les cmdlets et leur syntaxe, utilisez : `Get-Help `*&lt;nom de la cmdlet&gt;* où *&lt;nom de la cmdlet&gt;* correspond au nom de la cmdlet que vous recherchez.</span><span class="sxs-lookup"><span data-stu-id="8b0c1-121">For more information about, or for the syntax of, any of the cmdlets, use: `Get-Help `*&lt;cmdlet name&gt;* where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="8b0c1-122">Pour obtenir des informations plus détaillées, vous pouvez exécuter l'une des applets de commande suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b0c1-122">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="8b0c1-123">`Get-Help `*&lt;nom_applet_de_commande&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="8b0c1-123">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="8b0c1-124">`Get-Help `*&lt;nom_applet_de_commande&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="8b0c1-124">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="8b0c1-125">`Get-Help `*&lt;nom_applet_de_commande&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="8b0c1-125">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="8b0c1-126">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="8b0c1-126">More Information</span></span>

<span data-ttu-id="8b0c1-127">Pour plus d’informations sur Accès Web PowerShell, consultez :</span><span class="sxs-lookup"><span data-stu-id="8b0c1-127">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="8b0c1-128">Installer et utiliser Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b0c1-128">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)