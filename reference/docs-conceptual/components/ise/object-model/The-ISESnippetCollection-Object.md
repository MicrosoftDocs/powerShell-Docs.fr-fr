---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086667"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="385a1-103">Objet ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="385a1-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="385a1-104">L’objet **ISESnippetCollection** est une collection d’objets **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="385a1-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="385a1-105">La collection de fichiers qui est associée à un objet **PowerShellTab** est un membre de cette classe.</span><span class="sxs-lookup"><span data-stu-id="385a1-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="385a1-106">La collection **$psISE.CurrentPowerShellTab.Files** en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="385a1-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="385a1-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="385a1-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="385a1-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="385a1-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="385a1-109">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="385a1-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="385a1-110">Charge un fichier .snippets.ps1xml qui contient des extraits de code défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="385a1-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="385a1-111">L’applet de commande New-IseSnippet est le moyen le plus simple de créer des extraits de code, car elle les stocke automatiquement dans votre dossier de profil pour qu’ils se chargent à chaque démarrage de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="385a1-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="385a1-112">**FilePathName** : chaîne Chemin et nom d’un fichier .snippets.ps1xml qui contient les définitions des extraits de code.</span><span class="sxs-lookup"><span data-stu-id="385a1-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="385a1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="385a1-113">See Also</span></span>

- [<span data-ttu-id="385a1-114">Objet ISESnippet</span><span class="sxs-lookup"><span data-stu-id="385a1-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="385a1-115">Objectif du modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="385a1-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="385a1-116">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="385a1-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)