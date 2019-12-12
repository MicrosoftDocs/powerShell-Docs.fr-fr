---
title: Mode liste (de base) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362808"
---
# <a name="list-view-basic"></a><span data-ttu-id="567c0-102">Vue de liste (De base)</span><span class="sxs-lookup"><span data-stu-id="567c0-102">List View (Basic)</span></span>

<span data-ttu-id="567c0-103">Cet exemple montre comment implémenter un affichage de liste de base qui affiche [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects retournés par l’applet [de commande obtient-service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="567c0-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="567c0-104">Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="567c0-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="567c0-105">Pour charger ce fichier de mise en forme</span><span class="sxs-lookup"><span data-stu-id="567c0-105">To load this formatting file</span></span>

1. <span data-ttu-id="567c0-106">Copiez le code XML de la section exemple de cette rubrique dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="567c0-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="567c0-107">Enregistrez le fichier texte.</span><span class="sxs-lookup"><span data-stu-id="567c0-107">Save the text file.</span></span> <span data-ttu-id="567c0-108">Veillez à ajouter l’extension de `format.ps1xml` au fichier pour l’identifier en tant que fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="567c0-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="567c0-109">Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="567c0-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="567c0-110">Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="567c0-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="567c0-111">Vous devez utiliser le paramètre `prependPath` lorsque vous exécutez l’applet de commande, et vous ne pouvez pas charger ce fichier de mise en forme en tant que module.</span><span class="sxs-lookup"><span data-stu-id="567c0-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="567c0-112">Démontre</span><span class="sxs-lookup"><span data-stu-id="567c0-112">Demonstrates</span></span>

<span data-ttu-id="567c0-113">Ce fichier de mise en forme montre les éléments XML suivants :</span><span class="sxs-lookup"><span data-stu-id="567c0-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="567c0-114">Élément [Name](./name-element-for-view-format.md) pour la vue.</span><span class="sxs-lookup"><span data-stu-id="567c0-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="567c0-115">Élément [ViewSelectedBy](./viewselectedby-element-format.md) qui définit les objets affichés par la vue.</span><span class="sxs-lookup"><span data-stu-id="567c0-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="567c0-116">Élément [ListControl](./listcontrol-element-format.md) qui définit la propriété qui est affichée par la vue.</span><span class="sxs-lookup"><span data-stu-id="567c0-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="567c0-117">Élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) qui définit ce qui est affiché dans une ligne de la vue liste.</span><span class="sxs-lookup"><span data-stu-id="567c0-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="567c0-118">Élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) qui définit la propriété qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="567c0-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="567c0-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="567c0-119">Example</span></span>

<span data-ttu-id="567c0-120">Le code XML suivant définit un affichage de liste qui affiche quatre propriétés de [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) , objet.</span><span class="sxs-lookup"><span data-stu-id="567c0-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="567c0-121">Dans chaque ligne, le nom de la propriété est affiché, suivi de la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="567c0-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <View>
    <Name>System.ServiceProcess.ServiceController</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <ListControl>
      <ListEntries>
        <ListEntry>
          <ListItems>
            <ListItem>
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="567c0-122">L’exemple suivant montre comment Windows PowerShell affiche [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects après le chargement du fichier de format.</span><span class="sxs-lookup"><span data-stu-id="567c0-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="567c0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="567c0-123">See Also</span></span>

[<span data-ttu-id="567c0-124">Exemples de mise en forme de fichiers</span><span class="sxs-lookup"><span data-stu-id="567c0-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="567c0-125">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="567c0-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
