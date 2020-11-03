---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 9017d2352f1d2735f21343f4c1194c5e97ce2848
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "93205250"
---
# <span data-ttu-id="67507-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="67507-103">Read-Host</span></span>

## <span data-ttu-id="67507-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="67507-104">SYNOPSIS</span></span>
<span data-ttu-id="67507-105">Lit une ligne d'entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="67507-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="67507-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="67507-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="67507-107">Description</span><span class="sxs-lookup"><span data-stu-id="67507-107">DESCRIPTION</span></span>

<span data-ttu-id="67507-108">L' `Read-Host` applet de commande lit une ligne d’entrée à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="67507-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="67507-109">Vous pouvez l'utiliser pour inviter un utilisateur à saisir une entrée.</span><span class="sxs-lookup"><span data-stu-id="67507-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="67507-110">Comme vous pouvez enregistrer l'entrée sous la forme d'une chaîne sécurisée, vous pouvez utiliser cette applet de commande pour inviter les utilisateurs à entrer des données de sécurité, telles que des mots de passe, ainsi que des données partagées.</span><span class="sxs-lookup"><span data-stu-id="67507-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="67507-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="67507-111">EXAMPLES</span></span>

### <span data-ttu-id="67507-112">Exemple 1 : enregistrer l’entrée de la console dans une variable</span><span class="sxs-lookup"><span data-stu-id="67507-112">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="67507-113">Cet exemple affiche la chaîne « Veuillez entrer votre âge : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="67507-113">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="67507-114">Quand une valeur est entrée et que la touche entrée est enfoncée, la valeur est stockée dans la `$Age` variable.</span><span class="sxs-lookup"><span data-stu-id="67507-114">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="67507-115">Exemple 2 : enregistrer l’entrée de la console en tant que chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="67507-115">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="67507-116">Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="67507-116">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="67507-117">Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="67507-117">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="67507-118">Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **SecureString** dans la `$pwd_secure_string` variable.</span><span class="sxs-lookup"><span data-stu-id="67507-118">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="67507-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="67507-119">PARAMETERS</span></span>

### <span data-ttu-id="67507-120">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="67507-120">-AsSecureString</span></span>

<span data-ttu-id="67507-121">Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée.</span><span class="sxs-lookup"><span data-stu-id="67507-121">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="67507-122">Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **SecureString** ( **System. Security. SecureString** ).</span><span class="sxs-lookup"><span data-stu-id="67507-122">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

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

### <span data-ttu-id="67507-123">-Invite</span><span class="sxs-lookup"><span data-stu-id="67507-123">-Prompt</span></span>

<span data-ttu-id="67507-124">Spécifie le texte de l'invite.</span><span class="sxs-lookup"><span data-stu-id="67507-124">Specifies the text of the prompt.</span></span>
<span data-ttu-id="67507-125">Tapez une chaîne.</span><span class="sxs-lookup"><span data-stu-id="67507-125">Type a string.</span></span>
<span data-ttu-id="67507-126">Si la chaîne inclut des espaces, mettez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="67507-126">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="67507-127">PowerShell ajoute un signe deux-points ( `:` ) au texte que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="67507-127">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="67507-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="67507-128">CommonParameters</span></span>

<span data-ttu-id="67507-129">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="67507-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="67507-130">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="67507-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="67507-131">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="67507-131">INPUTS</span></span>

### <span data-ttu-id="67507-132">Aucun</span><span class="sxs-lookup"><span data-stu-id="67507-132">None</span></span>

<span data-ttu-id="67507-133">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="67507-133">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="67507-134">SORTIES</span><span class="sxs-lookup"><span data-stu-id="67507-134">OUTPUTS</span></span>

### <span data-ttu-id="67507-135">System. String ou System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="67507-135">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="67507-136">Si le paramètre **AsSecureString** est utilisé, `Read-Host` retourne une **SecureString** .</span><span class="sxs-lookup"><span data-stu-id="67507-136">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString** .</span></span> <span data-ttu-id="67507-137">Sinon, une chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="67507-137">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="67507-138">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="67507-138">NOTES</span></span>

## <span data-ttu-id="67507-139">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="67507-139">RELATED LINKS</span></span>

[<span data-ttu-id="67507-140">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="67507-140">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="67507-141">Get-Host</span><span class="sxs-lookup"><span data-stu-id="67507-141">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="67507-142">Write-Host</span><span class="sxs-lookup"><span data-stu-id="67507-142">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="67507-143">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="67507-143">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
