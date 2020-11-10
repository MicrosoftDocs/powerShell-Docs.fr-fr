---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: e3d1c5c071a334bddbfbc547ef2cc07e9e5c90aa
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388346"
---
# <span data-ttu-id="1611c-103">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="1611c-103">Add-Computer</span></span>

## <span data-ttu-id="1611c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1611c-104">SYNOPSIS</span></span>
<span data-ttu-id="1611c-105">Ajoutez l’ordinateur local à un domaine ou à un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="1611c-105">Add the local computer to a domain or workgroup.</span></span>

## <span data-ttu-id="1611c-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="1611c-106">SYNTAX</span></span>

### <span data-ttu-id="1611c-107">Domaine (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1611c-107">Domain (Default)</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1611c-108">Groupe de travail</span><span class="sxs-lookup"><span data-stu-id="1611c-108">Workgroup</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="1611c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="1611c-109">DESCRIPTION</span></span>

<span data-ttu-id="1611c-110">L' `Add-Computer` applet de commande ajoute l’ordinateur local ou les ordinateurs distants à un domaine ou à un groupe de travail, ou les déplace d’un domaine à un autre.</span><span class="sxs-lookup"><span data-stu-id="1611c-110">The `Add-Computer` cmdlet adds the local computer or remote computers to a domain or workgroup, or moves them from one domain to another.</span></span> <span data-ttu-id="1611c-111">Elle crée également un compte de domaine si l’ordinateur est ajouté sans compte au domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-111">It also creates a domain account if the computer is added to the domain without an account.</span></span>

<span data-ttu-id="1611c-112">Vous pouvez utiliser les paramètres de cette applet de commande pour spécifier une unité d’organisation (OU, Organizational Unit) et un contrôleur de domaine ou pour exécuter une jonction non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1611c-112">You can use the parameters of this cmdlet to specify an organizational unit (OU) and domain controller or to perform an unsecure join.</span></span>

<span data-ttu-id="1611c-113">Pour obtenir les résultats de la commande, utilisez les paramètres **Verbose** et **PassThru**.</span><span class="sxs-lookup"><span data-stu-id="1611c-113">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span>

## <span data-ttu-id="1611c-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1611c-114">EXAMPLES</span></span>

### <span data-ttu-id="1611c-115">Exemple 1 : ajouter un ordinateur local à un domaine, puis redémarrer l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="1611c-115">Example 1: Add a local computer to a domain then restart the computer</span></span>

```powershell
Add-Computer -DomainName Domain01 -Restart
```

<span data-ttu-id="1611c-116">Cette commande ajoute l’ordinateur local au domaine Domain01, puis redémarre l’ordinateur pour que le changement devienne effectif.</span><span class="sxs-lookup"><span data-stu-id="1611c-116">This command adds the local computer to the Domain01 domain and then restarts the computer to make the change effective.</span></span>

### <span data-ttu-id="1611c-117">Exemple 2 : ajouter un ordinateur local à un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="1611c-117">Example 2: Add a local computer to a workgroup</span></span>

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

<span data-ttu-id="1611c-118">Cette commande ajoute l’ordinateur local au groupe de travail Workgroup-A.</span><span class="sxs-lookup"><span data-stu-id="1611c-118">This command adds the local computer to the Workgroup-A workgroup.</span></span>

### <span data-ttu-id="1611c-119">Exemple 3 : ajouter un ordinateur local à un domaine</span><span class="sxs-lookup"><span data-stu-id="1611c-119">Example 3: Add a local computer to a domain</span></span>

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

<span data-ttu-id="1611c-120">Cette commande ajoute l’ordinateur local au domaine Domain01 à l’aide du contrôleur de domaine Domain01\DC01.</span><span class="sxs-lookup"><span data-stu-id="1611c-120">This command adds the local computer to the Domain01 domain by using the Domain01\DC01 domain controller.</span></span>

<span data-ttu-id="1611c-121">La commande utilise les paramètres **PassThru** et **Verbose** pour obtenir des informations détaillées sur les résultats de la commande.</span><span class="sxs-lookup"><span data-stu-id="1611c-121">The command uses the **PassThru** and **Verbose** parameters to get detailed information about the results of the command.</span></span>

### <span data-ttu-id="1611c-122">Exemple 4 : ajouter un ordinateur local à un domaine à l’aide du paramètre OUPath</span><span class="sxs-lookup"><span data-stu-id="1611c-122">Example 4: Add a local computer to a domain using the OUPath parameter</span></span>

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

<span data-ttu-id="1611c-123">Cette commande ajoute l’ordinateur local au domaine Domain02.</span><span class="sxs-lookup"><span data-stu-id="1611c-123">This command adds the local computer to the Domain02 domain.</span></span>
<span data-ttu-id="1611c-124">Elle utilise le paramètre OUPath pour spécifier l’unité d’organisation des nouveaux comptes.</span><span class="sxs-lookup"><span data-stu-id="1611c-124">It uses the OUPath parameter to specify the organizational unit for the new accounts.</span></span>

### <span data-ttu-id="1611c-125">Exemple 5 : ajouter un ordinateur local à un domaine à l’aide des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="1611c-125">Example 5: Add a local computer to a domain using credentials</span></span>

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

<span data-ttu-id="1611c-126">Cette commande ajoute l’ordinateur Server01 au domaine Domain02.</span><span class="sxs-lookup"><span data-stu-id="1611c-126">This command adds the Server01 computer to the Domain02 domain.</span></span> <span data-ttu-id="1611c-127">Elle utilise le paramètre **LocalCredential** pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à l’ordinateur Server01.</span><span class="sxs-lookup"><span data-stu-id="1611c-127">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the Server01 computer.</span></span> <span data-ttu-id="1611c-128">Elle utilise le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de joindre des ordinateurs au domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-128">It uses the **Credential** parameter to specify a user account that has permission to join computers to the domain.</span></span> <span data-ttu-id="1611c-129">Elle utilise le paramètre **Restart** pour redémarrer l’ordinateur à la fin de l’opération de jonction et le paramètre **Force** pour supprimer les messages de confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1611c-129">It uses the **Restart** parameter to restart the computer after the join operation completes and the **Force** parameter to suppress user confirmation messages.</span></span>

### <span data-ttu-id="1611c-130">Exemple 6 : déplacer un groupe d’ordinateurs vers un nouveau domaine</span><span class="sxs-lookup"><span data-stu-id="1611c-130">Example 6: Move a group of computers to a new domain</span></span>

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="1611c-131">Cette commande déplace les ordinateurs Server01 et Server02, et l’ordinateur local, de Domain01 vers Domain02.</span><span class="sxs-lookup"><span data-stu-id="1611c-131">This command moves the Server01 and Server02 computers, and the local computer, from Domain01 to Domain02.</span></span>

<span data-ttu-id="1611c-132">Elle utilise le paramètre **LocalCredential** pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter aux trois ordinateurs concernés.</span><span class="sxs-lookup"><span data-stu-id="1611c-132">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the three affected computers.</span></span> <span data-ttu-id="1611c-133">Elle utilise le paramètre **UnjoinDomainCredential** pour spécifier un compte d’utilisateur qui a l’autorisation de disjoindre les ordinateurs du domaine Domain01 et le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de joindre les ordinateurs au domaine Domain02.</span><span class="sxs-lookup"><span data-stu-id="1611c-133">It uses the **UnjoinDomainCredential** parameter to specify a user account that has permission to unjoin the computers from the Domain01 domain and the **Credential** parameter to specify a user account that has permission to join the computers to the Domain02 domain.</span></span> <span data-ttu-id="1611c-134">Elle utilise le paramètre **Restart** pour redémarrer les trois ordinateurs une fois le déplacement terminé.</span><span class="sxs-lookup"><span data-stu-id="1611c-134">It uses the **Restart** parameter to restart all three computers after the move is complete.</span></span>

### <span data-ttu-id="1611c-135">Exemple 7 : déplacement d’un ordinateur vers un nouveau domaine et modification du nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="1611c-135">Example 7: Move a computer to a new domain and change the name of the computer</span></span>

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="1611c-136">Cette commande déplace l’ordinateur Server01 vers le domaine Domain02 et remplace le nom d’ordinateur par Server044.</span><span class="sxs-lookup"><span data-stu-id="1611c-136">This command moves the Server01 computer to the Domain02 and changes the machine name to Server044.</span></span>

<span data-ttu-id="1611c-137">La commande utilise les informations d’identification de l’utilisateur actuel pour se connecter à l’ordinateur Server01 et le disjoindre de son domaine actuel.</span><span class="sxs-lookup"><span data-stu-id="1611c-137">The command uses the credential of the current user to connect to the Server01 computer and unjoin it from its current domain.</span></span> <span data-ttu-id="1611c-138">Elle utilise le paramètre **Credential** pour spécifier un compte d’utilisateur qui a l’autorisation de joindre l’ordinateur au domaine Domain02.</span><span class="sxs-lookup"><span data-stu-id="1611c-138">It uses the **Credential** parameter to specify a user account that has permission to join the computer to the Domain02 domain.</span></span>

### <span data-ttu-id="1611c-139">Exemple 8 : ajouter des ordinateurs listés dans un fichier à un nouveau domaine</span><span class="sxs-lookup"><span data-stu-id="1611c-139">Example 8: Add computers listed in a file to a new domain</span></span>

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

<span data-ttu-id="1611c-140">Cette commande ajoute les ordinateurs qui sont répertoriés dans le fichier Servers.txt au domaine Domain02.</span><span class="sxs-lookup"><span data-stu-id="1611c-140">This command adds the computers that are listed in the Servers.txt file to the Domain02 domain.</span></span> <span data-ttu-id="1611c-141">Elle utilise le paramètre **Options** pour spécifier l’option **Win9xUpgrade**.</span><span class="sxs-lookup"><span data-stu-id="1611c-141">It uses the **Options** parameter to specify the **Win9xUpgrade** option.</span></span> <span data-ttu-id="1611c-142">Le paramètre **Restart** redémarre tous les ordinateurs nouvellement ajoutés à la fin de l'opération de jonction.</span><span class="sxs-lookup"><span data-stu-id="1611c-142">The **Restart** parameter restarts all of the newly added computers after the join operation completes.</span></span>

### <span data-ttu-id="1611c-143">Exemple 9 : ajouter un ordinateur à un domaine à l’aide des informations d’identification prédéfinies de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="1611c-143">Example 9: Add a computer to a domain using predefined computer credentials</span></span>

<span data-ttu-id="1611c-144">Cette première commande doit être exécutée par un administrateur à partir d’un ordinateur qui est déjà joint au domaine `Domain03` :</span><span class="sxs-lookup"><span data-stu-id="1611c-144">This first command should be run by an administrator from a computer that is already joined to domain `Domain03`:</span></span>

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

<span data-ttu-id="1611c-145">Cette combinaison de commandes crée un nouveau compte d’ordinateur avec un nom prédéfini et un mot de passe de jointure temporaire dans un domaine à l’aide d’un ordinateur joint à un domaine existant.</span><span class="sxs-lookup"><span data-stu-id="1611c-145">This combination of commands creates a new computer account with a predefined name and temporary join password in a domain using an existing domain-joined computer.</span></span> <span data-ttu-id="1611c-146">Ensuite, un ordinateur avec le nom prédéfini joint le domaine en utilisant uniquement le nom de l’ordinateur et le mot de passe de jointure temporaire.</span><span class="sxs-lookup"><span data-stu-id="1611c-146">Then separately, a computer with the predefined name joins the domain using only the computer name and the temporary join password.</span></span>
<span data-ttu-id="1611c-147">Le mot de passe prédéfini est utilisé uniquement pour prendre en charge l’opération de jointure et est remplacé dans le cadre des procédures de compte d’ordinateur normales une fois que l’ordinateur a terminé la jonction.</span><span class="sxs-lookup"><span data-stu-id="1611c-147">The predefined password is only used to support the join operation and is replaced as part of normal computer account procedures after the computer completes the join.</span></span>

## <span data-ttu-id="1611c-148">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="1611c-148">PARAMETERS</span></span>

### <span data-ttu-id="1611c-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1611c-149">-ComputerName</span></span>

<span data-ttu-id="1611c-150">Spécifie les ordinateurs à ajouter à un domaine ou à un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="1611c-150">Specifies the computers to add to a domain or workgroup.</span></span>
<span data-ttu-id="1611c-151">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1611c-151">The default is the local computer.</span></span>

<span data-ttu-id="1611c-152">Tapez le nom NetBIOS, une adresse IP (Internet Protocol) ou un nom de domaine complet de chacun des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="1611c-152">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of each of the remote computers.</span></span> <span data-ttu-id="1611c-153">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point ( `.` ) ou « localhost ».</span><span class="sxs-lookup"><span data-stu-id="1611c-153">To specify the local computer, type the computer name, a dot (`.`), or "localhost".</span></span>

<span data-ttu-id="1611c-154">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1611c-154">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="1611c-155">Vous pouvez utiliser le paramètre **ComputerName** de `Add-Computer` même si votre ordinateur n’est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="1611c-155">You can use the **ComputerName** parameter of `Add-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="1611c-156">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1611c-156">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="1611c-157">-Credential</span></span>

<span data-ttu-id="1611c-158">Spécifie un compte d’utilisateur qui a l’autorisation de joindre les ordinateurs à un nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-158">Specifies a user account that has permission to join the computers to a new domain.</span></span>
<span data-ttu-id="1611c-159">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="1611c-159">The default is the current user.</span></span>

<span data-ttu-id="1611c-160">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="1611c-160">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1611c-161">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="1611c-161">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="1611c-162">Pour spécifier un compte d’utilisateur qui a l’autorisation de supprimer l’ordinateur de son domaine actuel, utilisez le paramètre **UnjoinDomainCredential**.</span><span class="sxs-lookup"><span data-stu-id="1611c-162">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span> <span data-ttu-id="1611c-163">Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à un ordinateur distant, utilisez le paramètre **LocalCredential**.</span><span class="sxs-lookup"><span data-stu-id="1611c-163">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-164">-DomainName</span><span class="sxs-lookup"><span data-stu-id="1611c-164">-DomainName</span></span>

<span data-ttu-id="1611c-165">Spécifie le domaine auquel les ordinateurs sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="1611c-165">Specifies the domain to which the computers are added.</span></span> <span data-ttu-id="1611c-166">Ce paramètre est obligatoire lors de l’ajout des ordinateurs à un domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-166">This parameter is required when adding the computers to a domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-167">-Force</span><span class="sxs-lookup"><span data-stu-id="1611c-167">-Force</span></span>

<span data-ttu-id="1611c-168">Supprime la demande de confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1611c-168">Suppresses the user confirmation prompt.</span></span> <span data-ttu-id="1611c-169">Sans ce paramètre, `Add-Computer` vous devez confirmer l’ajout de chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1611c-169">Without this parameter, `Add-Computer` requires you to confirm the addition of each computer.</span></span>

<span data-ttu-id="1611c-170">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1611c-170">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-171">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="1611c-171">-LocalCredential</span></span>

<span data-ttu-id="1611c-172">Spécifie un compte d’utilisateur qui a l’autorisation de se connecter aux ordinateurs spécifiés par le paramètre **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="1611c-172">Specifies a user account that has permission to connect to the computers that are specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="1611c-173">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="1611c-173">The default is the current user.</span></span>

<span data-ttu-id="1611c-174">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="1611c-174">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1611c-175">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="1611c-175">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="1611c-176">Pour spécifier un compte d’utilisateur qui a l’autorisation d’ajouter les ordinateurs à un nouveau domaine, utilisez le paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="1611c-176">To specify a user account that has permission to add the computers to a new domain, use the **Credential** parameter.</span></span> <span data-ttu-id="1611c-177">Pour spécifier un compte d’utilisateur qui a l’autorisation de supprimer les ordinateurs de leur domaine actuel, utilisez le paramètre **UnjoinDomainCredential**.</span><span class="sxs-lookup"><span data-stu-id="1611c-177">To specify a user account that has permission to remove the computers from their current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="1611c-178">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1611c-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-179">-NewName</span><span class="sxs-lookup"><span data-stu-id="1611c-179">-NewName</span></span>

<span data-ttu-id="1611c-180">Spécifie un nouveau nom pour l’ordinateur dans le nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-180">Specifies a new name for the computer in the new domain.</span></span> <span data-ttu-id="1611c-181">Ce paramètre n’est valide que lorsqu’un ordinateur est ajouté ou déplacé.</span><span class="sxs-lookup"><span data-stu-id="1611c-181">This parameter is valid only when one computer is being added or moved.</span></span>

<span data-ttu-id="1611c-182">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1611c-182">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-183">-Options</span><span class="sxs-lookup"><span data-stu-id="1611c-183">-Options</span></span>

<span data-ttu-id="1611c-184">Spécifie les options avancées pour l’opération de jonction **Add-Computer** .</span><span class="sxs-lookup"><span data-stu-id="1611c-184">Specifies advanced options for the **Add-Computer** join operation.</span></span> <span data-ttu-id="1611c-185">Entrez une ou plusieurs valeurs dans une chaîne séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="1611c-185">Enter one or more values in a comma-separated string.</span></span>

<span data-ttu-id="1611c-186">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="1611c-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1611c-187">**AccountCreate** : crée un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-187">**AccountCreate** : Creates a domain account.</span></span> <span data-ttu-id="1611c-188">L’applet de commande **Add-Computer** crée automatiquement un compte de domaine lorsqu’il ajoute un ordinateur à un domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-188">The **Add-Computer** cmdlet automatically creates a domain account when it adds a computer to a domain.</span></span> <span data-ttu-id="1611c-189">Cette option est incluse par exhaustivité.</span><span class="sxs-lookup"><span data-stu-id="1611c-189">This option is included for completeness.</span></span>

- <span data-ttu-id="1611c-190">**Win9XUpgrade** : indique que l’opération de jointure fait partie d’une mise à niveau du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="1611c-190">**Win9XUpgrade** : Indicates that the join operation is part of a Windows operating system upgrade.</span></span>

- <span data-ttu-id="1611c-191">**UnsecuredJoin** : effectue une jointure non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1611c-191">**UnsecuredJoin** : Performs an unsecured join.</span></span> <span data-ttu-id="1611c-192">Pour demander une jointure non sécurisée, utilisez le paramètre *unsecure* ou cette option.</span><span class="sxs-lookup"><span data-stu-id="1611c-192">To request an unsecured join, use the *Unsecure* parameter or this option.</span></span> <span data-ttu-id="1611c-193">Si vous souhaitez transmettre un mot de passe d’ordinateur, vous devez utiliser cette option conjointement avec l' `PasswordPass` option.</span><span class="sxs-lookup"><span data-stu-id="1611c-193">If you want to pass a machine password, then you must use this option in combination with `PasswordPass` option.</span></span>

- <span data-ttu-id="1611c-194">**PasswordPass** : définit le mot de passe de l’ordinateur à la valeur du paramètre *Credential* (DomainCredential) après l’exécution d’une jointure non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1611c-194">**PasswordPass** : Sets the machine password to the value of the *Credential* (DomainCredential) parameter after performing an unsecured join.</span></span> <span data-ttu-id="1611c-195">Cette option indique également que la valeur du paramètre *Credential* (DomainCredential) est un mot de passe d’ordinateur et non un mot de passe d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1611c-195">This option also indicates that the value of the *Credential* (DomainCredential) parameter is a machine password, not a user password.</span></span> <span data-ttu-id="1611c-196">Cette option est valide uniquement lorsque l' `UnsecuredJoin` option est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1611c-196">This option is valid only when the `UnsecuredJoin` option is specified.</span></span> <span data-ttu-id="1611c-197">Lorsque cette option est utilisée, les informations d’identification fournies au `-Credential` paramètre *doivent* avoir un nom d’utilisateur null.</span><span class="sxs-lookup"><span data-stu-id="1611c-197">When using this option, the credential provided to the `-Credential` parameter *must* have a null username.</span></span>

- <span data-ttu-id="1611c-198">**JoinWithNewName** : renomme le nom de l’ordinateur dans le nouveau domaine par le nom spécifié par le paramètre *NewName* .</span><span class="sxs-lookup"><span data-stu-id="1611c-198">**JoinWithNewName** : Renames the computer name in the new domain to the name specified by the *NewName* parameter.</span></span> <span data-ttu-id="1611c-199">Lorsque vous utilisez le paramètre *NewName* , cette option est définie automatiquement.</span><span class="sxs-lookup"><span data-stu-id="1611c-199">When you use the *NewName* parameter, this option is set automatically.</span></span> <span data-ttu-id="1611c-200">Cette option est conçue pour être utilisée avec l’applet de commande Rename-Computer.</span><span class="sxs-lookup"><span data-stu-id="1611c-200">This option is designed to be used with the Rename-Computer cmdlet.</span></span> <span data-ttu-id="1611c-201">Si vous utilisez l’applet de commande **Rename-Computer** pour renommer l’ordinateur, mais que vous ne redémarrez pas l’ordinateur pour que la modification soit effective, vous pouvez utiliser ce paramètre pour joindre l’ordinateur à un domaine avec son nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="1611c-201">If you use the **Rename-Computer** cmdlet to rename the computer, but do not restart the computer to make the change effective, you can use this parameter to join the computer to a domain with its new name.</span></span>

- <span data-ttu-id="1611c-202">**JoinReadOnly** : utilise un compte d’ordinateur existant pour joindre l’ordinateur à un contrôleur de domaine en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="1611c-202">**JoinReadOnly** : Uses an existing machine account to join the computer to a read-only domain controller.</span></span> <span data-ttu-id="1611c-203">Le compte d’ordinateur doit être ajouté à la liste autorisée pour la stratégie de réplication de mot de passe et le mot de passe du compte doit être répliqué sur le contrôleur de domaine en lecture seule avant l’opération de jointure.</span><span class="sxs-lookup"><span data-stu-id="1611c-203">The machine account must be added to the allowed list for password replication policy and the account password must be replicated to the read-only domain controller prior to the join operation.</span></span>

- <span data-ttu-id="1611c-204">**InstallInvoke** : définit les indicateurs de création (0X2) et de suppression (0x4) du paramètre **FJoinOptions** de la méthode **JoinDomainOrWorkGroup** .</span><span class="sxs-lookup"><span data-stu-id="1611c-204">**InstallInvoke** : Sets the create (0x2) and delete (0x4) flags of the **FJoinOptions** parameter of the **JoinDomainOrWorkgroup** method.</span></span> <span data-ttu-id="1611c-205">Pour plus d’informations sur la méthode **JoinDomainOrWorkGroup** , consultez [méthode JoinDomainOrWorkGroup de la classe Win32_ComputerSystem](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem).</span><span class="sxs-lookup"><span data-stu-id="1611c-205">For more information about the **JoinDomainOrWorkgroup** method, see [JoinDomainOrWorkgroup method of the Win32_ComputerSystem class](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem).</span></span>
  <span data-ttu-id="1611c-206">Pour plus d’informations sur ces options, consultez [fonction NetJoinDomain](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain).</span><span class="sxs-lookup"><span data-stu-id="1611c-206">For more information about these options, see [NetJoinDomain function](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain).</span></span>

<span data-ttu-id="1611c-207">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1611c-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-208">-OUPath</span><span class="sxs-lookup"><span data-stu-id="1611c-208">-OUPath</span></span>

<span data-ttu-id="1611c-209">Spécifie une unité d’organisation pour le compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-209">Specifies an organizational unit (OU) for the domain account.</span></span> <span data-ttu-id="1611c-210">Entrez le nom unique complet de l’unité d’organisation entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="1611c-210">Enter the full distinguished name of the OU in quotation marks.</span></span> <span data-ttu-id="1611c-211">La valeur par défaut est l’unité d’organisation par défaut des objets ordinateur du domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-211">The default value is the default OU for machine objects in the domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-212">-PassThru</span><span class="sxs-lookup"><span data-stu-id="1611c-212">-PassThru</span></span>

<span data-ttu-id="1611c-213">Retourne un objet représentant l’élément que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="1611c-213">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="1611c-214">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="1611c-214">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1611c-215">-Restart</span><span class="sxs-lookup"><span data-stu-id="1611c-215">-Restart</span></span>

<span data-ttu-id="1611c-216">Redémarre les ordinateurs qui ont été ajoutés au domaine ou au groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="1611c-216">Restarts the computers that were added to the domain or workgroup.</span></span> <span data-ttu-id="1611c-217">Un redémarrage est souvent nécessaire pour que le changement devienne effectif.</span><span class="sxs-lookup"><span data-stu-id="1611c-217">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="1611c-218">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1611c-218">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-219">-Server</span><span class="sxs-lookup"><span data-stu-id="1611c-219">-Server</span></span>

<span data-ttu-id="1611c-220">Spécifie le nom d’un contrôleur de domaine qui ajoute l’ordinateur au domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-220">Specifies the name of a domain controller that adds the computer to the domain.</span></span> <span data-ttu-id="1611c-221">Entrez le nom sous la forme DomainName\ComputerName.</span><span class="sxs-lookup"><span data-stu-id="1611c-221">Enter the name in DomainName\ComputerName format.</span></span> <span data-ttu-id="1611c-222">Par défaut, aucun contrôleur de domaine n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1611c-222">By default, no domain controller is specified.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-223">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="1611c-223">-UnjoinDomainCredential</span></span>

<span data-ttu-id="1611c-224">Spécifie un compte d’utilisateur qui a l’autorisation de supprimer les ordinateurs de leurs domaines actuels.</span><span class="sxs-lookup"><span data-stu-id="1611c-224">Specifies a user account that has permission to remove the computers from their current domains.</span></span> <span data-ttu-id="1611c-225">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="1611c-225">The default is the current user.</span></span>

<span data-ttu-id="1611c-226">Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="1611c-226">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1611c-227">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="1611c-227">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="1611c-228">Utilisez ce paramètre lorsque vous déplacez des ordinateurs vers un autre domaine.</span><span class="sxs-lookup"><span data-stu-id="1611c-228">Use this parameter when you are moving computers to a different domain.</span></span> <span data-ttu-id="1611c-229">Pour spécifier un compte d’utilisateur qui a l’autorisation de joindre le nouveau domaine, utilisez le paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="1611c-229">To specify a user account that has permission to join the new domain, use the **Credential** parameter.</span></span> <span data-ttu-id="1611c-230">Pour spécifier un compte d’utilisateur qui a l’autorisation de se connecter à un ordinateur distant, utilisez le paramètre **LocalCredential**.</span><span class="sxs-lookup"><span data-stu-id="1611c-230">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="1611c-231">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1611c-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-232">-Non sécurisé</span><span class="sxs-lookup"><span data-stu-id="1611c-232">-Unsecure</span></span>

<span data-ttu-id="1611c-233">Exécute une jonction non sécurisée au domaine spécifié.</span><span class="sxs-lookup"><span data-stu-id="1611c-233">Performs an unsecure join to the specified domain.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-234">-WorkgroupName</span><span class="sxs-lookup"><span data-stu-id="1611c-234">-WorkgroupName</span></span>

<span data-ttu-id="1611c-235">Spécifie le nom d'un groupe de travail auquel les ordinateurs sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="1611c-235">Specifies the name of a workgroup to which the computers are added.</span></span> <span data-ttu-id="1611c-236">La valeur par défaut est « WORKGROUP ».</span><span class="sxs-lookup"><span data-stu-id="1611c-236">The default value is "WORKGROUP".</span></span>

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1611c-237">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1611c-237">-Confirm</span></span>

<span data-ttu-id="1611c-238">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1611c-238">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1611c-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1611c-239">-WhatIf</span></span>

<span data-ttu-id="1611c-240">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1611c-240">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1611c-241">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="1611c-241">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1611c-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1611c-242">CommonParameters</span></span>

<span data-ttu-id="1611c-243">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1611c-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1611c-244">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1611c-244">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1611c-245">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1611c-245">INPUTS</span></span>

### <span data-ttu-id="1611c-246">System.String</span><span class="sxs-lookup"><span data-stu-id="1611c-246">System.String</span></span>

<span data-ttu-id="1611c-247">Vous pouvez diriger les noms d’ordinateurs et les nouveaux noms vers l’applet de commande `Add-Computer` .</span><span class="sxs-lookup"><span data-stu-id="1611c-247">You can pipe computer names and new names to the `Add-Computer` Cmdlet.</span></span>

## <span data-ttu-id="1611c-248">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1611c-248">OUTPUTS</span></span>

### <span data-ttu-id="1611c-249">Microsoft. PowerShell. Commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="1611c-249">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="1611c-250">Quand vous utilisez le paramètre **PassThru** , `Add-Computer` retourne un objet **ComputerChangeInfo** .</span><span class="sxs-lookup"><span data-stu-id="1611c-250">When you use the **PassThru** parameter, `Add-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="1611c-251">Sinon, cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="1611c-251">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="1611c-252">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1611c-252">NOTES</span></span>

- <span data-ttu-id="1611c-253">Dans Windows PowerShell 2,0, le paramètre de **serveur** de `Add-Computer` échoue même lorsque le serveur est présent.</span><span class="sxs-lookup"><span data-stu-id="1611c-253">In Windows PowerShell 2.0, the **Server** parameter of `Add-Computer` fails even when the server is present.</span></span> <span data-ttu-id="1611c-254">Dans Windows PowerShell 3.0, l’implémentation du paramètre **Server** est modifiée pour qu’il fonctionne de façon fiable.</span><span class="sxs-lookup"><span data-stu-id="1611c-254">In Windows PowerShell 3.0, the implementation of the **Server** parameter is changed so that it works reliably.</span></span>

## <span data-ttu-id="1611c-255">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1611c-255">RELATED LINKS</span></span>

[<span data-ttu-id="1611c-256">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="1611c-256">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="1611c-257">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="1611c-257">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="1611c-258">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="1611c-258">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="1611c-259">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="1611c-259">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="1611c-260">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="1611c-260">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="1611c-261">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="1611c-261">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="1611c-262">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="1611c-262">Test-Connection</span></span>](Test-Connection.md)
