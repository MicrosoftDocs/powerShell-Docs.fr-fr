---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISESnippetCollection
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030498"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="3dc03-103">Objet ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="3dc03-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="3dc03-104">L’objet **ISESnippetCollection** est une collection d’objets **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="3dc03-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="3dc03-105">La collection de fichiers qui est associée à un objet **PowerShellTab** est un membre de cette classe.</span><span class="sxs-lookup"><span data-stu-id="3dc03-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="3dc03-106">La collection **$psISE.CurrentPowerShellTab.Files** en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="3dc03-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="3dc03-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3dc03-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="3dc03-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="3dc03-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="3dc03-109">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="3dc03-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="3dc03-110">Charge un fichier .snippets.ps1xml qui contient des extraits de code défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3dc03-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="3dc03-111">L’applet de commande New-IseSnippet est le moyen le plus simple de créer des extraits de code, car elle les stocke automatiquement dans votre dossier de profil pour qu’ils se chargent à chaque démarrage de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3dc03-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="3dc03-112">**FilePathName** : chaîne Chemin et nom d’un fichier .snippets.ps1xml qui contient les définitions des extraits de code.</span><span class="sxs-lookup"><span data-stu-id="3dc03-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="3dc03-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dc03-113">See Also</span></span>

- [<span data-ttu-id="3dc03-114">Objet ISESnippet</span><span class="sxs-lookup"><span data-stu-id="3dc03-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="3dc03-115">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3dc03-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="3dc03-116">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="3dc03-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
