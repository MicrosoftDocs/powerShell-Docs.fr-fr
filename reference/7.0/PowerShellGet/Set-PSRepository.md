---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 277bfc0ae4662e0c822ae7c227490eaf887c8ecb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201261"
---
# Set-PSRepository

## SYNOPSIS
Définit des valeurs pour un dépôt inscrit.

## SYNTAX

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## Description

L' `Set-PSRepository` applet de commande définit des valeurs pour un référentiel de module inscrit. Les paramètres sont persistants pour l’utilisateur actuel et s’appliquent à toutes les versions de PowerShell installées pour cet utilisateur.

## EXEMPLES

### Exemple 1 : définir la stratégie d’installation d’un référentiel

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

Cette commande définit la stratégie d’installation pour le référentiel **myInternalSource** sur **approuvé** , de sorte que vous n’êtes pas invité à installer les modules à partir de cette source.

### Exemple 2 : définir les emplacements source et de publication d’un référentiel

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

Cette commande définit l’emplacement source et l’emplacement de publication de **myInternalSource** sur les URI spécifiés.

## PARAMETERS

### -Credential

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstallationPolicy

Spécifie la stratégie d’installation. Les valeurs valides sont : **approuvé** , **non** approuvé.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom du dépôt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PackageManagementProvider

Spécifie le fournisseur de gestion des packages.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation

Spécifie l’URI de l’emplacement de publication. Par exemple, pour les référentiels NuGet, l’emplacement de publication est semblable à `https://someNuGetUrl.com/api/v2/Packages` .

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptPublishLocation

Spécifie l’emplacement de publication du script.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

Spécifie l’emplacement source du script.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceLocation

Spécifie l’URI pour la découverte et l’installation de modules à partir de ce référentiel. Par exemple, pour les référentiels NuGet, l’emplacement source est semblable à `https://someNuGetUrl.com/api/v2` .

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

### System. Management. Automation. PSCredential

### System.Uri

## SORTIES

### System.Object

## REMARQUES

## LIENS CONNEXES

[Get-PSRepository](Get-PSRepository.md)

[Register-PSRepository](Register-PSRepository.md)

[Unregister-PSRepository](Unregister-PSRepository.md)
