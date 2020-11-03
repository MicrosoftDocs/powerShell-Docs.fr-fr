---
external help file: ISE-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202477"
---
# <span data-ttu-id="9b090-103">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="9b090-103">New-IseSnippet</span></span>

## <span data-ttu-id="9b090-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9b090-104">SYNOPSIS</span></span>
<span data-ttu-id="9b090-105">Crée un extrait de code Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-105">Creates a Windows PowerShell ISE code snippet.</span></span>

## <span data-ttu-id="9b090-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b090-106">SYNTAX</span></span>

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="9b090-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b090-107">DESCRIPTION</span></span>

<span data-ttu-id="9b090-108">L' `New-ISESnippet` applet de commande crée un « extrait » de texte réutilisable pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-108">The `New-ISESnippet` cmdlet creates a reusable text "snippet" for Windows PowerShell ISE.</span></span> <span data-ttu-id="9b090-109">Vous pouvez utiliser des extraits de code pour ajouter du texte au volet de script ou de commandes dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-109">You can use snippets to add text to the Script pane or Command pane in Windows PowerShell ISE.</span></span> <span data-ttu-id="9b090-110">Cette applet de commande est disponible uniquement dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-110">This cmdlet is available only in Windows PowerShell ISE.</span></span>

<span data-ttu-id="9b090-111">À compter de Windows PowerShell 3.0, Windows PowerShell ISE inclut une collection d'extraits de code intégrés.</span><span class="sxs-lookup"><span data-stu-id="9b090-111">Beginning in Windows PowerShell 3.0, Windows PowerShell ISE includes a collection of built-in snippets.</span></span> <span data-ttu-id="9b090-112">L' `New-ISESnippet` applet de commande vous permet de créer vos propres extraits de code à ajouter à la collection intégrée.</span><span class="sxs-lookup"><span data-stu-id="9b090-112">The `New-ISESnippet` cmdlet lets you create your own snippets to add to the built-in collection.</span></span> <span data-ttu-id="9b090-113">Vous pouvez afficher, modifier, ajouter, supprimer et partager les fichiers d'extraits de code et les inclure dans les modules Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b090-113">You can view, change, add, delete, and share snippet files and include them in Windows PowerShell modules.</span></span> <span data-ttu-id="9b090-114">Pour afficher les extraits de code dans Windows PowerShell ISE, dans le menu **Edition** , sélectionnez **Démarrer les extraits** ou appuyez sur <kbd>CTRL</kbd> + <kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b090-114">To see snippets in Windows PowerShell ISE, from the **Edit** menu, select **Start Snippets** or press <kbd>CTRL</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="9b090-115">L' `New-ISESnippet` applet de commande crée un `<Title>.Snippets.ps1xml` fichier dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire avec le titre que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="9b090-115">The `New-ISESnippet` cmdlet creates a `<Title>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory with the title that you specify.</span></span> <span data-ttu-id="9b090-116">Pour inclure un fichier d'extraits de code dans un module que vous créez, ajoutez le fichier d'extraits à un sous-répertoire Snippets de votre répertoire de module.</span><span class="sxs-lookup"><span data-stu-id="9b090-116">To include a snippet file in a module that you are authoring, add the snippet file to a Snippets subdirectory of your module directory.</span></span>

<span data-ttu-id="9b090-117">Vous ne pouvez pas utiliser d’extraits de code créés par l’utilisateur dans une session dans laquelle la stratégie d’exécution est **restreinte** ou **AllSigned** .</span><span class="sxs-lookup"><span data-stu-id="9b090-117">You cannot use user-created snippets in a session in which the execution policy is **Restricted** or **AllSigned** .</span></span>

<span data-ttu-id="9b090-118">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9b090-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="9b090-119">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9b090-119">EXAMPLES</span></span>

### <span data-ttu-id="9b090-120">Exemple 1 : créer un extrait de code d’aide Comment-Based</span><span class="sxs-lookup"><span data-stu-id="9b090-120">Example 1: Create a Comment-Based help snippet</span></span>

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

<span data-ttu-id="9b090-121">Cette commande crée un extrait de code Comment-BasedHelp pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-121">This command creates a Comment-BasedHelp snippet for Windows PowerShell ISE.</span></span> <span data-ttu-id="9b090-122">Il crée un fichier nommé `Comment-BasedHelp.snippets.ps1xml` dans le répertoire des extraits de code de l’utilisateur `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="9b090-122">It creates a file named `Comment-BasedHelp.snippets.ps1xml` in the user's Snippets directory `$home\Documents\WindowsPowerShell\Snippets`.</span></span>

### <span data-ttu-id="9b090-123">Exemple 2 : créer un extrait de code obligatoire</span><span class="sxs-lookup"><span data-stu-id="9b090-123">Example 2: Create a mandatory snippet</span></span>

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

<span data-ttu-id="9b090-124">Cet exemple crée un extrait de code nommé **obligatoire** pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-124">This example creates a snippet named **Mandatory** for Windows PowerShell ISE.</span></span> <span data-ttu-id="9b090-125">La première commande enregistre le texte de l’extrait de code dans la `$M` variable.</span><span class="sxs-lookup"><span data-stu-id="9b090-125">The first command saves the snippet text in the `$M` variable.</span></span> <span data-ttu-id="9b090-126">La deuxième commande utilise l' `New-ISESnippet` applet de commande pour créer l’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-126">The second command uses the `New-ISESnippet` cmdlet to create the snippet.</span></span> <span data-ttu-id="9b090-127">La commande utilise le paramètre **Force** pour remplacer un extrait de code précédent avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="9b090-127">The command uses the **Force** parameter to overwrite a previous snippet with the same name.</span></span>

### <span data-ttu-id="9b090-128">Exemple 3 : copier un extrait de code obligatoire d’un dossier vers un dossier de destination</span><span class="sxs-lookup"><span data-stu-id="9b090-128">Example 3: Copy a mandatory snippet from a folder to a destination folder</span></span>

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

<span data-ttu-id="9b090-129">Cette commande utilise la `Copy-Item` cmdlet pour copier l’extrait de code **obligatoire** à partir du dossier où `New-ISESnippet` il est placé dans le partage de fichiers Server\Share.</span><span class="sxs-lookup"><span data-stu-id="9b090-129">This command uses the `Copy-Item` cmdlet to copy the **Mandatory** snippet from the folder where `New-ISESnippet` places it to the Server\Share file share.</span></span>

## <span data-ttu-id="9b090-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9b090-130">PARAMETERS</span></span>

### <span data-ttu-id="9b090-131">-Auteur</span><span class="sxs-lookup"><span data-stu-id="9b090-131">-Author</span></span>

<span data-ttu-id="9b090-132">Spécifie l’auteur de l’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-132">Specifies the author of the snippet.</span></span> <span data-ttu-id="9b090-133">Le champ de l'auteur apparaît dans le fichier d'extraits de code, mais il n'apparaît pas quand vous cliquez sur le nom de l'extrait de code dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-133">The author field appears in the snippet file, but it does not appear when you click the snippet name in Windows PowerShell ISE.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b090-134">-CaretOffset</span><span class="sxs-lookup"><span data-stu-id="9b090-134">-CaretOffset</span></span>

<span data-ttu-id="9b090-135">Spécifie le caractère du texte de l’extrait de code sur lequel cette applet de commande place le curseur.</span><span class="sxs-lookup"><span data-stu-id="9b090-135">Specifies the character of the snippet text that this cmdlet places the cursor on.</span></span> <span data-ttu-id="9b090-136">Entrez un entier qui représente la position du curseur, « 1 » représentant le premier caractère de texte.</span><span class="sxs-lookup"><span data-stu-id="9b090-136">Enter an integer that represents the cursor position, with "1" representing the first character of text.</span></span> <span data-ttu-id="9b090-137">La valeur par défaut, 0 (zéro), place le curseur immédiatement avant le premier caractère de texte.</span><span class="sxs-lookup"><span data-stu-id="9b090-137">The default value, 0 (zero), places the cursor immediately before the first character of text.</span></span> <span data-ttu-id="9b090-138">Ce paramètre ne met pas en retrait le texte de l'extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-138">This parameter does not indent the snippet text.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b090-139">Description</span><span class="sxs-lookup"><span data-stu-id="9b090-139">-Description</span></span>

<span data-ttu-id="9b090-140">Spécifie une description de l’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-140">Specifies a description of the snippet.</span></span> <span data-ttu-id="9b090-141">La valeur de description s'affiche quand vous cliquez sur le nom de l'extrait de code dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-141">The description value appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="9b090-142">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9b090-142">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b090-143">-Force</span><span class="sxs-lookup"><span data-stu-id="9b090-143">-Force</span></span>

<span data-ttu-id="9b090-144">Indique que cette applet de commande remplace les fichiers d’extrait de code portant le même nom au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="9b090-144">Indicates that this cmdlet overwrites snippet files with the same name in the same location.</span></span> <span data-ttu-id="9b090-145">Par défaut, `New-ISESnippet` ne remplace pas les fichiers.</span><span class="sxs-lookup"><span data-stu-id="9b090-145">By default, `New-ISESnippet` does not overwrite files.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b090-146">-Texte</span><span class="sxs-lookup"><span data-stu-id="9b090-146">-Text</span></span>

<span data-ttu-id="9b090-147">Spécifie la valeur de texte qui est ajoutée quand vous sélectionnez l'extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-147">Specifies the text value that is added when you select the snippet.</span></span> <span data-ttu-id="9b090-148">Le texte de l'extrait apparaît quand vous cliquez sur le nom de l'extrait de code dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-148">The snippet text appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="9b090-149">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9b090-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b090-150">-Title</span><span class="sxs-lookup"><span data-stu-id="9b090-150">-Title</span></span>

<span data-ttu-id="9b090-151">Spécifie un titre ou un nom pour l'extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-151">Specifies a title or name for the snippet.</span></span> <span data-ttu-id="9b090-152">Le titre nomme également le fichier d'extraits de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-152">The title also names the snippet file.</span></span> <span data-ttu-id="9b090-153">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9b090-153">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b090-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b090-154">CommonParameters</span></span>

<span data-ttu-id="9b090-155">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b090-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b090-156">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b090-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b090-157">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9b090-157">INPUTS</span></span>

### <span data-ttu-id="9b090-158">Aucun</span><span class="sxs-lookup"><span data-stu-id="9b090-158">None</span></span>

<span data-ttu-id="9b090-159">Cette applet de commande n'accepte pas d'entrée provenant du pipeline.</span><span class="sxs-lookup"><span data-stu-id="9b090-159">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="9b090-160">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9b090-160">OUTPUTS</span></span>

### <span data-ttu-id="9b090-161">Aucun</span><span class="sxs-lookup"><span data-stu-id="9b090-161">None</span></span>

<span data-ttu-id="9b090-162">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="9b090-162">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9b090-163">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9b090-163">NOTES</span></span>

<span data-ttu-id="9b090-164">`New-IseSnippet` stocke les nouveaux extraits de code créés par l’utilisateur dans les fichiers. ps1xml non signés.</span><span class="sxs-lookup"><span data-stu-id="9b090-164">`New-IseSnippet` stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="9b090-165">En conséquence, Windows PowerShell ne peut pas les ajouter à une session dans laquelle la stratégie d'exécution est **AllSigned** ou **Restricted** .</span><span class="sxs-lookup"><span data-stu-id="9b090-165">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="9b090-166">Dans une session **Restricted** ou **AllSigned** , vous pouvez créer, obtenir et importer des extraits de code créés par l'utilisateur non signés, mais vous ne pouvez pas les utiliser dans la session.</span><span class="sxs-lookup"><span data-stu-id="9b090-166">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

<span data-ttu-id="9b090-167">Si vous utilisez l' `New-IseSnippet` applet de commande dans une session **Restricted** ou **AllSigned** , l’extrait de code est créé, mais un message d’erreur s’affiche lorsque Windows PowerShell tente d’ajouter l’extrait de code nouvellement créé à la session.</span><span class="sxs-lookup"><span data-stu-id="9b090-167">If you use the `New-IseSnippet` cmdlet in a **Restricted** or **AllSigned** session, the snippet is created, but an error message appears when Windows PowerShell tries to add the newly created snippet to the session.</span></span> <span data-ttu-id="9b090-168">Pour utiliser le nouvel extrait de code (et d'autres extraits créés par l'utilisateur non signés), modifiez la stratégie d'exécution, puis redémarrez Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-168">To use the new snippet (and other unsigned user-created snippets), change the execution policy, and then restart Windows PowerShell ISE.</span></span>

<span data-ttu-id="9b090-169">Pour plus d'informations sur les stratégies d'exécution Windows PowerShell, consultez about_Execution_Policies.</span><span class="sxs-lookup"><span data-stu-id="9b090-169">For more information about Windows PowerShell execution policies, see about_Execution_Policies.</span></span>

- <span data-ttu-id="9b090-170">Pour modifier un extrait de code, modifiez le fichier d’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-170">To change a snippet, edit the snippet file.</span></span> <span data-ttu-id="9b090-171">Vous pouvez modifier les fichiers d’extrait de code dans le volet script de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-171">You can edit snippet files in the Script pane of Windows PowerShell ISE.</span></span>
- <span data-ttu-id="9b090-172">Pour supprimer un extrait de code que vous avez ajouté, supprimez le fichier d’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="9b090-172">To delete a snippet that you added, delete the snippet file.</span></span>
- <span data-ttu-id="9b090-173">Vous ne pouvez pas supprimer un extrait de code intégré, mais vous pouvez masquer tous les extraits de code intégrés à l’aide de l' $psise. Commande Options. ShowDefaultSnippets = $false».</span><span class="sxs-lookup"><span data-stu-id="9b090-173">You cannot delete a built-in snippet, but you can hide all built-in snippets by using the "$psise.Options.ShowDefaultSnippets=$false" command.</span></span>
- <span data-ttu-id="9b090-174">Vous pouvez créer un extrait de code qui porte le même nom qu’un extrait de code intégré.</span><span class="sxs-lookup"><span data-stu-id="9b090-174">You can create a snippet that has the same name as a built-in snippet.</span></span> <span data-ttu-id="9b090-175">Les deux extraits de code apparaissent dans le menu des extraits de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b090-175">Both snippets appear in the snippet menu in Windows PowerShell ISE.</span></span>

## <span data-ttu-id="9b090-176">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9b090-176">RELATED LINKS</span></span>

[<span data-ttu-id="9b090-177">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="9b090-177">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="9b090-178">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="9b090-178">Import-IseSnippet</span></span>](Import-IseSnippet.md)
