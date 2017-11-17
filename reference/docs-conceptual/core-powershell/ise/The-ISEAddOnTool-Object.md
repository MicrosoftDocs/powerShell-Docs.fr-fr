---
ms.date: 2017-06-05
keywords: powershell,applet de commande
title: Objet ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: b813fcac547c8069e84741081a3ceb00044bab87
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="87af3-103">Objet ISEAddOnTool</span><span class="sxs-lookup"><span data-stu-id="87af3-103">The ISEAddOnTool Object</span></span>
  <span data-ttu-id="87af3-104">Un objet **ISEAddonTool** représente un outil complémentaire installé qui apporte des fonctionnalités supplémentaires à Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="87af3-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="87af3-105">L’outil **Commandes** en est un exemple. Vous pouvez l’afficher en cliquant sur **Affichage**, puis sur **Afficher le composant additionnel de commande**.</span><span class="sxs-lookup"><span data-stu-id="87af3-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="87af3-106">Vous pouvez ensuite utiliser cet outil par le biais des différents objets **ISEAddOnTool** disponibles.</span><span class="sxs-lookup"><span data-stu-id="87af3-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

 <span data-ttu-id="87af3-107">Chaque outil complémentaire peut être associé au volet vertical ou horizontal.</span><span class="sxs-lookup"><span data-stu-id="87af3-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="87af3-108">Le volet vertical est ancré sur le bord droit de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="87af3-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="87af3-109">Le volet horizontal est ancré sur le bord inférieur.</span><span class="sxs-lookup"><span data-stu-id="87af3-109">The horizontal pane is docked to the bottom edge.</span></span>

 <span data-ttu-id="87af3-110">Chaque onglet PowerShell dans Windows PowerShell ISE peut avoir son propre ensemble d’outils complémentaires installés.</span><span class="sxs-lookup"><span data-stu-id="87af3-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="87af3-111">Consultez [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) et [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) pour accéder à la collection d’outils disponibles pour l’onglet actuellement sélectionné ou les propriétés communes à tous les objets **PowerShellTab** fournis dans l’objet collection [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="87af3-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="87af3-112">Méthodes</span><span class="sxs-lookup"><span data-stu-id="87af3-112">Methods</span></span>
 <span data-ttu-id="87af3-113">Il n’existe pas de méthode Windows PowerShell ISE spécifique pour les objets de cette classe.</span><span class="sxs-lookup"><span data-stu-id="87af3-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="87af3-114">Propriétés</span><span class="sxs-lookup"><span data-stu-id="87af3-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="87af3-115">Control</span><span class="sxs-lookup"><span data-stu-id="87af3-115">Control</span></span>
  <span data-ttu-id="87af3-116">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="87af3-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="87af3-117">La propriété **Control** fournit un accès en lecture à de nombreux détails de l’outil complémentaire Commandes.</span><span class="sxs-lookup"><span data-stu-id="87af3-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher

```

### <a name="isvisible"></a><span data-ttu-id="87af3-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="87af3-118">IsVisible</span></span>
  <span data-ttu-id="87af3-119">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="87af3-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="87af3-120">Propriété booléenne qui indique si l’outil complémentaire est actuellement visible dans le volet associé.</span><span class="sxs-lookup"><span data-stu-id="87af3-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="87af3-121">S’il est visible, vous pouvez définir la propriété **IsVisible** à la valeur **$false** pour masquer l’outil, ou définir la propriété **IsVisible** à la valeur **$true** pour afficher un outil complémentaire dans l’onglet PowerShell correspondant. Notez qu’un outil complémentaire masqué n’est plus accessible via l’objet **CurrentVisibleHorizontalTool** ou **CurrentVisibleVerticalTool**, et qu’il ne peut donc pas être affiché en définissant cette propriété sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="87af3-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

### <a name="name"></a><span data-ttu-id="87af3-122">Nom</span><span class="sxs-lookup"><span data-stu-id="87af3-122">Name</span></span>
  <span data-ttu-id="87af3-123">Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="87af3-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="87af3-124">Propriété en lecture seule qui obtient le nom de l’outil complémentaire.</span><span class="sxs-lookup"><span data-stu-id="87af3-124">The read-only property that gets the name of the add-on tool.</span></span>

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a><span data-ttu-id="87af3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87af3-125">See Also</span></span>
- [<span data-ttu-id="87af3-126">Objet ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="87af3-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="87af3-127">Modèle objet de script Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="87af3-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="87af3-128">Informations de référence sur le modèle objet Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="87af3-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="87af3-129">Hiérarchie du modèle objet ISE</span><span class="sxs-lookup"><span data-stu-id="87af3-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

