---
ms.date: 09/13/2016
ms.topic: reference
title: Vue de liste (De base)
description: Vue de liste (De base)
ms.openlocfilehash: d80ac9c6143b976d8bc13e2b184e4f5a2f8a37ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666635"
---
# <a name="list-view-basic"></a>Vue de liste (De base)

Cet exemple montre comment implémenter un affichage de liste de base qui affiche [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects retournés par l’applet [de commande obtient-service](/powershell/module/microsoft.powershell.management/get-service) . Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Pour charger ce fichier de mise en forme

1. Copiez le code XML de la section exemple de cette rubrique dans un fichier texte.

2. Enregistrez le fichier texte. Veillez à ajouter l' `format.ps1xml` extension au fichier pour l’identifier sous forme de fichier de mise en forme.

3. Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile` .

   > [!WARNING]
   > Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme Windows PowerShell. Vous devez utiliser le `prependPath` paramètre lorsque vous exécutez l’applet de commande, et vous ne pouvez pas charger ce fichier de mise en forme en tant que module.

## <a name="demonstrates"></a>Illustre le

Ce fichier de mise en forme montre les éléments XML suivants :

- Élément [Name](./name-element-for-view-format.md) pour la vue.

- Élément [ViewSelectedBy](./viewselectedby-element-format.md) qui définit les objets affichés par la vue.

- Élément [ListControl](./listcontrol-element-format.md) qui définit la propriété qui est affichée par la vue.

- Élément [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) qui définit ce qui est affiché dans une ligne de la vue liste.

- Élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) qui définit la propriété qui s’affiche.

## <a name="example"></a>Exemple

Le code XML suivant définit un affichage de liste qui affiche quatre propriétés de [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) , objet. Dans chaque ligne, le nom de la propriété est affiché, suivi de la valeur de la propriété.

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

L’exemple suivant montre comment Windows PowerShell affiche [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects après le chargement du fichier de format.

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

## <a name="see-also"></a>Voir aussi

[Exemples de fichiers de mise en forme](./examples-of-formatting-files.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
