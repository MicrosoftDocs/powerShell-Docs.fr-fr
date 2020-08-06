---
title: Mode liste (étiquettes) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: da45bd8dce7ac2149de6a34c11d5419d6cb4ddb0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773383"
---
# <a name="list-view-labels"></a>Vue de liste (Étiquettes)

Cet exemple montre comment implémenter un affichage de liste qui affiche une étiquette personnalisée pour chaque ligne de la liste. Ce mode liste affiche les propriétés de [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objet qui est retourné par l’applet de commande de l’applet [de](/powershell/module/Microsoft.PowerShell.Management/Get-Service) commande. Pour plus d’informations sur les composants d’un affichage de liste, consultez [création d’un mode liste](./creating-a-list-view.md).

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

- Élément [label](./label-element-for-listitem-for-listcontrol-format.md) qui définit ce qui est affiché dans une ligne de la vue liste.

- Élément [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) qui définit la propriété qui s’affiche.

## <a name="example"></a>Exemple

Le code XML suivant définit un affichage de liste qui affiche une étiquette personnalisée dans chaque ligne. Dans ce cas, l’étiquette comprend le nom de la propriété avec les lettres majuscules et le mot « propriété ». Dans chaque ligne, le nom de la propriété est affiché, suivi de la valeur de la propriété.

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

L’exemple suivant montre comment Windows PowerShell affiche [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects après le chargement du fichier de format.

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>Voir aussi

[Exemples de fichiers de mise en forme](./examples-of-formatting-files.md)

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
