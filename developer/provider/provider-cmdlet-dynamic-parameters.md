---
title: Paramètres dynamiques du fournisseur d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080966"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Paramètres dynamiques des applets de commande de fournisseur

Fournisseurs peuvent définir des paramètres dynamiques qui sont ajoutés à une applet de commande fournisseur lorsque l’utilisateur spécifie une certaine valeur pour l’un des paramètres statiques de l’applet de commande. Par exemple, un fournisseur peut ajouter des différents paramètres dynamiques en fonction sur le chemin d’accès de l’utilisateur spécifie lorsqu’ils appellent le `Get-Item` ou `Set-Item` applets de commande fournisseur.

## <a name="dynamic-parameter-methods"></a>Méthodes de paramètre dynamique

Les paramètres dynamiques sont définis en implémentant une des méthodes de paramètre dynamique, tel que le [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) et [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)méthodes de s. Ces méthodes retournent un objet qui a des propriétés publiques qui sont décorées avec des attributs similaires à celles des applets de commande autonome. Voici un exemple d’implémentation de la [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) méthode prise à partir du fournisseur de certificat :

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Contrairement aux paramètres statiques des applets de commande de fournisseur, vous pouvez spécifier les caractéristiques de ces paramètres de la même façon que les paramètres sont définis dans les applets de commande autonomes. Voici un exemple d’une classe de paramètre dynamique prise à partir du fournisseur de certificat :

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

Voici une liste des paramètres statiques qui peut être utilisé pour ajouter des paramètres dynamiques.

`Clear-Content` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de l’applet de commande Clear-Clear en implémentant la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) (méthode).

`Clear-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de la `Clear-Item` applet de commande en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) (méthode).

`Clear-ItemProperty` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de la `Clear-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) (méthode).

`Copy-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path`, `Destination`, et `Recurse` paramètres de le `Copy-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) (méthode).

Applet de commande Get-ChildItems, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `Recurse` paramètres de le `Get-ChildItem` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) et [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) méthodes.

`Get-Content` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de la `Get-Content` applet de commande en implémentant le [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) (méthode).

`Get-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de la `Get-Item` applet de commande en implémentant la [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) (méthode).

`Get-ItemProperty` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `Name` paramètres de le `Get-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) (méthode).

`Invoke-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de la `Invoke-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) (méthode).

`Move-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `Destination` paramètres de le `Move-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) (méthode).

`New-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path`, `ItemType`, et `Value` paramètres de le `New-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) (méthode).

`New-ItemProperty` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path`, `Name`, `PropertyType`, et `Value` paramètres de le `New-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) (méthode).

`New-PSDrive` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le [à savoir System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objet retourné par la `New-PSDrive` applet de commande en implémentant le [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) (méthode).

`Remove-Item` Vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `Recurse` paramètres de le `Remove-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) (méthode).

`Remove-ItemProperty` Vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `Name` paramètres de le `Remove-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) (méthode).

`Rename-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `NewName` paramètres de le `Rename-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) (méthode).

`Rename-ItemProperty` Vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path`, `Name`, et `NewName` paramètres de le `Rename-ItemProperty` applet de commande en implémentant le [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) (méthode).

`Set-Content` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de la `Set-Content` applet de commande en implémentant le [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) (méthode).

`Set-Item` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `Value` paramètres de le `Set-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) (méthode).

`Set-ItemProperty` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` et `Value` paramètres de le `Set-Item` applet de commande en implémentant le [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) (méthode).

`Test-Path` applet de commande, vous pouvez définir des paramètres dynamiques qui sont déclenchées par le `Path` paramètre de la `Test-Path` applet de commande en implémentant le [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) (méthode).

## <a name="see-also"></a>Voir aussi

[Écriture d’un fournisseur PowerShell de Windows](./writing-a-windows-powershell-provider.md)