---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 128a86312f424eaf9dcfb6cdc97ebd3e148c7886
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206190"
---
# <span data-ttu-id="c6bbb-103">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="c6bbb-103">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="c6bbb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c6bbb-104">SYNOPSIS</span></span>

<span data-ttu-id="c6bbb-105">Convertit une chaîne SDDL en objet personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-105">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="c6bbb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c6bbb-106">SYNTAX</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <Object>] [<CommonParameters>]
```

## <span data-ttu-id="c6bbb-107">Description</span><span class="sxs-lookup"><span data-stu-id="c6bbb-107">DESCRIPTION</span></span>

<span data-ttu-id="c6bbb-108">L' `ConvertFrom-SddlString` applet de commande convertit une chaîne de langage de définition de descripteur de sécurité en objet **PSCustomObject** personnalisé avec les propriétés suivantes : Owner, Group, DiscretionaryAcl, SystemAcl et RawDescriptor.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-108">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="c6bbb-109">Les propriétés Owner, Group, DiscretionaryAcl et SystemAcl contiennent une représentation textuelle lisible des droits d’accès spécifiés dans une chaîne SDDL.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-109">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="c6bbb-110">Cette applet de commande a été introduite dans PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-110">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="c6bbb-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c6bbb-111">EXAMPLES</span></span>

### <span data-ttu-id="c6bbb-112">Exemple 1 : convertir les SDDL droits d’accès du système de fichiers en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="c6bbb-112">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="c6bbb-113">La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité pour le dossier C:\Windows et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-113">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="c6bbb-114">La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-114">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="c6bbb-115">Exemple 2 : convertir les SDDL droits d’accès du registre en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="c6bbb-115">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="c6bbb-116">La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité de la clé HKLM : \ SOFTWARE\Microsoft\ et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-116">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="c6bbb-117">La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-117">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="c6bbb-118">Elle utilise le `-Type` paramètre pour spécifier que la chaîne SDDL représente un descripteur de sécurité du Registre.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-118">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="c6bbb-119">Exemple 3 : convertir les SDDL droits d’accès du registre en PSCustomObject à l’aide de ConvertFrom-SddlString avec et sans le `-Type` paramètre</span><span class="sxs-lookup"><span data-stu-id="c6bbb-119">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="c6bbb-120">La première commande utilise l' `Get-Acl` applet de commande pour obtenir le descripteur de sécurité de la clé HKLM : \ SOFTWARE\Microsoft\ et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="c6bbb-121">La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-121">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="c6bbb-122">Il n’utilise pas le `-Type` paramètre, de sorte que les droits d’accès indiqués pour le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-122">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="c6bbb-123">La troisième commande utilise l' `ConvertFrom-SddlString` applet de commande avec le `-Type` paramètre, de sorte que les droits d’accès retournés sont pour Registry.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-123">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

### <span data-ttu-id="c6bbb-124">Exemple 4 : convertir Active Directory SDDL de droits d’accès en un PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="c6bbb-124">Example 4: Convert Active Directory access rights SDDL to a PSCustomObject</span></span>

```powershell
$user = [ADSI]"LDAP://CN=username,CN=Users,DC=domain,DC=com"
ConvertFrom-SddlString $user.psbase.ObjectSecurity.Sddl -Type ActiveDirectoryRights
```

<span data-ttu-id="c6bbb-125">La première commande utilise les interfaces de service Active Directory (ADSI) pour récupérer l’objet utilisateur et l’enregistre dans la variable.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-125">The first command uses Active Directory Service Interfaces (ADSI) to get the user object and saves it in the variable.</span></span>

<span data-ttu-id="c6bbb-126">La deuxième commande utilise l' `ConvertFrom-SddlString` applet de commande pour récupérer la représentation textuelle de la chaîne SDDL, contenue dans la propriété SDDL de l’objet représentant le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-126">The second command uses the `ConvertFrom-SddlString` cmdlet to get text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="c6bbb-127">Elle utilise le `-Type` paramètre pour spécifier que la chaîne SDDL représente un descripteur de sécurité Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-127">It uses the `-Type` parameter to specify that SDDL string represents an Active Directory security descriptor.</span></span>

## <span data-ttu-id="c6bbb-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c6bbb-128">PARAMETERS</span></span>

### <span data-ttu-id="c6bbb-129">-SDDL</span><span class="sxs-lookup"><span data-stu-id="c6bbb-129">-Sddl</span></span>

<span data-ttu-id="c6bbb-130">Spécifie la chaîne représentant le descripteur de sécurité dans la syntaxe SDDL.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-130">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

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

### <span data-ttu-id="c6bbb-131">-Type</span><span class="sxs-lookup"><span data-stu-id="c6bbb-131">-Type</span></span>

<span data-ttu-id="c6bbb-132">Spécifie le type de droits que représente la chaîne SDDL.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-132">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="c6bbb-133">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="c6bbb-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c6bbb-134">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="c6bbb-134">FileSystemRights</span></span>
- <span data-ttu-id="c6bbb-135">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="c6bbb-135">RegistryRights</span></span>
- <span data-ttu-id="c6bbb-136">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="c6bbb-136">ActiveDirectoryRights</span></span>
- <span data-ttu-id="c6bbb-137">MutexRights</span><span class="sxs-lookup"><span data-stu-id="c6bbb-137">MutexRights</span></span>
- <span data-ttu-id="c6bbb-138">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="c6bbb-138">SemaphoreRights</span></span>
- <span data-ttu-id="c6bbb-139">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="c6bbb-139">CryptoKeyRights</span></span>
- <span data-ttu-id="c6bbb-140">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="c6bbb-140">EventWaitHandleRights</span></span>

<span data-ttu-id="c6bbb-141">Par défaut, l’applet de commande utilise les droits du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-141">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="c6bbb-142">CryptoKeyRights et ActiveDirectoryRights ne sont pas pris en charge dans PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-142">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6bbb-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6bbb-143">CommonParameters</span></span>
<span data-ttu-id="c6bbb-144">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c6bbb-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6bbb-145">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c6bbb-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c6bbb-146">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c6bbb-146">INPUTS</span></span>

### <span data-ttu-id="c6bbb-147">System.String</span><span class="sxs-lookup"><span data-stu-id="c6bbb-147">System.String</span></span>

<span data-ttu-id="c6bbb-148">Vous pouvez diriger une chaîne SDDL vers `ConvertFrom-SddlString` .</span><span class="sxs-lookup"><span data-stu-id="c6bbb-148">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="c6bbb-149">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c6bbb-149">OUTPUTS</span></span>

## <span data-ttu-id="c6bbb-150">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c6bbb-150">NOTES</span></span>

## <span data-ttu-id="c6bbb-151">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c6bbb-151">RELATED LINKS</span></span>

[<span data-ttu-id="c6bbb-152">Langage de définition du descripteur de sécurité</span><span class="sxs-lookup"><span data-stu-id="c6bbb-152">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)
