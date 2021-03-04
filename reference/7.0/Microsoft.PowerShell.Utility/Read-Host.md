---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 4f5a5705c726aef7150b734a6265308a5915decb
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685596"
---
# <span data-ttu-id="07934-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="07934-103">Read-Host</span></span>

## <span data-ttu-id="07934-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="07934-104">SYNOPSIS</span></span>
<span data-ttu-id="07934-105">Lit une ligne d'entrée de la console.</span><span class="sxs-lookup"><span data-stu-id="07934-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="07934-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07934-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="07934-107">Description</span><span class="sxs-lookup"><span data-stu-id="07934-107">DESCRIPTION</span></span>

<span data-ttu-id="07934-108">L' `Read-Host` applet de commande lit une ligne d’entrée à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="07934-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="07934-109">Vous pouvez l'utiliser pour inviter un utilisateur à saisir une entrée.</span><span class="sxs-lookup"><span data-stu-id="07934-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="07934-110">Comme vous pouvez enregistrer l'entrée sous la forme d'une chaîne sécurisée, vous pouvez utiliser cette applet de commande pour inviter les utilisateurs à entrer des données de sécurité, telles que des mots de passe, ainsi que des données partagées.</span><span class="sxs-lookup"><span data-stu-id="07934-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="07934-111">`Read-Host` a une limite de 1022 caractères qu’il peut accepter comme entrée d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07934-111">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="07934-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="07934-112">EXAMPLES</span></span>

### <span data-ttu-id="07934-113">Exemple 1 : enregistrer l’entrée de la console dans une variable</span><span class="sxs-lookup"><span data-stu-id="07934-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="07934-114">Cet exemple affiche la chaîne « Veuillez entrer votre âge : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="07934-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="07934-115">Quand une valeur est entrée et que la touche entrée est enfoncée, la valeur est stockée dans la `$Age` variable.</span><span class="sxs-lookup"><span data-stu-id="07934-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="07934-116">Exemple 2 : enregistrer l’entrée de la console en tant que chaîne sécurisée</span><span class="sxs-lookup"><span data-stu-id="07934-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="07934-117">Cet exemple affiche la chaîne « Entrez un mot de passe : » en tant qu’invite.</span><span class="sxs-lookup"><span data-stu-id="07934-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="07934-118">Quand une valeur est entrée, des astérisques ( `*` ) apparaissent sur la console à la place de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="07934-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="07934-119">Lorsque la touche entrée est enfoncée, la valeur est stockée sous la forme d’un objet **SecureString** dans la `$pwd_secure_string` variable.</span><span class="sxs-lookup"><span data-stu-id="07934-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="07934-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="07934-120">PARAMETERS</span></span>

### <span data-ttu-id="07934-121">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="07934-121">-AsSecureString</span></span>

<span data-ttu-id="07934-122">Indique que l’applet de commande affiche des astérisques ( `*` ) à la place des caractères que l’utilisateur tape comme entrée.</span><span class="sxs-lookup"><span data-stu-id="07934-122">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="07934-123">Lorsque vous utilisez ce paramètre, la sortie de l' `Read-Host` applet de commande est un objet **SecureString** (**System. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="07934-123">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="07934-124">-Invite</span><span class="sxs-lookup"><span data-stu-id="07934-124">-Prompt</span></span>

<span data-ttu-id="07934-125">Spécifie le texte de l'invite.</span><span class="sxs-lookup"><span data-stu-id="07934-125">Specifies the text of the prompt.</span></span> <span data-ttu-id="07934-126">Tapez une chaîne.</span><span class="sxs-lookup"><span data-stu-id="07934-126">Type a string.</span></span> <span data-ttu-id="07934-127">Si la chaîne inclut des espaces, mettez-la entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="07934-127">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="07934-128">PowerShell ajoute un signe deux-points ( `:` ) au texte que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="07934-128">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="07934-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07934-129">CommonParameters</span></span>

<span data-ttu-id="07934-130">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07934-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07934-131">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="07934-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07934-132">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="07934-132">INPUTS</span></span>

### <span data-ttu-id="07934-133">Aucun</span><span class="sxs-lookup"><span data-stu-id="07934-133">None</span></span>

<span data-ttu-id="07934-134">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="07934-134">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="07934-135">SORTIES</span><span class="sxs-lookup"><span data-stu-id="07934-135">OUTPUTS</span></span>

### <span data-ttu-id="07934-136">System. String ou System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="07934-136">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="07934-137">Si le paramètre **AsSecureString** est utilisé, `Read-Host` retourne une **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="07934-137">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="07934-138">Sinon, une chaîne est retournée.</span><span class="sxs-lookup"><span data-stu-id="07934-138">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="07934-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="07934-139">NOTES</span></span>

## <span data-ttu-id="07934-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="07934-140">RELATED LINKS</span></span>

[<span data-ttu-id="07934-141">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="07934-141">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="07934-142">Get-Host</span><span class="sxs-lookup"><span data-stu-id="07934-142">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="07934-143">Write-Host</span><span class="sxs-lookup"><span data-stu-id="07934-143">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="07934-144">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="07934-144">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
