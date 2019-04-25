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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083737"
---
# <a name="wide-view-basic"></a>Vue large (De base)

Cet exemple montre comment implémenter un affichage plus large base qui affiche le [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets retournés par la `Get-Service` applet de commande. Pour plus d’informations sur les composants d’un affichage plus large, consultez [création d’un affichage plus large](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Pour charger ce fichier de mise en forme

1. Copiez le code XML à partir de la section exemple de cette rubrique dans un fichier texte.

2. Enregistrez le fichier texte. Veillez à ajouter le `format.ps1xml` extension au fichier pour l’identifier comme un fichier de mise en forme.

3. Ouvrez Windows PowerShell et exécutez la commande suivante pour charger le fichier de mise en forme dans la session active : `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Ce fichier de mise en forme définit l’affichage d’un objet qui est déjà défini par un fichier de mise en forme de Windows PowerShell. Vous devez utiliser le `prependPath` paramètre lorsque vous exécutez l’applet de commande, et vous ne peut pas charger cette mise en forme de fichiers en tant que module.

## <a name="demonstrates"></a>Montre

Ce fichier de mise en forme montre les éléments XML suivants :

- Le [nom](./name-element-for-view-format.md) élément pour la vue.

- Le [ViewSelectedBy](./viewselectedby-element-format.md) élément qui définit quels objets sont affichés par la vue.

- Le [WideItem](./wideitem-element-for-widecontrol-format.md) élément qui définit la propriété est affichée par la vue.

## <a name="example"></a>Exemple

Le code XML suivant définit un affichage plus large qui affiche la valeur de la [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) propriété.

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

L’exemple suivant montre comment Windows PowerShell affiche le [System.Serviceprocess.Servicecontroller ? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objets une fois que ce fichier de format est chargé.

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>Voir aussi

[Exemples de fichiers de mise en forme](./examples-of-formatting-files.md)

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
