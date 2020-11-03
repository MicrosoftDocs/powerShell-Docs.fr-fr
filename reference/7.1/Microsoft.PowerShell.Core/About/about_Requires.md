---
description: Empêche un script de s’exécuter sans les éléments requis.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: 5c4eb4e272f214ffe906fd1a3f1c127824183d4a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208258"
---
# <a name="about-requires"></a>À propos de requires

## <a name="short-description"></a>Description courte
Empêche un script de s’exécuter sans les éléments requis.

## <a name="long-description"></a>Description longue

L' `#Requires` instruction empêche l’exécution d’un script, sauf si la version, les modules (et la version), les composants logiciels enfichables (et la version) et les composants logiciels enfichables de l’édition de PowerShell sont satisfaits. Si les conditions préalables ne sont pas remplies, PowerShell n’exécute pas le script.

### <a name="syntax"></a>Syntaxe

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

Pour plus d’informations sur la syntaxe, consultez [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).

### <a name="rules-for-use"></a>Règles d’utilisation

Un script peut inclure plusieurs `#Requires` instructions. Les `#Requires` instructions peuvent apparaître sur n’importe quelle ligne dans un script.

Le fait de placer une `#Requires` instruction à l’intérieur d’une fonction ne limite pas son étendue. Toutes les `#Requires` instructions sont toujours appliquées globalement et doivent être respectées avant que le script puisse s’exécuter.

> [!WARNING]
> Bien qu’une `#Requires` instruction puisse apparaître sur n’importe quelle ligne d’un script, sa position dans un script n’affecte pas la séquence de son application. L’état global `#Requires` que l’instruction présente doit être respecté avant l’exécution du script.

Exemple :

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

Vous pouvez penser que le code ci-dessus ne doit pas s’exécuter parce que le module requis a été supprimé avant l' `#Requires` instruction. Toutefois, l' `#Requires` État devait être respecté pour que le script puisse même s’exécuter. La première ligne du script n’a pas validé l’État requis.

### <a name="parameters"></a>Paramètres

#### <a name="-assembly-assembly-path--net-assembly-specification"></a>-Assembly \<Assembly path> |\<.NET assembly specification>

Spécifie le chemin d’accès au fichier DLL de l’assembly ou un nom d’assembly .NET. Le paramètre **assembly** a été introduit dans PowerShell 5,0. Pour plus d’informations sur les assemblys .NET, consultez [noms d’assembly](/dotnet/standard/assembly/names).

Par exemple :

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a>-Version \<N\> [. \<n\> ]

Spécifie la version minimale de PowerShell requise par le script. Entrez un numéro de version principale et un numéro de version mineure facultatif.

Par exemple :

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a>-PSSnapin \<PSSnapin-Name\> [-version \<N\> [. \<n\> ]]

Spécifie un composant logiciel enfichable PowerShell requis par le script. Entrez le nom du composant logiciel enfichable et un numéro de version facultatif.

Par exemple :

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a>-Modules \<Module-Name\> |\<Hashtable\>

Spécifie les modules PowerShell requis par le script. Entrez le nom du module et un numéro de version facultatif.

Si les modules requis ne se trouvent pas dans la session active, PowerShell les importe.
Si les modules ne peuvent pas être importés, PowerShell lève une erreur d’arrêt.

Pour chaque module, tapez le nom du module ( \<String\> ) ou une table de hachage. La valeur peut être une combinaison de chaînes et de tables de hachage. La table de hachage a les clés suivantes.

- `ModuleName` - **Obligatoire** Spécifie le nom du module.
- `GUID` - **Facultatif** Spécifie le GUID du module.
- Il est également **nécessaire** de spécifier l’une des trois clés ci-dessous. Ces clés ne peuvent pas être utilisées ensemble.
  - `ModuleVersion` -Spécifie une version minimale acceptable du module.
  - `RequiredVersion` -Spécifie une version exacte et obligatoire du module.
  - `MaximumVersion` -Spécifie la version maximale acceptable du module.

> [!NOTE]
> `RequiredVersion` a été ajouté dans Windows PowerShell 5,0.
> `MaximumVersion` a été ajouté dans Windows PowerShell 5,1.

Par exemple :

Exiger que `AzureRM.Netcore` (version `0.12.0` ou ultérieure) soit installé.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

Exiger que `AzureRM.Netcore` ( **seule** version `0.12.0` ) soit installé.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

Requiert l' `AzureRM.Netcore` installation de (version `0.12.0` ou inférieure).

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

Exiger que toutes les versions de `AzureRM.Netcore` et de `PowerShellGet` soient installées.

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

Lorsque vous utilisez la `RequiredVersion` clé, vérifiez que votre chaîne de version correspond exactement à la chaîne de version dont vous avez besoin.

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

L’exemple suivant échoue car **0,12** ne correspond pas exactement à **0.12.0** .

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a>-PSEdition \<PSEdition-Name\>

Spécifie une édition PowerShell dont le script a besoin. Les valeurs valides sont **Core** pour PowerShell Core et **Desktop** pour Windows PowerShell.

Par exemple :

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a>-ShellId

Spécifie l’interpréteur de commandes requis par le script. Entrez l’ID de l’interpréteur de commandes. Si vous utilisez le paramètre **ShellId** , vous devez également inclure le paramètre **PSSnapin** .
Vous pouvez rechercher le **ShellId** en cours en interrogeant la `$ShellId` variable automatique.

Par exemple :

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> Ce paramètre est destiné à être utilisé dans les mini-shells, qui ont été dépréciés.

#### <a name="-runasadministrator"></a>-RunAsAdministrator

Lorsque ce paramètre de commutateur est ajouté à votre `#Requires` instruction, il spécifie que la session PowerShell dans laquelle vous exécutez le script doit être démarrée avec des droits d’utilisateur élevés. Le paramètre **RunAsAdministrator** est ignoré sur un système d’exploitation autre que Windows. Le paramètre **RunAsAdministrator** a été introduit dans PowerShell 4,0.

Par exemple :

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a>Exemples

Le script suivant comporte deux `#Requires` instructions. Si les exigences spécifiées dans les deux instructions ne sont pas satisfaites, le script ne s’exécute pas. Chaque `#Requires` instruction doit être le premier élément d’une ligne :

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Language_Keywords](about_Language_Keywords.md)

