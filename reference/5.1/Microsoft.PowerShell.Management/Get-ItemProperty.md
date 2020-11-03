---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203997"
---
# Get-ItemProperty

## SYNOPSIS
Obtient les propriétés de l'élément spécifié.

## SYNTAX

### Chemin d’accès (par défaut)

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## Description

L' `Get-ItemProperty` applet de commande obtient les propriétés des éléments spécifiés.
Par exemple, vous pouvez utiliser cette applet de commande pour obtenir la valeur de la propriété LastAccessTime d’un objet fichier.
Vous pouvez également utiliser cette applet de commande pour afficher les entrées de Registre et leurs valeurs.

## EXEMPLES

### Exemple 1 : obtenir des informations sur un répertoire spécifique

Cette commande obtient des informations sur le répertoire « C:\Windows ».

```powershell
Get-ItemProperty C:\Windows
```

### Exemple 2 : obtenir les propriétés d’un fichier spécifique

Cette commande obtient les propriétés du fichier « C:\Test\Weather.xls ».
Le résultat est dirigé vers l' `Format-List` applet de commande pour afficher la sortie sous forme de liste.

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### Exemple 3 : afficher le nom de la valeur et les données des entrées de Registre dans une sous-clé de Registre

Cette commande affiche le nom de la valeur et les données de chacune des entrées de Registre contenues dans la sous-clé de Registre « CurrentVersion ».
Notez que la commande requiert l’existence d’un lecteur PowerShell nommé `HKLM:` qui est mappé à la ruche « HKEY_LOCAL_MACHINE » du Registre.
Un lecteur avec ce nom et ce mappage est disponible dans PowerShell par défaut.
Le chemin d'accès à cette sous-clé de Registre peut également être spécifié à l'aide du chemin d'accès suivant, commençant par le nom du fournisseur suivi de deux deux-points :

« Registry :: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion ».

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### Exemple 4 : obtenir le nom de la valeur et les données d’une entrée de Registre dans une sous-clé de Registre

Cette commande obtient le nom et les données de la valeur de l’entrée de Registre « ProgramFilesDir figurant » dans la sous-clé de Registre « CurrentVersion ».
La commande utilise le paramètre **path** pour spécifier la sous-clé et le paramètre Name pour spécifier le nom de la valeur de l’entrée.

La commande utilise une graduation ou un accent grave ( \` ), le caractère de continuation PowerShell, pour continuer la commande sur la deuxième ligne.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### Exemple 5 : obtenir les noms de valeur et les données des entrées de Registre dans une clé de Registre

Cette commande obtient les noms de valeur et les données des entrées de Registre dans la clé de Registre « PowerShellEngine ».
Les résultats sont présentés dans l'exemple de sortie suivant.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

### Exemple 6 : obtenir, mettre en forme et afficher les résultats des valeurs et des données de Registre

Cet exemple montre comment mettre en forme la sortie d’une `Get-ItemProperty` commande dans une liste pour faciliter l’affichage des valeurs et des données de Registre et pour faciliter l’interprétation des résultats.

La première commande utilise l' `Get-ItemProperty` applet de commande pour récupérer les entrées de Registre dans la sous-clé **Microsoft. PowerShell** .
Cette sous-clé stocke les options de l’interpréteur de commandes par défaut pour PowerShell.
Les résultats sont présentés dans l'exemple de sortie suivant.

La sortie indique qu’il existe deux entrées de Registre, « path » et « ExecutionPolicy ».
Lorsqu'une clé de Registre contient moins de cinq entrées, elle s'affiche par défaut dans un tableau, mais sa lecture est souvent plus facile dans une liste.

La deuxième commande utilise la même `Get-ItemProperty` commande.
Toutefois, cette fois-ci, la commande utilise un opérateur de pipeline ( `|` ) pour envoyer les résultats de la commande à l’applet de commande `Format-List` .
La `Format-List` commande utilise le paramètre Property avec la valeur' * ' (All) pour afficher toutes les propriétés des objets dans une liste.
Les résultats sont présentés dans l'exemple de sortie suivant.

L’affichage qui en résulte montre les entrées de Registre « Path » et « ExecutionPolicy », ainsi que plusieurs propriétés moins familières de l’objet de clé de registre.
Les autres propriétés, précédées de PS, sont des propriétés d’objets personnalisés PowerShell, tels que les objets qui représentent les clés de registre.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## PARAMETERS

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.
La valeur par défaut est l’utilisateur actuel.

Tapez un nom d’utilisateur, tel que « User01 » ou « Domain01\User01 », ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential`.
Si vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.

> [!WARNING]
> Ce paramètre n’est pas pris en charge par les fournisseurs installés avec Windows PowerShell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande exclut de l’opération.
La valeur de ce paramètre qualifie le paramètre **Path** .
Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ».
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Spécifie un filtre dans le format ou la langue du fournisseur.
La valeur de ce paramètre qualifie le paramètre **Path** .

La syntaxe du filtre, notamment l’utilisation de caractères génériques, dépend du fournisseur.
Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lorsque l’applet de commande obtient les objets au lieu de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Spécifie, sous la forme d’un tableau de chaînes, un ou des éléments que cette applet de commande comprend dans l’opération.
La valeur de ce paramètre qualifie le paramètre **Path** .
Entrez un élément ou un modèle de chemin d'accès, tel que « *.txt ».
Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le chemin d’accès à l’emplacement actuel de la propriété.
Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle que vous la tapez.
Aucun caractère n’est interprété en tant que caractère générique.
Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Spécifie le nom des propriétés à récupérer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Spécifie le chemin d'accès aux éléments.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseTransaction

Inclut la commande dans la transaction active.
Ce paramètre est uniquement valide au cours d’une transaction.
Pour plus d’informations, consultez comprend la commande dans la transaction active.
Ce paramètre est uniquement valide au cours d’une transaction.
Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` . Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## ENTRÉES

### System.String

Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-ItemProperty` .

## SORTIES

### System. Boolean, System. String, System. DateTime

`Get-ItemProperty` retourne un objet pour chaque propriété d’élément qu’il obtient.
Le type d'objet dépend de l'objet récupéré.
Par exemple, dans un lecteur du système de fichiers, un fichier ou un dossier peut être retourné.

## REMARQUES

L' `Get-ItemProperty` applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur. Pour répertorier les fournisseurs disponibles dans votre session, tapez « `Get-PSProvider` ». Pour plus d'informations, consultez about_Providers.

## LIENS CONNEXES

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)
