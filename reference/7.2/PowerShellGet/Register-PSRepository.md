---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: 179e672a099cfb92275795a0dc6129581a0e0299
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603889"
---
# Register-PSRepository

## SYNOPSIS
Inscrit un référentiel PowerShell.

## SYNTAXE

### NameParameterSet (par défaut)

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### PSGalleryParameterSet

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## Description

L' `Register-PSRepository` applet de commande inscrit le référentiel par défaut pour les modules PowerShell. Une fois qu’un référentiel est inscrit, vous pouvez le référencer à partir des `Find-Module` applets de commande, `Install-Module` et `Publish-Module` . Le référentiel inscrit devient le référentiel par défaut dans `Find-Module` et `Install-Module` .

Les référentiels enregistrés sont spécifiques à l’utilisateur. Ils ne sont pas enregistrés dans un contexte à l’échelle du système.

Chaque référentiel inscrit est associé à un fournisseur de packages OneGet, qui est spécifié avec le paramètre **PackageManagementProvider** . Chaque fournisseur OneGet est conçu pour interagir avec un type spécifique de référentiel. Par exemple, le fournisseur NuGet est conçu pour interagir avec les référentiels NuGet. Si aucun fournisseur OneGet n’est spécifié lors de l’inscription, PowerShellGet tente de trouver un fournisseur OneGet pouvant gérer l’emplacement source spécifié.

## EXEMPLES

### Exemple 1 : inscrire un dépôt

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

La première commande s’inscrit `https://www.myget.org/F/powershellgetdemo/` en tant que référentiel pour l’utilisateur actuel. Une fois myNuGetSource inscrit, vous pouvez le référencer explicitement lors de la recherche, de l’installation et de la publication des modules. Étant donné que le paramètre **PackageManagementProvider** n’est pas spécifié, le référentiel n’est pas associé explicitement à un fournisseur de packages OneGet, de sorte que PowerShellGet interroge les fournisseurs de packages disponibles et les associe au fournisseur NuGet.

La deuxième commande récupère les dépôts inscrits et affiche les résultats.

## PARAMETERS

### -Credential

Spécifie les informations d’identification d’un compte disposant des droits nécessaires pour inscrire un dépôt.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Par défaut

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstallationPolicy

Spécifie la stratégie d’installation. Les valeurs valides sont : approuvé, non approuvé. La valeur par défaut n’est pas fiable.

La stratégie d’installation d’un référentiel spécifie le comportement PowerShell lors de l’installation à partir de ce référentiel. Lorsque vous installez des modules à partir d’un référentiel non approuvé, l’utilisateur est invité à confirmer l’installation.

Vous pouvez définir **InstallationPolicy** avec l’applet de commande `Set-PSRepository` .

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

Spécifie le nom du dépôt à inscrire. Vous pouvez utiliser ce nom pour spécifier le référentiel dans les applets de commande telles que `Find-Module` et `Install-Module` .

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

Spécifie un fournisseur de packages OneGet. Si vous ne spécifiez pas de valeur pour ce paramètre, PowerShellGet interroge les fournisseurs de packages disponibles et associe ce dépôt au premier fournisseur de package qui indique qu’il peut gérer le référentiel.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
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

Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy**.

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
Parameter Sets: NameParameterSet
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
Parameter Sets: NameParameterSet
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
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceLocation

Spécifie l’URI pour la découverte et l’installation de modules à partir de ce référentiel. Un URI peut être un flux de serveur NuGet (situation la plus courante), HTTP, HTTPs, FTP ou un emplacement de fichier.

Par exemple, pour les référentiels NuGet, l’emplacement source est semblable à `https://someNuGetUrl.com/api/v2` .

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSCredential

### System.Uri

## SORTIES

### System.Object

## REMARQUES

> [!IMPORTANT]
> Depuis avril 2020, PowerShell Gallery ne prend plus en charge les versions 1.0 et 1.1 de Transport Layer Security (TLS). Si vous n'utilisez pas TLS 1.2 ou une version plus récente, vous recevez une erreur lorsque vous tentez d'accéder à PowerShell Gallery. Utilisez la commande suivante pour vous assurer que vous utilisez TLS 1.2 :
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Pour plus d’informations, consultez l’[annonce](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) sur le blog PowerShell.

## LIENS CONNEXES

[Get-PSRepository](Get-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Unregister-PSRepository](Unregister-PSRepository.md)
