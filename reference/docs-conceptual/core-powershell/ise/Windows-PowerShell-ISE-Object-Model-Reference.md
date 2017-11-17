---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: "Informations de référence sur le modèle objet Windows PowerShell ISE"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="5e8f1-103">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="5e8f1-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="5e8f1-104">Informations de référence sur le modèle objet</span><span class="sxs-lookup"><span data-stu-id="5e8f1-104">Object Model Reference</span></span>
 <span data-ttu-id="5e8f1-105">Cette section fournit des informations de référence sur les classes sous-jacentes qui définissent les différents objets de l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="5e8f1-106">Pour afficher les objets organisés dans leur hiérarchie, consultez [Hiérarchie des modèles objet ISE](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="5e8f1-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="5e8f1-107">[Objet ISEAddOnTool](The-ISEAddOnTool-Object.md) Exemples : $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="5e8f1-108">[Objet ISEAddOnTool](The-ISEAddOnTool-Object.md) [Objet ISEEditor](The-ISEEditor-Object.md) Exemples : $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) [The ISEEditor Object](The-ISEEditor-Object.md) Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="5e8f1-109">[Objet ISEFile](The-ISEFile-Object.md) Exemples : $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span><span class="sxs-lookup"><span data-stu-id="5e8f1-109">[The ISEFile Object](The-ISEFile-Object.md) Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="5e8f1-110">[Objet ISEFileCollection](The-ISEFileCollection-Object.md) Exemples : $psISE.PowerShellTabs.Files.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md) Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="5e8f1-111">[Objet ISEMenuItem](The-ISEMenuItem-Object.md) Exemples : $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span><span class="sxs-lookup"><span data-stu-id="5e8f1-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md) Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="5e8f1-112">[Objet ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) Exemple : $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md) Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="5e8f1-113">[Objet ISEOptions](The-ISEOptions-Object.md) Exemples : $psISE.Options, $psISE.Options.DefaultOptions.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-113">[The ISEOptions Object](The-ISEOptions-Object.md) Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="5e8f1-114">[Objet ObjectModelRoot](The-ObjectModelRoot-Object.md) Exemple : L’objet $psISE racine.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md) Example: The root $psISE object.</span></span>

 <span data-ttu-id="5e8f1-115">[Objet PowerShellTab](The-PowerShellTab-Object.md) Exemples : $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span><span class="sxs-lookup"><span data-stu-id="5e8f1-115">[The PowerShellTab Object](The-PowerShellTab-Object.md) Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="5e8f1-116">[Objet PowerShellTabCollection](The-PowerShellTabCollection-Object.md) Exemple : $psISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="5e8f1-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md) Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e8f1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e8f1-117">See Also</span></span>
- [<span data-ttu-id="5e8f1-118">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="5e8f1-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
