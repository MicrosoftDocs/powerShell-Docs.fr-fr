---
description: Décrit les fichiers de configuration de session, qui sont utilisés dans une configuration de session (également appelée « point de terminaison ») pour définir l’environnement des sessions qui utilisent la configuration de session.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 113c068022f37b22cbcc5dae61a6a5edf26187d8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206582"
---
# <a name="about-session-configuration-files"></a>À propos des fichiers de configuration de session

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les fichiers de configuration de session, qui sont utilisés dans une configuration de session (également appelée « point de terminaison ») pour définir l’environnement des sessions qui utilisent la configuration de session.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Un « fichier de configuration de session » est un fichier texte avec une extension de nom de fichier. PSSC qui contient une table de hachage des propriétés et des valeurs de configuration de session. Vous pouvez utiliser un fichier de configuration de session pour définir les propriétés d’une configuration de session. Cela définit l’environnement des sessions PowerShell qui utilisent cette configuration de session.

Les fichiers de configuration de session facilitent la création de configurations de session personnalisées sans utiliser d’assemblys ou de scripts C# complexes.

Une « configuration de session » ou un « point de terminaison » est une collection de paramètres d’ordinateur local qui déterminent des éléments tels que les utilisateurs qui peuvent créer des sessions sur l’ordinateur. les commandes que les utilisateurs peuvent exécuter dans ces sessions ; et si la session doit s’exécuter en tant que compte virtuel privilégié. Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](about_Session_Configurations.md).

Les configurations de session ont été introduites dans Windows PowerShell 2,0, et les fichiers de configuration de session ont été introduits dans Windows PowerShell 3,0. Vous devez utiliser Windows PowerShell 3,0 pour inclure un fichier de configuration de session dans une configuration de session. Toutefois, les utilisateurs de Windows PowerShell 2,0 (et versions ultérieures) sont affectés par les paramètres de la configuration de session.

## <a name="creating-custom-sessions"></a>Création de sessions personnalisées

Vous pouvez personnaliser de nombreuses fonctionnalités d’une session PowerShell en spécifiant les propriétés de session dans une configuration de session. Vous pouvez personnaliser une session en écrivant un programme C# qui définit une instance d’exécution personnalisée, ou vous pouvez utiliser un fichier de configuration de session pour définir les propriétés des sessions créées à l’aide de la configuration de session. En règle générale, il est plus facile d’utiliser le fichier de configuration de session que d’écrire un programme C#.

Vous pouvez utiliser un fichier de configuration de session pour créer des éléments tels que des sessions entièrement opérationnelles pour des utilisateurs hautement fiables. sessions verrouillées qui autorisent un accès minimal ; sessions destinées à des particuliers et qui contiennent uniquement les modules requis pour ces tâches ; et les sessions où les utilisateurs non privilégiés peuvent uniquement exécuter des commandes spécifiques en tant que compte privilégié.

En outre, vous pouvez gérer si les utilisateurs de la session peuvent utiliser des éléments de langage PowerShell tels que des blocs de script ou s’ils peuvent uniquement exécuter des commandes. Vous pouvez gérer la version des utilisateurs PowerShell qui peuvent s’exécuter dans la session. gérer les modules importés dans la session ; et gèrent les applets de commande, fonctions et alias que les utilisateurs de session peuvent exécuter. Lorsque vous utilisez le champ RoleDefinitions, vous pouvez fournir aux utilisateurs différentes fonctionnalités dans la session en fonction de l’appartenance à un groupe.

Pour plus d’informations sur RoleDefinitions et sur la définition de cette valeur, consultez la rubrique d’aide de l’applet de commande New-PSRoleCapabilityFile.

## <a name="creating-a-session-configuration-file"></a>Création d’un fichier de configuration de session

Le moyen le plus simple de créer un fichier de configuration de session consiste à utiliser l’applet de commande New-PSSessionConfigurationFile. Cette applet de commande génère un fichier qui utilise la syntaxe et le format corrects, et qui vérifie automatiquement la plupart des valeurs des propriétés du fichier de configuration.

Pour obtenir une description détaillée des propriétés que vous pouvez définir dans un fichier de configuration de session, consultez la rubrique d’aide de l’applet de commande New-PSSessionConfigurationFile.

La commande suivante crée un fichier de configuration de session qui utilise les valeurs par défaut. Le fichier de configuration résultant utilise uniquement les valeurs par défaut, car aucun paramètre autre que le paramètre Path (qui spécifie le chemin d’accès du fichier) n’est inclus :

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

Pour afficher le nouveau fichier de configuration dans votre éditeur de texte par défaut, utilisez la commande suivante :

```powershell
Invoke-Item -Path .\Defaults.pssc
```

Pour créer une configuration de session pour les sessions dans lesquelles l’utilisateur peut exécuter des commandes, mais pas utiliser d’autres éléments du langage PowerShell, tapez :

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

Dans la commande précédente, l’affectation de la valeur nolanguage au paramètre LanguageMode empêche les utilisateurs d’effectuer des opérations telles que l’écriture ou l’exécution de scripts ou l’utilisation de variables.

Pour créer une configuration de session pour les sessions dans lesquelles les utilisateurs peuvent uniquement utiliser les applets de commande obtenir, tapez :

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

Dans l’exemple précédent, la définition du paramètre VisibleCmdlets sur obtenir-* limite les utilisateurs aux applets de commande dont les noms commencent par la valeur de chaîne « obtenir- ».

Pour créer une configuration de session pour les sessions qui s’exécutent sous un compte virtuel privilégié au lieu des informations d’identification de l’utilisateur, tapez :

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

Pour créer une configuration de session pour les sessions dans lesquelles les commandes visibles par l’utilisateur sont spécifiées dans un fichier de capacités de rôle, tapez :

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a>Utilisation d’un fichier de configuration de session

Vous pouvez inclure un fichier de configuration de session lorsque vous créez une configuration de session ou ajoutez vous pouvez ajouter un fichier à la configuration de session ultérieurement.

Pour inclure un fichier de configuration de session lors de la création d’une configuration de session, utilisez le paramètre Path de l’applet de commande Register-PSSessionConfiguration.

Par exemple, la commande suivante utilise le fichier nolanguage. PSSC lorsqu’il crée une configuration de session nolanguage.

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

Lors du démarrage d’une nouvelle session nolanguage, les utilisateurs n’ont accès qu’aux commandes PowerShell.

Pour ajouter un fichier de configuration de session à une configuration de session existante, utilisez l’applet de commande Set-PSSessionConfiguration et le paramètre Path. Cela affecte les nouvelles sessions créées avec la configuration de session spécifiée. Notez que l’applet de commande Set-PSSessionConfiguration modifie la session elle-même et ne modifie pas le fichier de configuration de session.

Par exemple, la commande suivante ajoute le fichier nolanguage. PSSC à la configuration de session LockedDown.

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

Quand les utilisateurs utilisent la configuration de session LockedDown pour créer une session, ils peuvent exécuter des applets de commande, mais ils ne peuvent pas créer ou utiliser des variables, assigner des valeurs ou utiliser d’autres éléments de langage PowerShell.

La commande suivante utilise l’applet de commande New-PSSession pour créer une session sur l’ordinateur Srv01 qui utilise la configuration de session LockedDown, en enregistrant une référence d’objet dans la session dans la variable $s. La liste de contrôle d’accès (ACL) de la configuration de session détermine qui peut l’utiliser pour créer une session.

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

Étant donné que les contraintes nolanguage ont été ajoutées à la configuration de session LockedDown, les utilisateurs dans les sessions LockedDown pourront uniquement exécuter des commandes et des applets de commande PowerShell. Par exemple, les deux commandes suivantes utilisent l’applet de commande Invoke-Command pour exécuter des commandes dans la session référencée dans la variable $s. La première commande, qui exécute l’applet de commande Get-UICulture et n’utilise pas de variables, est réussie. La deuxième commande, qui obtient la valeur de la variable $PSUICulture, échoue.

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a>Modification d'un fichier de configuration de session

Tous les paramètres d’une configuration de session, à l’exception de Runasvirtualaccount doit avoir et RunAsVirtualAccountGroups, peuvent être modifiés en modifiant le fichier de configuration de session utilisé par la configuration de session. Pour ce faire, commencez par Rechercher la copie active du fichier de configuration de session.

Quand vous utilisez un fichier de configuration de session dans une configuration de session, PowerShell crée une copie active du fichier de configuration de session et le stocke dans le \$ \\ répertoire pshome SessionConfig sur l’ordinateur local.

L’emplacement de la copie active d’un fichier de configuration de session est stocké dans la propriété ConfigFilePath de l’objet de configuration de session.

La commande suivante obtient l’emplacement du fichier de configuration de session pour la configuration de session nolanguage.

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

Cette commande retourne un chemin d’accès de fichier similaire à ce qui suit :

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

Vous pouvez modifier le fichier. PSSC dans n’importe quel éditeur de texte. Une fois le fichier enregistré, il est utilisé par les nouvelles sessions qui utilisent la configuration de session.

Si vous avez besoin de modifier les paramètres Runasvirtualaccount doit avoir ou RunAsVirtualAccountGroups, vous devez annuler l’inscription de la configuration de session et enregistrer à nouveau un fichier de configuration de session qui comprend les valeurs modifiées.

## <a name="testing-a-session-configuration-file"></a>Test d’un fichier de configuration de session

Utilisez l’applet de commande Test-PSSessionConfigurationFile pour tester les fichiers de configuration de session modifiés manuellement. Cela est important : si la syntaxe et les valeurs de fichier ne sont pas valides, les utilisateurs ne pourront pas utiliser la configuration de session pour créer une session.

Par exemple, la commande suivante teste le fichier de configuration de session active de la configuration de session nolanguage.

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

Si la syntaxe et les valeurs du fichier de configuration sont valides Test-PSSessionConfigurationFile retourne la valeur true. Si la syntaxe et les valeurs ne sont pas valides, l’applet de commande retourne false.

Vous pouvez utiliser Test-PSSessionConfigurationFile pour tester un fichier de configuration de session, y compris les fichiers créés par l’applet de commande New-PSSessionConfiguration. Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande Test-PSSessionConfigurationFile.

## <a name="removing-a-session-configuration-file"></a>Suppression d’un fichier de configuration de session

Vous ne pouvez pas supprimer un fichier de configuration de session d’une configuration de session.
Toutefois, vous pouvez remplacer le fichier par un nouveau fichier qui utilise les paramètres par défaut. Cela a pour effet d’annuler les paramètres utilisés par le fichier de configuration d’origine.

Pour remplacer un fichier de configuration de session, créez un fichier de configuration de session qui utilise les paramètres par défaut, puis utilisez l’applet de commande Set-PSSessionConfiguration pour remplacer le fichier de configuration de session personnalisé par le nouveau fichier.

Par exemple, les commandes suivantes créent un fichier de configuration de session par défaut, puis remplacent le fichier de configuration de session actif dans la configuration de session nolanguage.

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

Lorsque ces commandes sont terminées, la configuration de session nolanguage fournit en fait une prise en charge linguistique complète (paramètre par défaut) pour toutes les sessions créées avec cette configuration de session.

Affichage des propriétés d’une configuration de session les objets de configuration de session qui représentent des configurations de session à l’aide de fichiers de configuration de session ont des propriétés supplémentaires qui facilitent la découverte et l’analyse de la configuration de session. (Notez que le nom de type indiqué ci-dessous comprend une définition de vue mise en forme.) Vous pouvez afficher les propriétés en exécutant l’applet de commande Get-PSSessionConfiguration et en canalisant les données renvoyées vers l’applet de commande Get-Member :

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

Ces propriétés facilitent la recherche de configurations de session spécifiques.
Par exemple, vous pouvez utiliser la propriété ExecutionPolicy pour rechercher une configuration de session qui prend en charge les sessions avec la stratégie d’exécution RemoteSigned.
Notez que, étant donné que la propriété ExecutionPolicy existe uniquement sur les sessions qui utilisent des fichiers de configuration de session, la commande peut ne pas retourner toutes les configurations de session éligibles.

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

La commande suivante obtient les configurations de session dans lesquelles le nom_d’emprunt est l’administrateur Exchange.

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

Pour afficher des informations sur les définitions de rôles associées à une configuration, utilisez l’applet de commande Get-PSSessionCapability. Cette applet de commande vous permet de déterminer les commandes et l’environnement disponibles pour des utilisateurs spécifiques dans des points de terminaison spécifiques.

## <a name="notes"></a>REMARQUES

Les configurations de session prennent également en charge un type de session connu sous le nom de session « vide ». Un type de session vide vous permet de créer des sessions personnalisées avec des commandes sélectionnées. Si vous n’ajoutez pas de modules, de fonctions ou de scripts à une session vide, la session est limitée aux expressions et peut ne pas être utilisée de façon pratique. La propriété SessionType vous indique si vous utilisez une session vide ou non.

## <a name="see-also"></a>VOIR AUSSI

[about_Session_Configurations](about_Session_Configurations.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[Get-PSSessionCapability](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[New-PSRoleCapabilityFile](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)
