---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595504"
---
# <span data-ttu-id="43e53-102">Split-Path</span><span class="sxs-lookup"><span data-stu-id="43e53-102">Split-Path</span></span>

## <span data-ttu-id="43e53-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="43e53-103">SYNOPSIS</span></span>
<span data-ttu-id="43e53-104">Retourne la partie spécifiée d'un chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-104">Returns the specified part of a path.</span></span>

## <span data-ttu-id="43e53-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="43e53-105">SYNTAX</span></span>

### <span data-ttu-id="43e53-106">ParentSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="43e53-106">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="43e53-107">LeafSet</span><span class="sxs-lookup"><span data-stu-id="43e53-107">LeafSet</span></span>

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="43e53-108">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="43e53-108">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="43e53-109">ExtensionSet</span><span class="sxs-lookup"><span data-stu-id="43e53-109">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="43e53-110">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="43e53-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="43e53-111">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="43e53-111">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="43e53-112">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="43e53-112">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="43e53-113">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="43e53-113">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="43e53-114">Description</span><span class="sxs-lookup"><span data-stu-id="43e53-114">DESCRIPTION</span></span>

<span data-ttu-id="43e53-115">L' `Split-Path` applet de commande retourne uniquement la partie spécifiée d’un chemin d’accès, par exemple le dossier parent, un sous-dossier ou un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="43e53-115">The `Split-Path` cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span> <span data-ttu-id="43e53-116">Elle peut également obtenir des éléments qui sont référencés par le chemin d’accès fractionné et indiquer si le chemin d’accès est relatif ou absolu.</span><span class="sxs-lookup"><span data-stu-id="43e53-116">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="43e53-117">Vous pouvez utiliser cette applet de commande pour obtenir ou envoyer uniquement une partie sélectionnée d’un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-117">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="43e53-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="43e53-118">EXAMPLES</span></span>

### <span data-ttu-id="43e53-119">Exemple 1 : obtenir le qualificateur d’un chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="43e53-119">Example 1: Get the qualifier of a path</span></span>

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

<span data-ttu-id="43e53-120">Cette commande retourne uniquement le qualificateur du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-120">This command returns only the qualifier of the path.</span></span> <span data-ttu-id="43e53-121">Le qualificateur est le lecteur.</span><span class="sxs-lookup"><span data-stu-id="43e53-121">The qualifier is the drive.</span></span>

### <span data-ttu-id="43e53-122">Exemple 2 : afficher les noms de fichiers</span><span class="sxs-lookup"><span data-stu-id="43e53-122">Example 2: Display file names</span></span>

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

<span data-ttu-id="43e53-123">Cette commande affiche les fichiers qui sont référencés par le chemin d’accès fractionné.</span><span class="sxs-lookup"><span data-stu-id="43e53-123">This command displays the files that are referenced by the split path.</span></span> <span data-ttu-id="43e53-124">Étant donné que ce chemin d’accès est fractionné au dernier élément, également connu sous le nom de feuille, la commande affiche uniquement les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="43e53-124">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="43e53-125">Le paramètre **Resolve** indique `Split-Path` à d’afficher les éléments référencés par le chemin d’accès de fractionnement, au lieu d’afficher le chemin d’accès de fractionnement.</span><span class="sxs-lookup"><span data-stu-id="43e53-125">The **Resolve** parameter tells `Split-Path` to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="43e53-126">Comme toutes les `Split-Path` commandes, cette commande retourne des chaînes.</span><span class="sxs-lookup"><span data-stu-id="43e53-126">Like all `Split-Path` commands, this command returns strings.</span></span> <span data-ttu-id="43e53-127">Elle ne retourne pas d’objets **FileInfo** représentant les fichiers.</span><span class="sxs-lookup"><span data-stu-id="43e53-127">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="43e53-128">Exemple 3 : récupération du conteneur parent</span><span class="sxs-lookup"><span data-stu-id="43e53-128">Example 3: Get the parent container</span></span>

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="43e53-129">Cette commande retourne uniquement les conteneurs parents du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-129">This command returns only the parent containers of the path.</span></span> <span data-ttu-id="43e53-130">Comme il n’inclut pas de paramètres pour spécifier le fractionnement, `Split-Path` utilise la valeur par défaut de l’emplacement de fractionnement, qui est le **parent**.</span><span class="sxs-lookup"><span data-stu-id="43e53-130">Because it does not include any parameters to specify the split, `Split-Path` uses the split location default, which is **Parent**.</span></span>

### <span data-ttu-id="43e53-131">Exemple 4 : détermine si un chemin d’accès est absolu</span><span class="sxs-lookup"><span data-stu-id="43e53-131">Example 4: Determines whether a path is absolute</span></span>

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

<span data-ttu-id="43e53-132">Cette commande détermine si le chemin d’accès est relatif ou absolu.</span><span class="sxs-lookup"><span data-stu-id="43e53-132">This command determines whether the path is relative or absolute.</span></span> <span data-ttu-id="43e53-133">Dans ce cas, étant donné que le chemin d’accès est relatif au dossier actif, représenté par un point ( `.` ), il retourne `$False` .</span><span class="sxs-lookup"><span data-stu-id="43e53-133">In this case, because the path is relative to the current folder, which is represented by a dot (`.`), it returns `$False`.</span></span>

### <span data-ttu-id="43e53-134">Exemple 5 : modifier l’emplacement d’un chemin d’accès spécifié</span><span class="sxs-lookup"><span data-stu-id="43e53-134">Example 5: Change location to a specified path</span></span>

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="43e53-135">Cette commande remplace votre emplacement par le dossier qui contient le profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43e53-135">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="43e53-136">La commande entre parenthèses utilise `Split-Path` pour retourner uniquement le parent du chemin d’accès stocké dans la `$Profile` variable intégrée.</span><span class="sxs-lookup"><span data-stu-id="43e53-136">The command in parentheses uses `Split-Path` to return only the parent of the path stored in the built-in `$Profile` variable.</span></span> <span data-ttu-id="43e53-137">Le paramètre **parent** est le paramètre d’emplacement de fractionnement par défaut.</span><span class="sxs-lookup"><span data-stu-id="43e53-137">The **Parent** parameter is the default split location parameter.</span></span>
<span data-ttu-id="43e53-138">Par conséquent, vous pouvez l’omettre de la commande.</span><span class="sxs-lookup"><span data-stu-id="43e53-138">Therefore, you can omit it from the command.</span></span> <span data-ttu-id="43e53-139">Les parenthèses indiquent à PowerShell d’exécuter la commande en premier.</span><span class="sxs-lookup"><span data-stu-id="43e53-139">The parentheses direct PowerShell to run the command first.</span></span> <span data-ttu-id="43e53-140">Il s’agit d’une méthode utile pour vous déplacer vers un dossier qui a un nom de chemin d’accès long.</span><span class="sxs-lookup"><span data-stu-id="43e53-140">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="43e53-141">Exemple 6 : fractionner un chemin d’accès à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="43e53-141">Example 6: Split a path by using the pipeline</span></span>

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="43e53-142">Cette commande utilise un opérateur de pipeline ( `|` ) pour envoyer un chemin d’accès à `Split-Path` .</span><span class="sxs-lookup"><span data-stu-id="43e53-142">This command uses a pipeline operator (`|`) to send a path to `Split-Path`.</span></span> <span data-ttu-id="43e53-143">Le chemin d’accès figure entre guillemets pour indiquer qu’il s’agit d’un jeton unique.</span><span class="sxs-lookup"><span data-stu-id="43e53-143">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="43e53-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43e53-144">PARAMETERS</span></span>

### <span data-ttu-id="43e53-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="43e53-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="43e53-146">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43e53-146">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="43e53-147">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="43e53-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="43e53-148">-Extension</span><span class="sxs-lookup"><span data-stu-id="43e53-148">-Extension</span></span>

<span data-ttu-id="43e53-149">Indique que cette applet de commande retourne uniquement l’extension de la feuille.</span><span class="sxs-lookup"><span data-stu-id="43e53-149">Indicates that this cmdlet returns only the extension of the leaf.</span></span> <span data-ttu-id="43e53-150">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement `.log` .</span><span class="sxs-lookup"><span data-stu-id="43e53-150">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="43e53-151">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="43e53-151">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-152">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="43e53-152">-IsAbsolute</span></span>

<span data-ttu-id="43e53-153">Indique que cette applet de commande retourne $True si le chemin d’accès est absolu et $False s’il est relatif.</span><span class="sxs-lookup"><span data-stu-id="43e53-153">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span> <span data-ttu-id="43e53-154">Un chemin d’accès absolu a une longueur supérieure à zéro et n’utilise pas de point ( `.` ) pour indiquer le chemin d’accès actuel.</span><span class="sxs-lookup"><span data-stu-id="43e53-154">An absolute path has a length greater than zero and does not use a dot (`.`) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-155">-Feuille</span><span class="sxs-lookup"><span data-stu-id="43e53-155">-Leaf</span></span>

<span data-ttu-id="43e53-156">Indique que cette applet de commande retourne uniquement le dernier élément ou conteneur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-156">Indicates that this cmdlet returns only the last item or container in the path.</span></span> <span data-ttu-id="43e53-157">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement PASS1. log.</span><span class="sxs-lookup"><span data-stu-id="43e53-157">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-158">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="43e53-158">-LeafBase</span></span>

<span data-ttu-id="43e53-159">Indique que cette applet de commande retourne uniquement le nom de base de la feuille.</span><span class="sxs-lookup"><span data-stu-id="43e53-159">Indicates that this cmdlet returns only base name of the leaf.</span></span> <span data-ttu-id="43e53-160">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement `Pass1` .</span><span class="sxs-lookup"><span data-stu-id="43e53-160">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="43e53-161">Ce paramètre a été introduit dans PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="43e53-161">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="43e53-162">-LiteralPath</span></span>

<span data-ttu-id="43e53-163">Spécifie les chemins d’accès à fractionner.</span><span class="sxs-lookup"><span data-stu-id="43e53-163">Specifies the paths to be split.</span></span> <span data-ttu-id="43e53-164">Contrairement au paramètre **Path**, la valeur de **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="43e53-164">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="43e53-165">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="43e53-165">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="43e53-166">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="43e53-166">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="43e53-167">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="43e53-167">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-168">-NoQualifier</span><span class="sxs-lookup"><span data-stu-id="43e53-168">-NoQualifier</span></span>

<span data-ttu-id="43e53-169">Indique que cette applet de commande retourne le chemin d’accès sans le qualificateur.</span><span class="sxs-lookup"><span data-stu-id="43e53-169">Indicates that this cmdlet returns the path without the qualifier.</span></span> <span data-ttu-id="43e53-170">Pour les fournisseurs de système de fichiers ou de Registre, le qualificateur est le lecteur du chemin d’accès du fournisseur, tel que `C:` ou `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="43e53-170">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span> <span data-ttu-id="43e53-171">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement `\Test\Logs\Pass1.log` .</span><span class="sxs-lookup"><span data-stu-id="43e53-171">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `\Test\Logs\Pass1.log`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-172">-Parent</span><span class="sxs-lookup"><span data-stu-id="43e53-172">-Parent</span></span>

<span data-ttu-id="43e53-173">Indique que cette applet de commande retourne uniquement les conteneurs parents de l’élément ou du conteneur spécifié par le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-173">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span> <span data-ttu-id="43e53-174">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne `C:\Test\Logs` .</span><span class="sxs-lookup"><span data-stu-id="43e53-174">For example, in the path `C:\Test\Logs\Pass1.log`, it returns `C:\Test\Logs`.</span></span>
<span data-ttu-id="43e53-175">Le paramètre **parent** est le paramètre d’emplacement de fractionnement par défaut.</span><span class="sxs-lookup"><span data-stu-id="43e53-175">The **Parent** parameter is the default split location parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-176">-Path</span><span class="sxs-lookup"><span data-stu-id="43e53-176">-Path</span></span>

<span data-ttu-id="43e53-177">Spécifie les chemins d’accès à fractionner.</span><span class="sxs-lookup"><span data-stu-id="43e53-177">Specifies the paths to be split.</span></span> <span data-ttu-id="43e53-178">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="43e53-178">Wildcard characters are permitted.</span></span> <span data-ttu-id="43e53-179">Si le chemin d’accès inclut des espaces, mettez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="43e53-179">If the path includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="43e53-180">Vous pouvez également diriger un chemin vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="43e53-180">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="43e53-181">-Qualificateur</span><span class="sxs-lookup"><span data-stu-id="43e53-181">-Qualifier</span></span>

<span data-ttu-id="43e53-182">Indique que cette applet de commande retourne uniquement le qualificateur du chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="43e53-182">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span> <span data-ttu-id="43e53-183">Pour les fournisseurs de système de fichiers ou de Registre, le qualificateur est le lecteur du chemin d’accès du fournisseur, tel que `C:` ou `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="43e53-183">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43e53-184">-Résoudre</span><span class="sxs-lookup"><span data-stu-id="43e53-184">-Resolve</span></span>

<span data-ttu-id="43e53-185">Indique que cette applet de commande affiche les éléments qui sont référencés par le chemin d’accès de fractionnement résultant au lieu d’afficher les éléments de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-185">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="43e53-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43e53-186">CommonParameters</span></span>

<span data-ttu-id="43e53-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="43e53-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43e53-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="43e53-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43e53-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="43e53-189">INPUTS</span></span>

### <span data-ttu-id="43e53-190">System.String</span><span class="sxs-lookup"><span data-stu-id="43e53-190">System.String</span></span>

<span data-ttu-id="43e53-191">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="43e53-191">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="43e53-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="43e53-192">OUTPUTS</span></span>

### <span data-ttu-id="43e53-193">System. String, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="43e53-193">System.String, System.Boolean</span></span>

<span data-ttu-id="43e53-194">`Split-Path` retourne des chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="43e53-194">`Split-Path` returns text strings.</span></span> <span data-ttu-id="43e53-195">Lorsque vous spécifiez le paramètre **Resolve** , `Split-Path` retourne une chaîne qui décrit l’emplacement des éléments ; il ne retourne pas d’objets qui représentent les éléments, tels qu’un objet **FileInfo** ou **RegistryKey** .</span><span class="sxs-lookup"><span data-stu-id="43e53-195">When you specify the **Resolve** parameter, `Split-Path` returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="43e53-196">Lorsque vous spécifiez le paramètre **IsAbsolute** , `Split-Path` retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="43e53-196">When you specify the **IsAbsolute** parameter, `Split-Path` returns a **Boolean** value.</span></span>

## <span data-ttu-id="43e53-197">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="43e53-197">NOTES</span></span>

- <span data-ttu-id="43e53-198">Les paramètres d’emplacement de fractionnement (**qualifier**, **parent**, **extension**, **feuille**, **LeafBase** et **NoQualifier**) sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="43e53-198">The split location parameters (**Qualifier**, **Parent**, **Extension**, **Leaf**, **LeafBase**, and **NoQualifier**) are exclusive.</span></span> <span data-ttu-id="43e53-199">Autrement dit, vous ne pouvez utiliser qu’un seul de ces paramètres dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="43e53-199">You can use only one in each command.</span></span>

- <span data-ttu-id="43e53-200">Les applets de commande qui contiennent le nom de **chemin** d’accès (les applets de commande **path** ) fonctionnent avec des noms de chemins d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter.</span><span class="sxs-lookup"><span data-stu-id="43e53-200">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="43e53-201">Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.</span><span class="sxs-lookup"><span data-stu-id="43e53-201">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="43e53-202">Utilisez-les de la même façon que vous utilisez **dirname**, **Normpath**, **realpath**, **join** ou d’autres manipulateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="43e53-202">Use them in the way that you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

- <span data-ttu-id="43e53-203">Vous pouvez utiliser les applets de commande **path** avec plusieurs fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="43e53-203">You can use the **Path** cmdlets together with several providers.</span></span> <span data-ttu-id="43e53-204">Il s’agit notamment des fournisseurs de système de fichiers, de Registre et de certificats.</span><span class="sxs-lookup"><span data-stu-id="43e53-204">These include the FileSystem, Registry, and Certificate providers.</span></span>

- <span data-ttu-id="43e53-205">`Split-Path` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="43e53-205">`Split-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="43e53-206">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="43e53-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="43e53-207">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="43e53-207">For more information, see about_Providers.</span></span>

## <span data-ttu-id="43e53-208">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="43e53-208">RELATED LINKS</span></span>

[<span data-ttu-id="43e53-209">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="43e53-209">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="43e53-210">Join-Path</span><span class="sxs-lookup"><span data-stu-id="43e53-210">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="43e53-211">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="43e53-211">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="43e53-212">Test-Path</span><span class="sxs-lookup"><span data-stu-id="43e53-212">Test-Path</span></span>](Test-Path.md)