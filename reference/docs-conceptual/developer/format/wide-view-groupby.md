---
ms.date: 09/13/2016
ms.topic: reference
title: Vue large (GroupBy)
description: Vue large (GroupBy)
ms.openlocfilehash: 807bea2a5d44c38e2c9977f792bea2fb9bca0fc3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667672"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="98ba7-103">Vue large (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="98ba7-103">Wide View (GroupBy)</span></span>

<span data-ttu-id="98ba7-104">Cet exemple montre comment implémenter une vue étendue qui affiche des groupes de [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects retournés par l’applet de commande `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="98ba7-104">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="98ba7-105">Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="98ba7-105">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="98ba7-106">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="98ba7-106">To load this formatting file</span></span>

1. <span data-ttu-id="98ba7-107">Copiez le code XML de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="98ba7-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="98ba7-108">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="98ba7-108">Save the text file.</span></span> <span data-ttu-id="98ba7-109">Veillez à ajouter l' `format.ps1xml` extension au fichier pour l’identifier sous forme de fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="98ba7-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="98ba7-110">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="98ba7-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="98ba7-111">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par des fichiers de mise en forme Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98ba7-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="98ba7-112">Vous devez utiliser le `prependPath` paramètre lorsque vous exécutez l’applet de commande, et vous ne pouvez pas charger ce fichier de mise en forme en tant que module.</span><span class="sxs-lookup"><span data-stu-id="98ba7-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="98ba7-113">Illustre le</span><span class="sxs-lookup"><span data-stu-id="98ba7-113">Demonstrates</span></span>

<span data-ttu-id="98ba7-114">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="98ba7-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="98ba7-115">Élément [Name](./name-element-for-view-format.md) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="98ba7-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="98ba7-116">Élément [ViewSelectedBy](./viewselectedby-element-format.md) qui définit les objets affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="98ba7-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="98ba7-117">Élément [GroupBy](./groupby-element-for-view-format.md) qui définit le moment où un nouveau groupe est affiché.</span><span class="sxs-lookup"><span data-stu-id="98ba7-117">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="98ba7-118">Élément [WideItem](./wideitem-element-for-widecontrol-format.md) qui définit la propriété qui est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="98ba7-118">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="98ba7-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="98ba7-119">Example</span></span>

<span data-ttu-id="98ba7-120">Le code XML suivant définit une vue étendue qui affiche des groupes d’objets.</span><span class="sxs-lookup"><span data-stu-id="98ba7-120">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="98ba7-121">Chaque nouveau groupe est démarré lorsque la valeur de la propriété [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) change.</span><span class="sxs-lookup"><span data-stu-id="98ba7-121">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="98ba7-122">L’exemple suivant montre comment Windows PowerShell affiche [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects après le chargement du fichier de format.</span><span class="sxs-lookup"><span data-stu-id="98ba7-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="98ba7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98ba7-123">See Also</span></span>

[<span data-ttu-id="98ba7-124">Exemples de fichiers de mise en forme</span><span class="sxs-lookup"><span data-stu-id="98ba7-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="98ba7-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="98ba7-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
