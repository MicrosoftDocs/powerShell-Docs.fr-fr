---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: 5adba912d91369250ee9891ee2bb2ca0f8cba796
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202349"
---
# Add-PSSnapin

## SYNOPSIS
Ajoute un ou plusieurs composants logiciels enfichables Windows PowerShell à la session active.

## SYNTAX

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## Description

L' `Add-PSSnapin` applet de commande ajoute les composants logiciels enfichables Windows PowerShell inscrits à la session active. Après avoir ajouté les composants logiciels enfichables, vous pouvez utiliser les applets de commande et les fournisseurs pris en charge par les composants logiciels enfichables dans la session active.

Pour ajouter le composant logiciel enfichable à toutes les futures sessions Windows PowerShell, ajoutez une `Add-PSSnapin` commande à votre profil Windows PowerShell. Pour plus d’informations, consultez [about_Profiles](about/about_Profiles.md).

À compter de Windows PowerShell 3.0, les commandes de base qui sont incluses dans Windows PowerShell sont packagés dans des modules. L'exception est **Microsoft.PowerShell.Core** , qui est un composant logiciel enfichable (PSSnapin).
Par défaut, seul le composant logiciel enfichable **Microsoft.PowerShell.Core** est ajouté à la session. Les modules sont importés automatiquement à la première utilisation, et vous pouvez utiliser l’applet de commande Import-Module pour les importer.

## EXEMPLES

### Exemple 1 : ajouter des composants logiciels enfichables

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

Cette commande ajoute les composants logiciels enfichables Microsoft Exchange et Active Directory à la session active.

### Exemple 2 : ajouter tous les composants logiciels enfichables inscrits

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

Cette commande ajoute tous les composants logiciels enfichables Windows PowerShell inscrits à la session. Elle utilise l’applet de commande Get-PSSnapin avec le paramètre **Registered** pour récupérer des objets représentant chacun des composants logiciels enfichables inscrits. L’opérateur de pipeline (|) passe le résultat à `Add-PSSnapin` , qui les ajoute à la session. Le paramètre **PassThru** retourne des objets qui représentent chacun des composants logiciels enfichables ajoutés.

### Exemple 3 : inscrire un composant logiciel enfichable et l’ajouter

La première commande obtient les composants logiciels enfichables qui ont été ajoutés à la session active qui incluent les composants logiciels enfichables qui sont installés avec Windows PowerShell. Dans cet exemple, ManagementFeatures n'est pas retourné. Cela indique qu'il n'a pas été ajouté à la session.

La deuxième commande récupère les composants logiciels enfichables qui ont été inscrits sur votre système, y compris ceux qui ont déjà été ajoutés à la session. Il n’inclut pas les composants logiciels enfichables qui sont installés avec Windows PowerShell. Dans ce cas, la commande ne retourne aucun composant logiciel enfichable. Cela indique que le composant logiciel enfichable ManagementFeatures n’a pas été inscrit sur le système.

La troisième commande crée un alias, installutil, pour le chemin d’accès de l’outil InstallUtil dans .NET Framework.

La quatrième commande utilise l’outil InstallUtil pour inscrire le composant logiciel enfichable. La commande spécifie le chemin d’accès de ManagementCmdlets.dll, le nom de fichier ou le nom de module du composant logiciel enfichable.

La cinquième commande est identique à la deuxième commande. Cette fois, vous l'utilisez pour vérifier que le composant logiciel enfichable ManagementCmdlets est inscrit.

La sixième commande utilise l' `Add-PSSnapin` applet de commande pour ajouter le composant logiciel enfichable ManagementFeatures à la session. Elle spécifie le nom du composant logiciel enfichable, ManagementFeatures, et non pas le nom de fichier.

Pour vérifier que le composant logiciel enfichable est ajouté à la session, la septième commande utilise le paramètre **module** de l’applet de commande Get-Command. Elle affiche les éléments qui ont été ajoutés à la session par un composant logiciel enfichable ou un module.

Vous pouvez également utiliser la propriété **PSSnapin** de l’objet retourné par l' `Get-Command` applet de commande pour trouver le composant logiciel enfichable ou le module dans lequel provient une applet de commande. La huitième commande utilise la notation par points pour rechercher la valeur de la propriété PSSnapin de l’applet de commande Set-Alias.

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

Cet exemple montre le processus d'inscription d'un composant logiciel enfichable sur votre système, puis son ajout à votre session. Elle utilise ManagementFeatures, un composant logiciel enfichable fictif implémenté dans un fichier nommé ManagementCmdlets.dll.

## PARAMETERS

### -Name

Spécifie le nom du composant logiciel enfichable. Il s’agit du nom, et non de AssemblyName ou ModuleName. Les caractères génériques sont autorisés.

Pour rechercher les noms des composants logiciels enfichables inscrits sur votre système, tapez `Get-PSSnapin -Registered` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Indique que cette applet de commande retourne un objet qui représente chaque composant logiciel enfichable ajouté. Par défaut, cette applet de commande ne génère aucun résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun
Vous ne pouvez pas rediriger des objets vers cette applet de commande.

## SORTIES

### None ou System. Management. Automation. PSSnapInInfo

Cette applet de commande retourne un objet PSSnapInInfo qui représente le composant logiciel enfichable si vous spécifiez le paramètre **PassThru** . Sinon, cette applet de commande ne génère aucune sortie.

## REMARQUES

* À compter de Windows PowerShell 3.0, les commandes de base qui sont installées avec Windows PowerShell sont packagées dans des modules. Dans Windows PowerShell 2,0 et dans les programmes hôtes qui créent des sessions de style plus anciennes dans les versions ultérieures de Windows PowerShell, les commandes de base sont empaquetées dans des composants logiciels enfichables (PSSnapins). L’exception est **Microsoft. PowerShell. Core** , qui est toujours un composant logiciel enfichable. En outre, les sessions à distance, telles que celles démarrées par l’applet de commande New-PSSession, sont des sessions de style plus anciennes qui incluent des composants logiciels enfichables principaux.

  Pour plus d’informations sur la méthode **CreateDefault2** qui crée des sessions de style plus récentes avec des modules de base, consultez [méthode CreateDefault2](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) dans MSDN Library.

* Pour plus d’informations sur les composants logiciels enfichables, consultez [about_Pssnapins](About/about_PSSnapins.md) et [comment créer un composant logiciel enfichable Windows PowerShell](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).
* `Add-PSSnapin` Ajoute le composant logiciel enfichable uniquement à la session active. Pour ajouter le composant logiciel enfichable à toutes les sessions Windows PowerShell, ajoutez-le à votre profil Windows PowerShell. Pour plus d'informations, consultez about_Providers.
* Vous pouvez ajouter n’importe quel composant logiciel enfichable qui a été inscrit à l’aide de l’utilitaire d’installation Microsoft .NET Framework. Pour plus d’informations, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).
* Pour obtenir la liste des composants logiciels enfichables inscrits sur votre ordinateur, tapez `Get-PSSnapin -Registered` .
* Avant d’ajouter un composant logiciel enfichable, `Add-PSSnapin` vérifie la version du composant logiciel enfichable pour s’assurer qu’il est compatible avec la version actuelle de Windows PowerShell. Si la version du composant logiciel enfichable n'est pas compatible, Windows PowerShell signale une erreur.

## LIENS CONNEXES

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
