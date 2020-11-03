---
external help file: ISE-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205338"
---
# <span data-ttu-id="b78b6-103">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="b78b6-103">Get-IseSnippet</span></span>

## <span data-ttu-id="b78b6-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b78b6-104">SYNOPSIS</span></span>
<span data-ttu-id="b78b6-105">Obtient les extraits de code créés par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b78b6-105">Gets snippets that the user created.</span></span>

## <span data-ttu-id="b78b6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b78b6-106">SYNTAX</span></span>

```
Get-IseSnippet [<CommonParameters>]
```

## <span data-ttu-id="b78b6-107">Description</span><span class="sxs-lookup"><span data-stu-id="b78b6-107">DESCRIPTION</span></span>

<span data-ttu-id="b78b6-108">L' `Get-IseSnippet` applet de commande obtient les fichiers ps1xml qui contiennent des extraits de texte réutilisables que l’utilisateur a créés.</span><span class="sxs-lookup"><span data-stu-id="b78b6-108">The `Get-IseSnippet` cmdlet gets the PS1XML files that contain reusable text snippets that the user created.</span></span> <span data-ttu-id="b78b6-109">Elle fonctionne uniquement dans Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="b78b6-109">It works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="b78b6-110">Lorsque vous utilisez l' `New-IseSnippet` applet de commande pour créer un extrait de code, `New-IseSnippet` crée un `<SnippetTitle>.Snippets.ps1xml` fichier dans le `$home\Documents\WindowsPowerShell\Snippets` répertoire.</span><span class="sxs-lookup"><span data-stu-id="b78b6-110">When you use the `New-IseSnippet` cmdlet to create a snippet, `New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
<span data-ttu-id="b78b6-111">`Get-IseSnippet` Obtient les fichiers d’extraits de code dans le répertoire des extraits de code.</span><span class="sxs-lookup"><span data-stu-id="b78b6-111">`Get-IseSnippet` gets the snippet files in the Snippets directory.</span></span>

<span data-ttu-id="b78b6-112">Cette applet de commande n’obtient pas les extraits de code intégrés ni les extraits de code importés à partir des modules via l’applet de commande `Import-IseSnippet` .</span><span class="sxs-lookup"><span data-stu-id="b78b6-112">This cmdlet does not get built-in snippets or snippets that are imported from modules through the `Import-IseSnippet` cmdlet.</span></span>

<span data-ttu-id="b78b6-113">Cette applet de commande a été introduite dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b78b6-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b78b6-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b78b6-114">EXAMPLES</span></span>

### <span data-ttu-id="b78b6-115">Exemple 1 : récupération de tous les extraits de code définis par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="b78b6-115">Example 1: Get all user-defined snippets</span></span>

<span data-ttu-id="b78b6-116">Cet exemple obtient tous les extraits de code définis par l’utilisateur dans le répertoire snippets.</span><span class="sxs-lookup"><span data-stu-id="b78b6-116">This example gets all user-define snippets in the Snippets directory.</span></span>

```powershell
Get-IseSnippet
```

### <span data-ttu-id="b78b6-117">Exemple 2 : copier tous les extraits de code définis par l’utilisateur à partir d’ordinateurs distants dans un répertoire partagé</span><span class="sxs-lookup"><span data-stu-id="b78b6-117">Example 2: Copy all user-defined snippets from remote computers to a shared directory</span></span>

<span data-ttu-id="b78b6-118">Cet exemple copie tous les extraits de code créés par l’utilisateur à partir d’un groupe d’ordinateurs distants dans un répertoire d’extraits de code partagé.</span><span class="sxs-lookup"><span data-stu-id="b78b6-118">This example copies all of the user-created snippets from a group of remote computers to a shared Snippets directory.</span></span>

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

<span data-ttu-id="b78b6-119">`Invoke-Command` s’exécute `Get-IseSnippet` sur les ordinateurs du `Servers.txt` fichier.</span><span class="sxs-lookup"><span data-stu-id="b78b6-119">`Invoke-Command` runs `Get-IseSnippet` on the computers in the `Servers.txt` file.</span></span> <span data-ttu-id="b78b6-120">Un opérateur de pipeline ( `|` ) envoie les fichiers d’extraits de code à l’applet de commande `Copy-Item` , qui les copie dans le répertoire spécifié par le paramètre de **destination** .</span><span class="sxs-lookup"><span data-stu-id="b78b6-120">A pipeline operator (`|`) sends the snippet files to the `Copy-Item` cmdlet, which copies them to the directory that is specified by the **Destination** parameter.</span></span>

### <span data-ttu-id="b78b6-121">Exemple 3 : afficher le titre et le texte de chaque extrait de code sur un ordinateur local</span><span class="sxs-lookup"><span data-stu-id="b78b6-121">Example 3: Display the title and text of each snippet on a local computer</span></span>

<span data-ttu-id="b78b6-122">Cet exemple utilise les `Get-IseSnippet` applets de commande et `Select-Xml` pour afficher le titre et le texte de chaque extrait de code sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b78b6-122">This example uses the `Get-IseSnippet` and `Select-Xml` cmdlets to display the title and text of each snippet on the local computer.</span></span>

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### <span data-ttu-id="b78b6-123">Exemple 4 : afficher le titre et la description de tous les extraits de code dans la session</span><span class="sxs-lookup"><span data-stu-id="b78b6-123">Example 4: Display the title and description of all snippets in the session</span></span>

<span data-ttu-id="b78b6-124">Cet exemple affiche le titre et la description de tous les extraits de code dans la session, y compris les extraits de code intégrés, les extraits de code définis par l’utilisateur et les extraits importés.</span><span class="sxs-lookup"><span data-stu-id="b78b6-124">This example displays the title and description of all snippets in the session, including built-in snippets, user-defined snippets, and imported snippets.</span></span>

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

<span data-ttu-id="b78b6-125">La `$PSISE` variable représente le programme hôte Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b78b6-125">The `$PSISE` variable represents the Windows PowerShell ISE host program.</span></span> <span data-ttu-id="b78b6-126">La propriété **CurrentPowerShellTab** de la `$PSISE` variable représente la session active.</span><span class="sxs-lookup"><span data-stu-id="b78b6-126">The **CurrentPowerShellTab** property of the `$PSISE` variable represent the current session.</span></span> <span data-ttu-id="b78b6-127">La propriété **Snippets** représente les extraits de code dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b78b6-127">The **Snippets** property represents snippets in the current session.</span></span>

<span data-ttu-id="b78b6-128">La `$PSISE.CurrentPowerShellTab.Snippets` commande retourne un objet **Microsoft. PowerShell. Host. ISE. ISESnippet** qui représente un extrait de code, contrairement à l’applet de commande `Get-IseSnippet` .</span><span class="sxs-lookup"><span data-stu-id="b78b6-128">The `$PSISE.CurrentPowerShellTab.Snippets` command returns a **Microsoft.PowerShell.Host.ISE.ISESnippet** object that represents a snippet, unlike the `Get-IseSnippet` cmdlet.</span></span> <span data-ttu-id="b78b6-129">`Get-IseSnippet` retourne un objet de fichier (System. IO. FileInfo) qui représente un fichier d’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="b78b6-129">`Get-IseSnippet` returns a file object (System.Io.FileInfo) that represents a snippet file.</span></span>

<span data-ttu-id="b78b6-130">L' `Format-Table` applet de commande affiche les propriétés **DisplayTitle** et **Description** des extraits de code dans une table.</span><span class="sxs-lookup"><span data-stu-id="b78b6-130">The `Format-Table` cmdlet displays the **DisplayTitle** and **Description** properties of the snippets in a table.</span></span>

## <span data-ttu-id="b78b6-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b78b6-131">PARAMETERS</span></span>

### <span data-ttu-id="b78b6-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b78b6-132">CommonParameters</span></span>

<span data-ttu-id="b78b6-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b78b6-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b78b6-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b78b6-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b78b6-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b78b6-135">INPUTS</span></span>

## <span data-ttu-id="b78b6-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b78b6-136">OUTPUTS</span></span>

### <span data-ttu-id="b78b6-137">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="b78b6-137">System.IO.FileInfo</span></span>

<span data-ttu-id="b78b6-138">Cette applet de commande retourne un objet de fichier qui représente le fichier d’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="b78b6-138">This cmdlet returns a file object that represents the snippet file.</span></span>

## <span data-ttu-id="b78b6-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b78b6-139">NOTES</span></span>

* <span data-ttu-id="b78b6-140">L' `New-IseSnippet` applet de commande stocke les nouveaux extraits de code créés par l’utilisateur dans les fichiers. ps1xml non signés.</span><span class="sxs-lookup"><span data-stu-id="b78b6-140">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="b78b6-141">En conséquence, Windows PowerShell ne peut pas les ajouter à une session dans laquelle la stratégie d'exécution est **AllSigned** ou **Restricted** .</span><span class="sxs-lookup"><span data-stu-id="b78b6-141">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="b78b6-142">Dans une session **Restricted** ou **AllSigned** , vous pouvez créer, obtenir et importer des extraits de code créés par l'utilisateur non signés, mais vous ne pouvez pas les utiliser dans la session.</span><span class="sxs-lookup"><span data-stu-id="b78b6-142">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="b78b6-143">Pour utiliser des extraits de code créés par l’utilisateur non signés que l’applet de commande `Get-IseSnippet` retourne, modifiez la stratégie d’exécution, puis redémarrez Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b78b6-143">To use unsigned user-created snippets that the `Get-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="b78b6-144">Pour plus d'informations sur les stratégies d'exécution Windows PowerShell, consultez [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="b78b6-144">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="b78b6-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b78b6-145">RELATED LINKS</span></span>

[<span data-ttu-id="b78b6-146">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="b78b6-146">New-IseSnippet</span></span>](New-IseSnippet.md)

[<span data-ttu-id="b78b6-147">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="b78b6-147">Import-IseSnippet</span></span>](Import-IseSnippet.md)
