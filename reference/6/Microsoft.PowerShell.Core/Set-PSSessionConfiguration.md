---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 30950cb31a6d70b61416883a16603262c297f0d1
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345406"
---
# Set-PSSessionConfiguration

## SYNOPSIS
Modifie les propriétés d'une configuration de session enregistrée.

## SYNTAXE

### NameParameterSet (par défaut)

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

L' `Set-PSSessionConfiguration` applet de commande modifie les propriétés des configurations de session sur l’ordinateur local.

Utilisez le paramètre **Name** pour identifier la configuration de session que vous souhaitez modifier. Utilisez les autres paramètres pour spécifier les nouvelles valeurs des propriétés de la configuration de session. Pour supprimer une valeur de propriété de la configuration et utiliser la valeur par défaut, entrez une chaîne vide ("") ou une valeur `$Null` pour le paramètre correspondant.

À compter de PowerShell 3,0, vous pouvez utiliser un fichier de configuration de session pour définir une configuration de session. Cette fonctionnalité offre une méthode simple et intuitive pour définir ou modifier les propriétés des sessions qui utilisent la configuration de session. Pour spécifier un fichier de configuration de session, utilisez le paramètre **path** de `Set-PSSessionConfiguration` . Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).
Pour plus d’informations sur la création et la modification d’un fichier de configuration de session, consultez l’applet de commande `New-PSSessionConfigurationFile` .

Les configurations de session définissent l’environnement des sessions à distance ( **sessions PSSession** ) qui se connectent à l’ordinateur local. Chaque session **PSSession** utilise une configuration de session. La configuration de session détermine les fonctionnalités de la session **PSSession** , telles que les modules qui sont disponibles dans la session, les applets de commande qui sont autorisées à s’exécuter, le mode de langage, les quotas et les délais d’attente. Le descripteur de sécurité de la configuration de session détermine qui peut utiliser la configuration de session pour se connecter à l’ordinateur local. Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).

Pour afficher les propriétés d’une configuration de session, utilisez l’applet de commande `Get-PSSessionConfiguration` ou le fournisseur WSMan. Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help WSMan` .

## EXEMPLES

### Exemple 1 : créer et modifier une configuration de session

Cet exemple montre comment ajouter et supprimer un script de démarrage d’une configuration.

La première commande crée la configuration **AdminShell** . La deuxième commande ajoute le `AdminConfig.ps1` script à la configuration. La modification est effective quand vous redémarrez **WinRM**.
La troisième commande supprime le `AdminConfig.ps1` script de la configuration.

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### Exemple 2 : afficher les résultats

Cet exemple augmente la valeur de la propriété **MaximumReceivedObjectSizeMB** à 20. Cette commande vous invite également à redémarrer le service **WinRM** . La modification n’est pas effective tant que le service **WinRM** n’est pas redémarré.

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### Exemple 3 : afficher les résultats de différentes façons

Dans cet exemple, `Set-PSSessionConfiguration` modifie le script de démarrage dans la configuration de session **MaintenanceShell** en `Maintenance.ps1` . La sortie affiche la modification et vous invite à redémarrer le service **WinRM** . La réponse est « y » (Oui).

`Get-PSSessionConfiguration` Obtient la configuration de session **MaintenanceShell** . L’opérateur de pipeline (|) envoie les résultats de la commande à `Format-List` , qui affiche toutes les propriétés de l’objet de configuration dans une liste. Ensuite, à l’aide du fournisseur WSMan, nous allons voir les paramètres d’initialisation de la configuration **MaintenanceShell** . `Get-ChildItem` (alias `dir` ) Obtient les éléments enfants dans le nœud **InitializationParameters** pour le plug-in **MaintenanceShell** . Pour plus d’informations sur le fournisseur WSMan, tapez `Get-Help wsman` .

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## PARAMÈTRES

### -AccessMode

Active et désactive la configuration de session et détermine si elle peut être utilisée pour les sessions locales ou distantes sur l'ordinateur. Les valeurs valides pour ce paramètre sont :

- Désactivé. désactive la configuration de session. Elle ne peut pas être utilisée pour l'accès local ou distant à l'ordinateur. Cette valeur affecte la **Enabled** valeur `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` **false** à la propriété Enabled de la configuration de session ().
- Local. ajoute un entrée **Network_Deny_All** au descripteur de sécurité de la configuration de session.
  Les utilisateurs de l’ordinateur local peuvent utiliser la configuration de session pour créer une session de bouclage locale sur le même ordinateur, mais l’accès est refusé aux utilisateurs distants.
- Distant. supprime les entrées **Deny_All** et **Network_Deny_All** des descripteurs de sécurité de la configuration de session. Les utilisateurs des ordinateurs locaux et distants peuvent utiliser la configuration de session pour créer des sessions et exécuter des commandes sur cet ordinateur.

La valeur par défaut est **Remote**.

D’autres applets de commande peuvent remplacer la valeur de ce paramètre ultérieurement. Par exemple, l' `Enable-PSRemoting` applet de commande active toutes les configurations de session sur l’ordinateur et autorise l’accès à distance à celles-ci, et l’applet de commande `Disable-PSRemoting` autorise uniquement l’accès local à toutes les configurations de session sur l’ordinateur.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationBase

Spécifie le chemin d’accès du fichier d’assembly ( \* . dll) qui est spécifié dans la valeur du paramètre **AssemblyName** .

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssemblyName

Spécifie le nom de l’assembly. Cette applet de commande crée une configuration de session basée sur une classe définie dans un assembly.

Entrez le nom de fichier ou le chemin d’accès complet d’un fichier. dll d’assembly qui définit une configuration de session. Si vous entrez uniquement le nom du fichier, vous pouvez entrer le chemin d’accès dans la valeur du paramètre **ApplicationBase** .

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTypeName

Spécifie le type de la configuration de session définie dans l'assembly dans le paramètre **AssemblyName**. Le type que vous spécifiez doit implémenter la classe **System.Management.Automation.Remoting.PSSessionConfiguration**.

Ce paramètre est obligatoire quand vous spécifiez un nom d'assembly.

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Supprime toutes les invites utilisateur et redémarre le service **WinRM** sans demander confirmation. Le redémarrage du service permet d'appliquer la modification de configuration.

Pour éviter un redémarrage et supprimer l'invite de redémarrage, utilisez le paramètre **NoServiceRestart**.

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

### -MaximumReceivedDataSizePerCommandMB

Spécifie la limite de la quantité de données qui peut être envoyée à cet ordinateur dans une commande à distance unique. Entrez la taille des données en mégaoctets (Mo). La valeur par défaut est 50 Mo.

Si une limite de taille des données est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée. La valeur de ce paramètre est ignorée.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSizeMB

Spécifie les limites de la quantité de données qui peuvent être envoyées à cet ordinateur dans un objet unique.
Entrez la taille des données en mégaoctets. La valeur par défaut est 10 Mo.

Si une limite de taille d’objet est définie dans le type de configuration spécifié dans le paramètre **ConfigurationTypeName** , la limite du type de configuration est utilisée. La valeur de ce paramètre est ignorée.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Spécifie les modules et les composants logiciels enfichables qui sont automatiquement importés dans les sessions qui utilisent la configuration de session. Entrez les noms des modules et des composants logiciels enfichables.

Par défaut, seul le composant logiciel enfichable **Microsoft. PowerShell. Core** est importé dans les sessions, mais à moins que les applets de commande ne soient exclues, vous pouvez utiliser les `Import-Module` applets de commande et Add-PSSnapin pour ajouter des modules et des composants logiciels enfichables à la session.

Les modules spécifiés dans cette valeur de paramètre sont importés en compléments des modules spécifiés dans le fichier de configuration de session ( `New-PSSessionConfigurationFile` ). Toutefois, les paramètres dans le fichier de configuration de session peuvent masquer les commandes exportées par les modules ou empêcher les utilisateurs de les utiliser.

Les modules spécifiés dans cette valeur de paramètre remplacent la liste de modules spécifiée à l’aide du paramètre **ModulesToImport** de l’applet de commande `Register-PSSessionConfiguration` .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie le nom de la configuration de session que vous souhaitez modifier.

Vous ne pouvez pas utiliser ce paramètre pour modifier le nom de la configuration de session.

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

### -NoServiceRestart

Ne redémarre pas le service **WinRM** et supprime l’invite de redémarrage du service.

Par défaut, lorsque vous exécutez `Set-PSSessionConfiguration` , vous êtes invité à redémarrer le service **WinRM** pour que la nouvelle configuration de session soit effective. Tant que le service **WinRM** n’est pas redémarré, la nouvelle configuration de session n’est pas effective.

Pour redémarrer le service **WinRM** sans invite, utilisez le paramètre **force** . Pour redémarrer manuellement le service **WinRM** , utilisez l' `Restart-Service` applet de commande.

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

### -Path

Spécifie le chemin d’accès d’un fichier de configuration de session (. PSSC), tel que celui créé par l’applet de commande `New-PSSessionConfigurationFile` . Si vous omettez le chemin d'accès, la valeur par défaut est le répertoire actif.

Pour plus d’informations sur la modification d’un fichier de configuration de session, consultez la rubrique d’aide de l’applet de commande `New-PSSessionConfigurationFile` .

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSVersion

Spécifie la version de PowerShell dans les sessions qui utilisent cette configuration de session.

La valeur de ce paramètre est prioritaire sur la valeur de la clé **PowerShellVersion** dans le fichier de configuration de session.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsCredential

Spécifie des informations d’identification pour les commandes dans la session. Par défaut, les commandes s'exécutent avec les autorisations de l'utilisateur actuel.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecurityDescriptorSddl

Spécifie une chaîne SDDL (Security Descriptor Definition Language) différente pour la configuration.

Cette chaîne détermine les autorisations qui sont nécessaires pour utiliser la nouvelle configuration de session. Pour utiliser une configuration de session dans une session, les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour la configuration.

Pour utiliser le descripteur de sécurité par défaut pour la configuration, entrez une chaîne vide ("") ou une valeur `$Null` . La valeur par défaut est le SDDL racine dans le WSMan:.

Si le descripteur de sécurité est complexe, envisagez d’utiliser le paramètre **ShowSecurityDescriptorUI** au lieu de celui-ci. Vous ne pouvez pas utiliser les deux paramètres dans la même commande.

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

### -SessionTypeOption

Spécifie les options spécifiques au type pour la configuration de session. Entrez un objet d’options de type de session, tel que l’objet **PSWorkflowExecutionOption** retourné par l’applet de commande `New-PSWorkflowExecutionOption` .

Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session. Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session. Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowSecurityDescriptorUI

Indique que cette applet de commande est une feuille de propriétés qui vous aide à créer un nouveau SDDL pour la configuration de session. La feuille de propriétés s’affiche après l’exécution de la `Set-PSSessionConfiguration` commande, puis le redémarrage du service **WinRM** .

Lorsque vous définissez des autorisations sur la configuration, n’oubliez pas que les utilisateurs doivent disposer au moins de l’autorisation EXECUTE (Invoke) pour utiliser la configuration de session dans une session.

Vous ne pouvez pas utiliser le paramètre **SecurityDescriptorSDDL** et ce paramètre dans la même commande.

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

### -StartupScript

Spécifie le script de démarrage pour la configuration. Entrez le chemin d’accès complet d’un script PowerShell. Le script spécifié est exécuté dans la nouvelle session qui utilise la configuration de session.

Pour supprimer un script de démarrage d’une configuration de session, entrez une chaîne vide ("") ou une valeur `$Null` .

Vous pouvez utiliser un script de démarrage pour configurer davantage la session utilisateur. Si le script génère une erreur, même une erreur sans fin d’exécution, la session n’est pas créée et la `New-PSSession` commande échoue.

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

### -ThreadOptions

Spécifie le paramètre des options de thread dans la configuration. Ce paramètre définit comment les threads sont créés et utilisés quand une commande est exécutée dans la session. Les valeurs valides pour ce paramètre sont :

- Default
- ReuseThread
- UseCurrentThread
- UseNewThread

La valeur par défaut est **UseCurrentThread**.

Pour plus d’informations, consultez [énumération PSThreadOptions](/dotnet/api/system.management.automation.runspaces.psthreadoptions).

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransportOption

Spécifie les options de transport pour la configuration de session. Entrez un objet d’options de transport, tel que l’objet **WSManConfigurationOption** retourné par l’applet de commande `New-PSTransportOption` .

Les options de sessions qui utilisent la configuration de session sont déterminées par les valeurs des options de session et par les options de configuration de session. Sauf indication contraire, les options définies dans la session, par exemple à l’aide de l’applet de commande `New-PSSessionOption` , sont prioritaires sur les options définies dans la configuration de session. Toutefois, les valeurs d'option de session ne peuvent pas dépasser les valeurs maximales définies dans la configuration de session.

Ce paramètre a été introduit dans PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSharedProcess

Utilisez un seul processus pour héberger toutes les sessions qui sont démarrées par le même utilisateur et utiliser la même configuration de session. Par défaut, chaque session est hébergée dans son propre processus.

Ce paramètre a été introduit dans PowerShell 3,0.

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

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

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

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Microsoft. WSMan. Management. WSManConfigLeafElement

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.

L' `Set-PSSessionConfiguration` applet de commande ne modifie pas le nom de la configuration et le fournisseur **WSMan** ne prend pas en charge l’applet de commande `Rename-Item` . Pour modifier le nom d’une configuration de session, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration, puis utilisez l' `Register-PSSessionConfiguration` applet de commande pour créer et inscrire une nouvelle configuration de session.

Vous pouvez utiliser l' `Set-PSSessionConfiguration` applet de commande pour modifier les configurations de session Microsoft. PowerShell et Microsoft. powershell32 par défaut. Elles ne sont pas protégées. Pour revenir à la version d’origine d’une configuration de session par défaut, utilisez l' `Unregister-PSSessionConfiguration` applet de commande pour supprimer la configuration de session par défaut, puis utilisez l' `Enable-PSRemoting` applet de commande pour la restaurer.

Les propriétés d'un objet de configuration de session varient selon les options définies pour la configuration de session et les valeurs de ces options. En outre, les configurations de sessions qui utilisent un fichier de configuration de session ont des propriétés supplémentaires.

Vous pouvez utiliser les commandes du lecteur WSMan pour modifier les propriétés des configurations de session.
Toutefois, vous ne pouvez pas utiliser le lecteur WSMan : dans PowerShell 2,0 pour modifier les propriétés de configuration de session introduites dans PowerShell 3,0, telles que **OutputBufferingMode**. Les commandes Windows PowerShell 2.0 ne génèrent pas d'erreur, mais elles sont inefficaces. Pour modifier les propriétés introduites dans PowerShell 3,0, utilisez le lecteur WSMan : dans PowerShell 3,0.

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
