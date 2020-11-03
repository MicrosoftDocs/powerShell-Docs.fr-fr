---
external help file: ISE-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202478"
---
# <span data-ttu-id="c0399-103">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="c0399-103">Import-IseSnippet</span></span>

## <span data-ttu-id="c0399-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c0399-104">SYNOPSIS</span></span>
<span data-ttu-id="c0399-105">Importe les extraits de code de l'environnement ISE dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0399-105">Imports ISE snippets into the current session</span></span>

## <span data-ttu-id="c0399-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0399-106">SYNTAX</span></span>

### <span data-ttu-id="c0399-107">FromFolder (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c0399-107">FromFolder (Default)</span></span>

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### <span data-ttu-id="c0399-108">FromModule</span><span class="sxs-lookup"><span data-stu-id="c0399-108">FromModule</span></span>

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="c0399-109">Description</span><span class="sxs-lookup"><span data-stu-id="c0399-109">DESCRIPTION</span></span>

<span data-ttu-id="c0399-110">L' `Import-IseSnippet` applet de commande importe des « extraits de code » de texte réutilisables à partir d’un module ou d’un répertoire dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0399-110">The `Import-IseSnippet` cmdlet imports reusable text "snippets" from a module or a directory into the current session.</span></span> <span data-ttu-id="c0399-111">Les extraits de code sont immédiatement disponibles pour une utilisation dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c0399-111">The snippets are immediately available for use in Windows PowerShell ISE.</span></span> <span data-ttu-id="c0399-112">Cette applet de commande fonctionne uniquement dans Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="c0399-112">This cmdlet works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="c0399-113">Pour afficher et utiliser les extraits de code importés, dans le menu Windows PowerShell ISE **Edition** , cliquez sur **Démarrer les extraits** ou appuyez sur <kbd>CTRL</kbd> + <kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c0399-113">To view and use the imported snippets, from the Windows PowerShell ISE **Edit** menu, click **Start Snippets** or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="c0399-114">Les extraits importés sont disponibles uniquement dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0399-114">Imported snippets are available only in the current session.</span></span> <span data-ttu-id="c0399-115">Pour importer les extraits de code dans toutes les sessions Windows PowerShell ISE, ajoutez une `Import-IseSnippet` commande à votre profil Windows PowerShell ou copiez les fichiers d’extraits de code dans votre répertoire d’extraits de code local `$home\Documents\WindowsPowershell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="c0399-115">To import the snippets into all Windows PowerShell ISE sessions, add an `Import-IseSnippet` command to your Windows PowerShell profile or copy the snippet files to your local snippets directory `$home\Documents\WindowsPowershell\Snippets`.</span></span>

<span data-ttu-id="c0399-116">Pour importer des extraits de code, ceux-ci doivent être correctement mis en forme dans l’extrait de code XML pour les extraits de Windows PowerShell ISE et enregistrés dans Snippet.ps1fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="c0399-116">To import snippets, they must be properly formatted in the snippet XML for Windows PowerShell ISE snippets and saved in Snippet.ps1xml files.</span></span> <span data-ttu-id="c0399-117">Pour créer des extraits de code éligibles, utilisez l’applet de commande `New-IseSnippet` .</span><span class="sxs-lookup"><span data-stu-id="c0399-117">To create eligible snippets, use the `New-IseSnippet` cmdlet.</span></span> <span data-ttu-id="c0399-118">`New-IseSnippet` crée un `<SnippetTitle>.Snippets.ps1xml` fichier dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire.</span><span class="sxs-lookup"><span data-stu-id="c0399-118">`New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span> <span data-ttu-id="c0399-119">Vous pouvez déplacer ou copier les extraits de code dans le répertoire Snippets d'un module Windows PowerShell ou dans tout autre répertoire.</span><span class="sxs-lookup"><span data-stu-id="c0399-119">You can move or copy the snippets to the Snippets directory of a Windows PowerShell module, or to any other directory.</span></span>

<span data-ttu-id="c0399-120">L' `Get-IseSnippet` applet de commande, qui obtient les extraits de code créés par l’utilisateur dans le répertoire des extraits de code locaux, n’obtient pas les extraits de code importés.</span><span class="sxs-lookup"><span data-stu-id="c0399-120">The `Get-IseSnippet` cmdlet, which gets user-created snippets in the local snippets directory, does not get imported snippets.</span></span>

<span data-ttu-id="c0399-121">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c0399-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="c0399-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c0399-122">EXAMPLES</span></span>

### <span data-ttu-id="c0399-123">Exemple 1 : importer des extraits de code à partir d’un répertoire</span><span class="sxs-lookup"><span data-stu-id="c0399-123">Example 1: Import snippets from a directory</span></span>

<span data-ttu-id="c0399-124">Cet exemple importe les extraits de code à partir du `\\Server01\Public\Snippets` répertoire dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0399-124">This example imports the snippets from the `\\Server01\Public\Snippets` directory into the current session.</span></span> <span data-ttu-id="c0399-125">Elle utilise le paramètre **recurse** pour récupérer des extraits de code à partir de tous les sous-répertoires du répertoire des extraits de code.</span><span class="sxs-lookup"><span data-stu-id="c0399-125">It uses the **Recurse** parameter to get snippets from all subdirectories of the Snippets directory.</span></span>

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### <span data-ttu-id="c0399-126">Exemple 2 : importer des extraits de code à partir d’un module</span><span class="sxs-lookup"><span data-stu-id="c0399-126">Example 2: Import snippets from a module</span></span>

<span data-ttu-id="c0399-127">Cet exemple importe les extraits de code à partir du module **SnippetModule** .</span><span class="sxs-lookup"><span data-stu-id="c0399-127">This example imports the snippets from the **SnippetModule** module.</span></span> <span data-ttu-id="c0399-128">La commande utilise le paramètre **listAvailable** pour importer les extraits de code même si le module **SnippetModule** n’est pas importé dans la session de l’utilisateur lors de l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="c0399-128">The command uses the **ListAvailable** parameter to import the snippets even if the **SnippetModule** module is not imported into the user's session when the command runs.</span></span>

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### <span data-ttu-id="c0399-129">Exemple 3 : Rechercher des extraits de code dans les modules</span><span class="sxs-lookup"><span data-stu-id="c0399-129">Example 3: Find snippets in modules</span></span>

<span data-ttu-id="c0399-130">Cet exemple obtient des extraits de code dans tous les modules installés dans la variable d’environnement PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="c0399-130">This example gets snippets in all installed modules in the PSModulePath environment variable.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### <span data-ttu-id="c0399-131">Exemple 4 : importer tous les extraits de code de module</span><span class="sxs-lookup"><span data-stu-id="c0399-131">Example 4: Import all module snippets</span></span>

<span data-ttu-id="c0399-132">Cet exemple importe tous les extraits de code de tous les modules installés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0399-132">This example imports all snippets from all installed modules into the current session.</span></span> <span data-ttu-id="c0399-133">En règle générale, vous n’avez pas besoin d’exécuter une commande comme celle-ci, car les modules qui ont des extraits de code utiliseront l’applet de commande `Import-IseSnippet` pour les importer pour vous lors de l’importation du module.</span><span class="sxs-lookup"><span data-stu-id="c0399-133">Typically, you don't need to run a command like this because modules that have snippets will use the `Import-IseSnippet` cmdlet to import them for you when the module is imported.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### <span data-ttu-id="c0399-134">Exemple 5 : copier tous les extraits de code de module</span><span class="sxs-lookup"><span data-stu-id="c0399-134">Example 5: Copy all module snippets</span></span>

<span data-ttu-id="c0399-135">Cet exemple copie les fichiers d’extraits de tous les modules installés dans le répertoire Snippets de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c0399-135">This example copies the snippet files from all installed modules into the Snippets directory of the current user.</span></span> <span data-ttu-id="c0399-136">Contrairement aux extraits de code importés qui affectent uniquement la session active, les extraits copiés sont disponibles dans toutes les sessions Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c0399-136">Unlike imported snippets, which affect only the current session, copied snippets are available in every Windows PowerShell ISE session.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## <span data-ttu-id="c0399-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0399-137">PARAMETERS</span></span>

### <span data-ttu-id="c0399-138">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="c0399-138">-ListAvailable</span></span>

<span data-ttu-id="c0399-139">Indique que cette applet de commande obtient les extraits de code des modules installés sur l’ordinateur, même si les modules ne sont pas importés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0399-139">Indicates that this cmdlet gets snippets from modules that are installed on the computer, even if the modules are not imported into the current session.</span></span> <span data-ttu-id="c0399-140">Si ce paramètre est omis et que le module spécifié par le paramètre **module** n’est pas importé dans la session active, la tentative d’extraction des extraits de code à partir du module échoue.</span><span class="sxs-lookup"><span data-stu-id="c0399-140">If this parameter is omitted, and the module that is specified by the **Module** parameter is not imported into the current session, the attempt to get the snippets from the module fails.</span></span>

<span data-ttu-id="c0399-141">Ce paramètre est valide uniquement quand le paramètre **Module** est utilisé dans la commande.</span><span class="sxs-lookup"><span data-stu-id="c0399-141">This parameter is valid only when the **Module** parameter is used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0399-142">-Module</span><span class="sxs-lookup"><span data-stu-id="c0399-142">-Module</span></span>

<span data-ttu-id="c0399-143">Importe des extraits de code du module spécifié dans la session active.</span><span class="sxs-lookup"><span data-stu-id="c0399-143">Imports snippets from the specified module into the current session.</span></span> <span data-ttu-id="c0399-144">Les caractères génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c0399-144">Wildcard characters are not supported.</span></span>

<span data-ttu-id="c0399-145">Ce paramètre importe des extraits de code à partir de Snippet.ps1fichiers XML dans le sous-répertoire snippets dans le chemin d’accès du module, tel que `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="c0399-145">This parameter imports snippets from Snippet.ps1xml files in the Snippets subdirectory in the module path, such as `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets`.</span></span>

<span data-ttu-id="c0399-146">Ce paramètre est conçu pour être utilisé par les auteurs de module dans un script de démarrage, tel qu'un script spécifié dans la clé **ScriptsToProcess** d'un manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="c0399-146">This parameter is designed to be used by module authors in a startup script, such as a script specified in the **ScriptsToProcess** key of a module manifest.</span></span> <span data-ttu-id="c0399-147">Les extraits de code d’un module ne sont pas importés automatiquement avec le module, mais vous pouvez utiliser une `Import-IseSnippet` commande pour les importer.</span><span class="sxs-lookup"><span data-stu-id="c0399-147">Snippets in a module are not automatically imported with the module, but you can use an `Import-IseSnippet` command to import them.</span></span>

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0399-148">-Path</span><span class="sxs-lookup"><span data-stu-id="c0399-148">-Path</span></span>

<span data-ttu-id="c0399-149">Spécifie le chemin d’accès au répertoire des extraits de code dans lequel cette applet de commande importe des extraits de code.</span><span class="sxs-lookup"><span data-stu-id="c0399-149">Specifies the path to the snippets directory in which this cmdlet imports snippets.</span></span>

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c0399-150">-Recurse</span><span class="sxs-lookup"><span data-stu-id="c0399-150">-Recurse</span></span>

<span data-ttu-id="c0399-151">Indique que cette applet de commande importe des extraits de code à partir de tous les sous-répertoires de la valeur du paramètre **path** .</span><span class="sxs-lookup"><span data-stu-id="c0399-151">Indicates that this cmdlet imports snippets from all subdirectories of the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="c0399-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0399-152">CommonParameters</span></span>

<span data-ttu-id="c0399-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0399-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0399-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c0399-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0399-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c0399-155">INPUTS</span></span>

### <span data-ttu-id="c0399-156">Aucun</span><span class="sxs-lookup"><span data-stu-id="c0399-156">None</span></span>

<span data-ttu-id="c0399-157">Cette applet de commande n'accepte pas d'entrée provenant du pipeline.</span><span class="sxs-lookup"><span data-stu-id="c0399-157">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="c0399-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c0399-158">OUTPUTS</span></span>

### <span data-ttu-id="c0399-159">Aucun</span><span class="sxs-lookup"><span data-stu-id="c0399-159">None</span></span>

<span data-ttu-id="c0399-160">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="c0399-160">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="c0399-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="c0399-161">NOTES</span></span>

- <span data-ttu-id="c0399-162">Vous ne pouvez pas utiliser l' `Get-IseSnippet` applet de commande pour récupérer des extraits de code importés.</span><span class="sxs-lookup"><span data-stu-id="c0399-162">You cannot use the `Get-IseSnippet` cmdlet to get imported snippets.</span></span> <span data-ttu-id="c0399-163">`Get-IseSnippet` Obtient uniquement les extraits de code dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire.</span><span class="sxs-lookup"><span data-stu-id="c0399-163">`Get-IseSnippet` gets only snippets in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
- <span data-ttu-id="c0399-164">`Import-IseSnippet` utilise la méthode statique **Load** des objets **Microsoft. PowerShell. Host. ISE. ISESnippetCollection** .</span><span class="sxs-lookup"><span data-stu-id="c0399-164">`Import-IseSnippet` uses the **Load** static method of **Microsoft.PowerShell.Host.ISE.ISESnippetCollection** objects.</span></span> <span data-ttu-id="c0399-165">Vous pouvez également utiliser la méthode **Load** des extraits de code dans le modèle objet Windows PowerShell ISE : `$psISE.CurrentPowerShellTab.Snippets.Load()`</span><span class="sxs-lookup"><span data-stu-id="c0399-165">You can also use the **Load** method of snippets in the Windows PowerShell ISE object model: `$psISE.CurrentPowerShellTab.Snippets.Load()`</span></span>
- <span data-ttu-id="c0399-166">L' `New-IseSnippet` applet de commande stocke les nouveaux extraits de code créés par l’utilisateur dans les fichiers. ps1xml non signés.</span><span class="sxs-lookup"><span data-stu-id="c0399-166">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="c0399-167">Par conséquent, Windows PowerShell ne peut pas les charger dans une session dans laquelle la stratégie d'exécution est **AllSigned** ou **Restricted** .</span><span class="sxs-lookup"><span data-stu-id="c0399-167">As such, Windows PowerShell cannot load them into a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="c0399-168">Dans une session **Restricted** ou **AllSigned** , vous pouvez créer, obtenir et importer des extraits de code créés par l'utilisateur non signés, mais vous ne pouvez pas les utiliser dans la session.</span><span class="sxs-lookup"><span data-stu-id="c0399-168">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="c0399-169">Pour utiliser des extraits de code créés par l’utilisateur non signés que l’applet de commande `Import-IseSnippet` retourne, modifiez la stratégie d’exécution, puis redémarrez Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c0399-169">To use unsigned user-created snippets that the `Import-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="c0399-170">Pour plus d'informations sur les stratégies d'exécution Windows PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="c0399-170">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="c0399-171">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="c0399-171">RELATED LINKS</span></span>

[<span data-ttu-id="c0399-172">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="c0399-172">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="c0399-173">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="c0399-173">New-IseSnippet</span></span>](New-IseSnippet.md)
