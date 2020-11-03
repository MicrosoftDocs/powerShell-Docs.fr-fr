---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: 5d92acbe080b0d232047f1184c9a369b8837845c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203486"
---
# <span data-ttu-id="71cea-103">Split-Path</span><span class="sxs-lookup"><span data-stu-id="71cea-103">Split-Path</span></span>

## <span data-ttu-id="71cea-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="71cea-104">SYNOPSIS</span></span>
<span data-ttu-id="71cea-105">Retourne la partie spécifiée d'un chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-105">Returns the specified part of a path.</span></span>

## <span data-ttu-id="71cea-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="71cea-106">SYNTAX</span></span>

### <span data-ttu-id="71cea-107">ParentSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="71cea-107">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="71cea-108">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="71cea-108">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-NoQualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="71cea-109">LeafSet</span><span class="sxs-lookup"><span data-stu-id="71cea-109">LeafSet</span></span>

```
Split-Path [-Path] <String[]> [-Leaf] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="71cea-110">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="71cea-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-Qualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="71cea-111">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="71cea-111">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] [-IsAbsolute] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="71cea-112">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="71cea-112">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="71cea-113">Description</span><span class="sxs-lookup"><span data-stu-id="71cea-113">DESCRIPTION</span></span>

<span data-ttu-id="71cea-114">L’applet de commande **Split-Path** retourne uniquement la partie spécifiée d’un chemin d’accès, par exemple le dossier parent, un sous-dossier ou un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="71cea-114">The **Split-Path** cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span>
<span data-ttu-id="71cea-115">Elle peut également obtenir des éléments qui sont référencés par le chemin d’accès fractionné et indiquer si le chemin d’accès est relatif ou absolu.</span><span class="sxs-lookup"><span data-stu-id="71cea-115">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="71cea-116">Vous pouvez utiliser cette applet de commande pour obtenir ou envoyer uniquement une partie sélectionnée d’un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-116">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="71cea-117">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="71cea-117">EXAMPLES</span></span>

### <span data-ttu-id="71cea-118">Exemple 1 : obtenir le qualificateur d’un chemin d’accès</span><span class="sxs-lookup"><span data-stu-id="71cea-118">Example 1: Get the qualifier of a path</span></span>

```
PS C:\> Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
HKCU:
```

<span data-ttu-id="71cea-119">Cette commande retourne uniquement le qualificateur du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-119">This command returns only the qualifier of the path.</span></span>
<span data-ttu-id="71cea-120">Le qualificateur est le lecteur.</span><span class="sxs-lookup"><span data-stu-id="71cea-120">The qualifier is the drive.</span></span>

### <span data-ttu-id="71cea-121">Exemple 2 : afficher les noms de fichiers</span><span class="sxs-lookup"><span data-stu-id="71cea-121">Example 2: Display file names</span></span>

```
PS C:\> Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
Pass1.log
Pass2.log
...
```

<span data-ttu-id="71cea-122">Cette commande affiche les fichiers qui sont référencés par le chemin d’accès fractionné.</span><span class="sxs-lookup"><span data-stu-id="71cea-122">This command displays the files that are referenced by the split path.</span></span>
<span data-ttu-id="71cea-123">Étant donné que ce chemin d’accès est fractionné au dernier élément, également connu sous le nom de feuille, la commande affiche uniquement les noms de fichiers.</span><span class="sxs-lookup"><span data-stu-id="71cea-123">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="71cea-124">Le paramètre *Resolve* indique à **Split-Path** d’afficher les éléments référencés par le chemin d’accès de fractionnement, au lieu d’afficher le chemin d’accès de fractionnement.</span><span class="sxs-lookup"><span data-stu-id="71cea-124">The *Resolve* parameter tells **Split-Path** to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="71cea-125">Comme toutes les commandes **Split-Path** , cette commande retourne des chaînes.</span><span class="sxs-lookup"><span data-stu-id="71cea-125">Like all **Split-Path** commands, this command returns strings.</span></span>
<span data-ttu-id="71cea-126">Elle ne retourne pas d’objets **FileInfo** représentant les fichiers.</span><span class="sxs-lookup"><span data-stu-id="71cea-126">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="71cea-127">Exemple 3 : récupération du conteneur parent</span><span class="sxs-lookup"><span data-stu-id="71cea-127">Example 3: Get the parent container</span></span>

```
PS C:\> Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="71cea-128">Cette commande retourne uniquement les conteneurs parents du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-128">This command returns only the parent containers of the path.</span></span>
<span data-ttu-id="71cea-129">Comme il n’inclut pas de paramètres pour spécifier le fractionnement, **Split-Path** utilise la valeur par défaut de l’emplacement de fractionnement, qui est le *parent* .</span><span class="sxs-lookup"><span data-stu-id="71cea-129">Because it does not include any parameters to specify the split, **Split-Path** uses the split location default, which is *Parent* .</span></span>

### <span data-ttu-id="71cea-130">Exemple 4 : détermine si un chemin d’accès est absolu</span><span class="sxs-lookup"><span data-stu-id="71cea-130">Example 4: Determines whether a path is absolute</span></span>

```
PS C:\> Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
False
```

<span data-ttu-id="71cea-131">Cette commande détermine si le chemin d’accès est relatif ou absolu.</span><span class="sxs-lookup"><span data-stu-id="71cea-131">This command determines whether the path is relative or absolute.</span></span>
<span data-ttu-id="71cea-132">Dans ce cas, étant donné que le chemin d’accès est relatif au dossier actif, représenté par un point (.), il retourne $False.</span><span class="sxs-lookup"><span data-stu-id="71cea-132">In this case, because the path is relative to the current folder, which is represented by a dot (.), it returns $False.</span></span>

### <span data-ttu-id="71cea-133">Exemple 5 : modifier l’emplacement d’un chemin d’accès spécifié</span><span class="sxs-lookup"><span data-stu-id="71cea-133">Example 5: Change location to a specified path</span></span>

```
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="71cea-134">Cette commande remplace votre emplacement par le dossier qui contient le profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71cea-134">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="71cea-135">La commande entre parenthèses utilise **Split-Path** pour retourner uniquement le parent du chemin d’accès stocké dans la variable $profile intégrée.</span><span class="sxs-lookup"><span data-stu-id="71cea-135">The command in parentheses uses **Split-Path** to return only the parent of the path stored in the built-in $Profile variable.</span></span>
<span data-ttu-id="71cea-136">Le paramètre *parent* est le paramètre d’emplacement de fractionnement par défaut.</span><span class="sxs-lookup"><span data-stu-id="71cea-136">The *Parent* parameter is the default split location parameter.</span></span>
<span data-ttu-id="71cea-137">Par conséquent, vous pouvez l’omettre de la commande.</span><span class="sxs-lookup"><span data-stu-id="71cea-137">Therefore, you can omit it from the command.</span></span>
<span data-ttu-id="71cea-138">Les parenthèses indiquent à PowerShell d’exécuter la commande en premier.</span><span class="sxs-lookup"><span data-stu-id="71cea-138">The parentheses direct PowerShell to run the command first.</span></span>
<span data-ttu-id="71cea-139">Il s’agit d’une méthode utile pour vous déplacer vers un dossier qui a un nom de chemin d’accès long.</span><span class="sxs-lookup"><span data-stu-id="71cea-139">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="71cea-140">Exemple 6 : fractionner un chemin d’accès à l’aide du pipeline</span><span class="sxs-lookup"><span data-stu-id="71cea-140">Example 6: Split a path by using the pipeline</span></span>

```
PS C:\> 'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="71cea-141">Cette commande utilise un opérateur de pipeline (|) pour envoyer un chemin d’accès à **Split-Path** .</span><span class="sxs-lookup"><span data-stu-id="71cea-141">This command uses a pipeline operator (|) to send a path to **Split-Path** .</span></span>
<span data-ttu-id="71cea-142">Le chemin d’accès figure entre guillemets pour indiquer qu’il s’agit d’un jeton unique.</span><span class="sxs-lookup"><span data-stu-id="71cea-142">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="71cea-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="71cea-143">PARAMETERS</span></span>

### <span data-ttu-id="71cea-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="71cea-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="71cea-145">Ce paramètre n’est pas pris en charge par les fournisseurs installés avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71cea-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="71cea-146">Pour emprunter l’identité d’un autre utilisateur ou élever vos informations d’identification lors de l’exécution de cette applet de commande, utilisez [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="71cea-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="71cea-147">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="71cea-147">-IsAbsolute</span></span>

<span data-ttu-id="71cea-148">Indique que cette applet de commande retourne $True si le chemin d’accès est absolu et $False s’il est relatif.</span><span class="sxs-lookup"><span data-stu-id="71cea-148">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span>
<span data-ttu-id="71cea-149">Un chemin d’accès absolu a une longueur supérieure à zéro et n’utilise pas de point (.) pour indiquer le chemin d’accès actuel.</span><span class="sxs-lookup"><span data-stu-id="71cea-149">An absolute path has a length greater than zero and does not use a dot (.) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="71cea-150">-Feuille</span><span class="sxs-lookup"><span data-stu-id="71cea-150">-Leaf</span></span>

<span data-ttu-id="71cea-151">Indique que cette applet de commande retourne uniquement le dernier élément ou conteneur dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-151">Indicates that this cmdlet returns only the last item or container in the path.</span></span>
<span data-ttu-id="71cea-152">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement PASS1. log.</span><span class="sxs-lookup"><span data-stu-id="71cea-152">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="71cea-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="71cea-153">-LiteralPath</span></span>

<span data-ttu-id="71cea-154">Spécifie les chemins d’accès à fractionner.</span><span class="sxs-lookup"><span data-stu-id="71cea-154">Specifies the paths to be split.</span></span>
<span data-ttu-id="71cea-155">Contrairement au paramètre *Path* , la valeur de *LiteralPath* est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="71cea-155">Unlike *Path* , the value of *LiteralPath* is used exactly as it is typed.</span></span>
<span data-ttu-id="71cea-156">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="71cea-156">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="71cea-157">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="71cea-157">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="71cea-158">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="71cea-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="71cea-159">-NoQualifier</span><span class="sxs-lookup"><span data-stu-id="71cea-159">-NoQualifier</span></span>

<span data-ttu-id="71cea-160">Indique que cette applet de commande retourne le chemin d’accès sans le qualificateur.</span><span class="sxs-lookup"><span data-stu-id="71cea-160">Indicates that this cmdlet returns the path without the qualifier.</span></span>
<span data-ttu-id="71cea-161">Pour les fournisseurs de système de fichiers ou de Registre, le qualificateur est le lecteur du chemin d’accès du fournisseur (C: ou HKCU:, par exemple).</span><span class="sxs-lookup"><span data-stu-id="71cea-161">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>
<span data-ttu-id="71cea-162">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne uniquement \Test\Logs\Pass1.log.</span><span class="sxs-lookup"><span data-stu-id="71cea-162">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only \Test\Logs\Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="71cea-163">-Parent</span><span class="sxs-lookup"><span data-stu-id="71cea-163">-Parent</span></span>

<span data-ttu-id="71cea-164">Indique que cette applet de commande retourne uniquement les conteneurs parents de l’élément ou du conteneur spécifié par le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-164">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span>
<span data-ttu-id="71cea-165">Par exemple, dans le chemin d’accès `C:\Test\Logs\Pass1.log` , elle retourne C:\Test\Logs.</span><span class="sxs-lookup"><span data-stu-id="71cea-165">For example, in the path `C:\Test\Logs\Pass1.log`, it returns C:\Test\Logs.</span></span>
<span data-ttu-id="71cea-166">Le paramètre *parent* est le paramètre d’emplacement de fractionnement par défaut.</span><span class="sxs-lookup"><span data-stu-id="71cea-166">The *Parent* parameter is the default split location parameter.</span></span>

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

### <span data-ttu-id="71cea-167">-Path</span><span class="sxs-lookup"><span data-stu-id="71cea-167">-Path</span></span>

<span data-ttu-id="71cea-168">Spécifie les chemins d’accès à fractionner.</span><span class="sxs-lookup"><span data-stu-id="71cea-168">Specifies the paths to be split.</span></span>
<span data-ttu-id="71cea-169">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="71cea-169">Wildcard characters are permitted.</span></span>
<span data-ttu-id="71cea-170">Si le chemin d’accès inclut des espaces, mettez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="71cea-170">If the path includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="71cea-171">Vous pouvez également diriger un chemin vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71cea-171">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, NoQualifierSet, LeafSet, QualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="71cea-172">-Qualificateur</span><span class="sxs-lookup"><span data-stu-id="71cea-172">-Qualifier</span></span>

<span data-ttu-id="71cea-173">Indique que cette applet de commande retourne uniquement le qualificateur du chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="71cea-173">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span>
<span data-ttu-id="71cea-174">Pour les fournisseurs de système de fichiers ou de Registre, le qualificateur est le lecteur du chemin d’accès du fournisseur (C: ou HKCU:, par exemple).</span><span class="sxs-lookup"><span data-stu-id="71cea-174">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="71cea-175">-Résoudre</span><span class="sxs-lookup"><span data-stu-id="71cea-175">-Resolve</span></span>

<span data-ttu-id="71cea-176">Indique que cette applet de commande affiche les éléments qui sont référencés par le chemin d’accès de fractionnement résultant au lieu d’afficher les éléments de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-176">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="71cea-177">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="71cea-177">-UseTransaction</span></span>

<span data-ttu-id="71cea-178">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="71cea-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="71cea-179">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="71cea-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="71cea-180">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="71cea-180">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="71cea-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71cea-181">CommonParameters</span></span>

<span data-ttu-id="71cea-182">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="71cea-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71cea-183">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="71cea-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71cea-184">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="71cea-184">INPUTS</span></span>

### <span data-ttu-id="71cea-185">System.String</span><span class="sxs-lookup"><span data-stu-id="71cea-185">System.String</span></span>

<span data-ttu-id="71cea-186">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="71cea-186">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="71cea-187">SORTIES</span><span class="sxs-lookup"><span data-stu-id="71cea-187">OUTPUTS</span></span>

### <span data-ttu-id="71cea-188">System. String, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="71cea-188">System.String, System.Boolean</span></span>

<span data-ttu-id="71cea-189">**Split-Path retourne des chaînes de** texte.</span><span class="sxs-lookup"><span data-stu-id="71cea-189">**Split-Path** returns text strings.</span></span>
<span data-ttu-id="71cea-190">Lorsque vous spécifiez le paramètre *Resolve* , **Split-Path** retourne une chaîne qui décrit l’emplacement des éléments. elle ne retourne pas d’objets qui représentent les éléments, tels qu’un objet **FileInfo** ou **RegistryKey** .</span><span class="sxs-lookup"><span data-stu-id="71cea-190">When you specify the *Resolve* parameter, **Split-Path** returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="71cea-191">Lorsque vous spécifiez le paramètre *IsAbsolute* , **Split-Path** retourne une valeur **booléenne** .</span><span class="sxs-lookup"><span data-stu-id="71cea-191">When you specify the *IsAbsolute* parameter, **Split-Path** returns a **Boolean** value.</span></span>

## <span data-ttu-id="71cea-192">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="71cea-192">NOTES</span></span>

* <span data-ttu-id="71cea-193">Les paramètres d’emplacement de fractionnement ( *qualifier* , *parent* , *feuille* et *NoQualifier* ) sont exclusifs.</span><span class="sxs-lookup"><span data-stu-id="71cea-193">The split location parameters ( *Qualifier* , *Parent* , *Leaf* , and *NoQualifier* ) are exclusive.</span></span> <span data-ttu-id="71cea-194">Autrement dit, vous ne pouvez utiliser qu’un seul de ces paramètres dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="71cea-194">You can use only one in each command.</span></span>

  <span data-ttu-id="71cea-195">Les applets de commande qui contiennent le nom de **chemin** d’accès (les applets de commande **path** ) fonctionnent avec des noms de chemins d’accès et retournent les noms dans un format concis que tous les fournisseurs PowerShell peuvent interpréter.</span><span class="sxs-lookup"><span data-stu-id="71cea-195">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span>
<span data-ttu-id="71cea-196">Elles sont conçues pour être utilisées dans des programmes et des scripts dans lesquels vous voulez afficher l’intégralité ou une partie d’un nom de chemin d’accès dans un format particulier.</span><span class="sxs-lookup"><span data-stu-id="71cea-196">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="71cea-197">Utilisez-les de la même façon que vous utilisez **dirname** , **Normpath** , **realpath** , **join** ou d’autres manipulateurs de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="71cea-197">Use them in the way that you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

  <span data-ttu-id="71cea-198">Vous pouvez utiliser les applets de commande **path** avec plusieurs fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="71cea-198">You can use the **Path** cmdlets together with several providers.</span></span>
<span data-ttu-id="71cea-199">Il s’agit notamment des fournisseurs de système de fichiers, de Registre et de certificats.</span><span class="sxs-lookup"><span data-stu-id="71cea-199">These include the FileSystem, Registry, and Certificate providers.</span></span>

  <span data-ttu-id="71cea-200">**Split-Path** est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="71cea-200">**Split-Path** is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="71cea-201">Pour répertorier les fournisseurs disponibles dans votre session, tapez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="71cea-201">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="71cea-202">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="71cea-202">For more information, see about_Providers.</span></span>

## <span data-ttu-id="71cea-203">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="71cea-203">RELATED LINKS</span></span>

[<span data-ttu-id="71cea-204">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="71cea-204">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="71cea-205">Join-Path</span><span class="sxs-lookup"><span data-stu-id="71cea-205">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="71cea-206">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="71cea-206">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="71cea-207">Test-Path</span><span class="sxs-lookup"><span data-stu-id="71cea-207">Test-Path</span></span>](Test-Path.md)
