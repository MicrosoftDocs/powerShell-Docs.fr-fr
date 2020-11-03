---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: adf6c1ac6f6f9288233d530b7ea2101f4b7688e4
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205426"
---
# Get-CimAssociatedInstance

## SYNOPSIS
Récupère les instances CIM qui sont connectées à une instance CIM spécifique par une association.

## SYNTAX

### ComputerSet (par défaut)

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### SessionSet

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## Description

L' `Get-CimAssociatedInstance` applet de commande récupère les instances CIM connectées à une instance CIM spécifique, appelée instance source, par une association.

Dans une association, chaque instance CIM a un rôle nommé et la même instance CIM peut participer à une association dans des rôles différents.

Si le paramètre InputObject n’est pas spécifié, l’applet de commande fonctionne de l’une des manières suivantes :

- Si le paramètre **ComputerName** ou le paramètre **CimSession** n’est pas spécifié, cette applet de commande fonctionne sur le Windows Management Instrumentation local (WMI) à l’aide d’une session com (Component Object Model).
- Si le paramètre **ComputerName** ou le paramètre **CimSession** est spécifié, cette applet de commande fonctionne sur le serveur CIM spécifié par le paramètre **ComputerName** ou le paramètre **CimSession** .

## EXEMPLES

### Exemple 1 : obtenir toutes les instances associées d’une instance spécifique

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

Cet ensemble de commandes récupère les instances de la classe nommée Win32_LogicalDisk et stocke les informations dans une variable nommée `$disk` à l’aide de l’applet de commande `Get-CimInstance` . La première instance de disque logique dans la variable est ensuite utilisée comme objet d’entrée pour l’applet de commande `Get-CimAssociatedInstance` afin d’obtenir toutes les instances CIM associées de l’instance CIM spécifiée.

### Exemple 2 : obtenir toutes les instances associées d’un type spécifique

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

Ce jeu de commandes récupère toutes les instances de la classe **Win32_LogicalDisk** et les stocke dans une variable nommée `$disk` . La première instance de disque logique dans la variable est ensuite utilisée comme objet d’entrée pour l' `Get-CimAssociatedInstance` applet de commande afin d’obtenir toutes les instances associées qui sont associées via la classe d’association spécifiée **Win32_DiskPartition** .

### Exemple 3 : obtenir toutes les instances associées par le biais du qualificateur d’une classe spécifique

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

Cet ensemble de commandes récupère les services qui dépendent du service WMI et les stocke dans une variable nommée `$s` . Le nom de la classe d’association pour le **Win32_DependentService** est récupéré à l’aide de l' `Get-CimClass` applet de commande en spécifiant **Association** comme qualificateur et est ensuite transmis avec $s à l' `Get-CimAssociatedInstance` applet de commande pour obtenir toutes les instances associées de la classe d’association récupérée.

## PARAMETERS

### -Association

Spécifie le nom de la classe d’association. Si vous ne spécifiez pas ce paramètre, l’applet de commande retourne tous les objets Association existants de tout type.

Par exemple, si la classe A est associée à la classe B par le biais de deux associations, AB1 et AB2, ce paramètre peut être utilisé pour spécifier le type d’association, AB1 ou AB2.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CimSession

Exécute la commande à l’aide de la session CIM spécifiée. Entrez une variable qui contient la session CIM ou une commande qui crée ou obtient la session CIM, telle que `New-CimSession` ou `Get-CimSession` . Pour plus d’informations, consultez [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

Spécifie le nom de l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM. Vous pouvez spécifier un nom de domaine complet (FQDN) ou un nom NetBIOS.

Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.

Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).

Si plusieurs opérations sont exécutées sur le même ordinateur, la connexion à l’aide d’une session CIM offre de meilleures performances.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Spécifie l'entrée de cette applet de commande. Vous pouvez utiliser ce paramètre ou vous adresser l'entrée à cette applet de commande.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Uniquement

Retourne les objets avec uniquement les propriétés de clé remplies. Cela réduit la quantité de données transférées sur le réseau.

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

### -Espace de noms

Spécifie l’espace de noms pour l’opération CIM. L’espace de noms par défaut est root/cimv2.

> [!NOTE]
> Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.

```yaml
Type: System.String
Parameter Sets: (All)
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

Spécifie l’URI (Uniform Resource Identifier) de la ressource de la classe ou de l’instance de ressource. L'URI est utilisé pour identifier un type particulier de ressource, comme un disque ou un processus, sur un ordinateur.

Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource. Par exemple :

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

Par défaut, si vous ne spécifiez pas ce paramètre, l’URI de ressource standard DMTF `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` est utilisé et le nom de la classe y est ajouté.

**Resourceuri** peut être utilisé uniquement avec les sessions CIM créées à l’aide du protocole WSMan, ou lors de la spécification du paramètre **ComputerName** , qui crée une session CIM à l’aide de wsman. Si vous spécifiez ce paramètre sans spécifier le paramètre **ComputerName** ou si vous spécifiez une session CIM créée à l’aide du protocole DCOM, vous recevez une erreur, car le protocole DCOM ne prend pas en charge le paramètre **resourceuri** .

Si le paramètre **resourceuri** et le paramètre **Filter** sont tous deux spécifiés, le paramètre **Filter** est ignoré.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultClassName

Spécifie le nom de la classe des instances associées. Une instance CIM peut être associée à une ou plusieurs instances CIM. Toutes les instances CIM associées sont retournées si vous ne spécifiez pas le nom de classe de résultat.

Par défaut, la valeur de ce paramètre est null et toutes les instances CIM associées sont retournées.

Vous pouvez filtrer les résultats d’association pour qu’ils correspondent à un nom de classe spécifique. Le filtrage se produit sur le serveur. Si ce paramètre n’est pas spécifié, `Get-CIMAssociatedInstance` retourne toutes les associations existantes. Par exemple, si la classe A est associée aux classes B, C et D, ce paramètre peut être utilisé pour limiter la sortie à un type spécifique (B, C ou D).

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

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n’accepte aucun objet d’entrée.

## SORTIES

### System.Object

Cette applet de commande retourne un objet.

## REMARQUES

## LIENS CONNEXES

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)
