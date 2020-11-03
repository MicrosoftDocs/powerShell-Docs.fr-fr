---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: d7b75b9aec6cba352d72176de59af82155d1fa17
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202717"
---
# Publish-Module

## SYNOPSIS
Publie un module spécifié à partir de l’ordinateur local sur une galerie en ligne.

## SYNTAX

### ModuleNameParameterSet (par défaut)

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModulePathParameterSet

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Publish-Module` applet de commande publie un module dans une galerie en ligne NuGet à l’aide d’une clé API, stockée en tant que partie du profil d’un utilisateur dans la Galerie. Vous pouvez indiquer le module à publier par son nom ou par le chemin d’accès au dossier le contenant.

Lorsque vous spécifiez un module par son nom, `Publish-Module` publie le premier module qui serait trouvé en exécutant `Get-Module -ListAvailable <Name>` . Si vous spécifiez une version minimale d’un module à publier, `Publish-Module` publie le premier module avec une version qui est supérieure ou égale à la version minimale que vous avez spécifiée.

La publication d’un module nécessite des métadonnées affichées dans la page de la galerie pour le module. Les métadonnées requises incluent le nom du module, la version, la description et l’auteur. Bien que la plupart des métadonnées proviennent du manifeste de module, certaines métadonnées doivent être spécifiées dans des `Publish-Module` paramètres tels que **tag** , **ReleaseNote** , **iconUri** , **ProjectUri** et **LicenseUri** , car ces paramètres correspondent aux champs d’une galerie NuGet.

## EXEMPLES

### Exemple 1 : publier un module

Dans cet exemple, MyDscModule est publié dans la galerie en ligne à l’aide de la clé API pour indiquer le compte de la galerie en ligne du propriétaire du module. Si MyDscModule n’est pas un module de manifeste valide qui spécifie un nom, une version, une description et un auteur, une erreur se produit.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### Exemple 2 : publier un module avec les métadonnées de la Galerie

Dans cet exemple, MyDscModule est publié dans la galerie en ligne à l’aide de la clé API pour indiquer le compte de la Galerie du propriétaire du module. Les métadonnées supplémentaires fournies sont affichées sur la page Web du module dans la Galerie. Le propriétaire ajoute deux balises de recherche pour le module, en les associant à Active Directory ; une brève note de publication est ajoutée. Si MyDscModule n’est pas un module de manifeste valide qui spécifie un nom, une version, une description et un auteur, une erreur se produit.

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## PARAMETERS

### -AllowPrerelease

Autorise la publication des modules marqués comme préversion.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous invite à confirmer l’exécution de l' `Publish-Module` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui dispose des droits nécessaires pour publier un module pour un fournisseur de package ou une source spécifiés.

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

### -Exclude

Définit les fichiers à exclure du module publié.

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatVersion

Accepte uniquement les valeurs valides spécifiées par l’attribut **ValidateSet** .

Pour plus d’informations, consultez [déclaration d’attribut ValidateSet](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) et [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

Spécifie l’URL d’une icône pour le module. L’icône spécifiée s’affiche sur la page Web de la Galerie pour le module.

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

### -LicenseUri

Spécifie l’URL des termes du contrat de licence pour le module que vous souhaitez publier.

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

### -Name

Spécifie le nom du module que vous souhaitez publier. `Publish-Module` recherche le nom de module spécifié dans `$Env:PSModulePath` .

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NuGetApiKey

Spécifie la clé API que vous souhaitez utiliser pour publier un module dans la galerie en ligne. La clé API fait partie de votre profil dans la galerie en ligne, et se trouve sur la page de votre compte d’utilisateur dans la Galerie. La clé API est une fonctionnalité spécifique de NuGet.

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

### -Path

Spécifie le chemin d’accès au module que vous souhaitez publier. Ce paramètre accepte le chemin d’accès au dossier qui contient le module.

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProjectUri

Spécifie l’URL d’une page Web relative à ce projet.

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

### -ReleaseNotes

Spécifie une chaîne contenant des notes de publication ou des commentaires que vous souhaitez mettre à la disposition des utilisateurs de cette version du module.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Référentiel

Spécifie le nom convivial d’un référentiel qui a été enregistré en exécutant `Register-PSRepository` . Le référentiel doit avoir un **PublishLocation** , qui est un URI NuGet valide.
Le **PublishLocation** peut être défini en exécutant `Set-PSRepository` .

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

### -RequiredVersion

Spécifie la version exacte d’un module unique à publier.

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipAutomaticTags

Supprime les commandes et les ressources d’être incluses en tant que balises. Ignore l’ajout automatique de balises à un module.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tags

Ajoute une ou plusieurs balises au module que vous publiez. Exemples de balises : DesiredStateConfiguration, DSC, DSCResourceKit ou PSModule. Séparez plusieurs balises par des virgules.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passerait si le `Publish-Module` s’exécute. L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

### System. Management. Automation. PSCredential

## SORTIES

### System.Object

## REMARQUES

`Publish-Module` s’exécute sur les versions PowerShell 3,0 ou ultérieures de PowerShell, sur Windows 7 ou Windows 2008 R2 et versions ultérieures de Windows.

La publication d’un module nécessite des métadonnées affichées dans la page de la galerie pour le module. Les métadonnées requises incluent le nom du module, la version, la description et l’auteur. La plupart des métadonnées proviennent du manifeste de module, mais certaines métadonnées peuvent être spécifiées dans des `Publish-Module` paramètres, tels que **tag** , **ReleaseNote** , **iconUri** , **ProjectUri** et **LicenseUri** . Pour plus d’informations, consultez [valeurs de manifeste du package qui ont un impact sur l’interface utilisateur PowerShell Gallery](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).

## LIENS CONNEXES

[Find-Module](Find-Module.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

