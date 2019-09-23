---
ms.date: 09/13/2019
title: Création de requêtes Get-WinEvent avec FilterHashtable
ms.openlocfilehash: 1bf321c09c20736de36eb896fabced31cfdfbd75
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143672"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="0d387-102">Création de requêtes Get-WinEvent avec FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="0d387-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="0d387-103">Pour lire le billet de blog **Scripting Guy** d’origine du 3 juin 2014, voir [Utiliser FilterHashtable pour filtrer le journal des événements avec PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span><span class="sxs-lookup"><span data-stu-id="0d387-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="0d387-104">Cet article est un extrait du billet de blog d’origine qui explique comment utiliser le paramètre **FilterHashtable** de la cmdlet `Get-WinEvent` pour filtrer les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="0d387-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="0d387-105">La cmdlet `Get-WinEvent` de PowerShell représente un puissant moyen de filtrer des journaux de diagnostic et des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="0d387-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="0d387-106">Les performances sont meilleures quand la requête `Get-WinEvent` utilise le paramètre **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="0d387-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="0d387-107">Avec des journaux des événements volumineux, il n’est pas efficace d’envoyer des objets à une commande `Where-Object` à travers le pipeline.</span><span class="sxs-lookup"><span data-stu-id="0d387-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="0d387-108">Avant PowerShell 6, la cmdlet `Get-EventLog` offrait un autre moyen de récupérer des données de journal.</span><span class="sxs-lookup"><span data-stu-id="0d387-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="0d387-109">Par exemple, les commandes suivantes sont inefficaces pour filtrer les journaux **Microsoft-Windows-Defrag** :</span><span class="sxs-lookup"><span data-stu-id="0d387-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="0d387-110">La commande suivante utilise une table de hachage qui améliore les performances :</span><span class="sxs-lookup"><span data-stu-id="0d387-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="0d387-111">Billets de blog sur l’énumération</span><span class="sxs-lookup"><span data-stu-id="0d387-111">Blog posts about enumeration</span></span>

<span data-ttu-id="0d387-112">Cet article explique comment utiliser des valeurs énumérées dans une table de hachage.</span><span class="sxs-lookup"><span data-stu-id="0d387-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="0d387-113">Pour plus d’informations sur l’énumération, voir ces billets de blog **Scripting Guy**.</span><span class="sxs-lookup"><span data-stu-id="0d387-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="0d387-114">Pour créer une fonction qui retourne les valeurs énumérées, voir [Énumérations et valeurs](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="0d387-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="0d387-115">Pour plus d’informations, voir la [série de billets de blog Scripting Guy sur l’énumération](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="0d387-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="0d387-116">Paires clé/valeur de table de hachage</span><span class="sxs-lookup"><span data-stu-id="0d387-116">Hash table key/value pairs</span></span>

<span data-ttu-id="0d387-117">Pour générer des requêtes efficaces, utilisez la cmdlet `Get-WinEvent` avec le paramètre **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="0d387-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="0d387-118">**FilterHashtable** prend une table de hachage comme filtre pour obtenir des informations spécifiques dans les journaux des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="0d387-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="0d387-119">Une table de hachage utilise des paires **clé/valeur**.</span><span class="sxs-lookup"><span data-stu-id="0d387-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="0d387-120">Pour plus d’informations sur les tables de hachage, voir [À propos des tables de hachage](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="0d387-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="0d387-121">Si les paires **clé/valeur** se trouvent sur la même ligne, elles doivent être séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="0d387-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="0d387-122">Si chaque paire **clé/valeur** est sur une ligne distincte, le point-virgule n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0d387-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="0d387-123">Cet article, par exemple, place une paire **clé/valeur** par ligne et n’utilise pas de points-virgules.</span><span class="sxs-lookup"><span data-stu-id="0d387-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="0d387-124">Cet exemple utilise plusieurs paires **clé/valeur** du paramètre **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="0d387-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="0d387-125">La requête comporte **LogName**, **ProviderName**, **Keywords**, **ID** et **Level**.</span><span class="sxs-lookup"><span data-stu-id="0d387-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="0d387-126">Les paires **clé/valeur** acceptées sont présentées dans le tableau suivant ainsi que dans la documentation relative au paramètre [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="0d387-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="0d387-127">Le tableau suivant indique les noms de clés et les types de données, et précise si les caractères génériques sont acceptés comme valeurs de données.</span><span class="sxs-lookup"><span data-stu-id="0d387-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="0d387-128">Nom de clé</span><span class="sxs-lookup"><span data-stu-id="0d387-128">Key name</span></span>    | <span data-ttu-id="0d387-129">Type de données valeur</span><span class="sxs-lookup"><span data-stu-id="0d387-129">Value data type</span></span> | <span data-ttu-id="0d387-130">Accepte les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="0d387-130">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="0d387-131">LogName</span><span class="sxs-lookup"><span data-stu-id="0d387-131">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="0d387-132">Oui</span><span class="sxs-lookup"><span data-stu-id="0d387-132">Yes</span></span>                          |
| <span data-ttu-id="0d387-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="0d387-133">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="0d387-134">Oui</span><span class="sxs-lookup"><span data-stu-id="0d387-134">Yes</span></span>                          |
| <span data-ttu-id="0d387-135">Path</span><span class="sxs-lookup"><span data-stu-id="0d387-135">Path</span></span>           | `<String[]>`    | <span data-ttu-id="0d387-136">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-136">No</span></span>                           |
| <span data-ttu-id="0d387-137">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0d387-137">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="0d387-138">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-138">No</span></span>                           |
| <span data-ttu-id="0d387-139">ID</span><span class="sxs-lookup"><span data-stu-id="0d387-139">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="0d387-140">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-140">No</span></span>                           |
| <span data-ttu-id="0d387-141">Niveau</span><span class="sxs-lookup"><span data-stu-id="0d387-141">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="0d387-142">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-142">No</span></span>                           |
| <span data-ttu-id="0d387-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="0d387-143">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="0d387-144">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-144">No</span></span>                           |
| <span data-ttu-id="0d387-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="0d387-145">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="0d387-146">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-146">No</span></span>                           |
| <span data-ttu-id="0d387-147">UserID</span><span class="sxs-lookup"><span data-stu-id="0d387-147">UserID</span></span>         | `<SID>`         | <span data-ttu-id="0d387-148">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-148">No</span></span>                           |
| <span data-ttu-id="0d387-149">Données</span><span class="sxs-lookup"><span data-stu-id="0d387-149">Data</span></span>           | `<String[]>`    | <span data-ttu-id="0d387-150">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-150">No</span></span>                           |
| <span data-ttu-id="0d387-151">\<named-data\></span><span class="sxs-lookup"><span data-stu-id="0d387-151">\<named-data\></span></span> | `<String[]>`    | <span data-ttu-id="0d387-152">Non</span><span class="sxs-lookup"><span data-stu-id="0d387-152">No</span></span>                           |

<span data-ttu-id="0d387-153">La clé \<named-data\> représente un champ de données d'événement nommé.</span><span class="sxs-lookup"><span data-stu-id="0d387-153">The \<named-data\> key represents a named event data field.</span></span> <span data-ttu-id="0d387-154">Par exemple, l'événement Perflib 1008 peut contenir les données d'événement suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d387-154">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="0d387-155">Vous pouvez rechercher ces événements à l'aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0d387-155">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="0d387-156">Créer une requête avec une table de hachage</span><span class="sxs-lookup"><span data-stu-id="0d387-156">Building a query with a hash table</span></span>

<span data-ttu-id="0d387-157">Pour pouvoir vérifier les résultats et résoudre les problèmes, il est plus facile de créer la table de hachage une paire **clé/valeur** à la fois.</span><span class="sxs-lookup"><span data-stu-id="0d387-157">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="0d387-158">La requête récupère des données auprès du journal **Application**.</span><span class="sxs-lookup"><span data-stu-id="0d387-158">The query gets data from the **Application** log.</span></span> <span data-ttu-id="0d387-159">La table de hachage est équivalente à `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="0d387-159">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="0d387-160">Pour commencer, créez la requête `Get-WinEvent`.</span><span class="sxs-lookup"><span data-stu-id="0d387-160">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="0d387-161">Utilisez la paire **clé/valeur** du paramètre **FilterHashtable** avec la clé **LogName** et la valeur **Application**.</span><span class="sxs-lookup"><span data-stu-id="0d387-161">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="0d387-162">Continuez à créer la table de hachage avec la clé **ProviderName**.</span><span class="sxs-lookup"><span data-stu-id="0d387-162">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="0d387-163">**ProviderName** correspond au nom qui apparaît dans le champ **Source** de **l’Observateur d’événements Windows**,</span><span class="sxs-lookup"><span data-stu-id="0d387-163">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="0d387-164">par exemple **.NET Runtime** dans la capture d’écran suivante :</span><span class="sxs-lookup"><span data-stu-id="0d387-164">For example, **.NET Runtime** in the following screenshot:</span></span>

![Image des sources de l’observateur d’événements Windows](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="0d387-166">Mettez à jour la table de hachage en incluant la paire **clé/valeur** avec la clé \*\*ProviderName et la valeur **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="0d387-166">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="0d387-167">Si votre requête doit récupérer des données dans des journaux des événements archivés, utilisez la clé **Path**.</span><span class="sxs-lookup"><span data-stu-id="0d387-167">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="0d387-168">La valeur **Path** spécifie le chemin d’accès complet au fichier journal.</span><span class="sxs-lookup"><span data-stu-id="0d387-168">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="0d387-169">Pour plus d’informations, voir le billet de blog **Scripting Guy** [Utiliser PowerShell pour analyser la présence d’erreurs dans des journaux des événements enregistrés](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="0d387-169">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="0d387-170">Utiliser des valeurs énumérées dans une table de hachage</span><span class="sxs-lookup"><span data-stu-id="0d387-170">Using enumerated values in a hash table</span></span>

<span data-ttu-id="0d387-171">**Keywords** est la clé suivante de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="0d387-171">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="0d387-172">Le type de données **Keywords** est un tableau du type valeur `[long]` contenant un grand nombre.</span><span class="sxs-lookup"><span data-stu-id="0d387-172">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="0d387-173">Utilisez la commande suivante pour rechercher la valeur maximale de `[long]` :</span><span class="sxs-lookup"><span data-stu-id="0d387-173">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="0d387-174">Pour la clé **Keywords**, PowerShell utilise un nombre, et non une chaîne comme **Security**.</span><span class="sxs-lookup"><span data-stu-id="0d387-174">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="0d387-175">**L’Observateur d’événements Windows** affiche **Keywords** sous forme de chaînes, alors qu’il s’agit de valeurs énumérées.</span><span class="sxs-lookup"><span data-stu-id="0d387-175">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="0d387-176">Dans la table de hachage, si la clé **Keywords** est utilisée avec une valeur de chaîne, un message d’erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0d387-176">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="0d387-177">Ouvrez **l’Observateur d’événements Windows** ; dans le volet **Actions**, cliquez sur **Filtrer le journal actuel**.</span><span class="sxs-lookup"><span data-stu-id="0d387-177">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="0d387-178">Le menu déroulant **Keywords** indique les mots clés disponibles, comme dans la capture d’écran suivante :</span><span class="sxs-lookup"><span data-stu-id="0d387-178">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Image des mots clés de l’observateur d’événements Windows](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="0d387-180">Utilisez la commande suivante pour afficher les noms de propriétés `StandardEventKeywords`.</span><span class="sxs-lookup"><span data-stu-id="0d387-180">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="0d387-181">Les valeurs énumérées sont documentées dans **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="0d387-181">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="0d387-182">Pour plus d’informations, voir [Énumération StandardEventKeywords](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="0d387-182">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="0d387-183">Les noms et valeurs énumérées **Keywords** sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d387-183">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="0d387-184">Name</span><span class="sxs-lookup"><span data-stu-id="0d387-184">Name</span></span>             |  <span data-ttu-id="0d387-185">Valeur</span><span class="sxs-lookup"><span data-stu-id="0d387-185">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="0d387-186">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="0d387-186">AuditFailure</span></span>     | <span data-ttu-id="0d387-187">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="0d387-187">4503599627370496</span></span>  |
| <span data-ttu-id="0d387-188">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="0d387-188">AuditSuccess</span></span>     | <span data-ttu-id="0d387-189">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="0d387-189">9007199254740992</span></span>  |
| <span data-ttu-id="0d387-190">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="0d387-190">CorrelationHint2</span></span> | <span data-ttu-id="0d387-191">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="0d387-191">18014398509481984</span></span> |
| <span data-ttu-id="0d387-192">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="0d387-192">EventLogClassic</span></span>  | <span data-ttu-id="0d387-193">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="0d387-193">36028797018963968</span></span> |
| <span data-ttu-id="0d387-194">Sqm</span><span class="sxs-lookup"><span data-stu-id="0d387-194">Sqm</span></span>              | <span data-ttu-id="0d387-195">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="0d387-195">2251799813685248</span></span>  |
| <span data-ttu-id="0d387-196">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="0d387-196">WdiDiagnostic</span></span>    | <span data-ttu-id="0d387-197">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="0d387-197">1125899906842624</span></span>  |
| <span data-ttu-id="0d387-198">WdiContext</span><span class="sxs-lookup"><span data-stu-id="0d387-198">WdiContext</span></span>       | <span data-ttu-id="0d387-199">562949953421312</span><span class="sxs-lookup"><span data-stu-id="0d387-199">562949953421312</span></span>   |
| <span data-ttu-id="0d387-200">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="0d387-200">ResponseTime</span></span>     | <span data-ttu-id="0d387-201">281474976710656</span><span class="sxs-lookup"><span data-stu-id="0d387-201">281474976710656</span></span>   |
| <span data-ttu-id="0d387-202">Aucune</span><span class="sxs-lookup"><span data-stu-id="0d387-202">None</span></span>             | <span data-ttu-id="0d387-203">0</span><span class="sxs-lookup"><span data-stu-id="0d387-203">0</span></span>                 |

<span data-ttu-id="0d387-204">Mettez à jour la table de hachage en incluant la paire **clé/valeur** avec la clé **Keywords** et la valeur d’énumération **EventLogClassic** **36028797018963968**.</span><span class="sxs-lookup"><span data-stu-id="0d387-204">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="0d387-205">Valeur de propriété statique Keywords (facultatif)</span><span class="sxs-lookup"><span data-stu-id="0d387-205">Keywords static property value (optional)</span></span>

<span data-ttu-id="0d387-206">La clé **Keywords** est énumérée, mais il est possible d’utiliser un nom de propriété statique dans la requête de table de hachage.</span><span class="sxs-lookup"><span data-stu-id="0d387-206">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="0d387-207">Au lieu de recourir à la chaîne retournée, il faut convertir le nom de propriété en une valeur avec la propriété **Value__**.</span><span class="sxs-lookup"><span data-stu-id="0d387-207">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="0d387-208">Par exemple, le script suivant utilise la propriété **Value__** .</span><span class="sxs-lookup"><span data-stu-id="0d387-208">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="0d387-209">Filtrage par ID d’événement</span><span class="sxs-lookup"><span data-stu-id="0d387-209">Filtering by Event Id</span></span>

<span data-ttu-id="0d387-210">Pour affiner les données, les résultats de la requête sont filtrés par **ID d’événement**. La table de hachage y fait référence comme à la clé **ID** ; la valeur correspond à un **ID d’événement** en particulier. **L’Observateur d’événements Windows** affiche **l’ID d’événement**. Cet exemple utilise **l’ID d’événement 1023**.</span><span class="sxs-lookup"><span data-stu-id="0d387-210">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="0d387-211">Mettez à jour la table de hachage en incluant la paire **clé/valeur** avec la clé **ID** et la valeur **1023**.</span><span class="sxs-lookup"><span data-stu-id="0d387-211">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="0d387-212">Filtrage par niveau</span><span class="sxs-lookup"><span data-stu-id="0d387-212">Filtering by Level</span></span>

<span data-ttu-id="0d387-213">Pour affiner encore les résultats en les restreignant aux événements correspondant à des erreurs, utilisez la clé **Level**.</span><span class="sxs-lookup"><span data-stu-id="0d387-213">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="0d387-214">**L’Observateur d’événements Windows** affiche **Level** sous forme de valeurs de chaîne, alors qu’il s’agit de valeurs énumérées.</span><span class="sxs-lookup"><span data-stu-id="0d387-214">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="0d387-215">Dans la table de hachage, si la clé **Level** est utilisée avec une valeur de chaîne, un message d’erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0d387-215">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="0d387-216">**Level** peut prendre différentes valeurs, notamment **Error**, **Warning** et **Informational**.</span><span class="sxs-lookup"><span data-stu-id="0d387-216">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="0d387-217">Utilisez la commande suivante pour afficher les noms de propriétés `StandardEventLevel`.</span><span class="sxs-lookup"><span data-stu-id="0d387-217">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="0d387-218">Les valeurs énumérées sont documentées dans **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="0d387-218">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="0d387-219">Pour plus d’informations, voir [Énumération StandardEventLevel](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="0d387-219">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="0d387-220">Les noms et valeurs énumérées de la clé **Level** sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0d387-220">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="0d387-221">Name</span><span class="sxs-lookup"><span data-stu-id="0d387-221">Name</span></span>           | <span data-ttu-id="0d387-222">Valeur</span><span class="sxs-lookup"><span data-stu-id="0d387-222">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="0d387-223">Verbose</span><span class="sxs-lookup"><span data-stu-id="0d387-223">Verbose</span></span>        |   <span data-ttu-id="0d387-224">5</span><span class="sxs-lookup"><span data-stu-id="0d387-224">5</span></span>   |
| <span data-ttu-id="0d387-225">Informationnel</span><span class="sxs-lookup"><span data-stu-id="0d387-225">Informational</span></span>  |   <span data-ttu-id="0d387-226">4</span><span class="sxs-lookup"><span data-stu-id="0d387-226">4</span></span>   |
| <span data-ttu-id="0d387-227">Avertissement</span><span class="sxs-lookup"><span data-stu-id="0d387-227">Warning</span></span>        |   <span data-ttu-id="0d387-228">3</span><span class="sxs-lookup"><span data-stu-id="0d387-228">3</span></span>   |
| <span data-ttu-id="0d387-229">Erreur</span><span class="sxs-lookup"><span data-stu-id="0d387-229">Error</span></span>          |   <span data-ttu-id="0d387-230">2</span><span class="sxs-lookup"><span data-stu-id="0d387-230">2</span></span>   |
| <span data-ttu-id="0d387-231">Critique</span><span class="sxs-lookup"><span data-stu-id="0d387-231">Critical</span></span>       |   <span data-ttu-id="0d387-232">1</span><span class="sxs-lookup"><span data-stu-id="0d387-232">1</span></span>   |
| <span data-ttu-id="0d387-233">LogAlways</span><span class="sxs-lookup"><span data-stu-id="0d387-233">LogAlways</span></span>      |   <span data-ttu-id="0d387-234">0</span><span class="sxs-lookup"><span data-stu-id="0d387-234">0</span></span>   |

<span data-ttu-id="0d387-235">La table de hachage de la requête comporte la clé **Level** et la valeur **2**.</span><span class="sxs-lookup"><span data-stu-id="0d387-235">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="0d387-236">Propriété statique Level dans une énumération (facultative)</span><span class="sxs-lookup"><span data-stu-id="0d387-236">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="0d387-237">La clé **Level** est énumérée, mais il est possible d’utiliser un nom de propriété statique dans la requête de la table de hachage.</span><span class="sxs-lookup"><span data-stu-id="0d387-237">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="0d387-238">Au lieu de recourir à la chaîne retournée, il faut convertir le nom de propriété en une valeur avec la propriété **Value__**.</span><span class="sxs-lookup"><span data-stu-id="0d387-238">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="0d387-239">Par exemple, le script suivant utilise la propriété **Value__** .</span><span class="sxs-lookup"><span data-stu-id="0d387-239">For example, the following script uses the **Value__** property.</span></span>

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