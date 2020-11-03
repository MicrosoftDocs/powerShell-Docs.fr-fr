---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 7e88e873c5c6aa0733869cdaaf1fba583468261d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202441"
---
# <span data-ttu-id="981fe-103">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="981fe-103">Resolve-Path</span></span>

## <span data-ttu-id="981fe-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="981fe-104">SYNOPSIS</span></span>
<span data-ttu-id="981fe-105">Résout les caractères génériques inclus dans un chemin d'accès et affiche le contenu de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="981fe-105">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="981fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="981fe-106">SYNTAX</span></span>

### <span data-ttu-id="981fe-107">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="981fe-107">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="981fe-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="981fe-108">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="981fe-109">Description</span><span class="sxs-lookup"><span data-stu-id="981fe-109">DESCRIPTION</span></span>

<span data-ttu-id="981fe-110">L' `Resolve-Path` applet de commande affiche les éléments et les conteneurs qui correspondent au modèle de caractère générique à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="981fe-110">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="981fe-111">La correspondance peut inclure des fichiers, des dossiers, des clés de registre ou tout autre objet accessible à partir d’un fournisseur PSDrive.</span><span class="sxs-lookup"><span data-stu-id="981fe-111">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="981fe-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="981fe-112">EXAMPLES</span></span>

### <span data-ttu-id="981fe-113">Exemple 1 : résoudre le chemin d’accès du dossier de démarrage</span><span class="sxs-lookup"><span data-stu-id="981fe-113">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="981fe-114">Le caractère tilde (~) est une notation abrégée pour le dossier de démarrage de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="981fe-114">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="981fe-115">Cet exemple montre comment `Resolve-Path` retourner la valeur de chemin qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="981fe-115">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="981fe-116">Exemple 2 : résoudre le chemin d’accès du dossier Windows</span><span class="sxs-lookup"><span data-stu-id="981fe-116">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="981fe-117">Lorsqu’elle est exécutée à partir de la racine du lecteur C :, cette commande retourne le chemin d’accès du dossier Windows sur le lecteur C :.</span><span class="sxs-lookup"><span data-stu-id="981fe-117">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="981fe-118">Exemple 3 : récupération de tous les chemins d’accès dans le dossier Windows</span><span class="sxs-lookup"><span data-stu-id="981fe-118">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="981fe-119">Cette commande retourne tous les dossiers du dossier C:\Windows.</span><span class="sxs-lookup"><span data-stu-id="981fe-119">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="981fe-120">La commande utilise un opérateur de pipeline (|) pour envoyer une chaîne de chemin d’accès à `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="981fe-120">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="981fe-121">Exemple 4 : résoudre un chemin d’accès UNC</span><span class="sxs-lookup"><span data-stu-id="981fe-121">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="981fe-122">Cette commande résout un chemin d'accès UNC (Universal Naming Convention) et retourne les partages dans le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="981fe-122">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="981fe-123">Exemple 5 : récupérer les chemins d’accès relatifs</span><span class="sxs-lookup"><span data-stu-id="981fe-123">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="981fe-124">Cette commande retourne des chemins d'accès relatifs aux répertoires situés à la racine du lecteur C:.</span><span class="sxs-lookup"><span data-stu-id="981fe-124">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="981fe-125">Exemple 6 : résoudre un chemin d’accès contenant des crochets</span><span class="sxs-lookup"><span data-stu-id="981fe-125">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="981fe-126">Cet exemple utilise le paramètre **LiteralPath** pour résoudre le chemin d’accès du \[ \] sous-dossier XML de test.</span><span class="sxs-lookup"><span data-stu-id="981fe-126">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="981fe-127">L’utilisation de **LiteralPath** provoque le traitement des crochets comme des caractères normaux plutôt qu’une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="981fe-127">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="981fe-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="981fe-128">PARAMETERS</span></span>

### <span data-ttu-id="981fe-129">-Credential</span><span class="sxs-lookup"><span data-stu-id="981fe-129">-Credential</span></span>

<span data-ttu-id="981fe-130">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="981fe-130">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="981fe-131">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="981fe-131">The default is the current user.</span></span>

<span data-ttu-id="981fe-132">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou transmettez un objet **PSCredential** .</span><span class="sxs-lookup"><span data-stu-id="981fe-132">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="981fe-133">Vous pouvez créer un objet **PSCredential** à l’aide de l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="981fe-133">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="981fe-134">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="981fe-134">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="981fe-135">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="981fe-135">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="981fe-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="981fe-136">-LiteralPath</span></span>

<span data-ttu-id="981fe-137">Spécifie le chemin d'accès à résoudre.</span><span class="sxs-lookup"><span data-stu-id="981fe-137">Specifies the path to be resolved.</span></span> <span data-ttu-id="981fe-138">La valeur du paramètre **LiteralPath** est utilisée exactement comme entrée.</span><span class="sxs-lookup"><span data-stu-id="981fe-138">The value of the **LiteralPath** parameter is used exactly as typed.</span></span> <span data-ttu-id="981fe-139">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="981fe-139">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="981fe-140">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="981fe-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="981fe-141">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="981fe-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="981fe-142">-Path</span><span class="sxs-lookup"><span data-stu-id="981fe-142">-Path</span></span>

<span data-ttu-id="981fe-143">Spécifie le chemin d’accès PowerShell à résoudre.</span><span class="sxs-lookup"><span data-stu-id="981fe-143">Specifies the PowerShell path to resolve.</span></span> <span data-ttu-id="981fe-144">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="981fe-144">This parameter is required.</span></span> <span data-ttu-id="981fe-145">Vous pouvez également diriger une chaîne de chemin vers `Resolve-Path` .</span><span class="sxs-lookup"><span data-stu-id="981fe-145">You can also pipe a path string to `Resolve-Path`.</span></span> <span data-ttu-id="981fe-146">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="981fe-146">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="981fe-147">-Relatif</span><span class="sxs-lookup"><span data-stu-id="981fe-147">-Relative</span></span>

<span data-ttu-id="981fe-148">Indique que cette applet de commande retourne un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="981fe-148">Indicates that this cmdlet returns a relative path.</span></span>

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

### <span data-ttu-id="981fe-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="981fe-149">CommonParameters</span></span>

<span data-ttu-id="981fe-150">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="981fe-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="981fe-151">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="981fe-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="981fe-152">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="981fe-152">INPUTS</span></span>

### <span data-ttu-id="981fe-153">System.String</span><span class="sxs-lookup"><span data-stu-id="981fe-153">System.String</span></span>

<span data-ttu-id="981fe-154">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="981fe-154">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="981fe-155">SORTIES</span><span class="sxs-lookup"><span data-stu-id="981fe-155">OUTPUTS</span></span>

### <span data-ttu-id="981fe-156">System. Management. Automation. PathInfo, System. String</span><span class="sxs-lookup"><span data-stu-id="981fe-156">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="981fe-157">Retourne un objet **PathInfo** .</span><span class="sxs-lookup"><span data-stu-id="981fe-157">Returns a **PathInfo** object.</span></span> <span data-ttu-id="981fe-158">Retourne une valeur de chaîne pour le chemin d’accès résolu si vous spécifiez le paramètre **relatif** .</span><span class="sxs-lookup"><span data-stu-id="981fe-158">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="981fe-159">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="981fe-159">NOTES</span></span>

<span data-ttu-id="981fe-160">Les `*-Path` applets de commande fonctionnent avec le système de fichiers, le registre et les fournisseurs de certificats.</span><span class="sxs-lookup"><span data-stu-id="981fe-160">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="981fe-161">`Resolve-Path` est conçu pour fonctionner avec n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="981fe-161">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="981fe-162">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="981fe-162">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="981fe-163">Pour plus d’informations, consultez [about_Providers](../microsoft.powershell.core/about/about_providers.md).</span><span class="sxs-lookup"><span data-stu-id="981fe-163">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="981fe-164">`Resolve-Path` résout uniquement les chemins d’accès existants.</span><span class="sxs-lookup"><span data-stu-id="981fe-164">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="981fe-165">Il ne peut pas être utilisé pour résoudre un emplacement qui n’existe pas encore.</span><span class="sxs-lookup"><span data-stu-id="981fe-165">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="981fe-166">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="981fe-166">RELATED LINKS</span></span>

[<span data-ttu-id="981fe-167">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="981fe-167">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="981fe-168">Join-Path</span><span class="sxs-lookup"><span data-stu-id="981fe-168">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="981fe-169">Split-Path</span><span class="sxs-lookup"><span data-stu-id="981fe-169">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="981fe-170">Test-Path</span><span class="sxs-lookup"><span data-stu-id="981fe-170">Test-Path</span></span>](Test-Path.md)
