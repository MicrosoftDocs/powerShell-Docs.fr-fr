---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 7ec2c3025f62a64cd24298c0749d40fa5eff4904
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346086"
---
# <span data-ttu-id="0e791-103">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="0e791-103">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="0e791-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="0e791-104">SYNOPSIS</span></span>
<span data-ttu-id="0e791-105">Convertit une chaîne SDDL en objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0e791-105">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="0e791-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="0e791-106">SYNTAX</span></span>

### <span data-ttu-id="0e791-107">Tous</span><span class="sxs-lookup"><span data-stu-id="0e791-107">All</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## <span data-ttu-id="0e791-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e791-108">DESCRIPTION</span></span>

<span data-ttu-id="0e791-109">L' `ConvertFrom-SddlString` applet de commande convertit une chaîne de langage de définition de descripteur de sécurité en objet **PSCustomObject** personnalisé avec les propriétés suivantes : Owner, Group, DiscretionaryAcl, SystemAcl et RawDescriptor.</span><span class="sxs-lookup"><span data-stu-id="0e791-109">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="0e791-110">Les propriétés Owner, Group, DiscretionaryAcl et SystemAcl contiennent une représentation textuelle lisible des droits d’accès spécifiés dans une chaîne SDDL.</span><span class="sxs-lookup"><span data-stu-id="0e791-110">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="0e791-111">Cette applet de commande a été introduite dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="0e791-111">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="0e791-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0e791-112">EXAMPLES</span></span>

### <span data-ttu-id="0e791-113">Exemple 1 : convertir les SDDL droits d’accès du système de fichiers en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0e791-113">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="0e791-114">La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité pour le dossier C:\Windows et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="0e791-114">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="0e791-115">La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0e791-115">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="0e791-116">Exemple 2 : convertir les SDDL droits d’accès du registre en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0e791-116">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="0e791-117">La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité de la clé HKLM : \ SOFTWARE\Microsoft\ et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="0e791-117">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="0e791-118">La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0e791-118">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="0e791-119">Elle utilise le `-Type` paramètre pour spécifier que la chaîne SDDL représente un descripteur de sécurité du Registre.</span><span class="sxs-lookup"><span data-stu-id="0e791-119">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="0e791-120">Exemple 3 : convertir les SDDL droits d’accès du registre en PSCustomObject à l’aide de ConvertFrom-SddlString avec et sans le `-Type` paramètre</span><span class="sxs-lookup"><span data-stu-id="0e791-120">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="0e791-121">La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité de la clé HKLM : \ SOFTWARE\Microsoft\ et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="0e791-121">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="0e791-122">La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0e791-122">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="0e791-123">Il n’utilise pas le `-Type` paramètre, de sorte que les droits d’accès indiqués pour le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="0e791-123">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="0e791-124">La troisième commande utilise l' `ConvertFrom-SddlString` applet de commande avec le `-Type` paramètre, de sorte que les droits d’accès retournés sont pour Registry.</span><span class="sxs-lookup"><span data-stu-id="0e791-124">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

## <span data-ttu-id="0e791-125">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="0e791-125">PARAMETERS</span></span>

### <span data-ttu-id="0e791-126">-SDDL</span><span class="sxs-lookup"><span data-stu-id="0e791-126">-Sddl</span></span>

<span data-ttu-id="0e791-127">Spécifie la chaîne représentant le descripteur de sécurité dans la syntaxe SDDL.</span><span class="sxs-lookup"><span data-stu-id="0e791-127">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0e791-128">-Type</span><span class="sxs-lookup"><span data-stu-id="0e791-128">-Type</span></span>

<span data-ttu-id="0e791-129">Spécifie le type de droits que représente la chaîne SDDL.</span><span class="sxs-lookup"><span data-stu-id="0e791-129">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="0e791-130">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="0e791-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0e791-131">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="0e791-131">FileSystemRights</span></span>
- <span data-ttu-id="0e791-132">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="0e791-132">RegistryRights</span></span>
- <span data-ttu-id="0e791-133">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="0e791-133">ActiveDirectoryRights</span></span>
- <span data-ttu-id="0e791-134">MutexRights</span><span class="sxs-lookup"><span data-stu-id="0e791-134">MutexRights</span></span>
- <span data-ttu-id="0e791-135">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="0e791-135">SemaphoreRights</span></span>
- <span data-ttu-id="0e791-136">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="0e791-136">CryptoKeyRights</span></span>
- <span data-ttu-id="0e791-137">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="0e791-137">EventWaitHandleRights</span></span>

<span data-ttu-id="0e791-138">Par défaut, l’applet de commande utilise les droits du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="0e791-138">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="0e791-139">CryptoKeyRights et ActiveDirectoryRights ne sont pas pris en charge dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="0e791-139">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e791-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0e791-140">CommonParameters</span></span>

<span data-ttu-id="0e791-141">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0e791-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0e791-142">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0e791-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0e791-143">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="0e791-143">INPUTS</span></span>

### <span data-ttu-id="0e791-144">System.String</span><span class="sxs-lookup"><span data-stu-id="0e791-144">System.String</span></span>

<span data-ttu-id="0e791-145">Vous pouvez diriger une chaîne SDDL vers `ConvertFrom-SddlString` .</span><span class="sxs-lookup"><span data-stu-id="0e791-145">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="0e791-146">SORTIES</span><span class="sxs-lookup"><span data-stu-id="0e791-146">OUTPUTS</span></span>

## <span data-ttu-id="0e791-147">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="0e791-147">NOTES</span></span>

<span data-ttu-id="0e791-148">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="0e791-148">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="0e791-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="0e791-149">RELATED LINKS</span></span>

[<span data-ttu-id="0e791-150">Langage de définition du descripteur de sécurité</span><span class="sxs-lookup"><span data-stu-id="0e791-150">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)
