---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: 891c62692ce694e7e7238814a4dc30da59f7c98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205122"
---
# <span data-ttu-id="920c1-103">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="920c1-103">Get-PSSessionCapability</span></span>

## <span data-ttu-id="920c1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="920c1-104">SYNOPSIS</span></span>
<span data-ttu-id="920c1-105">Obtient les fonctionnalités d’un utilisateur spécifique sur une configuration de session avec restriction.</span><span class="sxs-lookup"><span data-stu-id="920c1-105">Gets the capabilities of a specific user on a constrained session configuration.</span></span>

## <span data-ttu-id="920c1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="920c1-106">SYNTAX</span></span>

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## <span data-ttu-id="920c1-107">Description</span><span class="sxs-lookup"><span data-stu-id="920c1-107">DESCRIPTION</span></span>

<span data-ttu-id="920c1-108">L’applet de commande **obtenir-PSSessionCapability** obtient les fonctionnalités d’un utilisateur spécifique sur une configuration de session avec restriction.</span><span class="sxs-lookup"><span data-stu-id="920c1-108">The **Get-PSSessionCapability** cmdlet gets the capabilities of a specific user on a constrained session configuration.</span></span>
<span data-ttu-id="920c1-109">Utilisez cette applet de commande pour auditer les configurations de session personnalisées pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="920c1-109">Use this cmdlet to audit customized session configurations for users.</span></span>

<span data-ttu-id="920c1-110">À compter de Windows PowerShell 5,0, vous pouvez utiliser la propriété **RoleDefinitions** dans un fichier de configuration de session (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="920c1-110">Starting in Windows PowerShell 5.0, you can use the **RoleDefinitions** property in a session configuration (.pssc) file.</span></span>
<span data-ttu-id="920c1-111">L’utilisation de cette propriété vous permet d’accorder aux utilisateurs des fonctionnalités différentes sur un point de terminaison unique en fonction de l’appartenance à un groupe.</span><span class="sxs-lookup"><span data-stu-id="920c1-111">Using this property lets you grant users different capabilities on a single constrained endpoint based on group membership.</span></span>
<span data-ttu-id="920c1-112">L’applet de commande **obtenir-PSSessionCapability** réduit la complexité lors de l’audit de ces points de terminaison en vous permettant de déterminer les fonctionnalités exactes accordées à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="920c1-112">The **Get-PSSessionCapability** cmdlet reduces complexity when auditing these endpoints by letting you determine the exact capabilities granted to a user.</span></span>

<span data-ttu-id="920c1-113">Par défaut, l’applet de commande **obtenir-PSSessionCapability** retourne une liste de commandes que l’utilisateur spécifié peut exécuter dans le point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="920c1-113">By default, the **Get-PSSessionCapability** cmdlet returns a list of commands the specified user can run in the specified endpoint.</span></span>
<span data-ttu-id="920c1-114">Cela équivaut à l’exécution de la **commande de commande** dans le point de terminaison spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="920c1-114">This is equivalent to the user running **Get-Command** in the specified endpoint.</span></span>
<span data-ttu-id="920c1-115">Quand elle est exécutée avec le paramètre *Full* , cette applet de commande retourne un objet **InitialSessionState** .</span><span class="sxs-lookup"><span data-stu-id="920c1-115">When run with the *Full* parameter, this cmdlet returns an **InitialSessionState** object.</span></span>
<span data-ttu-id="920c1-116">Cet objet contient des détails sur l’instance d’exécution PowerShell avec laquelle l’utilisateur spécifié interagit pour le point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="920c1-116">This object contains details about the PowerShell runspace the specified user would interact with for the specified endpoint.</span></span>
<span data-ttu-id="920c1-117">Il comprend des informations telles que le mode de langage, la stratégie d’exécution et les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="920c1-117">It includes information such as Language Mode, Execution Policy, and Environmental Variables.</span></span>

## <span data-ttu-id="920c1-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="920c1-118">EXAMPLES</span></span>

### <span data-ttu-id="920c1-119">Exemple 1 : obtenir les commandes disponibles pour un utilisateur</span><span class="sxs-lookup"><span data-stu-id="920c1-119">Example 1: Get commands available for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

<span data-ttu-id="920c1-120">Cet exemple retourne les commandes disponibles pour l’utilisateur CONTOSO\User lors de la connexion au point de terminaison con Endpoint1 sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="920c1-120">This example returns the commands available to the user CONTOSO\User when connecting to the Endpoint1 constrained endpoint on the local computer.</span></span>

### <span data-ttu-id="920c1-121">Exemple 2 : obtenir des détails sur une instance d’exécution pour un utilisateur</span><span class="sxs-lookup"><span data-stu-id="920c1-121">Example 2: Get details about a runspace for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

<span data-ttu-id="920c1-122">Cet exemple retourne des détails sur l’instance d’exécution avec laquelle l’utilisateur CONTOSO\User interagit lors de la connexion au point de terminaison avec restriction Endpoint1.</span><span class="sxs-lookup"><span data-stu-id="920c1-122">This example returns details about the runspace the user CONTOSO\User would interact with when connecting to the Endpoint1 constrained endpoint.</span></span>

## <span data-ttu-id="920c1-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="920c1-123">PARAMETERS</span></span>

### <span data-ttu-id="920c1-124">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="920c1-124">-ConfigurationName</span></span>

<span data-ttu-id="920c1-125">Spécifie la configuration de session avec restriction (point de terminaison) que vous Inspectez.</span><span class="sxs-lookup"><span data-stu-id="920c1-125">Specifies the constrained session configuration (endpoint) that you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="920c1-126">-Full</span><span class="sxs-lookup"><span data-stu-id="920c1-126">-Full</span></span>

<span data-ttu-id="920c1-127">Indique que cette applet de commande retourne l’intégralité de l’état de session initial pour l’utilisateur spécifié sur le point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="920c1-127">Indicates that this cmdlet returns the entire initial session state for the specified user at the specified constrained endpoint.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="920c1-128">-Username</span><span class="sxs-lookup"><span data-stu-id="920c1-128">-Username</span></span>

<span data-ttu-id="920c1-129">Spécifie l’utilisateur dont vous Inspectez les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="920c1-129">Specifies the user whose capabilities you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="920c1-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="920c1-130">CommonParameters</span></span>

<span data-ttu-id="920c1-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="920c1-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="920c1-132">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="920c1-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="920c1-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="920c1-133">INPUTS</span></span>

## <span data-ttu-id="920c1-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="920c1-134">OUTPUTS</span></span>

### <span data-ttu-id="920c1-135">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="920c1-135">System.Management.Automation.AliasInfo</span></span>

### <span data-ttu-id="920c1-136">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="920c1-136">System.Management.Automation.FunctionInfo</span></span>

### <span data-ttu-id="920c1-137">System.Management.Automation.Runspaces.InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="920c1-137">System.Management.Automation.Runspaces.InitialSessionState</span></span>

## <span data-ttu-id="920c1-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="920c1-138">NOTES</span></span>

## <span data-ttu-id="920c1-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="920c1-139">RELATED LINKS</span></span>

[<span data-ttu-id="920c1-140">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="920c1-140">New-PSRoleCapabilityFile</span></span>](New-PSRoleCapabilityFile.md)

