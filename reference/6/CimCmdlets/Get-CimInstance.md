---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 49838449bd2ffe949c4b2f1310c3f68c40867908
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205425"
---
# Get-CimInstance

## SYNOPSIS
Obtient les instances CIM d’une classe à partir d’un serveur CIM.

## SYNTAX

### ClassNameComputerSet (par défaut)

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QuerySessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### CimInstanceComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### ResourceUriComputerSet

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QueryComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## Description

L' `Get-CimInstance` applet de commande obtient les instances CIM d’une classe à partir d’un serveur CIM. Vous pouvez spécifier soit le nom de la classe, soit une requête pour cette applet de commande. Cette applet de commande retourne un ou plusieurs objets d’instance CIM représentant une capture instantanée des instances CIM présentes sur le serveur CIM.

Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :

- Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).
- Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .

Si le paramètre **InputObject** est spécifié, l’applet de commande fonctionne de l’une des manières suivantes :

- Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande utilise la session CIM ou le nom de l’ordinateur à partir de l’objet d’entrée.
- Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande utilise soit la valeur du paramètre CimSession, soit la valeur du paramètre **ComputerName** .

## EXEMPLES

### Exemple 1 : obtenir les instances CIM d’une classe spécifiée

Cet exemple récupère les instances CIM d’une classe nommée **Win32_Process** .

```powershell
Get-CimInstance -ClassName Win32_Process
```

### Exemple 2 : obtenir la liste des espaces de noms d’un serveur WMI

Cet exemple récupère une liste d’espaces de noms sous l’espace de noms **racine** sur un serveur WMI.

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### Exemple 3 : obtenir des instances d’une classe filtrées à l’aide d’une requête

Cet exemple récupère toutes les instances CIM qui commencent par la lettre **P** d’une classe nommée **Win32_Process** à l’aide de la requête spécifiée par un paramètre de **requête** .

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### Exemple 4 : obtenir des instances d’une classe filtrées à l’aide d’un nom de classe et d’une expression de filtre

Cet exemple récupère toutes les instances CIM qui commencent par la lettre **P** d’une classe nommée **Win32_Process** à l’aide du paramètre Filter.

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### Exemple 5 : récupération des instances CIM avec uniquement les propriétés clés remplies

Cet exemple crée une nouvelle instance CIM en mémoire pour une classe nommée **Win32_Process** avec la propriété de clé `@{ "Handle"=0 }` et la stocke dans une variable nommée `$x` . La variable est transmise en tant qu’instance CIM à l' `Get-CimInstance` applet de commande pour obtenir une instance particulière.

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### Exemple 6 : récupérer des instances CIM et les réutiliser

Cet exemple obtient les instances CIM d’une classe nommée **Win32_Process** et les stocke dans les variables `$x` et `$y` . La variable `$x` est ensuite mise en forme dans une table contenant uniquement les propriétés **Name** et **KernelModeTime** , la table définie sur **AutoSize** .

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### Exemple 7 : récupérer des instances CIM à partir d’un ordinateur distant

Cet exemple récupère les instances CIM d’une classe nommée **Win32_ComputerSystem** à partir des ordinateurs distants **SERVEUR01** et **Server02** .

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### Exemple 8 : obtention uniquement des propriétés de clé, et non de toutes les propriétés

Cet exemple récupère uniquement les propriétés de clé, ce qui réduit la taille de l’objet et du trafic réseau.

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### Exemple 9 : obtention d’un seul sous-ensemble de propriétés, au lieu de toutes les propriétés

Cet exemple récupère uniquement un sous-ensemble de propriétés, ce qui réduit la taille de l’objet et du trafic réseau.

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

L’instance Récupérée avec le paramètre **Property** peut être utilisée pour effectuer d’autres opérations CIM, par exemple `Set-CimInstance` ou `Invoke-CimMethod` .

### Exemple 10 : récupération de l’instance CIM à l’aide d’une session CIM

Cet exemple crée une session CIM sur les ordinateurs nommés **SERVEUR01** et **Server02** à l’aide de l’applet de commande `New-CimSession` et stocke les informations de session dans une variable nommée `$s` . Le contenu de la variable est ensuite passé à `Get-CimInstance` en utilisant le paramètre **CimSession** pour récupérer les instances CIM de la classe nommée **Win32_ComputerSystem** .

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## PARAMETERS

### -CimSession

Spécifie la session CIM à utiliser pour cette applet de commande. Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` . Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Spécifie le nom de la classe CIM pour laquelle récupérer les instances CIM. Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Spécifie l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM. Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP. Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).

Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.

Si plusieurs opérations sont exécutées sur le même ordinateur, connectez-vous à l’aide d’une session CIM pour obtenir de meilleures performances.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

Spécifie une clause WHERE à utiliser comme filtre. Spécifiez la clause dans le langage de requête **WQL** ou **CQL** . N’incluez pas le `WHERE` mot clé dans la valeur du paramètre.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

Spécifie un objet d’instance CIM à utiliser comme entrée.

Si vous utilisez déjà un objet d’instance CIM, vous pouvez utiliser ce paramètre pour passer l’objet d’instance CIM afin d’obtenir l’instantané le plus récent à partir du serveur CIM. Lorsque vous transmettez un objet d’instance CIM en tant qu’entrée, `Get-CimInstance` retourne l’objet à partir du serveur à l’aide d’une opération d’extraction CIM, au lieu d’une opération d’énumération ou de requête. L’utilisation d’une opération obtenir CIM est plus efficace que la récupération de toutes les instances, puis leur filtrage.

Si la classe CIM n’implémente pas l’opération d’extraction, le fait de spécifier le paramètre **InputObject** retourne une erreur.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Uniquement

Indique que seuls les objets avec des propriétés de clé renseignés sont retournés. La spécification du paramètre **keyonly** réduit la quantité de données transférées sur le réseau.

Utilisez le paramètre **keyonly** pour retourner uniquement une petite partie de l’objet, qui peut être utilisée pour d’autres opérations, telles que `Set-CimInstance` les `Get-CimAssociatedInstance` applets de commande ou.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Espace de noms

Spécifie l’espace de noms de la classe CIM.

L’espace de noms par défaut est **root/cimv2** . Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur. Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.

Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Propriété

Spécifie un jeu de propriétés d’instance à récupérer. Utilisez ce paramètre lorsque vous devez réduire la taille de l’objet retourné, soit en mémoire, soit sur le réseau. L’objet retourné contient également les propriétés de clé, même si vous ne les avez pas listées à l’aide du paramètre **Property** . D’autres propriétés de la classe sont présentes, mais elles ne sont pas remplies.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

Spécifie une requête à exécuter sur le serveur CIM. Si la valeur spécifiée contient des guillemets doubles, des `"` guillemets simples `'` ou une barre oblique inverse `\` , vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder d’une barre oblique inverse. Si la valeur spécifiée utilise l’opérateur **Like** WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les plaçant entre crochets `[]` : pourcentage, trait de `%` soulignement `_` ou crochet ouvrant `[` .

Vous ne pouvez pas utiliser une requête de métadonnées pour récupérer une liste de classes ou une requête d’événement. Pour récupérer une liste de classes, utilisez l' `Get-CimClass` applet de commande. Pour récupérer une requête d’événement, utilisez l’applet de commande `Register-CimIndicationEvent` .

Vous pouvez spécifier le dialecte de requête à l’aide du paramètre **QueryDialect** .

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

Spécifie le langage de requête utilisé pour le paramètre de requête. Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL** . La valeur par défaut est **WQL** .

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource. L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.

Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource. Par exemple :

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.

**Resourceuri** peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre **ComputerName** , qui crée une session CIM à l’aide de wsman. Si vous spécifiez ce paramètre sans spécifier le paramètre **ComputerName** ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous obtiendrez une erreur, car le protocole DCOM ne prend pas en charge le paramètre **resourceuri** .

Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Superficielle

Indique que les instances d’une classe sont retournées sans inclure les instances des classes enfants. Par défaut, l’applet de commande retourne les instances d’une classe et de ses classes enfants.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### Instance CIM

Cette applet de commande accepte un objet d’entrée spécifié avec le paramètre InputObject.

## SORTIES

### Instance CIM

Cette applet de commande retourne un ou plusieurs objets d’instance CIM représentant une capture instantanée des instances CIM sur le serveur CIM.

## REMARQUES

## LIENS CONNEXES

[Format-Table](../microsoft.powershell.utility/format-table.md)

[Get-CimAssociatedInstance](Get-CimAssociatedInstance.md)

[Get-CimClass](Get-CimClass.md)

[Invoke-CimMethod](invoke-cimmethod.md)

[New-CimInstance](New-CimInstance.md)

[Register-CimIndicationEvent](Register-CimIndicationEvent.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
