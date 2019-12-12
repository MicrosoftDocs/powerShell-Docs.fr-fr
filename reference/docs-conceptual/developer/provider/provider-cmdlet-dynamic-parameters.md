---
title: Paramètres dynamiques des applets de commande du fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359948"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Paramètres dynamiques des applets de commande de fournisseur

Les fournisseurs peuvent définir des paramètres dynamiques qui sont ajoutés à une applet de commande de fournisseur lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres statiques de l’applet de commande. Par exemple, un fournisseur peut ajouter des paramètres dynamiques différents en fonction du chemin d’accès que l’utilisateur spécifie lorsqu’il appelle les applets de commande du fournisseur `Get-Item` ou `Set-Item`.

## <a name="dynamic-parameter-methods"></a>Méthodes de paramètres dynamiques

Les paramètres dynamiques sont définis en implémentant l’une des méthodes de paramètre dynamique, telles que les méthodes [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) et [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s. Ces méthodes retournent un objet dont les propriétés publiques sont décorées avec des attributs similaires à ceux des applets de commande autonomes. Voici un exemple d’implémentation de la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) extraite du fournisseur de certificats :

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Contrairement aux paramètres statiques des applets de commande du fournisseur, vous pouvez spécifier les caractéristiques de ces paramètres de la même façon que les paramètres sont définis dans des applets de commande autonomes. Voici un exemple de classe de paramètres dynamiques tirée du fournisseur de certificats :

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Voici une liste des paramètres statiques qui peuvent être utilisés pour ajouter des paramètres dynamiques.

`Clear-Content` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande Clear-Clear en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

`Clear-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande `Clear-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

`Clear-ItemProperty` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande `Clear-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

`Copy-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path`, `Destination`et `Recurse` de l’applet de commande `Copy-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

Applet de commande ChildItems : vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `Recurse` de l’applet de commande `Get-ChildItem` en implémentant les méthodes [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) et [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .

`Get-Content` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande `Get-Content` en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) .

`Get-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande `Get-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

`Get-ItemProperty` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `Name` de l’applet de commande `Get-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

`Invoke-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande `Invoke-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

`Move-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `Destination` de l’applet de commande `Move-Item` en implémentant la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .

`New-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path`, `ItemType`et `Value` de l’applet de commande `New-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

`New-ItemProperty` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path`, `Name`, `PropertyType`et `Value` de l’applet de commande `New-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

`New-PSDrive` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par l’objet [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) renvoyé par l’applet de commande `New-PSDrive` en implémentant la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item` vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `Recurse` de l’applet de commande `Remove-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

`Remove-ItemProperty` vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `Name` de l’applet de commande `Remove-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

`Rename-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `NewName` de l’applet de commande `Rename-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

`Rename-ItemProperty` vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path`, `Name`et `NewName` de l’applet de commande `Rename-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

`Set-Content` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande `Set-Content` en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) .

`Set-Item` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `Value` de l’applet de commande `Set-Item` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

`Set-ItemProperty` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par les paramètres `Path` et `Value` de l’applet de commande `Set-Item` en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

`Test-Path` applet de commande vous pouvez définir des paramètres dynamiques qui sont déclenchés par le paramètre `Path` de l’applet de commande `Test-Path` en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur Windows PowerShell](./writing-a-windows-powershell-provider.md)