---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-member?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Member
ms.openlocfilehash: 56f5d62115474a9791e139646383b1ae725664bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204614"
---
# Get-Member

## SYNOPSIS
Obtient les propriétés et méthodes des objets.

## SYNTAX

```
Get-Member [-InputObject <PSObject>] [[-Name] <String[]>] [-MemberType <PSMemberTypes>]
 [-View <PSMemberViewTypes>] [-Static] [-Force] [<CommonParameters>]
```

## Description

L' `Get-Member` applet de commande obtient les membres, les propriétés et les méthodes des objets.

Pour spécifier l’objet, utilisez le paramètre **InputObject** ou dirigez un objet vers `Get-Member` . Pour obtenir des informations sur les membres statiques, les membres de la classe, et non de l’instance, utilisent le paramètre **static** . Pour récupérer uniquement certains types de membres, tels que **NoteProperties** , utilisez le paramètre **MemberType** .

## EXEMPLES

### Exemple 1 : récupérer les membres des objets process

Cette commande affiche les propriétés et les méthodes des objets de service générés par l’applet de commande `Get-Service` .

Étant donné que la `Get-Member` partie de la commande n’a pas de paramètres, elle utilise les valeurs par défaut pour les paramètres. Par défaut, `Get-Member` n’obtient pas les membres statiques ou intrinsèques.

```powershell
Get-Service | Get-Member
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, System.EventArgs)
Close                     Method        void Close()
Continue                  Method        void Continue()
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.ServiceControllerSt...
BinaryPathName            Property      System.String {get;set;}
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DelayedAutoStart          Property      System.Boolean {get;set;}
DependentServices         Property      System.ServiceProcess.ServiceController[] DependentServices {get;}
Description               Property      System.String {get;set;}
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle ServiceHandle {get;}
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] ServicesDependedOn {get;}
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType {get;}
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartType {get;}
StartupType               Property      Microsoft.PowerShell.Commands.ServiceStartupType {get;set;}
Status                    Property      System.ServiceProcess.ServiceControllerStatus Status {get;}
UserName                  Property      System.String {get;set;}
ToString                  ScriptMethod  System.Object ToString();
```

### Exemple 2 : récupérer les membres des objets de service

Cet exemple obtient tous les membres (propriétés et méthodes) des objets de service récupérés par l' `Get-Service` applet de commande, y compris les membres intrinsèques, tels que **PSBase** , **PSObject** , et les méthodes **get_** et **set_** .

```powershell
Get-Service | Get-Member -Force
(Get-Service Schedule).PSBase
```

La `Get-Member` commande utilise le paramètre **force** pour ajouter à l’affichage les membres intrinsèques et les membres générés par le compilateur des objets. Vous pouvez utiliser ces propriétés et méthodes de la même façon que vous utilisez une méthode adaptée de l'objet. La deuxième commande montre comment afficher la valeur de la propriété PSBase du service Schedule.

### Exemple 3 : récupérer les membres étendus des objets de service

Cet exemple obtient les méthodes et les propriétés des objets de service qui ont été étendus à l’aide d’un `Types.ps1xml` fichier ou de l’applet de commande `Add-Member` .

```powershell
Get-Service | Get-Member -View Extended
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name             MemberType    Definition
----             ----------    ----------
Name             AliasProperty Name = ServiceName
RequiredServices AliasProperty RequiredServices = ServicesDependedOn
ToString         ScriptMethod  System.Object ToString();
```

La `Get-Member` commande utilise le paramètre **View** pour obtenir uniquement les membres étendus des objets de service. Dans ce cas, le membre étendu est la propriété **Name** , qui est une propriété alias de la propriété **ServiceName** .

### Exemple 4 : récupérer les propriétés de script des objets du journal des événements

Cet exemple obtient les propriétés de script des objets du journal des événements dans le journal système dans observateur d’événements.

```powershell
Get-WinEvent -LogName System -MaxEvents 1 | Get-Member -MemberType NoteProperty
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.EventLogRecord

Name    MemberType   Definition
----    ----------   ----------
Message NoteProperty string Message=The machine-default permission settings do not grant Local ...
```

Le paramètre **MemberType** obtient uniquement les objets dont la valeur est `NoteProperty` pour leur propriété **MemberType** .

La commande retourne la propriété **message** de l’objet **EventLogRecord** .

### Exemple 5 : obtenir des objets avec une propriété spécifiée

Cet exemple obtient les objets qui ont une propriété **MachineName** dans la sortie d’une liste d’applets de commande.

La `$list` variable contient une liste d’applets de commande à évaluer. L’instruction **foreach** appelle chaque commande et envoie les résultats à `Get-Member` . Le paramètre **Name** limite les résultats de `Get-Member` aux membres qui portent le nom **MachineName** .

```powershell
$list = "Get-Process", "Get-Service", "Get-Culture", "Get-PSDrive", "Get-ExecutionPolicy"
foreach ($cmdlet in $list) {& $cmdlet | Get-Member -Name MachineName}
```

```Output
   TypeName: System.Diagnostics.Process

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;}

   TypeName: System.Service.ServiceController#StartupType

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;set;}
```

Les résultats indiquent que seuls les objets de processus et les objets de service ont une propriété **MachineName** .

### Exemple 6 : obtenir des membres pour un tableau

Cet exemple montre comment rechercher les membres d’un tableau d’objets. Lorsque vous dirigez et tableau d’objets vers `Get-Member` , l’applet de commande retourne une liste de membres pour chaque type d’objet unique dans le tableau.
Si vous transmettez le tableau à l’aide du paramètre **InputObject** , le tableau est traité comme un objet unique.

```powershell
$array = @(1,'hello')
$array | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType Definition
----        ---------- ----------
CompareTo   Method     int CompareTo(System.Object value), int CompareTo(int value), int ICompar...
Equals      Method     bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int...
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
GetTypeCode Method     System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method     bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method     byte IConvertible.ToByte(System.IFormatProvider provider)
...

   TypeName: System.String

Name                 MemberType            Definition
----                 ----------            ----------
Clone                Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo            Method                int CompareTo(System.Object value), int CompareTo(str...
Contains             Method                bool Contains(string value), bool Contains(string val...
CopyTo               Method                void CopyTo(int sourceIndex, char[] destination, int ...
EndsWith             Method                bool EndsWith(string value), bool EndsWith(string val...
EnumerateRunes       Method                System.Text.StringRuneEnumerator EnumerateRunes()
Equals               Method                bool Equals(System.Object obj), bool Equals(string va...
GetEnumerator        Method                System.CharEnumerator GetEnumerator(), System.Collect...
GetHashCode          Method                int GetHashCode(), int GetHashCode(System.StringCompa...
...
```

```powershell
Get-Member -InputObject $array
```

```Output
   TypeName: System.Object[]

Name           MemberType            Definition
----           ----------            ----------
Add            Method                int IList.Add(System.Object value)
Address        Method                System.Object&, System.Private.CoreLib, Version=4.0.0.0, Cu...
Clear          Method                void IList.Clear()
Clone          Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo      Method                int IStructuralComparable.CompareTo(System.Object other, Sy...
...
```

La `$array` variable contient un objet **Int32** et un objet **String** , comme indiqué lorsque le tableau est dirigé vers `Get-Member` . Lorsque `$array` est passé à l’aide du paramètre **InputObject** `Get-Member` , retourne les membres du type **Object []** .

### Exemple 7 : déterminer les propriétés d’objet que vous pouvez définir

Cet exemple montre comment déterminer les propriétés d'un objet qui peuvent être modifiées.

```powershell
$File = Get-Item c:\test\textFile.txt
$File.PSObject.Properties | Where-Object isSettable | Select-Object -Property Name
```

```Output
Name
----
PSPath
PSParentPath
PSChildName
PSDrive
PSProvider
PSIsContainer
IsReadOnly
CreationTime
CreationTimeUtc
LastAccessTime
LastAccessTimeUtc
LastWriteTime
LastWriteTimeUtc
Attributes
```

## PARAMETERS

### -Force

Ajoute les membres intrinsèques et les méthodes **get_** et **set_** générées par le compilateur à l’affichage.
La liste suivante décrit les propriétés ajoutées lorsque vous utilisez le paramètre **force** :

- **PSBase** : propriétés d’origine de l’objet .net sans extension ou adaptation. Il s’agit des propriétés définies pour la classe d’objet.
- **PSAdapted** . Propriétés et méthodes définies dans le système de type étendu PowerShell.
- **PSExtended** . Les propriétés et les méthodes qui ont été ajoutées dans les `Types.ps1xml` fichiers ou à l’aide de l’applet de commande `Add-Member` .
- **PSObject** . Adaptateur qui convertit l’objet de base en objet de **PSObject** PowerShell.
- **PSTypeNames** . liste des types d'objets qui décrivent l'objet, par ordre de spécificité. Lors de la mise en forme de l’objet, PowerShell recherche les types dans les `Format.ps1xml` fichiers dans le répertoire d’installation de PowerShell ( `$PSHOME` ). Il utilise la définition de la mise en forme du premier type qu'il trouve.

Par défaut, `Get-Member` obtient ces propriétés dans toutes les vues, à l’exception de **base** et **adaptée** , mais ne les affiche pas.

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

### -InputObject

Spécifie l'objet dont les membres sont récupérés.

L’utilisation du paramètre **InputObject** n’est pas identique à la conduite d’un objet à `Get-Member` . Les différences sont les suivantes :

- Quand vous dirigez une collection d’objets vers `Get-Member` , `Get-Member` obtient les membres des objets individuels dans la collection, tels que les propriétés de chaque chaîne dans un tableau de chaînes.
- Quand vous utilisez **InputObject** pour envoyer une collection d’objets, `Get-Member` obtient les membres de la collection, tels que les propriétés du tableau dans un tableau de chaînes.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

Spécifie le type de membre que cette applet de commande obtient. La valeur par défaut est **Tous** .

Les valeurs valides pour ce paramètre sont :

- AliasProperty
- CodeProperty
- Propriété
- NoteProperty
- ScriptProperty
- Propriétés
- PropertySet
- Méthode
- CodeMethod
- ScriptMethod
- Méthodes
- ParameterizedProperty
- PEL
- Événement
- Dynamique
- Tous

Pour plus d’informations sur ces valeurs, consultez [énumération PSMemberTypes](/dotnet/api/system.management.automation.psmembertypes).

Certains objets n'ont pas chaque type de membre. Si vous spécifiez un type de membre que l’objet n’a pas, PowerShell retourne une valeur null.

Pour obtenir les types de membres associés, tels que les membres étendus, utilisez le paramètre **View** . Si vous utilisez le paramètre **MemberType** avec les paramètres **statiques** ou de **vue** , `Get-Member` obtient les membres qui appartiennent aux deux ensembles.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Spécifie les noms d'une ou plusieurs propriétés ou méthodes de l'objet. `Get-Member` Obtient uniquement les propriétés et les méthodes spécifiées.

Si vous utilisez le paramètre **Name** avec les paramètres **MemberType** , **View** ou **static** , `Get-Member` obtient uniquement les membres qui répondent aux critères de tous les paramètres.

Pour obtenir un membre statique par nom, utilisez le paramètre **static** avec le paramètre **Name** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Static

Indique que cette applet de commande obtient uniquement les propriétés et les méthodes statiques de l’objet. Les méthodes et propriétés statiques sont définies sur la classe d'objets, et non sur une instance particulière de la classe.

Si vous utilisez le paramètre **static** avec le paramètre **View** , le paramètre **View** est ignoré.
Si vous utilisez le paramètre **static** avec le paramètre **MemberType** , `Get-Member` obtient uniquement les membres qui appartiennent aux deux ensembles.

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

### -Afficher

Spécifie que cette applet de commande obtient uniquement les propriétés et les méthodes de types spécifiques. Spécifiez une ou plusieurs des valeurs. La valeur par défaut est **adapted** , **Extended** .

Les valeurs valides pour ce paramètre sont :

- Base. Obtient uniquement les propriétés et les méthodes d’origine de l’objet .NET (sans extension ou adaptation).
- Adaptées. Obtient uniquement les propriétés et méthodes définies dans le système de type étendu PowerShell.
- Longues. Obtient uniquement les propriétés et les méthodes qui ont été ajoutées dans un `Types.ps1xml` fichier ou à l’aide de l’applet de commande `Add-Member` .
- Tout le monde. obtient les membres des vues Base, Adapted et Extended.

Le paramètre **View** détermine les membres récupérés, pas uniquement l’affichage de ces membres.

Pour connaître les types de membre particuliers, tels que les propriétés de script, utilisez le paramètre **MemberType** . Si vous utilisez les paramètres **MemberType** et **View** dans la même commande, `Get-Member` obtient les membres qui appartiennent aux deux ensembles. Si vous utilisez les paramètres **static** et **View** dans la même commande, le paramètre **View** est ignoré.

```yaml
Type: System.Management.Automation.PSMemberViewTypes
Parameter Sets: (All)
Aliases:
Accepted values: Extended, Adapted, Base, All

Required: False
Position: Named
Default value: Adapted, Extended
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. Management. Automation. PSObject

Vous pouvez diriger n’importe quel objet vers `Get-Member` .

## SORTIES

### Microsoft. PowerShell. Commands. MemberDefinition

`Get-Member` retourne un objet pour chaque propriété ou méthode qu’il obtient.

## REMARQUES

Vous pouvez obtenir des informations sur un objet collection en utilisant le paramètre **InputObject** ou en canalisant l’objet, précédé d’une virgule, vers `Get-Member` .

Vous pouvez utiliser la `$This` variable Automatic dans des blocs de script qui définissent les valeurs des nouvelles propriétés et méthodes. La `$This` variable fait référence à l’instance de l’objet auquel les propriétés et les méthodes sont ajoutées. Pour plus d’informations sur la `$This` variable, consultez [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

Si vous transmettez un objet représentant un _type_ , comme un littéral de type comme `[int]` , retourne des `Get-Member` informations sur le `[System.RuntimeType]` type. Toutefois, lorsque vous utilisez le paramètre **static** , `Get-Member` retourne les membres statiques du type spécifique représenté par l' `System.RuntimeType` instance.

## LIENS CONNEXES

[Add-Member](Add-Member.md)
