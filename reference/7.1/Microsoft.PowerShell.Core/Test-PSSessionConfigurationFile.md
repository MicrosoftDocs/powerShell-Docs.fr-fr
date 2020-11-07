---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: 6786210fb2b89102c6193c755168af4264fae58c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345797"
---
# Test-PSSessionConfigurationFile

## SYNOPSIS
Vérifie les clés et les valeurs d'un fichier de configuration de session.

## SYNTAXE

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

Cette applet de commande vérifie qu’un fichier de configuration de session contient des clés valides et que les valeurs sont de type correct. Pour les valeurs énumérées, l'applet de commande vérifie que les valeurs spécifiées sont valides.

L’applet de commande retourne `$True` si le fichier réussit tous les tests et `$False` si ce n’est pas le cas. Pour rechercher des erreurs, utilisez le paramètre **Verbose** .

`Test-PSSessionConfigurationFile` vérifie les fichiers de configuration de session, tels que ceux créés par l’applet de commande `New-PSSessionConfigurationFile` . Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md). Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

Cette applet de commande a été introduite dans PowerShell 3,0.

## EXEMPLES

### Exemple 1 : tester un fichier de configuration de session

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### Exemple 2 : tester le fichier de configuration de session d’une configuration de session

Dans cet exemple, nous testons le fichier de configuration utilisé dans la configuration de session **restreinte** .
La valeur du paramètre **path** est le résultat de la `Get-PSSessionConfiguration` commande qui obtient la configuration de session **restreinte** . Le chemin d’accès du fichier de configuration de session est stocké dans la valeur de la propriété **ConfigFilePath** de la configuration de session.

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### Exemple 3 : tester tous les fichiers de configuration de session

Dans cet exemple, la fonction teste tous les fichiers de configuration de session sur l’ordinateur local. La fonction utilise l' `Get-PSSessionConfiguration` applet de commande pour récupérer toutes les configurations de session. Le code à l’intérieur de la `ForEach-Object` boucle affiche le chemin d’accès du fichier et teste chacune des configurations de session.

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

La propriété **ConfigFilePath** d’une configuration de session contient le chemin d’accès du fichier de configuration de session utilisé dans la configuration de session, le cas échéant.

Si la valeur de la propriété **ConfigFilePath** est remplie (vraie), la commande obtient (affiche) la valeur de la propriété **ConfigFilePath**. Elle utilise ensuite l' `Test-PSSessionConfigurationFile` applet de commande pour tester le fichier dans la valeur **ConfigFilePath** . Le paramètre **Verbose** retourne l'erreur de fichier en cas d'échec du test du fichier.

## PARAMÈTRES

### -Path

Spécifie le chemin d’accès et le nom de fichier d’un fichier de configuration de session (. PSSC). Si vous omettez le chemin d’accès, la valeur par défaut est le dossier actif. Les caractères génériques sont pris en charge, mais ils doivent être résolus en un seul fichier. Vous pouvez également diriger un chemin d’accès de fichier de configuration de session vers `Test-PSSessionConfigurationFile` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System.String

Vous pouvez diriger un chemin d’accès de fichier de configuration de session vers `Test-PSSessionConfigurationFile` .

## SORTIES

### System.Boolean

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

## LIENS CONNEXES

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[Fournisseur WSMan](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
