---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202230"
---
# <span data-ttu-id="234de-103">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="234de-103">Get-LocalUser</span></span>

## <span data-ttu-id="234de-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="234de-104">SYNOPSIS</span></span>
<span data-ttu-id="234de-105">Obtient les comptes d’utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="234de-105">Gets local user accounts.</span></span>

## <span data-ttu-id="234de-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="234de-106">SYNTAX</span></span>

### <span data-ttu-id="234de-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="234de-107">Default (Default)</span></span>

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="234de-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="234de-108">SecurityIdentifier</span></span>

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="234de-109">Description</span><span class="sxs-lookup"><span data-stu-id="234de-109">DESCRIPTION</span></span>

<span data-ttu-id="234de-110">L' `Get-LocalUser` applet de commande obtient les comptes d’utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="234de-110">The `Get-LocalUser` cmdlet gets local user accounts.</span></span> <span data-ttu-id="234de-111">Cette applet de commande obtient les comptes d’utilisateur intégrés par défaut, les comptes d’utilisateurs locaux que vous avez créés et les comptes locaux que vous avez connectés aux comptes Microsoft.</span><span class="sxs-lookup"><span data-stu-id="234de-111">This cmdlet gets default built-in user accounts, local user accounts that you created, and local accounts that you connected to Microsoft accounts.</span></span>

> [!NOTE]
> <span data-ttu-id="234de-112">Le module Microsoft. PowerShell. LocalAccounts n’est pas disponible dans PowerShell 32 bits sur un système 64 bits.</span><span class="sxs-lookup"><span data-stu-id="234de-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="234de-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="234de-113">EXAMPLES</span></span>

### <span data-ttu-id="234de-114">Exemple 1 : récupération d’un compte à l’aide de son nom</span><span class="sxs-lookup"><span data-stu-id="234de-114">Example 1: Get an account by using its name</span></span>

<span data-ttu-id="234de-115">Cet exemple obtient un compte d’utilisateur nommé AdminContoso02.</span><span class="sxs-lookup"><span data-stu-id="234de-115">This example gets a user account named AdminContoso02.</span></span>

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### <span data-ttu-id="234de-116">Exemple 2 : obtenir un compte connecté à un compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="234de-116">Example 2: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="234de-117">Cet exemple obtient un compte d’utilisateur qui est connecté à un compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="234de-117">This example gets a user account that is connected to a Microsoft account.</span></span> <span data-ttu-id="234de-118">Cet exemple utilise une valeur d’espace réservé pour le nom d’utilisateur d’un compte sur Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="234de-118">This example uses a placeholder value for the username of an account at Outlook.com.</span></span>

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### <span data-ttu-id="234de-119">Exemple 3 : obtenir un compte connecté à un compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="234de-119">Example 3: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="234de-120">Cet exemple obtient un compte d’utilisateur local qui a le SID spécifié.</span><span class="sxs-lookup"><span data-stu-id="234de-120">This example gets a local user account that has the specified SID.</span></span>

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## <span data-ttu-id="234de-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="234de-121">PARAMETERS</span></span>

### <span data-ttu-id="234de-122">-Name</span><span class="sxs-lookup"><span data-stu-id="234de-122">-Name</span></span>

<span data-ttu-id="234de-123">Spécifie un tableau de noms de comptes d’utilisateur que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="234de-123">Specifies an array of names of user accounts that this cmdlet gets.</span></span> <span data-ttu-id="234de-124">Vous pouvez utiliser le caractère générique.</span><span class="sxs-lookup"><span data-stu-id="234de-124">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="234de-125">-SID</span><span class="sxs-lookup"><span data-stu-id="234de-125">-SID</span></span>

<span data-ttu-id="234de-126">Spécifie un tableau d’ID de sécurité (SID) des comptes d’utilisateur que cette applet de commande obtient.</span><span class="sxs-lookup"><span data-stu-id="234de-126">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="234de-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="234de-127">CommonParameters</span></span>

<span data-ttu-id="234de-128">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="234de-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="234de-129">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="234de-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="234de-130">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="234de-130">INPUTS</span></span>

### <span data-ttu-id="234de-131">System. String, System. Security. principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="234de-131">System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="234de-132">Vous pouvez diriger une chaîne ou un SID vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="234de-132">You can pipe a string or SID to this cmdlet.</span></span>

## <span data-ttu-id="234de-133">SORTIES</span><span class="sxs-lookup"><span data-stu-id="234de-133">OUTPUTS</span></span>

### <span data-ttu-id="234de-134">System. Management. Automation. SecurityAccountsManager. LocalUser []</span><span class="sxs-lookup"><span data-stu-id="234de-134">System.Management.Automation.SecurityAccountsManager.LocalUser[]</span></span>

<span data-ttu-id="234de-135">Cette applet de commande retourne les comptes d’utilisateurs locaux.</span><span class="sxs-lookup"><span data-stu-id="234de-135">This cmdlet returns local user accounts.</span></span>

## <span data-ttu-id="234de-136">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="234de-136">NOTES</span></span>

<span data-ttu-id="234de-137">La propriété **PrincipalSource** sur les objets **LocalUser** , **LocalGroup** et **LocalPrincipal** décrit la source de l’objet.</span><span class="sxs-lookup"><span data-stu-id="234de-137">The **PrincipalSource** property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects describes the source of the object.</span></span> <span data-ttu-id="234de-138">Les sources possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="234de-138">The possible sources are as follows:</span></span>

- <span data-ttu-id="234de-139">Local</span><span class="sxs-lookup"><span data-stu-id="234de-139">Local</span></span>
- <span data-ttu-id="234de-140">Active Directory</span><span class="sxs-lookup"><span data-stu-id="234de-140">Active Directory</span></span>
- <span data-ttu-id="234de-141">Groupe Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="234de-141">Azure Active Directory group</span></span>
- <span data-ttu-id="234de-142">Compte Microsoft</span><span class="sxs-lookup"><span data-stu-id="234de-142">Microsoft Account</span></span>

<span data-ttu-id="234de-143">**PrincipalSource** est pris en charge uniquement par Windows 10, windows server 2016 et les versions ultérieures du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="234de-143">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="234de-144">Pour les versions antérieures, la propriété est vide.</span><span class="sxs-lookup"><span data-stu-id="234de-144">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="234de-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="234de-145">RELATED LINKS</span></span>

[<span data-ttu-id="234de-146">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="234de-146">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="234de-147">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="234de-147">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="234de-148">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="234de-148">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="234de-149">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="234de-149">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="234de-150">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="234de-150">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="234de-151">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="234de-151">Set-LocalUser</span></span>](Set-LocalUser.md)
