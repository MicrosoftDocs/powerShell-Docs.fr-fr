---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: b76fc092046a29dcad52f755794fd55dd84ac675
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "93205249"
---
# <span data-ttu-id="f9e18-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="f9e18-103">Read-Host</span></span>

## <span data-ttu-id="f9e18-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="f9e18-104">SYNOPSIS</span></span>
<span data-ttu-id="f9e18-105">Lit une ligne d'entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="f9e18-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="f9e18-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9e18-106">SYNTAX</span></span>

### <span data-ttu-id="f9e18-107">AsString (par défaut)</span><span class="sxs-lookup"><span data-stu-id="f9e18-107">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="f9e18-108">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="f9e18-108">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="f9e18-109">Description</span><span class="sxs-lookup"><span data-stu-id="f9e18-109">DESCRIPTION</span></span>

<span data-ttu-id="f9e18-110">L' `Read-Host` applet de commande lit une ligne d’entrée à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="f9e18-110">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="f9e18-111">Vous pouvez l'utiliser pour inviter un utilisateur à saisir une entrée.</span><span class="sxs-lookup"><span data-stu-id="f9e18-111">You can use it to prompt a user for input.</span></span> <span data-ttu-id="f9e18-112">Comme vous pouvez enregistrer l'entrée sous la forme d'une chaîne sécurisée, vous pouvez utiliser cette applet de commande pour inviter les utilisateurs à entrer des données de sécurité, telles que des mots de passe, ainsi que des données partagées.</span><span class="sxs-lookup"><span data-stu-id="f9e18-112">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="f9e18-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="f9e18-113">EXAMPLES</span></span>

### <span data-ttu-id="f9e18-114">Exemple 1 : enregistrer l’entrée de la console dans une variable</span><span class="sxs-lookup"><span data-stu-id="f9e18-114">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="f9e18-115">Cet exemple affiche la chaîne « Veuillez entrer votre âge : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="f9e18-115">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="f9e18-116">Quand une valeur est entrée et que la touche entrée est enfoncée, la valeur est stockée dans la `$Age` variable.</span><span class="sxs-lookup"><span data-stu-id="f9e18-116">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="f9e18-117">Exemple 2 : enregistrer l’entrée de la console en tant que chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="f9e18-117">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="f9e18-118">Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="f9e18-118">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="f9e18-119">Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="f9e18-119">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="f9e18-120">Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **SecureString** dans la `$pwd_secure_string` variable.</span><span class="sxs-lookup"><span data-stu-id="f9e18-120">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="f9e18-121">Exemple 3 : entrée de masque et sous forme de chaîne en texte brut</span><span class="sxs-lookup"><span data-stu-id="f9e18-121">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="f9e18-122">Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="f9e18-122">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="f9e18-123">Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="f9e18-123">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="f9e18-124">Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **chaîne** en texte clair dans la `$pwd_string` variable.</span><span class="sxs-lookup"><span data-stu-id="f9e18-124">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="f9e18-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9e18-125">PARAMETERS</span></span>

### <span data-ttu-id="f9e18-126">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="f9e18-126">-AsSecureString</span></span>

<span data-ttu-id="f9e18-127">Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée.</span><span class="sxs-lookup"><span data-stu-id="f9e18-127">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="f9e18-128">Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **SecureString** ( **System. Security. SecureString** ).</span><span class="sxs-lookup"><span data-stu-id="f9e18-128">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9e18-129">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="f9e18-129">-MaskInput</span></span>

<span data-ttu-id="f9e18-130">Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée.</span><span class="sxs-lookup"><span data-stu-id="f9e18-130">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="f9e18-131">Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="f9e18-131">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="f9e18-132">Cela vous permet de demander en toute sécurité un mot de passe qui est retourné sous forme de texte brut au lieu de **SecureString** .</span><span class="sxs-lookup"><span data-stu-id="f9e18-132">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9e18-133">-Invite</span><span class="sxs-lookup"><span data-stu-id="f9e18-133">-Prompt</span></span>

<span data-ttu-id="f9e18-134">Spécifie le texte de l'invite.</span><span class="sxs-lookup"><span data-stu-id="f9e18-134">Specifies the text of the prompt.</span></span>
<span data-ttu-id="f9e18-135">Tapez une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f9e18-135">Type a string.</span></span>
<span data-ttu-id="f9e18-136">Si la chaîne inclut des espaces, mettez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="f9e18-136">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="f9e18-137">PowerShell ajoute un signe deux-points ( `:` ) au texte que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="f9e18-137">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="f9e18-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9e18-138">CommonParameters</span></span>

<span data-ttu-id="f9e18-139">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f9e18-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9e18-140">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f9e18-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9e18-141">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="f9e18-141">INPUTS</span></span>

### <span data-ttu-id="f9e18-142">Aucun</span><span class="sxs-lookup"><span data-stu-id="f9e18-142">None</span></span>

<span data-ttu-id="f9e18-143">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f9e18-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f9e18-144">SORTIES</span><span class="sxs-lookup"><span data-stu-id="f9e18-144">OUTPUTS</span></span>

### <span data-ttu-id="f9e18-145">System. String ou System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="f9e18-145">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="f9e18-146">Si le paramètre **AsSecureString** est utilisé, `Read-Host` retourne une **SecureString** .</span><span class="sxs-lookup"><span data-stu-id="f9e18-146">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString** .</span></span> <span data-ttu-id="f9e18-147">Sinon, une chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="f9e18-147">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="f9e18-148">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="f9e18-148">NOTES</span></span>

## <span data-ttu-id="f9e18-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="f9e18-149">RELATED LINKS</span></span>

[<span data-ttu-id="f9e18-150">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="f9e18-150">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="f9e18-151">Get-Host</span><span class="sxs-lookup"><span data-stu-id="f9e18-151">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="f9e18-152">Write-Host</span><span class="sxs-lookup"><span data-stu-id="f9e18-152">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="f9e18-153">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="f9e18-153">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
