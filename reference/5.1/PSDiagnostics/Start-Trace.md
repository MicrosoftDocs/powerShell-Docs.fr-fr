---
external help file: PSDiagnostics-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: cbdb40edf85dd4645552f6e096a99384532b4443
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203045"
---
# <span data-ttu-id="32bdd-103">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="32bdd-103">Start-Trace</span></span>

## <span data-ttu-id="32bdd-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="32bdd-104">SYNOPSIS</span></span>
<span data-ttu-id="32bdd-105">Démarrez une session de journalisation de suivi des événements.</span><span class="sxs-lookup"><span data-stu-id="32bdd-105">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="32bdd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32bdd-106">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="32bdd-107">Description</span><span class="sxs-lookup"><span data-stu-id="32bdd-107">DESCRIPTION</span></span>
<span data-ttu-id="32bdd-108">Cette applet de commande démarre une session de journalisation de suivi d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="32bdd-108">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="32bdd-109">Cette applet de commande est utilisée par les applets de commande suivantes :</span><span class="sxs-lookup"><span data-stu-id="32bdd-109">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="32bdd-110">Vous devez exécuter cette applet de commande à partir d’une session PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="32bdd-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="32bdd-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="32bdd-111">EXAMPLES</span></span>

### <span data-ttu-id="32bdd-112">Exemple 1 : démarrer une session de journalisation de suivi WSMan</span><span class="sxs-lookup"><span data-stu-id="32bdd-112">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="32bdd-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32bdd-113">PARAMETERS</span></span>

### <span data-ttu-id="32bdd-114">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="32bdd-114">-BufferSizeInKB</span></span>
<span data-ttu-id="32bdd-115">Taille de la mémoire tampon de la session de suivi d’événements en kilo-octets (Ko).</span><span class="sxs-lookup"><span data-stu-id="32bdd-115">Event Trace Session buffer size in kilobytes (KB).</span></span>

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

### <span data-ttu-id="32bdd-116">-ETS</span><span class="sxs-lookup"><span data-stu-id="32bdd-116">-ETS</span></span>
<span data-ttu-id="32bdd-117">Envoyer des commandes aux sessions de suivi d’événements directement sans enregistrement ou planification.</span><span class="sxs-lookup"><span data-stu-id="32bdd-117">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="32bdd-118">-Format</span><span class="sxs-lookup"><span data-stu-id="32bdd-118">-Format</span></span>
<span data-ttu-id="32bdd-119">Spécifie le format du journal pour le collecteur de données.</span><span class="sxs-lookup"><span data-stu-id="32bdd-119">Specifies the log format for the data collector.</span></span> <span data-ttu-id="32bdd-120">Pour le format de base de données SQL, vous devez utiliser l’option **OutputFilePath** dans la ligne de commande avec la `dsn!log` valeur.</span><span class="sxs-lookup"><span data-stu-id="32bdd-120">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="32bdd-121">La valeur par défaut est Binary (bin).</span><span class="sxs-lookup"><span data-stu-id="32bdd-121">The default is binary (bin).</span></span> <span data-ttu-id="32bdd-122">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="32bdd-122">The possible values are:</span></span>

- <span data-ttu-id="32bdd-123">bin-binaire</span><span class="sxs-lookup"><span data-stu-id="32bdd-123">bin - binary</span></span>
- <span data-ttu-id="32bdd-124">bincirc-binaire avec journalisation circulaire</span><span class="sxs-lookup"><span data-stu-id="32bdd-124">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="32bdd-125">CSV-valeurs séparées par des virgules</span><span class="sxs-lookup"><span data-stu-id="32bdd-125">csv - Comma-separated values</span></span>
- <span data-ttu-id="32bdd-126">valeurs séparées par des tabulations TSV</span><span class="sxs-lookup"><span data-stu-id="32bdd-126">tsv - Tab-separated values</span></span>
- <span data-ttu-id="32bdd-127">SQL-SQL Database</span><span class="sxs-lookup"><span data-stu-id="32bdd-127">sql - SQL database</span></span>

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

### <span data-ttu-id="32bdd-128">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="32bdd-128">-MaxBuffers</span></span>
<span data-ttu-id="32bdd-129">Définit le nombre maximal de mémoires tampons de session de suivi d’événements.</span><span class="sxs-lookup"><span data-stu-id="32bdd-129">Sets the maximum number of Event Trace Session buffers.</span></span>

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

### <span data-ttu-id="32bdd-130">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="32bdd-130">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="32bdd-131">Définit la taille maximale du fichier journal en mégaoctets (Mo) ou le nombre d’enregistrements pour les journaux SQL.</span><span class="sxs-lookup"><span data-stu-id="32bdd-131">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

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

### <span data-ttu-id="32bdd-132">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="32bdd-132">-MinBuffers</span></span>
<span data-ttu-id="32bdd-133">Définit le nombre minimal de mémoires tampons de session de suivi d’événements.</span><span class="sxs-lookup"><span data-stu-id="32bdd-133">Sets the minimum number of Event Trace Session buffers.</span></span>

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

### <span data-ttu-id="32bdd-134">-OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="32bdd-134">-OutputFilePath</span></span>
<span data-ttu-id="32bdd-135">Chemin d’accès du fichier journal de sortie ou nom de l’ensemble de journaux et du journal dans une base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="32bdd-135">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="32bdd-136">Le chemin d’accès par défaut est : `$env:systemdrive\PerfLogs\Admin`.</span><span class="sxs-lookup"><span data-stu-id="32bdd-136">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

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

### <span data-ttu-id="32bdd-137">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="32bdd-137">-ProviderFilePath</span></span>
<span data-ttu-id="32bdd-138">Fichier répertoriant plusieurs fournisseurs de suivi d’événements à activer.</span><span class="sxs-lookup"><span data-stu-id="32bdd-138">File listing multiple Event Trace providers to enable.</span></span>

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

### <span data-ttu-id="32bdd-139">-Nom_session</span><span class="sxs-lookup"><span data-stu-id="32bdd-139">-SessionName</span></span>
<span data-ttu-id="32bdd-140">Nom de la session de suivi d’événements.</span><span class="sxs-lookup"><span data-stu-id="32bdd-140">The name of the Event Trace session.</span></span> <span data-ttu-id="32bdd-141">Pour arrêter une session de trace, vous devez connaître le nom de la session.</span><span class="sxs-lookup"><span data-stu-id="32bdd-141">To stop a trace session you must know the session name.</span></span>

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

### <span data-ttu-id="32bdd-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32bdd-142">CommonParameters</span></span>

<span data-ttu-id="32bdd-143">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32bdd-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32bdd-144">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="32bdd-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32bdd-145">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="32bdd-145">INPUTS</span></span>

### <span data-ttu-id="32bdd-146">Aucun</span><span class="sxs-lookup"><span data-stu-id="32bdd-146">None</span></span>

## <span data-ttu-id="32bdd-147">SORTIES</span><span class="sxs-lookup"><span data-stu-id="32bdd-147">OUTPUTS</span></span>

### <span data-ttu-id="32bdd-148">System.Object</span><span class="sxs-lookup"><span data-stu-id="32bdd-148">System.Object</span></span>

## <span data-ttu-id="32bdd-149">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="32bdd-149">NOTES</span></span>

## <span data-ttu-id="32bdd-150">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="32bdd-150">RELATED LINKS</span></span>

[<span data-ttu-id="32bdd-151">Suivi d’événements</span><span class="sxs-lookup"><span data-stu-id="32bdd-151">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="32bdd-152">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="32bdd-152">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="32bdd-153">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="32bdd-153">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="32bdd-154">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="32bdd-154">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="32bdd-155">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="32bdd-155">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="32bdd-156">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="32bdd-156">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
