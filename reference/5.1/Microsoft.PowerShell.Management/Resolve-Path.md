---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: a48f2c5f62990258f14195eda934bbf4bbe589a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203529"
---
# <span data-ttu-id="ee698-103">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="ee698-103">Resolve-Path</span></span>

## <span data-ttu-id="ee698-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ee698-104">SYNOPSIS</span></span>
<span data-ttu-id="ee698-105">Résout les caractères génériques inclus dans un chemin d'accès et affiche le contenu de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="ee698-105">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="ee698-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee698-106">SYNTAX</span></span>

### <span data-ttu-id="ee698-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee698-107">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="ee698-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ee698-108">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="ee698-109">Description</span><span class="sxs-lookup"><span data-stu-id="ee698-109">DESCRIPTION</span></span>

<span data-ttu-id="ee698-110">L' `Resolve-Path` applet de commande affiche les éléments et les conteneurs qui correspondent au modèle de caractère générique à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="ee698-110">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="ee698-111">La correspondance peut inclure des fichiers, des dossiers, des clés de registre ou tout autre objet accessible à partir d’un fournisseur PSDrive.</span><span class="sxs-lookup"><span data-stu-id="ee698-111">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="ee698-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ee698-112">EXAMPLES</span></span>

### <span data-ttu-id="ee698-113">Exemple 1 : résoudre le chemin d’accès du dossier de démarrage</span><span class="sxs-lookup"><span data-stu-id="ee698-113">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="ee698-114">Le caractère tilde (~) est une notation abrégée pour le dossier de démarrage de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ee698-114">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="ee698-115">Cet exemple montre comment `Resolve-Path` retourner la valeur de chemin qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="ee698-115">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="ee698-116">Exemple 2 : résoudre le chemin d’accès du dossier Windows</span><span class="sxs-lookup"><span data-stu-id="ee698-116">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="ee698-117">Lorsqu’elle est exécutée à partir de la racine du lecteur C :, cette commande retourne le chemin d’accès du dossier Windows sur le lecteur C :.</span><span class="sxs-lookup"><span data-stu-id="ee698-117">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="ee698-118">Exemple 3 : récupération de tous les chemins d’accès dans le dossier Windows</span><span class="sxs-lookup"><span data-stu-id="ee698-118">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="ee698-119">Cette commande retourne tous les dossiers du dossier C:\Windows.</span><span class="sxs-lookup"><span data-stu-id="ee698-119">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="ee698-120">La commande utilise un opérateur de pipeline (|) pour envoyer une chaîne de chemin d’accès à `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="ee698-120">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="ee698-121">Exemple 4 : résoudre un chemin d’accès UNC</span><span class="sxs-lookup"><span data-stu-id="ee698-121">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="ee698-122">Cette commande résout un chemin d'accès UNC (Universal Naming Convention) et retourne les partages dans le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="ee698-122">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="ee698-123">Exemple 5 : récupérer les chemins d’accès relatifs</span><span class="sxs-lookup"><span data-stu-id="ee698-123">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="ee698-124">Cette commande retourne des chemins d'accès relatifs aux répertoires situés à la racine du lecteur C:.</span><span class="sxs-lookup"><span data-stu-id="ee698-124">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="ee698-125">Exemple 6 : résoudre un chemin d’accès contenant des crochets</span><span class="sxs-lookup"><span data-stu-id="ee698-125">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="ee698-126">Cet exemple utilise le paramètre **LiteralPath** pour résoudre le chemin d’accès du \[ \] sous-dossier XML de test.</span><span class="sxs-lookup"><span data-stu-id="ee698-126">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="ee698-127">L’utilisation de **LiteralPath** provoque le traitement des crochets comme des caractères normaux plutôt qu’une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="ee698-127">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="ee698-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee698-128">PARAMETERS</span></span>

### <span data-ttu-id="ee698-129">-Credential</span><span class="sxs-lookup"><span data-stu-id="ee698-129">-Credential</span></span>

<span data-ttu-id="ee698-130">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="ee698-130">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="ee698-131">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ee698-131">The default is the current user.</span></span>

<span data-ttu-id="ee698-132">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou transmettez un objet **PSCredential** .</span><span class="sxs-lookup"><span data-stu-id="ee698-132">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="ee698-133">Vous pouvez créer un objet **PSCredential** à l’aide de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="ee698-133">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="ee698-134">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ee698-134">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="ee698-135">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ee698-135">This parameter is not supported by any providers installed with PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ee698-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ee698-136">-LiteralPath</span></span>

<span data-ttu-id="ee698-137">Spécifie le chemin d'accès à résoudre.</span><span class="sxs-lookup"><span data-stu-id="ee698-137">Specifies the path to be resolved.</span></span> <span data-ttu-id="ee698-138">La valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.</span><span class="sxs-lookup"><span data-stu-id="ee698-138">The value of the **LiteralPath** parameter is used exactly as typed.</span></span> <span data-ttu-id="ee698-139">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="ee698-139">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="ee698-140">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="ee698-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ee698-141">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="ee698-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ee698-142">-Path</span><span class="sxs-lookup"><span data-stu-id="ee698-142">-Path</span></span>

<span data-ttu-id="ee698-143">Spécifie le chemin d’accès PowerShell à résoudre.</span><span class="sxs-lookup"><span data-stu-id="ee698-143">Specifies the PowerShell path to resolve.</span></span> <span data-ttu-id="ee698-144">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ee698-144">This parameter is required.</span></span> <span data-ttu-id="ee698-145">Vous pouvez également diriger une chaîne de chemin vers `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="ee698-145">You can also pipe a path string to `Resolve-Path`.</span></span> <span data-ttu-id="ee698-146">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="ee698-146">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ee698-147">-Relatif</span><span class="sxs-lookup"><span data-stu-id="ee698-147">-Relative</span></span>

<span data-ttu-id="ee698-148">Indique que cette applet de commande retourne un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="ee698-148">Indicates that this cmdlet returns a relative path.</span></span>

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

### <span data-ttu-id="ee698-149">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="ee698-149">-UseTransaction</span></span>
<span data-ttu-id="ee698-150">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="ee698-150">Includes the command in the active transaction.</span></span>
<span data-ttu-id="ee698-151">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="ee698-151">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="ee698-152">Pour plus d’informations, consultez about_transactions.</span><span class="sxs-lookup"><span data-stu-id="ee698-152">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee698-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee698-153">CommonParameters</span></span>

<span data-ttu-id="ee698-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee698-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee698-155">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ee698-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ee698-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ee698-156">INPUTS</span></span>

### <span data-ttu-id="ee698-157">System.String</span><span class="sxs-lookup"><span data-stu-id="ee698-157">System.String</span></span>

<span data-ttu-id="ee698-158">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ee698-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="ee698-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ee698-159">OUTPUTS</span></span>

### <span data-ttu-id="ee698-160">System. Management. Automation. PathInfo, System. String</span><span class="sxs-lookup"><span data-stu-id="ee698-160">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="ee698-161">Retourne un objet **PathInfo** .</span><span class="sxs-lookup"><span data-stu-id="ee698-161">Returns a **PathInfo** object.</span></span> <span data-ttu-id="ee698-162">Retourne une valeur de chaîne pour le chemin d’accès résolu si vous spécifiez le paramètre **relatif** .</span><span class="sxs-lookup"><span data-stu-id="ee698-162">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="ee698-163">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ee698-163">NOTES</span></span>

<span data-ttu-id="ee698-164">Les `*-Path` applets de commande fonctionnent avec le système de fichiers, le registre et les fournisseurs de certificats.</span><span class="sxs-lookup"><span data-stu-id="ee698-164">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="ee698-165">`Resolve-Path` est conçu pour fonctionner avec n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="ee698-165">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="ee698-166">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="ee698-166">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="ee698-167">Pour plus d’informations, consultez [about_Providers](../microsoft.powershell.core/about/about_providers.md).</span><span class="sxs-lookup"><span data-stu-id="ee698-167">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="ee698-168">`Resolve-Path` résout uniquement les chemins d’accès existants.</span><span class="sxs-lookup"><span data-stu-id="ee698-168">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="ee698-169">Il ne peut pas être utilisé pour résoudre un emplacement qui n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="ee698-169">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="ee698-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ee698-170">RELATED LINKS</span></span>

[<span data-ttu-id="ee698-171">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="ee698-171">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="ee698-172">Join-Path</span><span class="sxs-lookup"><span data-stu-id="ee698-172">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="ee698-173">Split-Path</span><span class="sxs-lookup"><span data-stu-id="ee698-173">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="ee698-174">Test-Path</span><span class="sxs-lookup"><span data-stu-id="ee698-174">Test-Path</span></span>](Test-Path.md)
