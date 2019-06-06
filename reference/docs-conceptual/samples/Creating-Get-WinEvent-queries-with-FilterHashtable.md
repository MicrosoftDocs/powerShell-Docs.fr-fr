---
ms.date: 03/18/2019
title: Création de requêtes Get-WinEvent avec FilterHashtable
ms.openlocfilehash: 2f598fceb570f189bee776b6ed572b11a6938f64
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66471016"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Création de requêtes Get-WinEvent avec FilterHashtable

Pour lire le billet de blog **Scripting Guy** d’origine du 3 juin 2014, voir [Utiliser FilterHashtable pour filtrer le journal des événements avec PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

Cet article est un extrait du billet de blog d’origine qui explique comment utiliser le paramètre **FilterHashtable** de la cmdlet `Get-WinEvent` pour filtrer les journaux des événements. La cmdlet `Get-WinEvent` de PowerShell représente un puissant moyen de filtrer des journaux de diagnostic et des événements Windows. Les performances sont meilleures quand la requête `Get-WinEvent` utilise le paramètre **FilterHashtable**.

Avec des journaux des événements volumineux, il n’est pas efficace d’envoyer des objets à une commande `Where-Object` à travers le pipeline. Avant PowerShell 6, la cmdlet `Get-EventLog` offrait un autre moyen de récupérer des données de journal. Par exemple, les commandes suivantes sont inefficaces pour filtrer les journaux **Microsoft-Windows-Defrag** :

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

La commande suivante utilise une table de hachage qui améliore les performances :

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Billets de blog sur l’énumération

Cet article explique comment utiliser des valeurs énumérées dans une table de hachage. Pour plus d’informations sur l’énumération, voir ces billets de blog **Scripting Guy**. Pour créer une fonction qui retourne les valeurs énumérées, voir [Énumérations et valeurs](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Pour plus d’informations, voir la [série de billets de blog Scripting Guy sur l’énumération](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Paires clé/valeur de table de hachage

Pour générer des requêtes efficaces, utilisez la cmdlet `Get-WinEvent` avec le paramètre **FilterHashtable**.
**FilterHashtable** prend une table de hachage comme filtre pour obtenir des informations spécifiques dans les journaux des événements Windows. Une table de hachage utilise des paires **clé/valeur**. Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Si les paires **clé/valeur** se trouvent sur la même ligne, elles doivent être séparées par un point-virgule. Si chaque paire **clé/valeur** est sur une ligne distincte, le point-virgule n’est pas nécessaire. Cet article, par exemple, place une paire **clé/valeur** par ligne et n’utilise pas de points-virgules.

Cet exemple utilise plusieurs paires **clé/valeur** du paramètre **FilterHashtable**. La requête comporte **LogName**, **ProviderName**, **Keywords**, **ID** et **Level**.

Les paires **clé/valeur** acceptées sont présentées dans le tableau suivant ainsi que dans la documentation relative au paramètre [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable**.

Le tableau suivant indique les noms de clés et les types de données, et précise si les caractères génériques sont acceptés comme valeurs de données.

| Nom de clé     | Type de données valeur    | Accepte les caractères génériques ? |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | Oui |
| ProviderName | `<String[]>`       | Oui |
| Path         | `<String[]>`       | Non  |
| Mots clés     | `<Long[]>`         | Non  |
| ID           | `<Int32[]>`        | Non  |
| Niveau        | `<Int32[]>`        | Non  |
| StartTime    | `<DateTime>`       | Non  |
| EndTime      | `<DateTime>`       | Non  |
| UserID       | `<SID>`            | Non  |
| Données         | `<String[]>`       | Non  |
| *            | `<String[]>`       | Non  |

## <a name="building-a-query-with-a-hash-table"></a>Créer une requête avec une table de hachage

Pour pouvoir vérifier les résultats et résoudre les problèmes, il est plus facile de créer la table de hachage une paire **clé/valeur** à la fois. La requête récupère des données auprès du journal **Application**. La table de hachage est équivalente à `Get-WinEvent –LogName Application`.

Pour commencer, créez la requête `Get-WinEvent`. Utilisez la paire **clé/valeur** du paramètre **FilterHashtable** avec la clé **LogName** et la valeur **Application**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Continuez à créer la table de hachage avec la clé **ProviderName**. **ProviderName** correspond au nom qui apparaît dans le champ **Source** de **l’Observateur d’événements Windows**, par exemple **.NET Runtime** dans la capture d’écran suivante :

![Image des sources de l’observateur d’événements Windows](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Mettez à jour la table de hachage en incluant la paire **clé/valeur** avec la clé **ProviderName et la valeur **.NET Runtime**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Si votre requête doit récupérer des données dans des journaux des événements archivés, utilisez la clé **Path**. La valeur **Path** spécifie le chemin d’accès complet au fichier journal. Pour plus d’informations, voir le billet de blog **Scripting Guy** [Utiliser PowerShell pour analyser la présence d’erreurs dans des journaux des événements enregistrés](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Utiliser des valeurs énumérées dans une table de hachage

**Keywords** est la clé suivante de la table de hachage. Le type de données **Keywords** est un tableau du type valeur `[long]` contenant un grand nombre. Utilisez la commande suivante pour rechercher la valeur maximale de `[long]` :

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Pour la clé **Keywords**, PowerShell utilise un nombre, et non une chaîne comme **Security**. **L’Observateur d’événements Windows** affiche **Keywords** sous forme de chaînes, alors qu’il s’agit de valeurs énumérées. Dans la table de hachage, si la clé **Keywords** est utilisée avec une valeur de chaîne, un message d’erreur s’affiche.

Ouvrez **l’Observateur d’événements Windows** ; dans le volet **Actions**, cliquez sur **Filtrer le journal actuel**.
Le menu déroulant **Keywords** indique les mots clés disponibles, comme dans la capture d’écran suivante :

![Image des mots clés de l’observateur d’événements Windows](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Utilisez la commande suivante pour afficher les noms de propriétés `StandardEventKeywords`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

Les valeurs énumérées sont documentées dans **.NET Framework**. Pour plus d’informations, voir [Énumération StandardEventKeywords](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

Les noms et valeurs énumérées **Keywords** sont les suivantes :

| Name             |  Valeur            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Aucune             | 0                 |

Mettez à jour la table de hachage en incluant la paire **clé/valeur** avec la clé **Keywords** et la valeur d’énumération **EventLogClassic** **36028797018963968**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Valeur de propriété statique Keywords (facultatif)

La clé **Keywords** est énumérée, mais il est possible d’utiliser un nom de propriété statique dans la requête de table de hachage.
Au lieu de recourir à la chaîne retournée, il faut convertir le nom de propriété en une valeur avec la propriété **Value__** .

Par exemple, le script suivant utilise la propriété **Value__** .

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtrage par ID d’événement

Pour affiner les données, les résultats de la requête sont filtrés par **ID d’événement**. La table de hachage y fait référence comme à la clé **ID** ; la valeur correspond à un **ID d’événement** en particulier. **L’Observateur d’événements Windows** affiche **l’ID d’événement**. Cet exemple utilise **l’ID d’événement 1023**.

Mettez à jour la table de hachage en incluant la paire **clé/valeur** avec la clé **ID** et la valeur **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtrage par niveau

Pour affiner encore les résultats en les restreignant aux événements correspondant à des erreurs, utilisez la clé **Level**.
**L’Observateur d’événements Windows** affiche **Level** sous forme de valeurs de chaîne, alors qu’il s’agit de valeurs énumérées. Dans la table de hachage, si la clé **Level** est utilisée avec une valeur de chaîne, un message d’erreur s’affiche.

**Level** peut prendre différentes valeurs, notamment **Error**, **Warning** et **Informational**. Utilisez la commande suivante pour afficher les noms de propriétés `StandardEventLevel`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

Les valeurs énumérées sont documentées dans **.NET Framework**. Pour plus d’informations, voir [Énumération StandardEventLevel](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

Les noms et valeurs énumérées de la clé **Level** sont les suivantes :

| Name           | Valeur |
| -------------- | ----- |
| Verbose        |   5   |
| Informationnel  |   4   |
| Avertissement        |   3   |
| Erreur          |   2   |
| Critique       |   1   |
| LogAlways      |   0   |

La table de hachage de la requête comporte la clé **Level** et la valeur **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Propriété statique Level dans une énumération (facultative)

La clé **Level** est énumérée, mais il est possible d’utiliser un nom de propriété statique dans la requête de la table de hachage.
Au lieu de recourir à la chaîne retournée, il faut convertir le nom de propriété en une valeur avec la propriété **Value__** .

Par exemple, le script suivant utilise la propriété **Value__** .

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```