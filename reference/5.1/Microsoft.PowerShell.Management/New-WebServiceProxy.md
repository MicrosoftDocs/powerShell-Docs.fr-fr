---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203586"
---
# New-WebServiceProxy

## SYNOPSIS
Crée un objet proxy de service Web qui vous permet d’utiliser et de gérer le service Web dans PowerShell.

## SYNTAX

### Informations d’identification (par défaut)

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### Informations d'identification

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### UseDefaultCredential

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## Description

L' `New-WebServiceProxy` applet de commande vous permet d’utiliser un service Web dans PowerShell. L’applet de commande se connecte à un service Web et crée un objet proxy de service Web dans PowerShell. Vous pouvez utiliser l'objet proxy pour gérer le service Web.

Un service Web est un programme XML qui échange des données sur un réseau, en particulier sur Internet. Microsoft .NET Framework fournit des objets proxy de service Web qui représentent le service Web sous la forme d'un objet .NET Framework.

## EXEMPLES

### Exemple 1 : créer un proxy pour un service Web

Cet exemple crée un proxy .NET Framework du service Web Calculator dans Windows PowerShell.

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### Exemple 2 : créer un proxy pour un service Web et spécifier l’espace de noms et la classe

Cet exemple utilise l' `New-WebServiceProxy` applet de commande pour créer un proxy .NET Framework du service Web Calculator.

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

La commande utilise le paramètre **URI** pour spécifier l’URI et les paramètres d' **espace de noms** et de **classe** pour spécifier l’espace de noms et la classe de l’objet.

### Exemple 3 : afficher les méthodes d’un proxy de service Web

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

Cet exemple utilise l' `Get-Member` applet de commande pour afficher les méthodes de l’objet proxy de service Web dans la `$calc` variable. Nous utilisons ces méthodes dans l’exemple suivant.

Notez que le **TypeName** de l’objet proxy, WebServiceProxy, reflète les noms de l’espace de noms et de la classe qui ont été spécifiés dans l’exemple précédent.

### Exemple 4 : utiliser un proxy de service Web

```powershell
PS> $calc.Multiply(6,7)
42
```

Cet exemple utilise le proxy de service Web stocké dans la `$calc` variable. La commande utilise la méthode **Multiply** du proxy.

## PARAMETERS

### -Classe

Spécifie le nom de la classe proxy que l'applet de commande crée pour le service Web. La valeur de ce paramètre est utilisée avec le paramètre **namespace** pour fournir un nom qualifié complet pour la classe. La valeur par défaut est générée à partir de l’Uniform Resource Identifier (URI).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. La valeur par défaut est l’utilisateur actuel. Vous pouvez procéder de la sorte au lieu d'utiliser le paramètre **UseDefaultCredential** .

Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Espace de noms

Spécifie un espace de noms pour la nouvelle classe.

La valeur de ce paramètre est utilisée avec la valeur du paramètre **Class** pour générer un nom qualifié complet pour la classe. La valeur par défaut est **Microsoft. PowerShell. Commands. NewWebserviceProxy. AutogeneratedTypes** plus un type qui est généré à partir de l’URI.

Vous pouvez définir la valeur du paramètre d' **espace de noms** afin de pouvoir accéder à plusieurs services Web qui portent le même nom.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -URI

Spécifie l'URI du service Web. Entrez un URI ou le chemin d’accès et le nom de fichier d’un fichier qui contient une description de service.

L’URI doit retourner une `.asmx` page ou une page qui retourne une description de service. Pour retourner une description de service d’un service Web créé à l’aide de ASP.NET, ajoutez « ? WSDL "à l’URL du service Web (par exemple, `http://www.contoso.com/MyWebService.asmx?WSDL` ).

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredential

Indique que cette applet de commande utilise les informations d’identification par défaut. Cette applet de commande affecte la valeur true à la propriété **UseDefaultCredential** de l’objet proxy résultant. Vous pouvez procéder de la sorte au lieu d'utiliser le paramètre **Credential** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

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

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Objet proxy de service Web

Cette applet de commande retourne un objet proxy de service Web. L'espace de noms et la classe des objets sont déterminés par les paramètres de la commande. La valeur par défaut est générée à partir de l’URI d’entrée.

## REMARQUES

`New-WebServiceProxy` utilise la classe **System .net. WebClient** pour charger le service Web spécifié.

## LIENS CONNEXES

[New-Service](New-Service.md)
