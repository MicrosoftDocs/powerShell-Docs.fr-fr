---
title: Paramètres dynamiques des applets de commande du fournisseur | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4aaa5ee39e98de9a9925fc65cac3cc6c32d9c2bc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786813"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Paramètres dynamiques des applets de commande de fournisseur

Les fournisseurs peuvent définir des paramètres dynamiques qui sont ajoutés à une applet de commande de fournisseur lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres statiques de l’applet de commande. Par exemple, un fournisseur peut ajouter des paramètres dynamiques différents en fonction du chemin d’accès que l’utilisateur spécifie lorsqu’il appelle les `Get-Item` applets de commande ou `Set-Item` .

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

`Clear-Content`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l’applet de commande Clear-Clear en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) .

`Clear-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l' `Clear-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

`Clear-ItemProperty`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l' `Clear-ItemProperty` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

`Copy-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `Destination` paramètres, et `Recurse` de l’applet de commande `Copy-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

Applet de commande ChildItems vous pouvez définir des paramètres dynamiques qui sont déclenchés par `Path` les `Recurse` paramètres et de l’applet de commande `Get-ChildItem` en implémentant les méthodes [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) et [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .

`Get-Content`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l' `Get-Content` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) .

`Get-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l' `Get-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

`Get-ItemProperty`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `Name` paramètres et de l' `Get-ItemProperty` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

`Invoke-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l' `Invoke-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

`Move-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `Destination` paramètres et de l' `Move-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .

`New-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `ItemType` paramètres, et `Value` de l’applet de commande `New-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

`New-ItemProperty`vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `Name` paramètres,, `PropertyType` et `Value` de l’applet de commande `New-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

`New-PSDrive`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par l’objet [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) renvoyé par l' `New-PSDrive` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par `Path` les `Recurse` paramètres et de l’applet de commande `Remove-Item` en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

`Remove-ItemProperty`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par `Path` les `Name` paramètres et de l’applet de commande `Remove-ItemProperty` en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

`Rename-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `NewName` paramètres et de l' `Rename-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

`Rename-ItemProperty`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par `Path` les `Name` paramètres, et `NewName` de l' `Rename-ItemProperty` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

`Set-Content`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l' `Set-Content` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) .

`Set-Item`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `Value` paramètres et de l' `Set-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

`Set-ItemProperty`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par les `Path` `Value` paramètres et de l' `Set-Item` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

`Test-Path`Vous pouvez définir des paramètres dynamiques qui sont déclenchés par le `Path` paramètre de l' `Test-Path` applet de commande en implémentant la méthode [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur Windows PowerShell](./writing-a-windows-powershell-provider.md)
