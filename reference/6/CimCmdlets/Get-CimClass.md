---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 551ac39084ff7bf1729618d09cfa521cb6858242
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204350"
---
# Get-CimClass

## SYNOPSIS
Obtient une liste de classes CIM dans un espace de noms spécifique.

## SYNTAX

### ComputerSet (par défaut)

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### SessionSet

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## Description

L' `Get-CimClass` applet de commande récupère une liste de classes CIM dans un espace de noms spécifique. Si aucun nom de classe n’est fourni, l’applet de commande retourne toutes les classes de l’espace de noms. Contrairement à une instance CIM, les classes CIM ne contiennent pas le nom de session ou d’ordinateur CIM à partir duquel elles sont récupérées.

## EXEMPLES

### Exemple 1 : récupération de toutes les définitions de classe

Cet exemple obtient toutes les définitions de classe sous l’espace de noms **root/cimv2** .

```powershell
Get-CimClass
```

### Exemple 2 : obtenir les classes avec un nom spécifique

Cet exemple obtient les classes qui contiennent le mot « **Disk** » dans leur nom.

```powershell
Get-CimClass -ClassName *disk*
```

### Exemple 3 : obtenir les classes avec un nom de méthode spécifique

Cet exemple obtient les classes qui commencent par le nom **Win32** et qui ont un nom de méthode qui commence par **term** .

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### Exemple 4 : obtenir les classes avec un nom de propriété spécifique

Cet exemple obtient les classes qui commencent par le nom **Win32** et ont une propriété nommée **handle** .

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### Exemple 5 : obtenir les classes avec un nom de qualificateur spécifique

Cet exemple obtient les classes qui commencent par le nom **Win32** , qui contiennent le mot **Disk** dans leurs noms et qui disposent de l' **Association** de qualificateurs spécifiée.

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### Exemple 6 : obtenir les définitions de classe à partir d’un espace de noms spécifique

Cet exemple obtient les définitions de classe qui contiennent le mot **net** dans leurs noms à partir de la racine d’espace de noms spécifiée **/standardCimv2** .

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### Exemple 7 : obtenir les définitions de classe à partir d’un serveur distant

Cet exemple obtient les définitions de classe qui contiennent le mot « **Disk** » dans leurs noms à partir des serveurs distants **SERVEUR01** et **Server02** spécifiés.

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### Exemple 8 : obtenir les classes à l’aide d’une session CIM

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

Ce jeu de commandes crée une session avec plusieurs ordinateurs et le stocke dans une variable `$s` à l’aide de l’applet de commande `New-CimSession` , puis obtient les classes à l’aide de l’applet de commande `Get-CimClass` .

## PARAMETERS

### -CimSession

Exécute l’applet de commande dans une session à distance ou sur un ordinateur distant. Entrez un nom d’ordinateur ou un objet de session, tel que la sortie d’une applet de commande `New-CimSession` ou `Get-CimSession` . La valeur par défaut est la session active sur l’ordinateur local.

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

### -ClassName

Spécifie le nom de la classe CIM pour laquelle effectuer l’opération. Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des classes, car PowerShell obtient une liste des classes du serveur WMI local pour fournir une liste de noms de classe.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ComputerName

Spécifie l’ordinateur sur lequel vous souhaitez exécuter l’opération CIM. Vous pouvez spécifier un nom de domaine complet (FQDN), un nom NetBIOS ou une adresse IP.

Si vous spécifiez ce paramètre, l’applet de commande crée une session temporaire sur l’ordinateur spécifié à l’aide du protocole WsMan.

Si vous ne spécifiez pas ce paramètre, l’applet de commande effectue l’opération sur l’ordinateur local à l’aide du modèle COM (Component Object Model).

Si plusieurs opérations sont exécutées sur le même ordinateur, l’utilisation d’une session CIM offre de meilleures performances.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MethodName

Recherche les classes qui ont une méthode correspondant à ce nom. Vous pouvez utiliser des caractères génériques avec ce paramètre.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Espace de noms

Spécifie l’espace de noms pour l’opération CIM. L’espace de noms par défaut est **root/cimv2** . Vous pouvez utiliser la saisie semi-automatique via la touche Tab pour parcourir la liste des espaces de noms, car PowerShell obtient la liste des espaces de noms du serveur WMI local pour fournir la liste des espaces de noms.

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

### -PropertyName

Recherche les classes qui ont une propriété correspondant à ce nom. Vous pouvez utiliser des caractères génériques avec ce paramètre.

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

### -QualifierName

Filtre les classes par nom de qualificateur au niveau de la classe. Vous pouvez utiliser des caractères génériques avec ce paramètre.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Cette applet de commande n’accepte aucun objet d’entrée.

## SORTIES

### Microsoft. Management. infrastructure. CimClass

Cette applet de commande retourne un objet de classe CIM.

## REMARQUES

## LIENS CONNEXES

[New-CimSession](New-CimSession.md)
