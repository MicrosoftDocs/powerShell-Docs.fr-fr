---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 9d68e59cf00e94a2318190800c47a4248a384e6f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205546"
---
# Set-CimInstance

## SYNOPSIS
Modifie une instance CIM sur un serveur CIM en appelant la méthode ModifyInstance de la classe CIM.

## SYNTAX

### CimInstanceComputerSet (par défaut)

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QuerySessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

Cette applet de commande modifie une instance CIM sur un serveur CIM.

Si le paramètre **InputObject** n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :

- Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).
- Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .

Si le paramètre **InputObject** est spécifié, l’applet de commande fonctionne de l’une des manières suivantes :

- Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande utilise la session CIM ou le nom de l’ordinateur à partir de l’objet d’entrée.
- Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande utilise soit la valeur du paramètre **CimSession** , soit la valeur du paramètre **ComputerName** . Ce n’est pas très courant.

## EXEMPLES

### Exemple 1 : définir l’instance CIM

Cet exemple affecte à la propriété **VariableValue** la valeur **ABCD** à l’aide du paramètre de **requête** . Vous pouvez modifier les instances correspondant à une requête WQL (Windows Management Instrumentation Query Language).

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### Exemple 2 : définir la propriété d’instance CIM à l’aide d’un pipeline

Cet exemple récupère l’objet d’instance CIM filtré par le paramètre de **requête** à l’aide de l’applet de commande `Get-CimInstance` . L' `Set-CimInstance` applet de commande modifie la valeur de la propriété **VariableValue** en **ABCD** .

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### Exemple 3 : définir la propriété d’instance CIM à l’aide d’un objet d’entrée

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

Cet exemple récupère les objets d’instance CIM filtrés par le paramètre de requête dans une variable à `$x` l’aide de `Get-CimInstance` , puis passe le contenu de la variable à l’applet de commande `Set-CimInstance` . `Set-CimInstance` modifie ensuite la propriété **VariableValue** en **SomeValue** . Étant donné que le paramètre **PassThru** est utilisé, cet exemple retourne un objet d’instance CIM modifié.

### Exemple 4 : définir la propriété d’instance CIM

Cet exemple récupère l’objet d’instance CIM qui est spécifié dans le paramètre de **requête** dans une variable `$x` à l’aide de l’applet de commande `Get-CimInstance` , puis modifie la valeur de la propriété **VariableValue** de l’objet pour changer. L’objet d’instance CIM est ensuite enregistré à l’aide de l’applet de commande `Set-CimInstance` .
Étant donné que le paramètre **PassThru** est utilisé, cet exemple retourne un objet d’instance CIM modifié.

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### Exemple 5 : afficher la liste des instances CIM à modifier à l’aide de WhatIf

Cet exemple utilise le paramètre commun **WhatIf** pour spécifier que la modification ne doit pas être effectuée, mais uniquement en cas de résultat.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### Exemple 6 : définir l’instance CIM après la confirmation de l’utilisateur

Cet exemple utilise le paramètre commun **Confirm** pour spécifier que la modification doit être effectuée uniquement après confirmation de l’utilisateur.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### Exemple 7 : définir l’instance CIM créée

Cet exemple crée une instance CIM avec les propriétés spécifiées à l’aide de l’applet de commande `New-CimInstance` et récupère son contenu dans une variable `$x` . La variable est ensuite transmise à l’applet de commande `Set-CimInstance` , qui modifie la valeur de la propriété **VariableValue** en **SomeValue** .
Étant donné que le paramètre **PassThru** est utilisé, cet exemple retourne un objet d’instance CIM modifié.

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## PARAMETERS

### -CimSession

Exécute les applets de commande sur un ordinateur distant. Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande `New-CimSession` ou `Get-CimSession` .

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM. Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.

Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).

Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.

Si plusieurs opérations sont exécutées sur le même ordinateur, la connexion à l’aide d’une session CIM offre de meilleures performances.

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie un objet d’instance CIM à utiliser comme entrée.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Espace de noms

Spécifie l’espace de noms pour l’opération CIM. L’espace de noms par défaut est root/cimv2. Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
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

### -PassThru

Retourne un objet représentant l’élément que vous utilisez. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Propriété

Spécifie les propriétés de l’instance CIM sous la forme d’une table de hachage (à l’aide de paires nom-valeur). Seules les propriétés spécifiées à l’aide de ce paramètre sont modifiées. Les autres propriétés de l’instance CIM ne sont pas modifiées.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

Spécifie une requête à exécuter sur le serveur CIM pour récupérer les instances CIM sur lesquelles exécuter l’applet de commande. Vous pouvez spécifier le dialecte de requête à l’aide du paramètre QueryDialect.

Si la valeur spécifiée contient des guillemets doubles ( `"` ), des guillemets simples ( `'` ) ou une barre oblique inverse ( `\` ), vous devez placer ces caractères dans une séquence d’échappement en les faisant précéder du caractère de barre oblique inverse ( `\` ). Si la valeur spécifiée utilise l’opérateur **Like** WQL, vous devez placer les caractères suivants dans une séquence d’échappement en les mettant entre crochets ( `[]` ) : percent ( `%` ), trait de soulignement ( `_` ) ou crochet ouvrant ( `[` ).

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

Spécifie le langage de requête utilisé pour le paramètre de requête. Les valeurs acceptables pour ce paramètre sont les suivantes : **WQL** ou **CQL** . La valeur par défaut est **WQL** .

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
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

ResourceURI peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre ComputerName, qui crée une session CIM à l’aide de WSMan. Si vous spécifiez ce paramètre sans spécifier le paramètre ComputerName ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous obtiendrez une erreur, car le protocole DCOM ne prend pas en charge le paramètre ResourceURI.

Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
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

### Microsoft.Management.Infrastructure.CimInstance

## SORTIES

### Microsoft.Management.Infrastructure.CimInstance

Lorsque le paramètre **PassThru** est spécifié, cette applet de commande retourne un objet d’instance CIM modifié.

## REMARQUES

## LIENS CONNEXES

[Get-CimInstance](get-ciminstance.md)

[New-CimInstance](New-CimInstance.md)

[Remove-CimInstance](remove-ciminstance.md)
