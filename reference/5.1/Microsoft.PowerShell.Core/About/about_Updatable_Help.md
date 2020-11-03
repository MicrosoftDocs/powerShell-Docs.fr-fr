---
description: Décrit le système d’aide pouvant être mis à jour dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: 03425aef93f3d4bbb06aee87d30f4a441c0b2d86
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207905"
---
# <a name="about-updatable-help"></a>À propos de l’aide actualisable

## <a name="short-description"></a>Description courte
Décrit le système d’aide pouvant être mis à jour dans PowerShell.

## <a name="long-description"></a>Description longue

PowerShell offre différentes façons d’accéder aux rubriques d’aide les plus récentes pour les applets de commande et les concepts PowerShell.

Le système d’aide actualisable, introduit dans PowerShell 3,0, est conçu pour vous assurer que vous disposez toujours des dernières rubriques d’aide sur votre ordinateur local afin de pouvoir les lire sur la ligne de commande. Il facilite le téléchargement et l’installation des fichiers d’aide et leur mise à jour chaque fois que des fichiers d’aide plus récents sont disponibles.

Pour fournir une aide mise à jour pour plusieurs ordinateurs dans une entreprise et pour les ordinateurs qui n’ont pas accès à Internet, l’aide actualisable vous permet de télécharger les fichiers d’aide dans un répertoire de système de fichiers ou un partage de fichiers, puis d’installer les fichiers d’aide à partir du partage de fichiers.

Dans PowerShell 4,0, la propriété **HelpInfoUri** est conservée sur la communication à distance Windows PowerShell, ce qui permet `Save-Help` à de fonctionner pour les modules qui sont installés sur un ordinateur distant, mais qui ne sont pas nécessairement installés sur l’ordinateur local. Vous pouvez enregistrer un objet **PSModuleInfo** sur un disque ou sur un support amovible (tel qu’un lecteur USB) en exécutant `Export-Clixml` sur un ordinateur qui n’a pas accès à Internet, en important l’objet **PSModuleInfo** sur un ordinateur qui a accès à Internet, puis en cours `Save-Help` d’exécution sur l’objet **PSModuleInfo** . L’aide enregistrée peut être copiée sur l’ordinateur distant, déconnecté à l’aide d’un support amovible, puis installé en exécutant `Update-Help` . Ces améliorations de la `Save-Help` fonctionnalité vous permettent d’installer l’aide sur les ordinateurs qui ne disposent d’aucun accès réseau. Pour obtenir un exemple d’utilisation de la nouvelle `Save-Help` fonctionnalité, consultez [Comment mettre à jour l’aide d’un partage de fichiers](#how-to-update-help-from-a-file-share) dans cette rubrique.

L’aide actualisable prend également en charge l’accès en ligne aux dernières rubriques d’aide et à l’aide de base pour les applets de commande, même lorsqu’il n’y a aucun fichier d’aide sur l’ordinateur.

PowerShell 3,0 n’est pas fourni avec les fichiers d’aide. Vous pouvez utiliser la fonctionnalité d’aide actualisable pour installer les fichiers d’aide de toutes les commandes incluses par défaut dans PowerShell et pour tous les modules Windows.

## <a name="updatable-help-cmdlets"></a>Applets de commande d’aide actualisables

- `Update-Help`: Télécharge les fichiers d’aide les plus récents à partir d’Internet ou d’un partage de fichiers, puis les installe sur l’ordinateur local.

- `Save-Help`: Télécharge les fichiers d’aide les plus récents à partir d’Internet et les enregistre dans un répertoire de système de fichiers ou un partage de fichiers. Pour installer les fichiers d’aide sur les ordinateurs, utilisez `Update-Help` .

- `Get-Help`: Affiche les rubriques d’aide sur la ligne de commande. Obtient de l’aide à partir des fichiers d’aide sur l’ordinateur. Affiche l’aide générée automatiquement pour les applets de commande et les fonctions qui n’ont pas de fichiers d’aide. Ouvre les rubriques d’aide en ligne pour les applets de commande, les fonctions, les scripts et les flux de travail dans votre navigateur Internet par défaut.

## <a name="update-help-in-the-powershell-ise"></a>Mettre à jour l’aide dans PowerShell ISE

Vous pouvez également mettre à jour l’aide à l’aide de l’option **mettre à jour l’aide PowerShell** dans le menu aide de l’environnement d’écriture de scripts intégré de PowerShell (ISE).

L’élément **d’aide PowerShell Update** exécute une `Update-Help` commande sans paramètres.

## <a name="auto-generated-help-help-without-help-files"></a>Aide générée automatiquement : aide sans fichiers d’aide

Si vous ne disposez pas du fichier d’aide d’une applet de commande, d’une fonction ou d’un flux de travail sur l’ordinateur, l’applet de commande `Get-Help` affiche l’aide générée automatiquement et vous invite à télécharger les fichiers d’aide ou à les lire en ligne.

L’aide générée automatiquement comprend la syntaxe et les alias, ainsi que des remarques qui expliquent comment utiliser les applets de commande de l’aide actualisable et accéder aux rubriques d’aide en ligne.

Par exemple, la commande suivante obtient l’aide de base pour l’applet de commande `Get-Culture` . La sortie indique l' `Get-Help` affichage lorsqu’il n’y a aucun fichier d’aide sur l’ordinateur.

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a>Fichiers d’aide pour les modules

La plus petite unité d’aide actualisable est l’aide d’un module. L’aide du module comprend de l’aide sur toutes les applets de commande, fonctions, flux de travail, fournisseurs, scripts et concepts d’un module. Vous pouvez mettre à jour l’aide de tous les modules installés sur l’ordinateur, même s’ils ne sont pas importés dans la session active.

Vous pouvez mettre à jour l’aide pour l’ensemble du module, mais vous ne pouvez pas mettre à jour l’aide pour les applets de commande individuelles.

Pour rechercher le module qui contient une applet de commande particulière, utilisez le format de commande suivant :

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

Par exemple, pour rechercher le module qui contient l' `Set-ExecutionPolicy` applet de commande, tapez :

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

Pour mettre à jour l’aide d’un module particulier, tapez :

```powershell
Update-Help -Module <ModuleName>
```

Par exemple, pour mettre à jour l’aide pour le module qui contient l’applet de commande Set-ExecutionPolicy, tapez :

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a>Autorisations pour l’aide actualisable

Pour mettre à jour l’aide pour les modules de l’annuaire `$pshome/Modules` , vous devez être membre du groupe Administrateurs sur l’ordinateur.

Si vous n’êtes pas membre du groupe administrateurs, vous ne pouvez pas mettre à jour l’aide pour ces modules. Toutefois, si vous avez accès à Internet, vous pouvez afficher l’aide en ligne.

La mise à jour de l’aide pour les modules dans le `$home/Documents/PowerShell/Modules` ou les modules dans d’autres sous-répertoires du `$home` Répertoire ne nécessite pas d’autorisations spéciales.

Les `Update-Help` applets de commande et `Save-Help` ont un paramètre **UseDefaultCredentials** qui fournit les informations d’identification explicites de l’utilisateur actuel. Ce paramètre est conçu pour accéder à des emplacements Internet sécurisés.

Les `Update-Help` `Save-Help` applets de commande et possèdent également un paramètre **Credential** qui vous permet d’exécuter la commande sur un ordinateur distant et d’accéder à un partage de fichiers sur un troisième ordinateur. Le paramètre **Credential** est valide uniquement lorsque vous utilisez les paramètres SourcePath ou **LiteralPath** de `Update-Help` et les paramètres **DestinationPath** ou **LiteralPath** de `Save-Help` .

## <a name="how-to-install-and-update-help-files"></a>Procédure d’installation et de mise à jour des fichiers d’aide

Pour télécharger et installer les fichiers d’aide pour la première fois, ou pour mettre à jour les fichiers d’aide sur votre ordinateur, utilisez l’applet de commande `Update-Help` .

L' `Update-Help` applet de commande effectue tout le travail pour vous, y compris les tâches suivantes.

- Détermine les modules qui prennent en charge l’aide actualisable.
- Recherche l’emplacement Internet où chaque module stocke ses fichiers d’aide pouvant être mis à jour.
- Compare les fichiers d’aide pour chaque module de votre ordinateur avec les derniers fichiers d’aide disponibles pour chaque module.
- Télécharge les nouveaux fichiers à partir d’Internet.
- Désencapsule le package du fichier d’aide.
- Vérifie que les fichiers sont des fichiers d’aide valides.
- Installe les fichiers d’aide dans le sous-répertoire spécifique à la langue du répertoire du module.

Pour accéder aux nouvelles rubriques d’aide, utilisez l’applet de commande `Get-Help` . Vous n’avez pas besoin de redémarrer PowerShell.

Pour installer ou mettre à jour l’aide de tous les modules sur l’ordinateur qui prend en charge l’aide actualisable, tapez :

```powershell
Update-Help
```

Pour mettre à jour l’aide pour des modules particuliers, ajoutez le paramètre **module** de `Update-Help` . Les caractères génériques sont autorisés dans le nom du module.

Par exemple, pour mettre à jour l’aide du module ServerManager, tapez :

```powershell
Update-Help -Module ServerManager
```

Sans paramètres, `Update-Help` met à jour l’aide de tous les modules de la session et de tous les modules installés qui prennent en charge l’aide actualisable. Pour être inclus, les modules doivent être installés dans les répertoires qui sont répertoriés dans la valeur de la variable d’environnement PSModulePath. Il s’agit également de modules qui sont retournés par une commande « obtenir-Help-ListAvailable ».

Si la valeur du paramètre **module** est `*` (All), `Update-Help` tente de mettre à jour l’aide de tous les modules installés, y compris les modules qui ne prennent pas en charge l’aide actualisable. Cette commande génère généralement de nombreuses Erreurs lorsque l’applet de commande rencontre des modules qui ne prennent pas en charge l’aide actualisable.

## <a name="how-to-update-help-from-a-file-share"></a>Comment mettre à jour l’aide d’un partage de fichiers

Pour prendre en charge les ordinateurs qui ne sont pas connectés à Internet, ou pour contrôler ou simplifier la mise à jour de l’aide dans une entreprise, utilisez l’applet de commande `Save-Help` . L' `Save-Help` applet de commande télécharge les fichiers d’aide à partir d’Internet et les enregistre dans un répertoire de système de fichiers que vous spécifiez.

`Save-Help` compare les fichiers d’aide dans le répertoire spécifié aux fichiers d’aide les plus récents qui sont disponibles pour chaque module. Si le répertoire n’a pas de fichiers d’aide ou si des fichiers d’aide plus récents sont disponibles pour le module, l’applet de commande `Save-Help` télécharge les nouveaux fichiers à partir d’Internet. Toutefois, il ne désencapsule pas ou n’installe pas les fichiers d’aide.

Pour installer ou mettre à jour les fichiers d’aide sur un ordinateur à partir de fichiers d’aide enregistrés dans un répertoire FileSystem, utilisez le paramètre **SourcePath** de l’applet de commande `Update-Help` . L' `Update-Help` applet de commande identifie les fichiers d’aide les plus récents, les désencapsule et les valide et les installe dans les sous-répertoires spécifiques au langage des répertoires du module.

Par exemple, pour enregistrer l’aide de tous les modules installés dans le `\\Server\Share` répertoire, tapez :

```powershell
Save-Help -DestinationPath \\Server\Share
```

Ensuite, pour mettre à jour l’aide à partir de l' `\\Server\Share` annuaire, tapez :

```powershell
Update-Help -SourcePath \\Server\Share
```

Les exemples suivants illustrent l’utilisation de `Save-Help` pour enregistrer l’aide des modules qui ne sont pas installés sur l’ordinateur local. Dans cet exemple, l’administrateur s’exécute `Save-Help` pour enregistrer l’aide du module dhcpserver à partir d’un ordinateur client connecté à Internet, sans installer le module dhcpserver ou le rôle serveur DHCP sur l’ordinateur local.

Option 1 : exécutez `Invoke-Command` pour obtenir l’objet **PSModuleInfo** pour le module distant, enregistrez-le dans une variable `$m` ,, puis exécutez `Save-Help` sur l’objet **PSModuleInfo** en spécifiant la variable `$m` comme nom de module.

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

Option 2 : Ouvrez une session PSSession ciblée sur l’ordinateur qui exécute le module de serveur DHCP, pour obtenir l’objet **PSModuleInfo** pour le module, enregistrez-le dans une variable `$m` , puis exécutez `Save-Help` sur l’objet qui est enregistré dans la `$m` variable.

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

Option 3 : Ouvrez une session CIM, ciblée sur l’ordinateur qui exécute le module de serveur DHCP, pour obtenir l’objet **PSModuleInfo** pour le module, enregistrez-la dans une variable `$m` , puis exécutez `Save-Help` sur l’objet qui est enregistré dans la `$m` variable.

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

Dans l’exemple suivant, l’administrateur installe l’aide pour le module serveur DHCP sur un ordinateur qui ne dispose pas d’un accès réseau.

Tout d’abord, exécutez `Export-Clixml` pour exporter l’objet **PSModuleInfo** dans un dossier partagé ou sur un support amovible.

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

Ensuite, transférez le support amovible vers un ordinateur qui a accès à Internet, puis importez l’objet **PSModuleInfo** avec `Import-Clixml` . Exécutez `Save-Help` pour enregistrer l’aide de l’objet **PSModuleInfo** du module DhcpServer importé.

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

Enfin, transférez le support amovible sur l’ordinateur qui ne dispose pas d’un accès réseau, puis installez l’aide en exécutant `Update-Help` .

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

Sans paramètres, `Save-Help` télécharge l’aide pour tous les modules de la session et pour tous les modules installés qui prennent en charge l’aide actualisable. Pour être inclus, les modules doivent être installés dans des répertoires qui sont répertoriés dans la valeur de la `$env:PSModulePath` variable d’environnement, sur l’ordinateur local ou sur un ordinateur distant pour lequel vous souhaitez enregistrer l’aide. Il s’agit également de modules qui sont retournés par l’exécution d’une `Get-Help -ListAvailable` commande.

## <a name="how-to-update-help-files-in-different-languages"></a>Comment mettre à jour les fichiers d’aide dans différentes langues

Par défaut, les `Update-Help` applets de commande et `Save-Help` téléchargent l’aide dans la culture et la langue de l’interface utilisateur définies pour Windows sur l’ordinateur local. Si les fichiers d’aide pour les modules spécifiés ne sont pas disponibles dans la culture d’interface utilisateur locale, `Update-Help` et `Save-Help` utilisent les règles de secours de la langue Windows pour rechercher le meilleur langage pris en charge.

Toutefois, vous pouvez utiliser les paramètres **UICulture** des `Update-Help` applets de commande et `Save-Help` pour télécharger et installer les fichiers d’aide dans toutes les cultures d’interface utilisateur dans lesquelles ils sont disponibles.

Par exemple, pour enregistrer les fichiers d’aide les plus récents pour tous les modules de la session en japonais (ja-JP) et français (fr-FR), tapez :

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

Si les fichiers d’aide pour les modules ne sont pas disponibles dans les langues que vous avez spécifiées, les `Update-Help` applets de commande et `Save-Help` retournent un message d’erreur qui répertorie les langues dans lesquelles l’aide pour chaque module est disponible pour vous permettre de choisir celle qui répond le mieux à vos besoins.

> [!NOTE]
> Actuellement, le contenu de l’aide actualisable est publié uniquement en anglais (en-US).

## <a name="how-to-use-online-help"></a>Comment utiliser l’aide en ligne

Si vous ne pouvez pas ou choisissez de ne pas mettre à jour les fichiers d’aide sur votre ordinateur local, vous pouvez toujours obtenir les fichiers d’aide les plus récents en ligne.

Pour ouvrir la rubrique d’aide en ligne pour une applet de commande ou une fonction, utilisez le paramètre **Online** de l’applet de commande `Get-Help` .

Par exemple, la commande suivante ouvre la rubrique d’aide en ligne de l' `Get-Job` applet de commande dans votre navigateur Internet par défaut :

```powershell
Get-Help Get-Job -Online
```

Pour obtenir de l’aide en ligne sur un script, utilisez le paramètre **Online** et le chemin d’accès complet au script.

Le paramètre **Online** ne fonctionne pas avec à propos des rubriques. Pour voir les rubriques about pour PowerShell, y compris les rubriques d’aide sur le langage PowerShell, consultez les [rubriques relatives à PowerShell](about.md).

## <a name="how-to-minimize-or-prevent-internet-downloads"></a>Comment réduire ou empêcher les téléchargements Internet

Pour réduire les téléchargements Internet et fournir une aide actualisable aux utilisateurs qui ne sont pas connectés à Internet, utilisez l’applet de commande `Save-Help` . Téléchargez l’aide à partir d’Internet et enregistrez-la sur un partage réseau. Ensuite, créez un paramètre de stratégie de groupe ou une tâche planifiée qui exécute une `Update-Help` commande sur tous les ordinateurs. Définissez la valeur du paramètre **SourcePath** de l’applet de commande `Update-Help` sur le partage réseau.

Pour empêcher les utilisateurs qui disposent d’un accès à Internet de télécharger l’aide pouvant être mise à jour à partir d’Internet, utilisez le paramètre **définir le chemin source par défaut pour Update-help** stratégie de groupe.

Cette stratégie de groupe paramètre ajoute implicitement le paramètre **SourcePath** , avec l’emplacement du système de fichiers que vous spécifiez, à chaque `Update-Help` commande sur chaque ordinateur affecté. Les utilisateurs peuvent utiliser le paramètre **SourcePath** explicitement pour spécifier un emplacement de système de fichiers différent, mais ils ne peuvent pas exclure le paramètre **SourcePath** et télécharger l’aide à partir d’Internet.

> [!NOTE]
> Le paramètre **définir le chemin d’accès source par défaut pour la stratégie de groupe mise à jour-aide** apparaît sous **Configuration ordinateur** et **Configuration utilisateur** . Toutefois, seul le paramètre de stratégie sous **Configuration ordinateur** est effectif. Le paramètre de stratégie sous **Configuration utilisateur** est ignoré.

Pour plus d’informations, consultez [about_Group_Policy_Settings](about_Group_Policy_Settings.md).

## <a name="how-to-update-help-for-non-standard-modules"></a>Comment mettre à jour l’aide pour les modules non standard

Pour mettre à jour ou enregistrer l’aide d’un module qui n’est pas retourné par le paramètre **listAvailable** de l' `Get-Module` applet de commande, importez le module dans la session active avant d’exécuter une `Update-Help` `Save-Help` commande ou. Sur un ordinateur distant, avant d’exécuter la `Save-Help` commande, importez le module dans la session active, ou le `Invoke-Command` bloc de script, qui est connecté à l’ordinateur distant.

Quand le module est dans la session active, exécutez les `Update-Help` applets de commande ou `Save-Help` sans paramètres, ou utilisez le paramètre **module** pour spécifier le nom du module.

Les paramètres de **module** des `Update-Help` applets de commande et `Save-Help` acceptent uniquement un nom de module. Ils n’acceptent pas le chemin d’accès à un fichier de module.

Utilisez cette technique pour mettre à jour ou enregistrer l’aide des modules qui ne sont pas retournés par le paramètre **listAvailable** de l’applet de commande `Get-Module` , par exemple un module installé dans un emplacement qui n’est pas listé dans la `$env:PSModulePath` variable d’environnement, ou un module qui n’est pas correctement construit (le répertoire du module ne contient pas au moins un fichier dont le nom de la valeur est identique

## <a name="how-to-support-updatable-help"></a>Comment prendre en charge l’aide actualisable

Si vous créez un module, vous pouvez prendre en charge l’aide en ligne et l’aide actualisable pour vos modules. Pour plus d’informations, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/help/supporting-updatable-help) et prise en charge de l' [aide en ligne](/powershell/scripting/developer/module/supporting-online-help) dans le Microsoft docs.

Aide actualisable non disponible pour les composants logiciels enfichables PowerShell ou l’aide basée sur des commentaires.

## <a name="remarks"></a>Notes

Les `Update-Help` applets de commande et ne `Save-Help` sont pas prises en charge sur environnement de préinstallation Windows (WinPE) (Windows PE).

## <a name="see-also"></a>Voir aussi

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
