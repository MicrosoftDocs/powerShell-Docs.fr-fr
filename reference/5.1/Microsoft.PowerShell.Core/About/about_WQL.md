---
description: Décrit le langage de requêtes WMI (WQL) qui peut être utilisé pour obtenir des objets WMI dans Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207881"
---
# <a name="about-wql"></a>À propos de WQL

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit le langage de requêtes WMI (WQL) qui peut être utilisé pour obtenir des objets WMI dans Windows PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

WQL est le langage de requête Windows Management Instrumentation (WMI), qui est le langage utilisé pour obtenir des informations à partir de WMI.

Vous n’êtes pas obligé d’utiliser WQL pour exécuter une requête WMI dans Windows PowerShell.
Au lieu de cela, vous pouvez utiliser les paramètres des applets de commande Get-WmiObject ou Get-CimInstance. Les requêtes WQL sont un peu plus rapides que les commandes de Get-WmiObject standard et les performances améliorées sont évidentes lorsque les commandes s’exécutent sur des centaines de systèmes. Toutefois, veillez à ce que le temps que vous consacrez à l’écriture d’une requête WQL réussie n’compense pas l’amélioration des performances.

Les instructions WQL de base dont vous avez besoin pour utiliser WQL sont Select, where et from.

## <a name="when-to-use-wql"></a>QUAND UTILISER WQL

Lorsque vous travaillez avec WMI, et en particulier avec WQL, n’oubliez pas que vous utilisez également Windows PowerShell. Souvent, si une requête WQL ne fonctionne pas comme prévu, il est plus facile d’utiliser une commande Windows PowerShell standard que de déboguer la requête WQL.

À moins que vous ne retournaiez de grandes quantités de données à partir de systèmes distants limités en bande passante, il est rarement productif de consacrer des heures à une requête WQL compliquée et compliquée lorsqu’il existe une applet de commande Windows parfaitement acceptable qui fait la même chose, si un peu plus lentement.

## <a name="using-the-select-statement"></a>UTILISATION DE L’INSTRUCTION SELECT

Une requête WMI classique commence par une instruction SELECT qui obtient toutes les propriétés ou des propriétés particulières d’une classe WMI. Pour sélectionner toutes les propriétés d’une classe WMI, utilisez un astérisque ( \* ). Le mot clé from spécifie la classe WMI.

Une instruction SELECT a le format suivant :

```
Select <property> from <WMI-class>
```

Par exemple, l’instruction SELECT suivante sélectionne toutes les propriétés (*) des instances de la classe WMI Win32_Bios.

```
Select * from Win32_Bios
```

Pour sélectionner une propriété particulière d’une classe WMI, placez le nom de la propriété entre les mots clés SELECT et from.

La requête suivante sélectionne uniquement le nom du BIOS de la classe WMI Win32_Bios. La commande enregistre la requête dans la variable $queryName.

```
Select Name from Win32_Bios
```

Pour sélectionner plusieurs propriétés, utilisez des virgules pour séparer les noms de propriété.
La requête WMI suivante sélectionne le nom et la version de la classe Win32_Bios WMI. La commande enregistre la requête dans la variable $queryNameVersion.

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a>UTILISATION DE LA REQUÊTE WQL

Il existe trois façons d’utiliser la requête WQL dans la commande Windows PowerShell.

- Utiliser l’applet de commande Get-WmiObject
- Utiliser l’applet de commande Get-CimInstance
- Utilisez l’accélérateur de type [WmiSearcher].

## <a name="using-the-get-wmiobject-cmdlet"></a>UTILISATION DE L’APPLET DE COMMANDE « OBTIENT-WMIOBJECT »

La méthode la plus simple pour utiliser la requête WQL consiste à la placer entre guillemets (sous forme de chaîne), puis à utiliser la chaîne de requête comme valeur du paramètre de requête de l’applet de commande Get-WmiObject, comme indiqué dans l’exemple suivant.

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Vous pouvez également enregistrer l’instruction WQL dans une variable, puis utiliser la variable comme valeur du paramètre de requête, comme indiqué dans la commande suivante.

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

Vous pouvez utiliser l’un ou l’autre format avec n’importe quelle instruction WQL. La commande suivante utilise la requête de la variable $queryName pour obtenir uniquement les propriétés Name et version du BIOS système.

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

N’oubliez pas que vous pouvez utiliser les paramètres de l’applet de commande Get-WmiObject pour obtenir le même résultat. Par exemple, la commande suivante obtient également les valeurs des propriétés Name et version des instances de la classe Win32_Bios WMI.

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a>UTILISATION DE L’APPLET DE COMMANDE CIMINSTANCE

À compter de Windows PowerShell 3,0, vous pouvez utiliser l’applet de commande Get-CimInstance pour exécuter des requêtes WQL.

Get-CimInstance obtient des instances de classes conformes à CIM, y compris les classes WMI. Les applets de commande CIM, ont introduit Windows PowerShell 3,0, effectuent les mêmes tâches que les applets de commande WMI. Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme Common Information Model (CIM), qui permettent aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs Windows et les ordinateurs qui exécutent d’autres systèmes d’exploitation.

La commande suivante utilise l’applet de commande Get-CimInstance pour exécuter une requête WQL.

Toute requête WQL qui peut être utilisée avec Get-WmiObject peut également être utilisée avec la fonction CimInstance.

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Get-CimInstance retourne un objet CimInstance à la place du ManagementObject retourné par Get-WmiObject, mais les objets sont très similaires.

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a>UTILISATION de l’accélérateur de TYPE [WmiSearcher]

L’accélérateur de type [WmiSearcher] crée un objet ManagementObjectSearcher à partir d’une chaîne d’instruction WQL. L’objet ManagementObjectSearcher a de nombreuses propriétés et méthodes, mais la méthode la plus basique est la méthode d’extraction, qui appelle la requête WMI spécifiée et retourne les objets résultants.

À l’aide de [WmiSearcher], vous pouvez accéder facilement à la classe ManagementObjectSearcher .NET Framework. Cela vous permet d’interroger WMI et de configurer le mode d’exécution de la requête.

Pour utiliser l’accélérateur de type [WmiSearcher] :

1. Effectuez un cast de la chaîne WQL en objet ManagementObjectSearcher.
2. Appelez la méthode d’extraction de l’objet ManagementObjectSearcher.

Par exemple, la commande suivante convertit la requête « sélectionner tout », enregistre le résultat dans la variable $bios, puis appelle la méthode d’extraction de l’objet ManagementObjectSearcher dans la variable $bios.

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Remarque : seules les propriétés d’objet sélectionnées sont affichées par défaut. Ces propriétés sont définies dans le fichier XML Types.ps1.

Vous pouvez utiliser l’accélérateur de type [WmiSearcher] pour effectuer un cast de la requête ou de la variable. Dans l’exemple suivant, l’accélérateur de type [WmiSearcher] est utilisé pour effectuer un cast de la variable. Le résultat est le même.

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Quand vous utilisez l’accélérateur de type [WmiSearcher], il modifie la chaîne de requête en un objet ManagementObjectSearcher, comme indiqué dans les commandes suivantes.

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

Ce format de commande fonctionne sur toutes les requêtes. La commande suivante obtient la valeur de la propriété Name de la classe WMI Win32_Bios.

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

Vous pouvez effectuer cette opération dans une commande unique, bien que la commande soit un peu plus difficile à interpréter.

Dans ce format, vous utilisez l’accélérateur de type [WmiSearcher] pour effectuer un cast de la chaîne de requête WQL en ManagementObjectSearcher, puis appeler la méthode d’extraction sur l’objet, le tout dans une même commande. Les parenthèses () qui encadrent la chaîne transtypée dirigent Windows PowerShell pour effectuer un cast de la chaîne avant d’appeler la méthode.

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a>UTILISATION DE L’INSTRUCTION WHERE WQL DE BASE

Une instruction WHERE établit des conditions pour les données retournées par une instruction SELECT.

L’instruction WHERE a le format suivant :

```
where <property> <operator> <value>
```

Par exemple :

```
where Name = 'Notepad.exe'
```

L’instruction WHERE est utilisée avec l’instruction SELECT, comme illustré dans l’exemple suivant.

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

Lorsque vous utilisez l’instruction WHERE, le nom et la valeur de la propriété doivent être précis.

Par exemple, la commande suivante obtient les processus du bloc-notes sur l’ordinateur local.

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

Toutefois, la commande suivante échoue, car le nom du processus comprend l’extension de nom de fichier « . exe ».

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a>OPÉRATEURS DE COMPARAISON D’INSTRUCTIONS WHERE

Les opérateurs suivants sont valides dans une instruction WQL Where.

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

Il existe d’autres opérateurs, mais ceux-ci sont utilisés pour effectuer des comparaisons.

Par exemple, la requête suivante sélectionne les propriétés Name et Priority dans les processus de la classe Win32_Process, où la priorité du processus est supérieure ou égale à 11. L’applet de commande Get-WmiObject exécute la requête.

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a>UTILISATION DES OPÉRATEURS WQL DANS LE PARAMÈTRE FILTER

Les opérateurs WQL peuvent également être utilisés dans la valeur du paramètre Filter des applets de commande Get-WmiObject ou Get-CimInstance, ainsi que dans la valeur des paramètres de requête de ces applets de commande.

Par exemple, la commande suivante obtient les propriétés Name et ProcessID des cinq derniers processus dont les valeurs ProcessID sont supérieures à 1004. La commande utilise le paramètre Filter pour spécifier la condition ProcessID.

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a>UTILISATION DE L’OPÉRATEUR LIKE

L’opérateur Like vous permet d’utiliser des caractères génériques pour filtrer les résultats d’une requête WQL.

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

Lorsque l’opérateur Like est utilisé sans caractères génériques ou opérateurs de plage, il se comporte comme l’opérateur d’égalité (=) et retourne des objets uniquement lorsqu’il s’agit d’une correspondance exacte pour le modèle.

Vous pouvez combiner l’opération de plage avec le caractère générique de pourcentage pour créer des filtres simples, mais puissants.

### <a name="like-operator-examples"></a>LIKE, EXEMPLES D’OPÉRATEURS

#### <a name="example-1-range"></a>EXEMPLE 1 : [ \<range> ]

Les commandes suivantes démarrent le bloc-notes, puis recherchent une instance de la classe Win32_Process dont le nom commence par une lettre comprise entre « H » et « N » (non-respect de la casse).

La requête doit retourner n’importe quel processus de Hotpad.exe via Notepad.exe.

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a>EXEMPLE 2 : [ \<range> ] et%

Les commandes suivantes sélectionnent tous les processus dont le nom commence par une lettre comprise entre A et P (non-respect de la casse) suivi de zéro, une ou plusieurs lettres dans n’importe quelle combinaison.

L’applet de commande Get-WmiObject exécute la requête, l’applet de commande Select-Object obtient les propriétés Name et ProcessID, et l’applet de commande Sort-Object trie les résultats par ordre alphabétique par nom.

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a>EXEMPLE 3 : pas dans la plage (^)

La commande suivante obtient les processus dont les noms ne commencent pas par les lettres suivantes : A, S, W, P, R, C, U, N

et ont suivi zéro ou plusieurs lettres.

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a>EXEMPLE 4 : tous les caractères--ou aucun (%)

Les commandes suivantes obtiennent des processus dont le nom commence par « Calc ».
Le symbole% dans WQL est équivalent au symbole astérisque ( \* ) dans les expressions régulières.

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a>EXEMPLE 5 : un caractère (_)

Les commandes suivantes obtiennent les processus dont les noms ont le modèle suivant, « c_lc.exe », où le caractère de soulignement représente un caractère quelconque. Ce modèle met en correspondance n’importe quel nom de calc.exe via czlc.exe ou c9lc.exe, mais ne correspond pas aux noms dans lesquels « c » et « l » sont séparés par plusieurs caractères.

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a>EXEMPLE 6 : correspondance exacte

Les commandes suivantes obtiennent des processus nommés WLIDSVC.exe. Même si la requête utilise le mot clé like, elle nécessite une correspondance exacte, car la valeur n’inclut pas de caractères génériques.

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a>UTILISATION DE L’OPÉRATEUR OR

Pour spécifier plusieurs conditions indépendantes, utilisez le mot clé ou. Le mot clé ou apparaît dans la clause WHERE. Il effectue une opération inclusif ou sur deux (ou plus) conditions et retourne des éléments qui répondent à l’une des conditions.

L’opérateur or a le format suivant :

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

Par exemple, les commandes suivantes récupèrent toutes les instances de la classe Win32_Process WMI, mais les retournent uniquement si le nom du processus est winword.exe ou excel.exe.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

L’instruction ou peut être utilisée avec plus de deux conditions. Dans la requête suivante, l’instruction ou obtient Winword.exe, Excel.exe ou Powershell.exe.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a>UTILISATION DE L’OPÉRATEUR AND

Pour spécifier plusieurs conditions connexes, utilisez le mot clé and. Le mot clé et apparaît dans la clause WHERE. Elle retourne les éléments qui remplissent toutes les conditions.

L’opérateur and a le format suivant :

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

Par exemple, les commandes suivantes obtiennent des processus dont le nom est « Winword.exe » et l’ID de processus 6512.

Notez que les commandes utilisent l’applet de commande Get-CimInstance.

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

Tous les opérateurs, y compris les opérateurs like, sont valides avec les opérateurs or et and. Et, vous pouvez combiner les opérateurs or et and dans une seule requête avec des parenthèses qui indiquent à Windows PowerShell les clauses à traiter en premier.

Cette commande utilise le caractère de continuation Windows PowerShell (') divise la commande en deux lignes.

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a>RECHERCHE DE VALEURS NULL

La recherche de valeurs NULL dans WMI est complexe, car elle peut entraîner des résultats imprévisibles. NULL n’est pas égal à zéro et n’est pas équivalent ou n’est pas une chaîne vide. Certaines propriétés de classe WMI sont initialisées et d’autres pas. par conséquent, une recherche de valeur NULL peut ne pas fonctionner pour toutes les propriétés.

Pour rechercher des valeurs NULL, utilisez l’opérateur is avec la valeur « null ».

Par exemple, les commandes suivantes obtiennent des processus qui ont une valeur null pour la propriété IntallDate. Les commandes retournent de nombreux processus.

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

À l’inverse, la commande suivante obtient les comptes d’utilisateur qui ont une valeur null pour la propriété Description. Cette commande ne retourne aucun compte d’utilisateur, même si la plupart des comptes d’utilisateur n’ont aucune valeur pour la propriété Description.

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

Pour rechercher les comptes d’utilisateur qui n’ont pas de valeur pour la propriété Description, utilisez l’opérateur d’égalité pour obtenir une chaîne vide. Pour représenter la chaîne vide, utilisez deux guillemets simples consécutifs.

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a>UTILISATION DE TRUE OU FALSE

Pour récupérer des valeurs booléennes dans les propriétés des objets WMI, utilisez true et false.
Elles ne sont pas sensibles à la casse.

La requête WQL suivante retourne uniquement les comptes d’utilisateurs locaux d’un ordinateur joint à un domaine.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

Pour rechercher les comptes de domaine, utilisez la valeur false, comme indiqué dans l’exemple suivant.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a>UTILISATION DU CARACTÈRE D’ÉCHAPPEMENT

WQL utilise la barre oblique inverse ( \) comme caractère d’échappement. Ceci est différent de Windows PowerShell, qui utilise le caractère de soulignement («»).

Les guillemets, et les caractères utilisés pour les guillemets, doivent souvent être échappés afin qu’ils ne soient pas mal interprétés.

Pour rechercher un utilisateur dont le nom comprend un guillemet simple, utilisez une barre oblique inverse pour échapper le guillemet simple, comme indiqué dans la commande suivante.

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

Dans certains cas, la barre oblique inverse doit également être placée dans une séquence d’échappement. Par exemple, les commandes suivantes génèrent une erreur de requête non valide en raison de la barre oblique inverse dans la valeur de légende.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

Pour échapper à la barre oblique inverse, utilisez une deuxième barre oblique inverse, comme indiqué dans la commande suivante.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a>VOIR AUSSI

[about_Special_Characters](about_Special_Characters.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_WMI](about_WMI.md)

[about_WMI_Cmdlets](about_WMI_Cmdlets.md)
