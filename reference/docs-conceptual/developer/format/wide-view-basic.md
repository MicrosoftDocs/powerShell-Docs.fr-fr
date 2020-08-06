---
title: Vue étendue (de base) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d92c29c33c5104b6186ae53ccf544be197d657b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772397"
---
# <a name="wide-view-basic"></a>Vue large (De base)

Cet exemple montre comment implémenter un affichage étendu de base qui affiche [System. ServiceProcess. ServiceController ? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects retournés par l’applet de commande `Get-Service` . Pour plus d’informations sur les composants d’une vue étendue, consultez [création d’une vue étendue](./creating-a-wide-view.md).

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

- Élément [WideItem](./wideitem-element-for-widecontrol-format.md) qui définit la propriété qui est affichée par la vue.

## <a name="example"></a>Exemple

Le code XML suivant définit une vue étendue qui affiche la valeur de la propriété [System. ServiceProcess. ServiceController. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) .

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

L’exemple suivant montre comment Windows PowerShell affiche [System. ServiceProcess. ServiceController. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) Objects après le chargement du fichier de format.

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

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
