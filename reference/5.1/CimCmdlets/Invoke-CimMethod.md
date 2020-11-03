---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 328abb5776366f6e2d9b5106c93337f5d45533ed
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205342"
---
# Invoke-CimMethod

## SYNOPSIS
Appelle une méthode d’une classe CIM.

## SYNTAX

### ClassNameComputerSet (par défaut)

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ResourceUriComputerSet

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### CimInstanceComputerSet

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimClassComputerSet

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimClassSessionSet

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QueryComputerSet

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QuerySessionSet

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

L' `Invoke-CimMethod` applet de commande appelle une méthode d’une classe CIM ou d’une instance CIM à l’aide des paires nom-valeur spécifiées par le paramètre **arguments** .

Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :

- Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).
- Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .

Si le paramètre **InputObject** est spécifié, l’applet de commande fonctionne de l’une des manières suivantes :

- Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande utilise la session CIM ou le nom de l’ordinateur à partir de l’objet d’entrée.
- Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande utilise soit la valeur du paramètre **CimSession** , soit la valeur du paramètre **ComputerName** . Ce scénario n’est pas courant.

## EXEMPLES

### Exemple 1 : appeler une méthode

Cet exemple appelle la méthode **Terminate** de la classe **Win32_Process** .

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### Exemple 2 : appeler une méthode à l’aide d’un objet d’instance CIM

Cet exemple récupère l’objet d’instance CIM et le stocke dans une variable nommée `$x` à l’aide de l’applet de commande `Get-CimInstance` . Le contenu de la variable est ensuite utilisé comme **InputObject** pour l’applet de commande `Invoke-CimMethod` . La méthode **GetOwner** est appelée pour **CimInstance** .

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### Exemple 3 : appeler une méthode statique à l’aide d’arguments

Cet exemple appelle la méthode **Create** nommée à l’aide du paramètre **arguments** .

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### Exemple 4 : validation côté client

Cet exemple effectue une validation côté client pour la méthode **xyz** en passant un objet **CimClass** à `Invoke-CimMethod` .

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## PARAMETERS

### -Arguments

Spécifie les paramètres à passer à la méthode appelée. Spécifiez les valeurs de ce paramètre en tant que paires nom-valeur, stockées dans une table de hachage. L’ordre des valeurs entrées n’est pas important.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CimClass

Spécifie un objet de classe CIM qui représente une définition de classe CIM sur le serveur. Utilisez ce paramètre lors de l’appel d’une méthode statique d’une classe.

Vous pouvez utiliser l' `Get-CimClass` applet de commande pour récupérer une définition de classe à partir du serveur.

L’utilisation de ce paramètre permet d’améliorer les validations de schéma côté client.

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimSession

Exécute la commande à l’aide de la session CIM spécifiée. Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que les `New-CimSession` applets de commande ou `Get-CimSession` . Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

Spécifie le nom de la classe CIM pour laquelle effectuer l’opération. Ce paramètre est utilisé uniquement pour les méthodes statiques. Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM. Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.

Lors de l’utilisation de ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan. Dans le cas contraire, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).

Connectez-vous à l’aide d’une session CIM pour obtenir de meilleures performances lorsque plusieurs opérations sont exécutées sur le même ordinateur.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

Spécifie un objet d’instance CIM à utiliser comme entrée pour appeler une méthode. Ce paramètre ne peut être utilisé que pour appeler des méthodes d’instance. Pour appeler des méthodes statiques de classe, utilisez le paramètre **Class** ou le paramètre **CimClass** .

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

### -MethodName

Spécifie le nom de la méthode CIM à appeler. Ce paramètre est obligatoire et ne peut ni avoir la valeur Null ni être vide. Pour appeler la méthode statique d’une classe CIM, utilisez le paramètre **className** ou **CimClass** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Espace de noms

Spécifie l’espace de noms pour l’opération CIM. L’espace de noms par défaut est **root/cimv2** . Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Spécifie la durée pendant laquelle l’applet de commande attend une réponse de l’ordinateur. Par défaut, la valeur est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.

Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion par défaut de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables.

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

### -Query

Spécifie une requête à exécuter sur le serveur CIM. Une méthode est appelée sur les instances reçues à la suite de la requête. Vous pouvez spécifier le dialecte de requête à l’aide du paramètre **QueryDialect** .

Si la valeur spécifiée contient des guillemets doubles ( `"` ), des guillemets simples ( `'` ) ou une barre oblique inverse ( `\` ), vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder du caractère de barre oblique inverse ( `\` ). Si la valeur spécifiée utilise l’opérateur LIKE WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les mettant entre crochets ( `[]` ) : percent ( `%` ), trait de soulignement ( `_` ) ou crochet ouvrant ( `[` ).

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

Spécifie le langage de requête utilisé pour le paramètre de requête. Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL** .

La valeur par défaut est **WQL** .

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource.
L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.

Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource. Par exemple :

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.

**Resourceuri** peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre **ComputerName** , qui crée une session CIM à l’aide de wsman.

Lorsque vous spécifiez ce paramètre sans spécifier le paramètre **ComputerName** , ou lorsque vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous recevez une erreur. Le protocole DCOM ne prend pas en charge le paramètre **resourceuri** .

Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### Microsoft. Management. infrastructure. CimClass

Cette applet de commande accepte une classe CIM comme objet d’entrée.

### Microsoft.Management.Infrastructure.CimInstance

Cette applet de commande accepte une instance CIM comme objet d’entrée.

## SORTIES

### System. Management. Automation. PSCustomObject

Cette applet de commande retourne un objet.

## REMARQUES

## LIENS CONNEXES

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)
