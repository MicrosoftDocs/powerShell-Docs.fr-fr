---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203530"
---
# <span data-ttu-id="db637-103">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="db637-103">Reset-ComputerMachinePassword</span></span>

## <span data-ttu-id="db637-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="db637-104">SYNOPSIS</span></span>
<span data-ttu-id="db637-105">Réinitialise le mot de passe du compte ordinateur de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="db637-105">Resets the machine account password for the computer.</span></span>

## <span data-ttu-id="db637-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="db637-106">SYNTAX</span></span>

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="db637-107">Description</span><span class="sxs-lookup"><span data-stu-id="db637-107">DESCRIPTION</span></span>
<span data-ttu-id="db637-108">L’applet de commande **Reset-ComputerMachinePassword** change le mot de passe du compte d’ordinateur utilisé par les ordinateurs pour s’authentifier auprès des contrôleurs de domaine du domaine.</span><span class="sxs-lookup"><span data-stu-id="db637-108">The **Reset-ComputerMachinePassword** cmdlet changes the computer account password that the computers use to authenticate to the domain controllers in the domain.</span></span>
<span data-ttu-id="db637-109">Vous pouvez l’utiliser pour réinitialiser le mot de passe de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="db637-109">You can use it to reset the password of the local computer.</span></span>

## <span data-ttu-id="db637-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="db637-110">EXAMPLES</span></span>

### <span data-ttu-id="db637-111">Exemple 1 : réinitialiser le mot de passe de l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="db637-111">Example 1: Reset the password for the local computer</span></span>

```
PS C:\> Reset-ComputerMachinePassword
```

<span data-ttu-id="db637-112">Cette commande réinitialise le mot de passe de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="db637-112">This command resets the computer password for the local computer.</span></span>
<span data-ttu-id="db637-113">La commande s’exécute avec les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="db637-113">The command runs with the credentials of the current user.</span></span>

### <span data-ttu-id="db637-114">Exemple 2 : réinitialiser le mot de passe de l’ordinateur local à l’aide d’un contrôleur de domaine spécifié</span><span class="sxs-lookup"><span data-stu-id="db637-114">Example 2: Reset the password for the local computer by using a specified domain controller</span></span>

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

<span data-ttu-id="db637-115">Cette commande réinitialise le mot de passe de l’ordinateur local à l’aide du contrôleur de domaine DC01.</span><span class="sxs-lookup"><span data-stu-id="db637-115">This command resets the computer password of the local computer by using the DC01 domain controller.</span></span>
<span data-ttu-id="db637-116">Elle utilise le paramètre *Credential* pour spécifier un compte d’utilisateur qui a l’autorisation de réinitialiser un mot de passe d’ordinateur dans le domaine.</span><span class="sxs-lookup"><span data-stu-id="db637-116">It uses the *Credential* parameter to specify a user account that has permission to reset a computer password in the domain.</span></span>

### <span data-ttu-id="db637-117">Exemple 3 : réinitialiser le mot de passe sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="db637-117">Example 3: Reset the password on a remote computer</span></span>

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

<span data-ttu-id="db637-118">Cette commande utilise l’applet de commande Invoke-Command pour exécuter une commande **Reset-ComputerMachinePassword** sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="db637-118">This command uses the Invoke-Command cmdlet to run a **Reset-ComputerMachinePassword** command on the Server01 remote computer.</span></span>

<span data-ttu-id="db637-119">Pour plus d'informations sur les commandes à distance dans Windows PowerShell, consultez about_Remote et **Invoke-Command** .</span><span class="sxs-lookup"><span data-stu-id="db637-119">For more information about remote commands in Windows PowerShell, see about_Remote and **Invoke-Command** .</span></span>

## <span data-ttu-id="db637-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db637-120">PARAMETERS</span></span>

### <span data-ttu-id="db637-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="db637-121">-Credential</span></span>
<span data-ttu-id="db637-122">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="db637-122">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="db637-123">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="db637-123">The default is the current user.</span></span>

<span data-ttu-id="db637-124">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="db637-124">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="db637-125">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="db637-125">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="db637-126">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="db637-126">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db637-127">-Server</span><span class="sxs-lookup"><span data-stu-id="db637-127">-Server</span></span>
<span data-ttu-id="db637-128">Spécifie le nom d’un contrôleur de domaine à utiliser lorsque cette applet de commande définit le mot de passe du compte d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="db637-128">Specifies the name of a domain controller to use when this cmdlet sets the computer account password.</span></span>

<span data-ttu-id="db637-129">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="db637-129">This parameter is optional.</span></span>
<span data-ttu-id="db637-130">Si vous omettez ce paramètre, un contrôleur de domaine est choisi pour exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="db637-130">If you omit this parameter, a domain controller is chosen to service the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db637-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="db637-131">-Confirm</span></span>
<span data-ttu-id="db637-132">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db637-132">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db637-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="db637-133">-WhatIf</span></span>
<span data-ttu-id="db637-134">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db637-134">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="db637-135">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="db637-135">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db637-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db637-136">CommonParameters</span></span>
<span data-ttu-id="db637-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="db637-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db637-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="db637-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="db637-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="db637-139">INPUTS</span></span>

### <span data-ttu-id="db637-140">Aucun</span><span class="sxs-lookup"><span data-stu-id="db637-140">None</span></span>
<span data-ttu-id="db637-141">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="db637-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="db637-142">SORTIES</span><span class="sxs-lookup"><span data-stu-id="db637-142">OUTPUTS</span></span>

### <span data-ttu-id="db637-143">Aucun</span><span class="sxs-lookup"><span data-stu-id="db637-143">None</span></span>
<span data-ttu-id="db637-144">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="db637-144">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="db637-145">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="db637-145">NOTES</span></span>

## <span data-ttu-id="db637-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="db637-146">RELATED LINKS</span></span>

## <span data-ttu-id="db637-147">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="db637-147">RELATED LINKS</span></span>
