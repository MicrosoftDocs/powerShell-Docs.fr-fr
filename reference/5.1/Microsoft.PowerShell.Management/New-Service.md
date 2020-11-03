---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 3249ce91a63417f2790997d37e2420c6fcb374d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203589"
---
# New-Service

## SYNOPSIS
Crée un service Windows.

## SYNTAX

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## Description

L' `New-Service` applet de commande crée une entrée pour un service Windows dans le registre et dans la base de données du service. Un nouveau service nécessite un fichier exécutable qui s’exécute pendant le service.

Les paramètres de cette applet de commande vous permettent de définir le nom d'affichage, la description, le type de démarrage et les dépendances du service.

## EXEMPLES

### Exemple 1 : créer un service

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

Cette commande crée un service nommé TestService.

### Exemple 2 : créer un service qui comprend une description, un type de démarrage et un nom d’affichage

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

Cette commande crée un service nommé TestService. Elle utilise les paramètres de `New-Service` pour spécifier une description, un type de démarrage et un nom d’affichage pour le nouveau service.

### Exemple 3 : afficher le nouveau service

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

Cette commande utilise `Get-CimInstance` pour obtenir l’objet **Win32_Service** pour le nouveau service. Cet objet inclut le mode de démarrage et la description du service.

### Exemple 4 : supprimer un service

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

Cet exemple montre deux façons de supprimer le service TestService. La première commande utilise l’option DELETE de `Sc.exe` . La deuxième commande utilise la méthode **Delete** des objets **Win32_Service** qui `Get-CimInstance` retourne.

## PARAMETERS

### -BinaryPathName

Spécifie le chemin d’accès du fichier exécutable pour le service. Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie le compte utilisé par le service comme [compte d’ouverture de session du service](/windows/desktop/ad/about-service-logon-accounts).

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DependsOn

Spécifie le nom des autres services dont dépend le nouveau service. Lorsque vous entrez plusieurs noms de services, ajoutez une virgule entre chaque nom.

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

### Description

Spécifie une description du service.

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

### -DisplayName

Spécifie le nom d'affichage du service.

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

### -Name

Spécifie le nom du service.
Ce paramètre est obligatoire.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartupType

Définit le type de démarrage du service. Les valeurs valides pour ce paramètre sont :

- **Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.
  Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.
- **Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.
- **Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.
- **Démarrage** -indique que le service est un pilote de périphérique Démarré par le chargeur du système. Cette valeur est valide uniquement pour les pilotes de périphérique.
- **Système** : indique que le service est un pilote de périphérique Démarré par la fonction « IOInitSystem () ». Cette valeur est valide uniquement pour les pilotes de périphérique.

 La valeur par défaut est **automatique** .

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
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

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### System.ServiceProcess.ServiceController

Cette applet de commande retourne un objet qui représente le nouveau service.

## REMARQUES

Pour exécuter cette applet de commande sur Windows Vista et les versions ultérieures du système d’exploitation Windows, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.

Pour supprimer un service, utilisez Sc.exe ou utilisez l' `Get-CimInstance` applet de commande pour obtenir l’objet **Win32_Service** qui représente le service, puis utilisez la méthode **Delete** pour supprimer le service. L’objet qui `Get-Service` retourne n’a pas de méthode Delete.

## LIENS CONNEXES

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)