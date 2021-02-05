---
title: Mise en forme, alias, fournisseurs, comparaison
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: Ce chapitre présente les concepts relatifs à la mise en forme de la sortie, aux alias de commandes, aux fournisseurs et aux opérations de comparaison.
ms.openlocfilehash: 5573ca58601af0c6af15736b772a9792d8d77a79
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99596914"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a>Chapitre 5 - Mise en forme, alias, fournisseurs, comparaison

## <a name="requirements"></a>Spécifications

Certains des exemples présentés dans ce chapitre nécessitent le module SQL Server PowerShell. Le module est installé dans le cadre de [SQL Server Management Studio (SSMS)][SMSS]. Il est également utilisé dans les chapitres suivants. Téléchargez-le et installez-le sur votre ordinateur dans un environnement lab Windows 10.

## <a name="format-right"></a>Mettre en forme à droite

Dans le chapitre 4, vous avez appris à filtrer aussi loin que possible à gauche. La règle de mise en forme manuelle de la sortie d’une commande est similaire à cette règle, sauf qu’elle doit se produire aussi loin que possible à droite.

Les commandes de mise en forme les plus courantes sont `Format-Table` et `Format-List`. `Format-Wide` et `Format-Custom` peuvent également être utilisées, mais sont moins courantes.

Comme mentionné dans le chapitre 3, une commande qui retourne plus de quatre propriétés a comme valeur par défaut une liste, sauf si une mise en forme personnalisée est utilisée.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

Utilisez l’applet de commande `Format-Table` pour remplacer manuellement la mise en forme et afficher la sortie dans une table plutôt que dans une liste.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

La sortie par défaut de `Get-Service` est trois propriétés dans une table.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Utilisez l’applet de commande `Format-List` pour remplacer la mise en forme par défaut et retourner les résultats dans une liste.

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

Notez que la simple redirection de `Get-Service` vers `Format-List` lui a fait retourner des propriétés supplémentaires. Cela ne se produit pas avec chaque commande en raison de la façon dont la mise en forme de cette commande particulière est configurée en arrière-plan.

La première chose à connaître avec les applets de commande de mise en forme est qu’elles produisent des objets de mise en forme différents des objets normaux dans PowerShell.

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

Cela signifie que les commandes de mise en forme ne peuvent pas être redirigées vers la plupart des autres commandes. Elles peuvent être redirigées vers certaines des commandes `Out-*`, mais c’est à peu près tout. C’est pourquoi vous voulez effectuer une mise en forme à la toute fin de la ligne (mettre en forme à droite).

## <a name="aliases"></a>Alias

Dans PowerShell, un alias est un nom plus court pour une commande. PowerShell comprend un ensemble d’alias intégrés. Vous pouvez également définir vos propres alias.

L’applet de commande `Get-Alias` est utilisée pour rechercher des alias. Si vous connaissez déjà l’alias d’une commande, le paramètre **Name** est utilisé pour déterminer la commande à laquelle l’alias est associé.

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

Vous pouvez spécifier plusieurs alias pour la valeur du paramètre **Name**.

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

Vous verrez souvent que le paramètre **Name** est omis car il s’agit d’un paramètre positionnel.

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

Si vous voulez rechercher des alias pour une commande, vous devez utiliser le paramètre **Definition**.

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

Il n’est pas possible d’utiliser le paramètre **Definition** de façon positionnelle. Il doit donc être spécifié.

Les alias peuvent vous faire gagner quelques séquences de touches et ils fonctionnent correctement quand vous tapez des commandes dans la console.
Ils ne doivent pas être utilisés dans des scripts ou du code que vous enregistrez ou que vous partagez avec d’autres utilisateurs. Comme mentionné plus haut dans ce document, l’utilisation de noms d’applets de commande et de paramètres complets est auto-documentée et est plus facile à comprendre.

Soyez prudent lors de la création de vos propres alias car ils n’existent que dans votre session PowerShell actuelle sur votre ordinateur.

## <a name="providers"></a>Fournisseurs

Dans PowerShell, un fournisseur est une interface qui permet d’accéder à un magasin de données comme avec un système de fichiers. Il existe un certain nombre de fournisseurs intégrés dans PowerShell.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

Comme vous pouvez le voir dans les résultats précédents, il existe des fournisseurs intégrés pour le registre, les alias, les variables d’environnement, le système de fichiers, les fonctions, les variables, les certificats et WSMan.

Les lecteurs réels utilisés par ces fournisseurs pour exposer leur magasin de données peuvent être déterminés à l’aide de l’applet de commande `Get-PSDrive`. L’applet de commande `Get-PSDrive` affiche non seulement les lecteurs exposés par les fournisseurs, mais également les lecteurs logiques Windows, notamment les lecteurs mappés à des partages réseau.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

Les modules tiers comme le module Active Directory PowerShell et le module SQL Server PowerShell ajoutent tous les deux leur propre fournisseur PowerShell et PSDrive.

Importez les modules Active Directory et SQL Server PowerShell.

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

Vérifiez si des fournisseurs PowerShell supplémentaires ont été ajoutés.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

Notez que dans le jeu de résultats précédent, il existe désormais deux nouveaux fournisseurs PowerShell : un pour Active Directory et un autre pour SQL Server.

Un PSDrive a également été ajouté pour chacun de ces modules.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

Les PSDrive sont accessibles exactement comme un système de fichiers traditionnel.

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a>Opérateurs de comparaison

PowerShell contient un certain nombre d’opérateurs de comparaison utilisés pour comparer des valeurs ou rechercher des valeurs qui correspondent à certains modèles. Le tableau 5-1 contient une liste d’opérateurs de comparaison disponibles dans PowerShell.

|    Opérateur    |                          Définition                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | Égal à                                                     |
| `-ne`          | Différent de                                                 |
| `-gt`          | Supérieur à                                                 |
| `-ge`          | Supérieur ou égal à                                     |
| `-lt`          | Inférieur à                                                    |
| `-le`          | Inférieur ou égal à                                        |
| `-Like`        | Correspondance à l’aide du caractère générique `*`                       |
| `-NotLike`     | Absence de correspondance à l’aide du caractère générique `*`              |
| `-Match`       | Correspond à l’expression régulière spécifiée                     |
| `-NotMatch`    | Ne correspond pas à l’expression régulière spécifiée              |
| `-Contains`    | Détermine si la collection contient une valeur spécifiée        |
| `-NotContains` | Détermine si une collection ne contient pas de valeur spécifique |
| `-In`          | Détermine si une valeur spécifiée se trouve dans une collection           |
| `-NotIn`       | Détermine si une valeur spécifiée ne se trouve pas dans une collection       |
| `-Replace`     | Remplace la valeur spécifiée                                 |

Tous les opérateurs listés dans le tableau 5-1 ne respectent pas la casse. Placez un `c` devant l’opérateur listé dans le tableau 5-1 pour qu’il respecte la casse. Par exemple, `-ceq` est la version qui respecte la casse de l’opérateur de comparaison `-eq`.

La casse appropriée « PowerShell » est égale à « PowerShell » en minuscules lors de l’utilisation de l’opérateur de comparaison Égal à.

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

Elle n’est pas égale à l’utilisation de la version qui respecte la casse de l’opérateur de comparaison Égal à.

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

L’opérateur de comparaison Différent de inverse la condition.

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

Les opérateurs Supérieur à, Supérieur ou égal à, Inférieur à et Inférieur ou égal à fonctionnent tous avec des chaînes ou des valeurs numériques.

```powershell
5 -gt 5
```

```Output
False
```

L’utilisation de l’opérateur Supérieur ou égal à au lieu de Supérieur à avec l’exemple précédent retourne la valeur **booléenne** true puisque cinq est égal à cinq.

```powershell
5 -ge 5
```

```Output
True
```

En fonction des résultats des deux exemples précédents, vous pouvez probablement deviner comment les deux opérateurs Inférieur et Inférieur ou égal à fonctionnent.

```powershell
5 -lt 10
```

```Output
True
```

Les opérateurs `-Like` et `-Match` peuvent prêter à confusion, même pour les utilisateurs expérimentés de PowerShell. `-Like` est utilisé avec les caractères génériques `*` et `?` pour effectuer des correspondances « Like ».

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

`-Match` utilise une expression régulière pour effectuer la correspondance.

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

Utilisez l’opérateur de plage pour stocker les nombres 1 à 10 dans une variable.

```powershell
$Numbers = 1..10
```

```Output
```

Déterminez si la variable `$Numbers` inclut 15.

```powershell
$Numbers -contains 15
```

```Output
False
```

Déterminez si elle inclut le nombre 10.

```powershell
$Numbers -contains 10
```

```Output
True
```

`-NotContains` inverse la logique pour voir si la variable `$Numbers` ne contient pas de valeur.

```powershell
$Numbers -notcontains 15
```

```Output
True
```

L’exemple précédent retourne la valeur **booléenne** true car il est vrai que la variable `$Numbers` ne contient pas 15. Elle contient toutefois le nombre 10, donc le résultat est false quand elle est testée.

```powershell
$Numbers -notcontains 10
```

```Output
False
```

L’opérateur de comparaison « In » a été introduit pour la première fois dans PowerShell version 3.0. Il est utilisé pour déterminer si une valeur est présente dans (« in ») un tableau. La variable `$Numbers` est un tableau car elle contient plusieurs valeurs.

```powershell
15 -in $Numbers
```

```Output
False
```

En d’autres termes, `-in` effectue le même test que l’opérateur de comparaison Contains excepté de le sens contraire.

```powershell
10 -in $Numbers
```

```Output
True
```

Comme 15 ne se trouve pas dans le tableau `$Numbers`, la valeur false est retournée dans l’exemple suivant.

```powershell
15 -in $Numbers
```

```Output
False
```

Tout comme l’opérateur `-contains`, `not` inverse la logique de l’opérateur `-in`.

```powershell
10 -notin $Numbers
```

```Output
False
```

L’exemple précédent retourne la valeur false car le tableau `$Numbers` inclut 10 alors que la condition a été testée pour déterminer s’il ne contenait pas 10.

Comme 15 n’est pas dans (« not in ») le tableau `$Numbers`, il retourne la valeur **booléenne** true.

```powershell
15 -notin $Numbers
```

```Output
True
```

L’opérateur `-replace` fait exactement ce que vous pensez. Il est utilisé pour remplacer un élément. La spécification d’une seule valeur remplace cette valeur par rien. Dans l’exemple suivant, je remplace « Shell » par rien.

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

Si vous voulez remplacer une valeur par une autre valeur, spécifiez la nouvelle valeur après le modèle que vous voulez remplacer. SQL Saturday à Baton Rouge est un événement dont j’essaie de parler chaque année. Dans l’exemple suivant, je remplace le mot « Saturday » par l’abréviation « Sat ».

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

Il existe également des méthodes comme **Replace()** qui peuvent être utilisées pour remplacer des éléments de la même façon que l’opérateur Replace. Toutefois, l’opérateur `-Replace` n’est pas sensible à la casse par défaut, alors que la méthode **Replace()** l’est.

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

Notez que le mot « Saturday » n’a pas été remplacé dans l’exemple précédent. En effet, il était spécifié dans une casse différente de l’original. Quand le mot « Saturday » est spécifié dans la même casse que l’original, la méthode **Replace()** le remplace comme prévu.

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

Soyez prudent quand vous utilisez des méthodes pour transformer des données, car vous pouvez rencontrer des problèmes imprévus, comme l’échec du Test de Turquie (_Turkey Test_). Pour obtenir un exemple, consultez l’article de blog intitulé [Using Pester to Test PowerShell Code with Other Cultures][] (Utilisation de Pester pour tester du code PowerShell avec d’autres cultures). Je vous recommande d’utiliser autant que possible un opérateur plutôt qu’une méthode afin d’éviter ces types de problèmes.

Alors que les opérateurs de comparaison peuvent être utilisés comme indiqué dans les exemples précédents, je les utilise normalement avec l’applet de commande `Where-Object` pour effectuer un certain type de filtrage.

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez appris un certain nombre de rubriques différentes permettant d’inclure la mise en forme à droite, des alias, des fournisseurs et des opérateurs de comparaison.

## <a name="review"></a>Révision

1. Pourquoi est-il nécessaire d’effectuer une mise en forme aussi loin que possible à droite ?
1. Comment déterminer l’applet de commande réelle qui correspond à l’alias `%` ?
1. Pourquoi ne devez-vous pas utiliser des alias dans des scripts que vous enregistrez ou dans du code que vous partagez avec d’autres utilisateurs ?
1. Dressez une liste des répertoires présents sur les lecteurs qui sont associés à l’un des fournisseurs de registre.
1. Quel est l’un des principaux avantages de l’utilisation de l’opérateur Replace au lieu de la méthode replace ?

## <a name="recommended-reading"></a>Lecture recommandée

- [Format-Table][]
- [Format-List][]
- [Format-Wide][]
- [about_Aliases][]
- [about_Providers][]
- [about_Comparison_Operators][]
- [about_Arrays][]

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/ (Utilisation de Pester pour tester du code PowerShell avec d’autres cultures)
