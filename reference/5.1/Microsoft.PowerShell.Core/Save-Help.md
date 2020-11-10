---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 3264bdc41d43fdec55ee80514bc988b33772a792
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388516"
---
# Save-Help

## SYNOPSIS
Télécharge et enregistre les derniers fichiers d'aide dans un répertoire du système de fichiers.

## SYNTAXE

### Chemin d’accès (par défaut)

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [<CommonParameters>]
```

### LiteralPath

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force]
 [<CommonParameters>]
```

## DESCRIPTION

L' `Save-Help` applet de commande télécharge les fichiers d’aide les plus récents pour les modules PowerShell et les enregistre dans un répertoire que vous spécifiez. Cette fonctionnalité vous permet de mettre à jour les fichiers d'aide sur les ordinateurs qui n'ont pas accès à Internet et facilite la mise à jour des fichiers d'aide sur plusieurs ordinateurs.

Dans Windows PowerShell 3,0, `Save-Help` fonctionnait uniquement pour les modules qui sont installés sur l’ordinateur local. Bien qu’il soit possible d’importer un module à partir d’un ordinateur distant ou d’obtenir une référence à un objet **PSModuleInfo** à partir d’un ordinateur distant à l’aide de la communication à distance PowerShell, la propriété **HelpInfoUri** n’a pas été conservée et `Save-Help` ne fonctionnerait pas pour l’aide des modules distants.

Dans Windows PowerShell 4,0, la propriété **HelpInfoUri** est conservée via la communication à distance PowerShell, ce qui permet `Save-Help` à de fonctionner pour les modules qui sont installés sur des ordinateurs distants. Il est également possible d’enregistrer un objet **PSModuleInfo** sur un disque ou sur un support amovible en exécutant `Export-Clixml` sur un ordinateur qui n’a pas accès à Internet, d’importer l’objet sur un ordinateur qui a accès à Internet, puis `Save-Help` d’exécuter sur l’objet **PSModuleInfo** . L’aide enregistrée peut être transportée vers l’ordinateur distant à l’aide d’un support de stockage amovible, tel qu’un lecteur USB. L’aide peut être installée sur l’ordinateur distant en exécutant `Update-Help` . Ce processus peut être utilisé pour installer l'aide sur les ordinateurs qui ne disposent d'aucun accès réseau.

Pour installer les fichiers d’aide enregistrés, exécutez l’applet de commande `Update-Help` . Ajoutez son paramètre **SourcePath** pour spécifier le dossier dans lequel vous avez enregistré les fichiers d’aide.

Sans paramètres, une `Save-Help` commande télécharge l’aide la plus récente pour tous les modules de la session et les modules installés sur l’ordinateur à un emplacement répertorié dans la variable d’environnement **PSModulePath** . Cette action ignore les modules qui ne prennent pas en charge l’aide actualisable sans avertissement.

L' `Save-Help` applet de commande vérifie la version des fichiers d’aide dans le dossier de destination. Si des fichiers d’aide plus récents sont disponibles, cette applet de commande télécharge les fichiers d’aide les plus récents à partir d’Internet, puis les enregistre dans le dossier. L' `Save-Help` applet de commande fonctionne comme la `Update-Help` cmdlet, sauf qu’elle enregistre les fichiers CAB (. cab) téléchargés, au lieu d’extraire les fichiers d’aide des fichiers CAB et de les installer sur l’ordinateur.

L'aide enregistrée pour chaque module se compose d'un fichier d'informations d'aide (HelpInfo XML) et d'un fichier CAB pour les fichiers d'aide dans chaque culture d'interface utilisateur. Vous n’avez pas besoin d’extraire les fichiers d’aide du fichier CAB. L' `Update-Help` applet de commande extrait les fichiers d’aide, valide le code XML à des fins de sécurité, puis installe les fichiers d’aide et le fichier d’informations d’aide dans un sous-dossier spécifique à la langue du dossier du module.

Pour enregistrer les fichiers d’aide pour les modules dans le dossier d’installation de PowerShell ( `$pshome\Modules` ), démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur. Vous devez être membre du groupe Administrateurs sur l'ordinateur pour télécharger les fichiers d'aide pour ces modules.

Cette applet de commande a été introduite dans Windows PowerShell 3.0.

## EXEMPLES

### Exemple 1 : enregistrer l’aide du module DhcpServer

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module,
# save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

Cet exemple montre trois façons différentes d’utiliser `Save-Help` pour enregistrer l’aide du module **dhcpserver** à partir d’un ordinateur client connecté à Internet, sans installer le module **dhcpserver** ou le rôle serveur DHCP sur l’ordinateur local.

### Exemple 2 : installer l’aide pour le module DhcpServer

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the
# PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer
# module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and
# then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

Cet exemple montre comment installer l’aide que vous avez enregistrée dans l’exemple 1 pour le module **DhcpServer** sur un ordinateur qui n’a pas accès à Internet.

### Exemple 3 : enregistrer l’aide pour tous les modules

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

Cette commande télécharge les fichiers d'aide les plus récents pour tous les modules dans la culture d'interface utilisateur définie pour Windows sur l'ordinateur local. Elle enregistre les fichiers d’aide dans le `\\Server01\Fileshare01` dossier.

### Exemple 4 : enregistrer l’aide pour un module sur l’ordinateur

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

Cette commande télécharge les fichiers d’aide les plus récents pour le module **ServerManager** , puis les enregistre dans le `\\Server01\Fileshare01` dossier.

Quand un module est installé sur l'ordinateur, vous pouvez taper le nom du module comme valeur du paramètre **Module** , même si le module n'est pas importé dans la session active.

La commande utilise le paramètre **Credential** pour fournir les informations d'identification d'un utilisateur qui a l'autorisation d'écrire dans le partage de fichiers.

### Exemple 5 : enregistrer l’aide pour un module sur un autre ordinateur

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

Ces commandes téléchargent les fichiers d’aide les plus récents pour le module **CustomSQL** et les enregistrent dans le `\\Server01\Fileshare01` dossier.

Étant donné que le module **CustomSQL** n’est pas installé sur l’ordinateur, la séquence comprend une `Invoke-Command` commande qui obtient l’objet module pour le module CustomSQL à partir de l’ordinateur Server02, puis dirige l’objet module vers l’applet de commande `Save-Help` .

Lorsqu’un module n’est pas installé sur l’ordinateur, `Save-Help` il a besoin de l’objet de module, qui comprend des informations sur l’emplacement des fichiers d’aide les plus récents.

### Exemple 6 : enregistrer l’aide d’un module dans plusieurs langues

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

Cette commande enregistre l’aide pour les modules PowerShell Core dans quatre cultures d’interface utilisateur différentes. Il n’est pas nécessaire d’installer les modules linguistiques de ces paramètres régionaux sur l’ordinateur.

`Save-Help` peut télécharger des fichiers d’aide pour les modules dans des cultures d’interface utilisateur différentes uniquement lorsque le propriétaire du module rend les fichiers traduits disponibles sur Internet.

### Exemple 7 : enregistrer l’aide plusieurs fois par jour

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

Cette commande enregistre l'aide de tous les modules qui sont installés sur l'ordinateur. La commande spécifie le paramètre **force** pour remplacer la règle qui empêche l' `Save-Help` applet de commande de télécharger l’aide plusieurs fois par période de 24 heures.

Le paramètre **force** remplace également la restriction de 1 Go et contourne la vérification de version.
Par conséquent, vous pouvez télécharger des fichiers même si la version n’est pas ultérieure à la version dans le dossier de destination.

La commande utilise l' `Save-Help` applet de commande pour télécharger et enregistrer les fichiers d’aide dans le dossier spécifié.
Le paramètre **force** est obligatoire lorsque vous devez exécuter une `Save-Help` commande plusieurs fois par jour.

## PARAMÈTRES

### -Credential

Spécifie les informations d’identification de l’utilisateur. Cette applet de commande exécute la commande à l’aide des informations d’identification d’un utilisateur qui a l’autorisation d’accéder à l’emplacement du système de fichiers spécifié par le paramètre **DestinationPath** . Ce paramètre est valide uniquement lorsque le paramètre **DestinationPath** ou **LiteralPath** est utilisé dans la commande.

Ce paramètre vous permet d’exécuter `Save-Help` des commandes qui utilisent le paramètre **DestinationPath** sur des ordinateurs distants. En fournissant des informations d’identification explicites, vous pouvez exécuter la commande sur un ordinateur distant et accéder à un partage de fichiers sur un troisième ordinateur sans rencontrer une erreur d’accès refusé ou en utilisant l’authentification CredSSP pour déléguer les informations d’identification.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### -DestinationPath

Spécifie le chemin d’accès du dossier dans lequel les fichiers d’aide sont enregistrés. Ne spécifiez pas un nom de fichier ou une extension de nom de fichier.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique que cette applet de commande ne suit pas la limite d’une fois par jour, ignore la vérification de version et télécharge les fichiers qui dépassent la limite de 1 Go.

Sans ce paramètre, une seule `Save-Help` commande est autorisée pour chaque module au cours de chaque période de 24 heures, les téléchargements sont limités à 1 Go de contenu non compressé par module et les fichiers d’aide d’un module sont installés uniquement lorsqu’ils sont plus récents que les fichiers de l’ordinateur.

La limite d’une fois par jour protège les serveurs qui hébergent les fichiers d’aide et vous permet d’ajouter une `Save-Help` commande à votre profil PowerShell.

Pour enregistrer l’aide d’un module dans plusieurs cultures d’interface utilisateur sans le paramètre **force** , incluez toutes les cultures d’interface utilisateur dans la même commande, par exemple : `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### -FullyQualifiedModule

Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** . Consultez la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif. Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** . les deux paramètres s’excluent mutuellement.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d’accès du dossier de destination. Contrairement à la valeur du paramètre **DestinationPath** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

Spécifie les modules pour lesquels cette applet de commande télécharge l’aide. Entrez un ou plusieurs noms de module ou modèles de nom dans une liste séparée par des virgules ou dans un fichier qui a un nom de module sur chaque ligne. Les caractères génériques sont autorisés. Vous pouvez également diriger les objets de module de l’applet de commande `Get-Module` vers `Save-Help` .

Par défaut, `Save-Help` télécharge l’aide pour tous les modules qui prennent en charge l’aide actualisable et sont installés sur l’ordinateur local à un emplacement répertorié dans la variable d’environnement **PSModulePath** .

Pour enregistrer l’aide pour les modules qui ne sont pas installés sur l’ordinateur, exécutez une `Get-Module` commande sur un ordinateur distant. Ensuite, dirigez les objets de module résultants vers l’applet de commande `Save-Help` ou envoyez les objets de module en tant que valeur des paramètres **module** ou **InputObject** .

Si le module que vous spécifiez est installé sur l'ordinateur, vous pouvez entrer le nom du module ou un objet de module. Si le module n’est pas installé sur l’ordinateur, vous devez entrer un objet de module, tel que celui retourné par l’applet de commande `Get-Module` .

Le paramètre **module** de l' `Save-Help` applet de commande n’accepte pas le chemin d’accès complet d’un fichier de module ou d’un fichier manifeste de module. Pour enregistrer l’aide d’un module qui ne se trouve pas dans un emplacement **PSModulePath** , importez le module dans la session active avant d’exécuter la `Save-Help` commande.

La valeur « * » (tous) tente de mettre à jour l’aide de tous les modules installés sur l’ordinateur.
Cela comprend les modules qui ne prennent pas en charge l’aide actualisable. Cette valeur peut générer des erreurs quand la commande rencontre des modules qui ne prennent pas en charge l’aide actualisable.

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -UICulture

Spécifie les valeurs de culture d’interface utilisateur pour lesquelles cette applet de commande obtient les fichiers d’aide mis à jour. Entrez un ou plusieurs codes de langue, par exemple `es-ES` , une variable qui contient des objets de culture ou une commande qui obtient des objets de culture, telle qu’une `Get-Culture` `Get-UICulture` commande ou.

Les caractères génériques ne sont pas autorisés. Ne spécifiez pas de code de langue partielle, tel que « de ».

Par défaut, `Save-Help` obtient les fichiers d’aide dans la culture d’interface utilisateur définie pour Windows ou sa culture de secours.
Si vous spécifiez le paramètre **UICulture** , `Save-Help` recherche uniquement de l’aide pour la culture d’interface utilisateur spécifiée, et non dans une culture de secours.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

Indique que cette applet de commande exécute la commande, y compris le téléchargement Web, avec les informations d’identification de l’utilisateur actuel. Par défaut, la commande s'exécute sans informations d'identification explicites.

Ce paramètre est effectif uniquement quand le téléchargement web utilise NTLM, la négociation ou l'authentification Kerberos.

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSModuleInfo

Vous pouvez diriger un objet de module de l’applet de commande `Get-Module` vers le paramètre de **module** de `Save-Help` .

## SORTIES

### Aucun

Cette applet de commande ne génère aucune sortie.

## REMARQUES

- Pour enregistrer l’aide des modules dans le dossier $pshome nouvelle \modules., démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur. Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent télécharger l’aide pour les modules dans le dossier $pshome nouvelle \modules..
- L'aide enregistrée pour chaque module se compose d'un fichier d'informations d'aide (HelpInfo XML) et d'un fichier CAB pour les fichiers d'aide dans chaque culture d'interface utilisateur. Vous n’avez pas besoin d’extraire les fichiers d’aide du fichier CAB. L' `Update-Help` applet de commande extrait les fichiers d’aide, valide le XML, puis installe les fichiers d’aide et le fichier d’informations d’aide dans un sous-dossier spécifique à la langue du dossier du module.
- L' `Save-Help` applet de commande peut enregistrer l’aide pour les modules qui ne sont pas installés sur l’ordinateur. Toutefois, étant donné que les fichiers d’aide sont installés dans le dossier de module, l’applet de commande `Update-Help` peut installer le fichier d’aide mis à jour uniquement pour les modules qui sont installés sur l’ordinateur.
- Si `Save-Help` ne parvient pas à trouver les fichiers d’aide mis à jour pour un module ou ne peut pas trouver les fichiers d’aide mis à jour dans la langue spécifiée, il se poursuit en mode silencieux sans afficher de message d’erreur. Pour voir quels fichiers ont été enregistrés par la commande, spécifiez le paramètre **Verbose** .
- Les modules sont la plus petite unité d'aide actualisable. Vous ne pouvez pas enregistrer l’aide d’une applet de commande particulière, uniquement pour toutes les applets de commande du module. Pour rechercher le module qui contient une applet de commande particulière, utilisez la propriété **modulename** avec l' `Get-Command` applet de commande, par exemple, `(Get-Command \<cmdlet-name\>).ModuleName`
- `Save-Help` prend en charge tous les modules et les composants logiciels enfichables PowerShell Core. Elle ne prend en charge aucun autre composant logiciel enfichable.
- Les `Update-Help` `Save-Help` applets de commande et utilisent les ports suivants pour télécharger les fichiers d’aide : le port 80 pour http et le port 443 pour HTTPS.
- Les `Update-Help` applets de commande et ne `Save-Help` sont pas prises en charge sur environnement de préinstallation Windows (WinPE) (Windows PE).

## LIENS CONNEXES

[Get-Help](Get-Help.md)

[Get-Module](Get-Module.md)

[Update-Help](Update-Help.md)
