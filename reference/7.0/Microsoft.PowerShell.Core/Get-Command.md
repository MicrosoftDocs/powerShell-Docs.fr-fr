---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 12cf373e5e53a45f7cdadd5e3a9f3fec7a7a8bb8
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201949"
---
# Get-Command

## SYNOPSIS
Obtient toutes les commandes.

## SYNTAX

### CmdletSet (par défaut)

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### AllCommandSet

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## Description

L' `Get-Command` applet de commande obtient toutes les commandes qui sont installées sur l’ordinateur, y compris les applets de commande, les alias, les fonctions, les filtres, les scripts et les applications. `Get-Command` Obtient les commandes des modules PowerShell et des commandes qui ont été importées à partir d’autres sessions. Pour obtenir uniquement les commandes qui ont été importées dans la session active, utilisez le paramètre **ListImported** .

Sans paramètres, `Get-Command` obtient toutes les applets de commande, fonctions et alias installés sur l’ordinateur. `Get-Command *` Obtient tous les types de commandes, y compris tous les fichiers non-PowerShell dans la variable d’environnement PATH ( `$env:Path` ), qu’elle répertorie dans le type de commande de l’application.

`Get-Command` qui utilise le nom exact de la commande, sans caractères génériques, importe automatiquement le module qui contient la commande afin que vous puissiez utiliser la commande immédiatement. Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence. Pour plus d’informations, consultez [about_Preference_Variables](About/about_Preference_Variables.md).

`Get-Command` obtient ses données directement à partir du code de commande, contrairement `Get-Help` à, qui obtient ses informations à partir des rubriques d’aide.

À compter de Windows PowerShell 5,0, les résultats de l’applet de commande `Get-Command` affichent une colonne de **version** par défaut. Une nouvelle propriété de **version** a été ajoutée à la classe **CommandInfo** .

## EXEMPLES

### Exemple 1 : recevoir des applets de commande, des fonctions et des alias

Cette commande obtient les applets de commande, fonctions et alias PowerShell installés sur l’ordinateur.

```powershell
Get-Command
```

### Exemple 2 : récupérer des commandes dans la session active

Cette commande utilise le paramètre **ListImported** pour récupérer uniquement les commandes de la session active.

```powershell
Get-Command -ListImported
```

### Exemple 3 : obtenir des applets de commande et les afficher dans l’ordre

Cette commande obtient toutes les applets de commande, les trie par ordre alphabétique en fonction du nom de l'applet de commande, et les affiche ensuite dans des groupes basés sur le nom. Cet affichage peut vous aider à trouver les applets de commande d'une tâche.

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### Exemple 4 : obtenir des commandes dans un module

Cette commande utilise le paramètre **module** pour récupérer les commandes dans les modules Microsoft. PowerShell. Security et Microsoft. PowerShell. Utility.

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### Exemple 5 : obtenir des informations sur une applet de commande

Cette commande obtient des informations sur l’applet de commande `Get-AppLockerPolicy` . Elle importe également le module **AppLocker** , qui ajoute toutes les commandes du module **AppLocker** à la session active.

```powershell
Get-Command Get-AppLockerPolicy
```

Quand un module est importé automatiquement, l’effet est identique à l’utilisation de l’applet de commande Import-Module.
Le module peut ajouter des commandes, des types et des fichiers de mise en forme, puis exécuter des scripts dans la session. Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence. Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

### Exemple 6 : obtenir la syntaxe d’une applet de commande

Cette commande utilise les paramètres **argumentlist** et **Syntax** pour récupérer la syntaxe de l’applet de commande `Get-ChildItem` quand elle est utilisée dans le lecteur Cert :. Le lecteur Cert : est un lecteur PowerShell que le fournisseur de certificats ajoute à la session.

```powershell
Get-Command Get-Childitem -Args Cert: -Syntax
```

Lorsque vous comparez la syntaxe affichée dans la sortie avec la syntaxe qui s’affiche lorsque vous omettez le paramètre **args** ( **argumentlist** ), vous constatez que le **fournisseur de certificats** ajoute un paramètre dynamique, **CodeSigningCert** , à l’applet de commande `Get-ChildItem` .

Pour plus d’informations sur le fournisseur de certificats, consultez [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).

### Exemple 7 : récupération des paramètres dynamiques

La commande de l’exemple utilise la `Get-DynamicParameters` fonction pour récupérer les paramètres dynamiques que le fournisseur de certificats ajoute à l’applet de commande `Get-ChildItem` lorsqu’il est utilisé dans le lecteur Cert :.

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

`Get-DynamicParameters`Dans cet exemple, la fonction obtient les paramètres dynamiques d’une applet de commande. Il s'agit d'une alternative à la méthode utilisée dans l'exemple précédent. Un paramètre dynamique peut être ajouté à une applet de commande par une autre applet de commande ou un fournisseur.

### Exemple 8 : récupération de toutes les commandes de tous les types

Cette commande obtient toutes les commandes de tous les types sur l’ordinateur local, y compris les fichiers exécutables dans les chemins d’accès de la variable d’environnement **path** ( `$env:path` ).

```powershell
Get-Command *
```

Elle retourne un objet **ApplicationInfo** (System.Management.Automation.ApplicationInfo) pour chaque fichier, au lieu d'un objet **FileInfo** (System.IO.FileInfo).

### Exemple 9 : obtenir des applets de commande à l’aide d’un nom et d’un type de paramètre

Cette commande obtient les applets de commande qui ont un paramètre dont le nom comprend auth et dont le type est **AuthenticationMechanism** .

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

Vous pouvez vous servir d'une commande similaire à celle-ci pour rechercher les applets de commande qui vous permettent de spécifier la méthode utilisée pour authentifier l'utilisateur.

Le paramètre **ParameterType** distingue les paramètres qui acceptent une valeur **AuthenticationMechanism** par rapport à ceux qui acceptent un paramètre **AuthenticationLevel** , même quand ils ont des noms similaires.

### Exemple 10 : recevoir un alias

Cet exemple montre comment utiliser l' `Get-Command` applet de commande avec un alias.

```powershell
Get-Command dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

Bien qu’il soit généralement utilisé sur les applets de commande et les fonctions, il `Get-Command` obtient également les scripts, les fonctions, les alias et les fichiers exécutables.

La sortie de la commande montre l'affichage spécial de la valeur de propriété **Name** pour les alias. L'affichage montre l'alias et le nom de commande complet.

### Exemple 11 : récupération de toutes les instances de la commande Notepad

Cet exemple utilise le paramètre **All** de l' `Get-Command` applet de commande pour afficher toutes les instances de la commande « Notepad » sur l’ordinateur local.

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

Le paramètre **All** est utile quand il existe plusieurs commandes portant le même nom dans la session.

À compter de Windows PowerShell 3,0, par défaut, lorsque la session comprend plusieurs commandes portant le même nom, `Get-Command` obtient uniquement la commande qui s’exécute lorsque vous tapez le nom de la commande. Avec le paramètre **All** , `Get-Command` obtient toutes les commandes portant le nom spécifié et les retourne dans l’ordre de priorité d’exécution. Pour exécuter une autre commande que la première de la liste, tapez le chemin d'accès complet de la commande.

Pour plus d’informations sur la priorité des commandes, consultez [about_Command_Precedence](About/about_Command_Precedence.md).

### Exemple 12 : obtenir le nom d’un module qui contient une applet de commande

Cette commande obtient le nom du module dans lequel l’applet de commande `Get-Date` provient.
La commande utilise la propriété **ModuleName** de toutes les commandes.

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

Ce format de commande fonctionne sur les commandes dans les modules PowerShell, même s’ils ne sont pas importés dans la session.

### Exemple 13 : obtenir des applets de commande et des fonctions qui ont un type de sortie

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

Cette commande obtient les applets de commande et les fonctions qui ont un type de sortie, ainsi que le type d'objet qu'elles retournent.

La première partie de la commande obtient toutes les applets de commande.
Un opérateur de pipeline (|) envoie les applets de commande à l’applet de commande `Where-Object` , qui sélectionne uniquement celles dans lesquelles la propriété **OutputType** est remplie.
Un autre opérateur de pipeline envoie les objets d’applet de commande sélectionnés à l’applet de commande `Format-List` , qui affiche le nom et le type de sortie de chaque applet de commande dans une liste.

La propriété **OutputType** d'un objet **CommandInfo** a une valeur non null uniquement quand le code de l'applet de commande définit l'attribut **OutputType** de cette dernière.

### Exemple 14 : obtenir des applets de commande qui prennent un type d’objet spécifique comme entrée

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

Cette commande recherche les applets de commande qui acceptent des objets de carte réseau en entrée. Vous pouvez utiliser ce format de commande pour rechercher les applets de commande qui acceptent le type d'objet retourné par une commande.

La commande utilise la propriété intrinsèque **PSTypeNames** de tous les objets, qui obtient les types décrivant l'objet. Pour obtenir la propriété **PSTypeNames** d'une carte réseau, et non la propriété **PSTypeNames** d'une collection de cartes réseau, la commande utilise une notation de tableau. Ainsi, elle obtient la première carte réseau retournée par l'applet de commande.

### Exemple 15 : obtenir des commandes à l’aide d’une correspondance approximative

Dans cet exemple, le nom de la commande a délibérément une faute de frappe comme « commnd ».
À l’aide du `-UseFuzzyMatching` commutateur, l’applet de commande déterminait que la meilleure correspondance était `Get-Command` suivie par d’autres commandes natives sur le système qui étaient une correspondance similaire.

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## PARAMETERS

### -All

Indique que cette applet de commande obtient toutes les commandes, y compris les commandes du même type qui ont le même nom. Par défaut, `Get-Command` obtient uniquement les commandes qui s’exécutent lorsque vous tapez le nom de la commande.

Pour plus d’informations sur la méthode utilisée par PowerShell pour sélectionner la commande à exécuter quand plusieurs commandes portent le même nom, consultez [about_Command_Precedence](About/about_Command_Precedence.md).
Pour plus d’informations sur les noms de commande qualifiés du module et l’exécution de commandes qui ne s’exécutent pas par défaut en raison d’un conflit de noms, consultez [about_Modules](About/about_Modules.md).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

Dans Windows PowerShell 2,0, `Get-Command` obtient toutes les commandes par défaut.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

Spécifie un tableau d’arguments. Cette applet de commande obtient des informations sur une applet de commande ou une fonction quand elle est utilisée avec les paramètres spécifiés (« arguments »). L'alias d' **ArgumentList** est **Args** .

Pour détecter les paramètres dynamiques disponibles uniquement quand certains autres paramètres sont utilisés, affectez la valeur de **argumentlist** aux paramètres qui déclenchent les paramètres dynamiques.

Pour détecter les paramètres dynamiques qu’un fournisseur ajoute à une applet de commande, définissez la valeur du paramètre **argumentlist** sur un chemin d’accès dans le lecteur du fournisseur, par exemple WSMan :, HKLM : ou CERT :. Lorsque la commande est une applet de commande du fournisseur PowerShell, entrez un seul chemin d’accès dans chaque commande. Les applets de commande du fournisseur retournent uniquement les paramètres dynamiques du premier chemin d’accès de la valeur **argumentlist** . Pour plus d’informations sur les applets de commande du fournisseur, consultez [about_Providers](About/about_Providers.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

Spécifie les types de commandes que cette applet de commande obtient. Entrez un ou plusieurs types de commande. Utilisez **CommandType** ou son alias, **Type** . Par défaut, `Get-Command` obtient toutes les applets de commande, fonctions et alias.

Les valeurs valides pour ce paramètre sont :

- Affecté. Obtient les alias de toutes les commandes PowerShell. Pour plus d’informations, consultez [about_Aliases](About/about_Aliases.md).
- Tout le monde. obtient tous les types de commande. Cette valeur de paramètre est l’équivalent de `Get-Command *` .
- console. Obtient les fichiers non-PowerShell dans les chemins d’accès figurant dans la variable **d’environnement PATH** ($env :p Hemin), y compris les fichiers. txt,. exe et. dll. Pour plus d’informations sur la variable **d’environnement PATH** , consultez about_Environment_Variables.
- PolicySchedule. obtient toutes les applets de commande.
- ExternalScript. obtient tous les fichiers .ps1 des chemins d'accès répertoriés dans la variable d'environnement **Path** ($env:path).
- Filtre et fonction. Obtient tous les filtres et fonctions avancés et simples PowerShell.
- Script. obtient tous les blocs de script. Pour accéder aux scripts PowerShell (fichiers. ps1), utilisez la valeur ExternalScript.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullyQualifiedModule

Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** , décrits dans la section **Notes** du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié dans l’un des formats suivants :

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.

Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** . Les deux paramètres s’excluent mutuellement.

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

### -ListImported

Indique que cette applet de commande obtient uniquement les commandes de la session active.

À compter de PowerShell 3,0, par défaut, `Get-Command` obtient toutes les commandes installées, y compris, mais sans s’y limiter, les commandes de la session active. Dans PowerShell 2,0, elle obtient uniquement les commandes de la session active.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

Spécifie un tableau de modules. Cette applet de commande obtient les commandes provenant des modules spécifiés.
Entrez les noms des modules ou des objets de module.

Ce paramètre accepte les valeurs de chaîne, mais la valeur de ce paramètre peut également être un objet **PSModuleInfo** , tel que les objets `Get-Module` `Import-PSSession` retournés par les applets de commande et.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Name

Spécifie un tableau de noms. Cette applet de commande obtient uniquement les commandes qui portent le nom spécifié. Entrez un nom ou un modèle de nom. Les caractères génériques sont autorisés.

Pour obtenir les commandes qui ont le même nom, utilisez le paramètre **All** . Lorsque deux commandes portent le même nom, par défaut, `Get-Command` obtient la commande qui s’exécute lorsque vous tapez le nom de la commande.

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Substantif

Spécifie un tableau de noms de commandes. Cette applet de commande obtient les commandes, qui incluent des applets de commande, des fonctions et des alias, dont les noms incluent le nom spécifié. Entrez un ou plusieurs noms ou modèles de noms. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ParameterName

Spécifie un tableau de noms de paramètres. Cette applet de commande obtient les commandes de la session qui ont les paramètres spécifiés. Entrez les noms des paramètres ou les alias des paramètres. Les caractères génériques sont pris en charge.

Les paramètres **ParameterName** et **ParameterType** recherchent uniquement les commandes dans la session active.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ParameterType

Spécifie un tableau de noms de paramètres. Cette applet de commande obtient les commandes de la session qui ont des paramètres du type spécifié. Entrez le nom complet ou partiel d'un type de paramètre. Les caractères génériques sont pris en charge.

Les paramètres **ParameterName** et **ParameterType** recherchent uniquement les commandes dans la session active.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowCommandInfo

Indique que cette applet de commande affiche les informations de commande.

Ce paramètre a été introduit dans Windows PowerShell 5,0.

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

### -Syntaxe

Indique que cette applet de commande obtient uniquement les données spécifiées suivantes sur la commande :

- Alias. Obtient le nom standard.
- Applets. Obtient la syntaxe.
- Fonctions et filtres. Obtient la définition de la fonction.
- Scripts et applications ou fichiers. Obtient le chemin d’accès et le nom de fichier.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

Spécifie le nombre de commandes à récupérer. Vous pouvez utiliser ce paramètre pour limiter la sortie d'une commande.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseAbbreviationExpansion

Indique l’utilisation de la correspondance des caractères dans la commande pour rechercher des caractères majuscules dans une commande. Par exemple, `i-psdf` correspond à `Import-PowerShellDataFile` chaque caractère à trouver correspond à un caractère majuscule dans le résultat. En cas d’utilisation de ce type de correspondance, les caractères génériques n’aboutissent à aucune correspondance.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseFuzzyMatching

Indique l’utilisation d’un algorithme de correspondance approximative lors de la recherche de commandes. L’ordre de la sortie provient de la correspondance la plus proche à la plus petite correspondance probable. Les caractères génériques ne doivent pas être utilisés avec la correspondance approximative, car ils tentent de faire correspondre les commandes qui peuvent contenir ces caractères génériques.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verbe

Spécifie un tableau de verbes de commande. Cette applet de commande obtient les commandes, qui incluent des applets de commande, des fonctions et des alias, dont les noms incluent le verbe spécifié. Entrez un ou plusieurs verbes ou modèles de verbes. Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger les noms de commandes vers cette applet de commande.

## SORTIES

### System. Management. Automation. CommandInfo

Cette applet de commande retourne des objets dérivés de la classe **CommandInfo** . Le type d’objet retourné dépend du type de commande que `Get-Command` obtient.

### System. Management. Automation. AliasInfo

Représente des alias.

### System. Management. Automation. ApplicationInfo

Représente des applications et des fichiers.

### System. Management. Automation. CmdletInfo

Représente des applets de commande.

### System. Management. Automation. FunctionInfo

Représente des fonctions et des filtres.

## REMARQUES

* Quand plusieurs commandes portant le même nom sont disponibles pour la session, `Get-Command` retourne la commande qui s’exécute lorsque vous tapez le nom de la commande. Pour obtenir les commandes portant le même nom, listées dans ordre d’exécution, utilisez le paramètre **All** . Pour plus d’informations, consultez [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).
* Quand un module est importé automatiquement, l’effet est identique à l’utilisation de l’applet de commande `Import-Module` . Le module peut ajouter des commandes, des types et des fichiers de mise en forme, puis exécuter des scripts dans la session.
  Pour activer, désactiver et configurer l’importation automatique de modules, utilisez la `$PSModuleAutoLoadingPreference` variable de préférence. Pour plus d’informations, consultez [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

## LIENS CONNEXES

[Export-PSSession](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[Get-Help](Get-Help.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Get-PSDrive](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[about_Command_Precedence](About/about_Command_Precedence.md)
