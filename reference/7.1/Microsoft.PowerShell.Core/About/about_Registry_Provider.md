---
description: Registre
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur Registry
ms.openlocfilehash: e97fc607c456909dc0abdb50cb7dd5b5847998a0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208085"
---
# <a name="registry-provider"></a>Fournisseur de Registre

## <a name="provider-name"></a>Nom du fournisseur

Registre

## <a name="drives"></a>Lecteurs

`HKLM:`, `HKCU:`

## <a name="capabilities"></a>Fonctionnalités

**ShouldProcess** , **UseTransactions**

## <a name="short-description"></a>Description courte

Permet d’accéder aux clés, aux entrées et aux valeurs de Registre dans PowerShell.

## <a name="detailed-description"></a>Description détaillée

Le fournisseur **Registry** PowerShell vous permet d’extraire, d’ajouter, de modifier, d’effacer et de supprimer des clés, des entrées et des valeurs de Registre dans PowerShell.

Les lecteurs **du Registre** sont un espace de noms hiérarchique contenant les clés de Registre et les sous-clés de votre ordinateur. Les entrées et les valeurs de Registre ne sont pas des composants de cette hiérarchie. Ce sont en fait des propriétés de chacune des clés.

Le fournisseur **Registry** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a>Types exposés par ce fournisseur

Les clés de Registre sont représentées en tant qu’instances de la classe [Microsoft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) . Les entrées de Registre sont représentées en tant qu’instances de la classe [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .

## <a name="navigating-the-registry-drives"></a>Navigation dans les lecteurs de Registre

Le fournisseur de **Registre** expose son magasin de données comme deux lecteurs par défaut. L’emplacement du Registre HKEY_LOCAL_MACHINE est mappé au `HKLM:` lecteur et HKEY_CURRENT_USER est mappé au `HKCU:` lecteur. Pour utiliser le registre, vous pouvez modifier votre emplacement sur le lecteur à l' `HKLM:` aide de la commande suivante.

```powershell
Set-Location HKLM:
```

Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur. Par exemple, entrez :

```powershell
Set-Location C:
```

Vous pouvez également utiliser le fournisseur de **Registre** à partir de n’importe quel autre lecteur PowerShell. Pour faire référence à une clé de Registre à partir d’un autre emplacement, utilisez le nom du lecteur ( `HKLM:` , `HKCU:` ) dans le chemin d’accès. Utilisez une barre oblique inverse ( \\ ) ou une barre oblique (/) pour indiquer un niveau du lecteur de **registre** .

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> PowerShell utilise des alias pour vous permettre de travailler de façon familière avec les chemins d’accès des fournisseurs. Les commandes telles que `dir` et `ls` sont maintenant des alias pour [obtenir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` est un alias pour [set-location](xref:Microsoft.PowerShell.Management.Set-Location)et `pwd` est un alias pour la commande Set- [location](xref:Microsoft.PowerShell.Management.Get-Location).

Ce dernier exemple montre une autre syntaxe de chemin d’accès que vous pouvez utiliser pour naviguer dans le fournisseur de **Registre** . Cette syntaxe utilise le nom du fournisseur, suivi de deux signes deux-points `::` . Cette syntaxe vous permet d’utiliser le nom de la ruche complète au lieu du nom du lecteur mappé `HKLM` .

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a>Affichage du contenu des clés de Registre

Le Registre est divisé en clés, sous-clés et entrées. Pour plus d’informations sur la structure du Registre, consultez [structure du Registre](/windows/desktop/sysinfo/structure-of-the-registry).

Dans un lecteur de **Registre** , chaque clé est un conteneur. Une clé peut contenir un nombre quelconque de clés. Une clé de Registre qui a une clé parente est appelée une sous-clé. Vous pouvez utiliser `Get-ChildItem` pour afficher les clés de Registre et `Set-Location` accéder à un chemin d’accès de clé.

Les valeurs de Registre sont des attributs d’une clé de registre. Dans le lecteur de **Registre** , elles sont appelées **propriétés d’élément** . Une clé de Registre peut avoir à la fois des clés enfants et des propriétés d’élément.

Dans cet exemple, la différence entre `Get-Item` et `Get-ChildItem` est indiquée. Lorsque vous utilisez `Get-Item` sur la clé de Registre « Spooler », vous pouvez afficher ses propriétés.

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

Chaque clé de Registre peut également avoir des sous-clés. Lorsque vous utilisez `Get-Item` sur une clé de Registre, les sous-clés ne sont pas affichées. L' `Get-ChildItem` applet de commande affiche les éléments enfants de la clé « Spooler », y compris les propriétés de chaque sous-clé. Les propriétés de clés parentes ne sont pas affichées lors de l’utilisation de `Get-ChildItem` .

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

L' `Get-Item` applet de commande peut également être utilisée à l’emplacement actuel. L’exemple suivant permet d’accéder à la clé de Registre « spooler » et d’obtenir les propriétés de l’élément.
Le point `.` est utilisé pour indiquer l’emplacement actuel.

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

Pour plus d’informations sur les applets de commande décrites dans cette section, consultez les articles suivants.

-[Recevoir un élément](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Acquérir-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

## <a name="viewing-registry-key-values"></a>Affichage des valeurs de clés de Registre

Les valeurs de clé de Registre sont stockées en tant que propriétés de chaque clé de registre. L' `Get-ItemProperty` applet de commande affiche les propriétés de clé de registre en utilisant le nom que vous spécifiez. Le résultat est un **PSCustomObject** contenant les propriétés que vous spécifiez.

L’exemple suivant utilise l' `Get-ItemProperty` applet de commande pour afficher toutes les propriétés. Le stockage de l’objet résultant dans une variable vous permet d’accéder à la valeur de propriété souhaitée.

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

La spécification d’une valeur pour le `-Name` paramètre sélectionne les propriétés que vous spécifiez et retourne **PSCustomObject** .  L’exemple suivant illustre la différence de sortie lorsque vous utilisez le `-Name` paramètre.

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

À compter de PowerShell 5,0, l' `Get-ItemPropertyValue` applet de commande retourne uniquement la valeur de la propriété que vous spécifiez.

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.

- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Get-ItemPropertyValue](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a>Modification des valeurs de clés de Registre

L' `Set-ItemProperty` applet de commande définit les attributs des clés de registre. L’exemple suivant utilise `Set-ItemProperty` pour changer le type de démarrage du service Spooler en Manual. L’exemple rétablit la valeur *automatique* **à l’aide** de l’applet de commande `Set-Service` .

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

Chaque clé de registre a une valeur *par défaut* . Vous pouvez modifier la valeur *par défaut* d’une clé de Registre à l’aide de `Set-Item` ou de `Set-ItemProperty` .

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a>Création de clés et de valeurs de Registre

L' `New-Item` applet de commande crée des clés de Registre avec un nom que vous fournissez.
Vous pouvez également utiliser la `mkdir` fonction, qui appelle l’applet de commande en `New-Item` interne.

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

Vous pouvez utiliser l' `New-ItemProperty` applet de commande pour créer des valeurs dans une clé de registre que vous spécifiez. L’exemple suivant crée une nouvelle valeur DWORD sur la clé de Registre ContosoCompany.

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> Consultez la section paramètres dynamiques dans cet article pour connaître les autres valeurs de type autorisées.

Pour plus d’informations sur l’utilisation des applets de commande, consultez [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).

## <a name="copying-registry-keys-and-values"></a>Copie des clés et des valeurs de Registre

Dans le fournisseur de **Registre** , utilisez l’applet de commande pour `Copy-Item` copier les clés et les valeurs de registre. Utilisez l' `Copy-ItemProperty` applet de commande pour copier uniquement les valeurs de registre.
La commande suivante copie la clé de Registre « contoso » et ses propriétés à l’emplacement spécifié « HKLM : \ Software\Fabrikam ».

`Copy-Item` crée la clé de destination si elle n’existe pas. Si la clé de destination existe, `Copy-Item` crée un doublon de la clé source en tant qu’élément enfant (sous-clé) de la clé de destination.

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

La commande suivante utilise la `Copy-ItemProperty` cmdlet pour copier la valeur « Server » de la clé « contoso » sur la clé « fabrikam ».

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.

- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a>Déplacement des clés et des valeurs de Registre

Les `Move-Item` applets de commande et `Move-ItemProperty` se comportent comme leurs équivalents « copie ». Si la destination existe, `Move-Item` déplace la clé source sous la clé de destination. Si la clé de destination n’existe pas, la clé source est déplacée vers le chemin d’accès de destination.

La commande suivante déplace la clé « contoso » sur le chemin d’accès « HKLM : \ SOFTWARE\Fabrikam ».

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

Cette commande déplace toutes les propriétés de « HKLM : \ SOFTWARE\ContosoCompany » vers « HKLM : \ SOFTWARE\Fabrikam ».

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

Pour plus d’informations sur les applets de commande utilisées dans cette section, consultez les articles suivants.

- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a>Attribution d’un nouveau nom aux clés et valeurs de Registre

Vous pouvez renommer les clés et les valeurs de Registre comme vous le feriez avec des fichiers et des dossiers.
`Rename-Item` renomme les clés de Registre, tout en `Rename-ItemProperty` renomme les valeurs de registre.

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a>Modification des descripteurs de sécurité

Vous pouvez restreindre l’accès aux clés de Registre à l’aide des `Get-Acl` applets de commande et `Set-Acl` . L’exemple suivant ajoute un nouvel utilisateur avec un contrôle total à la clé de Registre « HKLM : \ SOFTWARE\Contoso ».

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

Pour obtenir plus d’exemples et des détails sur l’utilisation des applets de commande, consultez les articles suivants.

- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a>Suppression et effacement des clés et des valeurs de Registre

Vous pouvez supprimer des éléments contenus à l’aide de **Remove-Item** , mais vous serez invité à confirmer la suppression si l’élément contient autre chose. L’exemple suivant tente de supprimer une clé « HKLM : \ SOFTWARE\Contoso ».

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Pour supprimer des éléments contenus sans demander confirmation, spécifiez le `-Recurse` paramètre.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

Si vous souhaitez supprimer tous les éléments dans « HKLM : \ SOFTWARE\Contoso », mais pas « HKLM : \ SOFTWARE\Contoso », utilisez une barre oblique inverse de fin `\` suivie d’un caractère générique.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

Cette commande supprime la valeur de Registre « ContosoTest » de la clé de Registre « HKLM : \ SOFTWARE\Contoso ».

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

`Clear-Item` efface toutes les valeurs de Registre pour une clé. L’exemple suivant efface toutes les valeurs de la clé de Registre « HKLM : \ SOFTWARE\Contoso ». Pour effacer uniquement une propriété spécifique, utilisez `Clear-ItemProperty` .

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

Pour obtenir plus d’exemples et des détails sur l’utilisation des applets de commande, consultez les articles suivants.

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.

### <a name="type-microsoftwin32registryvaluekind"></a>Tapez <Microsoft. Win32. RegistryValueKind figurant>

Établit ou change le type de données d'une valeur de Registre. La valeur par défaut est `String` (REG_SZ).

Ce paramètre fonctionne comme prévu sur l'applet de commande [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty). Il est également disponible sur l'applet de commande [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) dans les lecteurs de Registre, mais il n'a pas effet.

|Valeur | Description |
| ---- | ----------- |
| `String` | Spécifie une chaîne terminée par NULL. Équivalent à REG_SZ. |
| `ExpandString` | Spécifie une chaîne terminée par le caractère null qui contient un non développé |
|                | références aux variables d’environnement qui sont développées quand |
|                | la valeur est récupérée. Équivalent à REG_EXPAND_SZ. |
| `Binary` | Spécifie des données binaires sous n'importe quelle forme. Équivalent à REG_BINARY. |
| `DWord` | Spécifie un nombre binaire de 32 bits. Équivalent à REG_DWORD. |
| `MultiString` | Spécifie un tableau de chaînes terminées par le caractère null qui se sont terminées par |
|               | deux caractères null. Équivalent à REG_MULTI_SZ. |
| `QWord` | Spécifie un nombre binaire de 64 bits. Équivalent à REG_DWORD. |
| `Unknown` | Indique un type de données de Registre non pris en charge, tel que |
|           | REG_RESOURCE_LIST. |

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a>Utilisation du pipeline

Les applets de commande du fournisseur acceptent l’entrée du pipeline. Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur. Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.

## <a name="getting-help"></a>Obtenir de l’aide

Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.

Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une `Get-Help` commande sur un lecteur du système de fichiers ou utilisez le paramètre **path** pour spécifier un lecteur du système de fichiers.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a>Voir aussi

 [about_Providers](../About/about_Providers.md)

