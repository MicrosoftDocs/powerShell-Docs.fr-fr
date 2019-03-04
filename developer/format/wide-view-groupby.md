---
title: Affichage plus large (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861625"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="f0030-102">Vue large (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="f0030-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="f0030-103">Cet exemple montre comment implémenter un affichage plus large qui affiche les groupes de [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets retournés par la `Get-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f0030-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="f0030-104">Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f0030-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="f0030-105">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="f0030-105">To load this formatting file</span></span>

1. <span data-ttu-id="f0030-106">Copiez le code XML à partir de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="f0030-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="f0030-107">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="f0030-107">Save the text file.</span></span> <span data-ttu-id="f0030-108">Veillez à ajouter le `format.ps1xml` extension au fichier pour l’identifier comme un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="f0030-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="f0030-109">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="f0030-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="f0030-110">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un mise en forme de fichiers de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f0030-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="f0030-111">Vous devez utiliser le `prependPath` paramètre lorsque vous exécutez l’applet de commande, et vous ne peut pas charger cette mise en forme de fichiers en tant que module.</span><span class="sxs-lookup"><span data-stu-id="f0030-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f0030-112">Montre</span><span class="sxs-lookup"><span data-stu-id="f0030-112">Demonstrates</span></span>

<span data-ttu-id="f0030-113">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="f0030-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="f0030-114">Le [nom](./name-element-for-view-format.md) élément pour la vue.</span><span class="sxs-lookup"><span data-stu-id="f0030-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="f0030-115">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément qui définit quels objets sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="f0030-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="f0030-116">Le [GroupBy](./groupby-element-for-view-format.md) élément qui définit quand un nouveau groupe s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f0030-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="f0030-117">Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément qui définit la propriété est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="f0030-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="f0030-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="f0030-118">Example</span></span>

<span data-ttu-id="f0030-119">Le code XML suivant définit un affichage plus large qui affiche les groupes d’objets.</span><span class="sxs-lookup"><span data-stu-id="f0030-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="f0030-120">Chaque nouveau groupe est démarré lorsque la valeur de la [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) les modifications de propriété.</span><span class="sxs-lookup"><span data-stu-id="f0030-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="f0030-121">L’exemple suivant montre comment Windows PowerShell affiche le [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets une fois que ce fichier de format est chargé.</span><span class="sxs-lookup"><span data-stu-id="f0030-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f0030-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0030-122">See Also</span></span>

[<span data-ttu-id="f0030-123">Exemples de fichiers de mise en forme</span><span class="sxs-lookup"><span data-stu-id="f0030-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="f0030-124">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f0030-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
