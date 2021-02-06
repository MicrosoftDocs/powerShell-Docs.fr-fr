---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 2efe75730ef7d35618dc0d1fbf7a8d6f8a5db5ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597545"
---
# <span data-ttu-id="b0401-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="b0401-102">Read-Host</span></span>

## <span data-ttu-id="b0401-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b0401-103">SYNOPSIS</span></span>
<span data-ttu-id="b0401-104">Lit une ligne d'entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="b0401-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="b0401-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b0401-105">SYNTAX</span></span>

### <span data-ttu-id="b0401-106">AsString (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b0401-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="b0401-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="b0401-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="b0401-108">Description</span><span class="sxs-lookup"><span data-stu-id="b0401-108">DESCRIPTION</span></span>

<span data-ttu-id="b0401-109">L' `Read-Host` applet de commande lit une ligne d’entrée à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="b0401-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="b0401-110">Vous pouvez l'utiliser pour inviter un utilisateur à saisir une entrée.</span><span class="sxs-lookup"><span data-stu-id="b0401-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="b0401-111">Comme vous pouvez enregistrer l'entrée sous la forme d'une chaîne sécurisée, vous pouvez utiliser cette applet de commande pour inviter les utilisateurs à entrer des données de sécurité, telles que des mots de passe, ainsi que des données partagées.</span><span class="sxs-lookup"><span data-stu-id="b0401-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="b0401-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b0401-112">EXAMPLES</span></span>

### <span data-ttu-id="b0401-113">Exemple 1 : enregistrer l’entrée de la console dans une variable</span><span class="sxs-lookup"><span data-stu-id="b0401-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="b0401-114">Cet exemple affiche la chaîne « Veuillez entrer votre âge : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="b0401-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="b0401-115">Quand une valeur est entrée et que la touche entrée est enfoncée, la valeur est stockée dans la `$Age` variable.</span><span class="sxs-lookup"><span data-stu-id="b0401-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="b0401-116">Exemple 2 : enregistrer l’entrée de la console en tant que chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="b0401-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="b0401-117">Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="b0401-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="b0401-118">Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b0401-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="b0401-119">Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **SecureString** dans la `$pwd_secure_string` variable.</span><span class="sxs-lookup"><span data-stu-id="b0401-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="b0401-120">Exemple 3 : entrée de masque et sous forme de chaîne en texte brut</span><span class="sxs-lookup"><span data-stu-id="b0401-120">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="b0401-121">Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="b0401-121">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="b0401-122">Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="b0401-122">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="b0401-123">Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **chaîne** en texte clair dans la `$pwd_string` variable.</span><span class="sxs-lookup"><span data-stu-id="b0401-123">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="b0401-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0401-124">PARAMETERS</span></span>

### <span data-ttu-id="b0401-125">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="b0401-125">-AsSecureString</span></span>

<span data-ttu-id="b0401-126">Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée.</span><span class="sxs-lookup"><span data-stu-id="b0401-126">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="b0401-127">Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **SecureString** (**System. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="b0401-127">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="b0401-128">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="b0401-128">-MaskInput</span></span>

<span data-ttu-id="b0401-129">Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée.</span><span class="sxs-lookup"><span data-stu-id="b0401-129">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="b0401-130">Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **String** .</span><span class="sxs-lookup"><span data-stu-id="b0401-130">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="b0401-131">Cela vous permet de demander en toute sécurité un mot de passe qui est retourné sous forme de texte brut au lieu de **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="b0401-131">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="b0401-132">-Invite</span><span class="sxs-lookup"><span data-stu-id="b0401-132">-Prompt</span></span>

<span data-ttu-id="b0401-133">Spécifie le texte de l'invite.</span><span class="sxs-lookup"><span data-stu-id="b0401-133">Specifies the text of the prompt.</span></span>
<span data-ttu-id="b0401-134">Tapez une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b0401-134">Type a string.</span></span>
<span data-ttu-id="b0401-135">Si la chaîne inclut des espaces, mettez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="b0401-135">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="b0401-136">PowerShell ajoute un signe deux-points ( `:` ) au texte que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="b0401-136">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="b0401-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0401-137">CommonParameters</span></span>

<span data-ttu-id="b0401-138">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0401-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0401-139">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b0401-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0401-140">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b0401-140">INPUTS</span></span>

### <span data-ttu-id="b0401-141">None</span><span class="sxs-lookup"><span data-stu-id="b0401-141">None</span></span>

<span data-ttu-id="b0401-142">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b0401-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b0401-143">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b0401-143">OUTPUTS</span></span>

### <span data-ttu-id="b0401-144">System. String ou System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="b0401-144">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="b0401-145">Si le paramètre **AsSecureString** est utilisé, `Read-Host` retourne une **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="b0401-145">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="b0401-146">Sinon, une chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="b0401-146">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="b0401-147">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b0401-147">NOTES</span></span>

## <span data-ttu-id="b0401-148">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b0401-148">RELATED LINKS</span></span>

[<span data-ttu-id="b0401-149">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="b0401-149">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="b0401-150">Get-Host</span><span class="sxs-lookup"><span data-stu-id="b0401-150">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="b0401-151">Write-Host</span><span class="sxs-lookup"><span data-stu-id="b0401-151">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="b0401-152">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="b0401-152">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
