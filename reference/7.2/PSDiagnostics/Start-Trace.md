---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: b1c6a596f3dc35028b928c3a6b5459a805bc2512
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595482"
---
# <span data-ttu-id="a51d5-102">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="a51d5-102">Start-Trace</span></span>

## <span data-ttu-id="a51d5-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a51d5-103">SYNOPSIS</span></span>
<span data-ttu-id="a51d5-104">Démarrez une session de journalisation de suivi des événements.</span><span class="sxs-lookup"><span data-stu-id="a51d5-104">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="a51d5-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="a51d5-105">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="a51d5-106">Description</span><span class="sxs-lookup"><span data-stu-id="a51d5-106">DESCRIPTION</span></span>
<span data-ttu-id="a51d5-107">Cette applet de commande démarre une session de journalisation de suivi d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="a51d5-107">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="a51d5-108">Cette applet de commande est utilisée par les applets de commande suivantes :</span><span class="sxs-lookup"><span data-stu-id="a51d5-108">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="a51d5-109">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="a51d5-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="a51d5-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a51d5-110">EXAMPLES</span></span>

### <span data-ttu-id="a51d5-111">Exemple 1 : démarrer une session de journalisation de suivi WSMan</span><span class="sxs-lookup"><span data-stu-id="a51d5-111">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="a51d5-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a51d5-112">PARAMETERS</span></span>

### <span data-ttu-id="a51d5-113">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="a51d5-113">-BufferSizeInKB</span></span>
<span data-ttu-id="a51d5-114">Taille de la mémoire tampon de la session de suivi d’événements en kilo-octets (Ko).</span><span class="sxs-lookup"><span data-stu-id="a51d5-114">Event Trace Session buffer size in kilobytes (KB).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-115">-ETS</span><span class="sxs-lookup"><span data-stu-id="a51d5-115">-ETS</span></span>
<span data-ttu-id="a51d5-116">Envoyer des commandes aux sessions de suivi d’événements directement sans enregistrement ou planification.</span><span class="sxs-lookup"><span data-stu-id="a51d5-116">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="a51d5-117">-Format</span><span class="sxs-lookup"><span data-stu-id="a51d5-117">-Format</span></span>
<span data-ttu-id="a51d5-118">Spécifie le format du journal pour le collecteur de données.</span><span class="sxs-lookup"><span data-stu-id="a51d5-118">Specifies the log format for the data collector.</span></span> <span data-ttu-id="a51d5-119">Pour le format de base de données SQL, vous devez utiliser l’option **OutputFilePath** dans la ligne de commande avec la `dsn!log` valeur.</span><span class="sxs-lookup"><span data-stu-id="a51d5-119">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="a51d5-120">La valeur par défaut est Binary (bin).</span><span class="sxs-lookup"><span data-stu-id="a51d5-120">The default is binary (bin).</span></span> <span data-ttu-id="a51d5-121">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a51d5-121">The possible values are:</span></span>

- <span data-ttu-id="a51d5-122">bin-binaire</span><span class="sxs-lookup"><span data-stu-id="a51d5-122">bin - binary</span></span>
- <span data-ttu-id="a51d5-123">bincirc-binaire avec journalisation circulaire</span><span class="sxs-lookup"><span data-stu-id="a51d5-123">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="a51d5-124">CSV-valeurs séparées par des virgules</span><span class="sxs-lookup"><span data-stu-id="a51d5-124">csv - Comma-separated values</span></span>
- <span data-ttu-id="a51d5-125">valeurs séparées par des tabulations TSV</span><span class="sxs-lookup"><span data-stu-id="a51d5-125">tsv - Tab-separated values</span></span>
- <span data-ttu-id="a51d5-126">SQL-SQL Database</span><span class="sxs-lookup"><span data-stu-id="a51d5-126">sql - SQL database</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-127">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="a51d5-127">-MaxBuffers</span></span>
<span data-ttu-id="a51d5-128">Définit le nombre maximal de mémoires tampons de session de suivi d’événements.</span><span class="sxs-lookup"><span data-stu-id="a51d5-128">Sets the maximum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-129">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="a51d5-129">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="a51d5-130">Définit la taille maximale du fichier journal en mégaoctets (Mo) ou le nombre d’enregistrements pour les journaux SQL.</span><span class="sxs-lookup"><span data-stu-id="a51d5-130">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-131">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="a51d5-131">-MinBuffers</span></span>
<span data-ttu-id="a51d5-132">Définit le nombre minimal de mémoires tampons de session de suivi d’événements.</span><span class="sxs-lookup"><span data-stu-id="a51d5-132">Sets the minimum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-133">-OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="a51d5-133">-OutputFilePath</span></span>
<span data-ttu-id="a51d5-134">Chemin d’accès du fichier journal de sortie ou nom de l’ensemble de journaux et du journal dans une base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="a51d5-134">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="a51d5-135">Le chemin d’accès par défaut est : `$env:systemdrive\PerfLogs\Admin`.</span><span class="sxs-lookup"><span data-stu-id="a51d5-135">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-136">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="a51d5-136">-ProviderFilePath</span></span>
<span data-ttu-id="a51d5-137">Fichier répertoriant plusieurs fournisseurs de suivi d’événements à activer.</span><span class="sxs-lookup"><span data-stu-id="a51d5-137">File listing multiple Event Trace providers to enable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-138">-Nom_session</span><span class="sxs-lookup"><span data-stu-id="a51d5-138">-SessionName</span></span>
<span data-ttu-id="a51d5-139">Nom de la session de suivi d’événements.</span><span class="sxs-lookup"><span data-stu-id="a51d5-139">The name of the Event Trace session.</span></span> <span data-ttu-id="a51d5-140">Pour arrêter une session de trace, vous devez connaître le nom de la session.</span><span class="sxs-lookup"><span data-stu-id="a51d5-140">To stop a trace session you must know the session name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a51d5-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a51d5-141">CommonParameters</span></span>

<span data-ttu-id="a51d5-142">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a51d5-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a51d5-143">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a51d5-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a51d5-144">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a51d5-144">INPUTS</span></span>

### <span data-ttu-id="a51d5-145">None</span><span class="sxs-lookup"><span data-stu-id="a51d5-145">None</span></span>

## <span data-ttu-id="a51d5-146">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a51d5-146">OUTPUTS</span></span>

### <span data-ttu-id="a51d5-147">None</span><span class="sxs-lookup"><span data-stu-id="a51d5-147">None</span></span>

## <span data-ttu-id="a51d5-148">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a51d5-148">NOTES</span></span>

## <span data-ttu-id="a51d5-149">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a51d5-149">RELATED LINKS</span></span>

[<span data-ttu-id="a51d5-150">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="a51d5-150">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="a51d5-151">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="a51d5-151">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="a51d5-152">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="a51d5-152">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="a51d5-153">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="a51d5-153">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="a51d5-154">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="a51d5-154">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="a51d5-155">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="a51d5-155">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

