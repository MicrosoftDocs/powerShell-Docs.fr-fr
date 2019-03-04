---
title: Affichage plus large (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860105"
---
# <a name="wide-view-basic"></a><span data-ttu-id="36381-102">Vue large (De base)</span><span class="sxs-lookup"><span data-stu-id="36381-102">Wide View (Basic)</span></span>

<span data-ttu-id="36381-103">Cet exemple montre comment implémenter un affichage plus large base qui affiche le [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets retournés par la `Get-Service` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="36381-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="36381-104">Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="36381-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="36381-105">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="36381-105">To load this formatting file</span></span>

1. <span data-ttu-id="36381-106">Copiez le code XML à partir de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="36381-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="36381-107">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="36381-107">Save the text file.</span></span> <span data-ttu-id="36381-108">Veillez à ajouter le `format.ps1xml` extension au fichier pour l’identifier comme un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="36381-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="36381-109">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="36381-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="36381-110">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36381-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="36381-111">Vous devez utiliser le `prependPath` paramètre lorsque vous exécutez l’applet de commande, et vous ne peut pas charger cette mise en forme de fichiers en tant que module.</span><span class="sxs-lookup"><span data-stu-id="36381-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="36381-112">Montre</span><span class="sxs-lookup"><span data-stu-id="36381-112">Demonstrates</span></span>

<span data-ttu-id="36381-113">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="36381-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="36381-114">Le [nom](./name-element-for-view-format.md) élément pour la vue.</span><span class="sxs-lookup"><span data-stu-id="36381-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="36381-115">Le [ViewSelectedBy](./viewselectedby-element-format.md) élément qui définit quels objets sont affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="36381-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="36381-116">Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément qui définit la propriété est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="36381-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="36381-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="36381-117">Example</span></span>

<span data-ttu-id="36381-118">Le code XML suivant définit un affichage plus large qui affiche la valeur de la [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) propriété.</span><span class="sxs-lookup"><span data-stu-id="36381-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="36381-119">L’exemple suivant montre comment Windows PowerShell affiche le [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets une fois que ce fichier de format est chargé.</span><span class="sxs-lookup"><span data-stu-id="36381-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="36381-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36381-120">See Also</span></span>

[<span data-ttu-id="36381-121">Exemples de fichiers de mise en forme</span><span class="sxs-lookup"><span data-stu-id="36381-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="36381-122">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="36381-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
