---
description: PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: e74e357d81eddf87ad27d023eb9a8ba2977156e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595471"
---
# <a name="about-logging-non-windows"></a><span data-ttu-id="1ddc6-103">À propos de la journalisation non-Windows</span><span class="sxs-lookup"><span data-stu-id="1ddc6-103">About Logging Non-Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="1ddc6-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="1ddc6-104">Short description</span></span>
<span data-ttu-id="1ddc6-105">PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-105">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="1ddc6-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="1ddc6-106">Long description</span></span>

<span data-ttu-id="1ddc6-107">PowerShell journalise les détails des opérations PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-107">PowerShell logs details of PowerShell operations.</span></span> <span data-ttu-id="1ddc6-108">Par exemple, PowerShell enregistre les opérations telles que le démarrage et l’arrêt du moteur, ainsi que le démarrage et l’arrêt des fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-108">For example, PowerShell will log operations such as starting and stopping the engine and starting and stopping providers.</span></span> <span data-ttu-id="1ddc6-109">Elle enregistre également des détails sur les commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-109">It will also log details about PowerShell commands.</span></span>

<span data-ttu-id="1ddc6-110">L’emplacement des journaux PowerShell dépend de la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-110">The location of PowerShell logs is dependent on the target platform.</span></span> <span data-ttu-id="1ddc6-111">Sur **Linux**, les journaux PowerShell dans **syslog** et **rsyslog. conf** peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-111">On **Linux**, PowerShell logs to **syslog** and **rsyslog.conf** can be used.</span></span> <span data-ttu-id="1ddc6-112">Pour plus d’informations, consultez les pages locales de l’ordinateur Linux `man` .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-112">For more information, refer to the Linux computer's local `man` pages.</span></span> <span data-ttu-id="1ddc6-113">Sur **MacOS**, le système de journalisation **os_log** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-113">On **macOS**, the **os_log** logging system is used.</span></span> <span data-ttu-id="1ddc6-114">Pour plus d’informations, consultez [os_log documentation pour développeurs](https://developer.apple.com/documentation/os/os_log).</span><span class="sxs-lookup"><span data-stu-id="1ddc6-114">For more information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

## <a name="viewing-powershell-log-output-on-linux"></a><span data-ttu-id="1ddc6-115">Affichage de la sortie de journal PowerShell sur Linux</span><span class="sxs-lookup"><span data-stu-id="1ddc6-115">Viewing PowerShell log output on Linux</span></span>

<span data-ttu-id="1ddc6-116">Les journaux PowerShell dans **syslog** sur Linux et les outils couramment utilisés pour afficher le contenu **syslog** peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-116">PowerShell logs to **syslog** on Linux and any of the tools commonly used to view **syslog** contents may be used.</span></span>

<span data-ttu-id="1ddc6-117">Le format des entrées de journal utilise le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="1ddc6-117">The format of the log entries uses the following template:</span></span>

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|<span data-ttu-id="1ddc6-118">Champ</span><span class="sxs-lookup"><span data-stu-id="1ddc6-118">Field</span></span>        |<span data-ttu-id="1ddc6-119">Description</span><span class="sxs-lookup"><span data-stu-id="1ddc6-119">Description</span></span>                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |<span data-ttu-id="1ddc6-120">Date/heure de génération de l’entrée de journal.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-120">A date/time when the log entry was produced.</span></span>            |
|`MACHINENAME`|<span data-ttu-id="1ddc6-121">Nom du système sur lequel le journal a été généré.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-121">The name of the system where the log was produced.</span></span>      |
|`PID`        |<span data-ttu-id="1ddc6-122">ID de processus du processus qui a écrit l’entrée de journal.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-122">The process ID of the process that wrote the log entry.</span></span> |
|`COMMITID`   |<span data-ttu-id="1ddc6-123">`git commit`ID ou balise utilisé pour générer la Build.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-123">The `git commit` ID or tag used to produce the build.</span></span>   |
|`TID`        |<span data-ttu-id="1ddc6-124">ID de thread du thread qui a écrit l’entrée de journal.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-124">The thread ID of the thread that wrote the log entry.</span></span>   |
|`CID`        |<span data-ttu-id="1ddc6-125">Identificateur de canal hexadécimal de l’entrée de journal.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-125">The hex channel identifier of the log entry.</span></span>            |
|             |<span data-ttu-id="1ddc6-126">10 = opérationnel, 11 = analyse</span><span class="sxs-lookup"><span data-stu-id="1ddc6-126">10 = Operational, 11 = Analytic</span></span>                         |
|`EVENTID`    |<span data-ttu-id="1ddc6-127">Identificateur d’événement de l’entrée de journal.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-127">The event identifier of the log entry.</span></span>                  |
|`TASK`       |<span data-ttu-id="1ddc6-128">Identificateur de tâche pour l’entrée d’événement.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-128">The task identifier for the event entry</span></span>                 |
|`OPCODE`     |<span data-ttu-id="1ddc6-129">Opcode de l’entrée d’événement.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-129">The opcode for the event entry</span></span>                          |
|`LEVEL`      |<span data-ttu-id="1ddc6-130">Niveau de journalisation de l’entrée d’événement.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-130">The log level for the event entry</span></span>                       |
|`MESSAGE`    |<span data-ttu-id="1ddc6-131">Message associé à l’entrée d’événement.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-131">The message associated with the event entry</span></span>             |

> [!NOTE]
> <span data-ttu-id="1ddc6-132">`EVENTID`, `TASK` , `OPCODE` et `LEVEL` sont les mêmes valeurs que celles utilisées lors de la journalisation dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-132">`EVENTID`, `TASK`, `OPCODE`, and `LEVEL` are the same values as used when logging to the Windows event log.</span></span>

### <a name="filtering-powershell-log-entries-using-rsyslog"></a><span data-ttu-id="1ddc6-133">Filtrage des entrées de journal PowerShell à l’aide de rsyslog</span><span class="sxs-lookup"><span data-stu-id="1ddc6-133">Filtering PowerShell log entries using rsyslog</span></span>

<span data-ttu-id="1ddc6-134">Normalement, les entrées de journal PowerShell sont écrites dans la valeur par défaut `location/file` pour **syslog**.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-134">Normally, PowerShell log entries are written to the default `location/file` for **syslog**.</span></span> <span data-ttu-id="1ddc6-135">Toutefois, il est possible de rediriger les entrées vers un fichier personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-135">However, it's possible to redirect the entries to a custom file.</span></span>

1. <span data-ttu-id="1ddc6-136">Créez une configuration de journal conf pour PowerShell et fournissez un nombre inférieur à 50 (pour `50-default.conf` ), par exemple `40-powershell.conf` .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-136">Create a conf for PowerShell log configuration and provide a number that's less than 50 (for `50-default.conf`), such as `40-powershell.conf`.</span></span> <span data-ttu-id="1ddc6-137">Le fichier doit être placé sous `/etc/rsyslog.d` .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-137">The file should be placed under `/etc/rsyslog.d`.</span></span>

1. <span data-ttu-id="1ddc6-138">Ajoutez l’entrée suivante au fichier :</span><span class="sxs-lookup"><span data-stu-id="1ddc6-138">Add the following entry to the file:</span></span>

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. <span data-ttu-id="1ddc6-139">Assurez-vous que `/etc/rsyslog.conf` le nouveau fichier est inclus.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-139">Make sure `/etc/rsyslog.conf` includes the new file.</span></span> <span data-ttu-id="1ddc6-140">Souvent, elle aura une instruction include générique qui ressemble à la configuration suivante :</span><span class="sxs-lookup"><span data-stu-id="1ddc6-140">Often, it will have a generic include statement that looks like following configuration:</span></span>

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   <span data-ttu-id="1ddc6-141">Si ce n’est pas le cas, vous devez ajouter une instruction include manuellement.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-141">If it doesn't, you'll need to add an include statement manually.</span></span>

1. <span data-ttu-id="1ddc6-142">Vérifiez que les attributs et les autorisations sont correctement définis.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-142">Make sure attributes and permissions are set appropriately.</span></span>

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. <span data-ttu-id="1ddc6-143">Définissez la propriété sur **root**.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-143">Set ownership to **root**.</span></span>

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. <span data-ttu-id="1ddc6-144">Définir les autorisations d’accès : la **racine** est en lecture/écriture, **les utilisateurs** ont accès en lecture.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-144">Set access permissions: **root** has read/write, **users** have read.</span></span>

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a><span data-ttu-id="1ddc6-145">Affichage de la sortie du journal PowerShell sur macOS</span><span class="sxs-lookup"><span data-stu-id="1ddc6-145">Viewing PowerShell log output on macOS</span></span>

<span data-ttu-id="1ddc6-146">La méthode la plus simple pour afficher la sortie de journal PowerShell sur macOS est l’utilisation de l’application **console** .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-146">The easiest method for viewing PowerShell log output on macOS is using the **Console** application.</span></span>

1. <span data-ttu-id="1ddc6-147">Recherchez l’application **console** et lancez-la.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-147">Search for the **Console** application and launch it.</span></span>
1. <span data-ttu-id="1ddc6-148">Sélectionnez le nom de l’ordinateur sous **appareils**.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-148">Select the Machine name under **Devices**.</span></span>
1. <span data-ttu-id="1ddc6-149">Dans le champ de **recherche** , entrez `pwsh` pour le binaire principal PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-149">In the **Search** field, enter `pwsh` for the PowerShell main binary.</span></span>
1. <span data-ttu-id="1ddc6-150">Remplacez le filtre de recherche `Any` par `Process` .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-150">Change the search filter from `Any` to `Process`.</span></span>
1. <span data-ttu-id="1ddc6-151">Effectuez les opérations.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-151">Perform the operations.</span></span>
1. <span data-ttu-id="1ddc6-152">Si vous le souhaitez, enregistrez la recherche pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-152">Optionally, save the search for future use.</span></span>

<span data-ttu-id="1ddc6-153">Pour filtrer sur une instance de processus spécifique de PowerShell dans la **console**, la variable `$pid` contient l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-153">To filter on a specific process instance of PowerShell in the **Console**, the variable `$pid` contains the process ID.</span></span>

1. <span data-ttu-id="1ddc6-154">Entrez le **PID** (ID de processus) dans le champ de **recherche** .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-154">Enter the **pid** (Process ID) in the **Search** field.</span></span>
1. <span data-ttu-id="1ddc6-155">Modifiez le filtre de recherche en `PID` .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-155">Change the search filter to `PID`.</span></span>
1. <span data-ttu-id="1ddc6-156">Effectuez les opérations.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-156">Perform the operations.</span></span>

### <a name="viewing-powershell-log-output-from-a-command-line"></a><span data-ttu-id="1ddc6-157">Affichage de la sortie de journal PowerShell à partir d’une ligne de commande</span><span class="sxs-lookup"><span data-stu-id="1ddc6-157">Viewing PowerShell log output from a command line</span></span>

<span data-ttu-id="1ddc6-158">La `log` commande peut être utilisée pour afficher les entrées de journal PowerShell à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-158">The `log` command can be used to view PowerShell log entries from the command line.</span></span>

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a><span data-ttu-id="1ddc6-159">Persistance de la sortie du journal PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ddc6-159">Persisting PowerShell log output</span></span>

<span data-ttu-id="1ddc6-160">Par défaut, PowerShell utilise la journalisation par défaut de la mémoire uniquement sur macOS.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-160">By default, PowerShell uses the default memory-only logging on macOS.</span></span> <span data-ttu-id="1ddc6-161">Ce comportement peut être modifié pour activer la persistance à l’aide de la `log config` commande.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-161">This behavior can be changed to enable persistence using the `log config` command.</span></span>

<span data-ttu-id="1ddc6-162">Le script suivant active la journalisation et la persistance au niveau des informations :</span><span class="sxs-lookup"><span data-stu-id="1ddc6-162">The following script enables info level logging and persistence:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

<span data-ttu-id="1ddc6-163">La commande suivante rétablit l’État par défaut de la journalisation PowerShell :</span><span class="sxs-lookup"><span data-stu-id="1ddc6-163">The following command reverts PowerShell logging to the default state:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

<span data-ttu-id="1ddc6-164">Une fois la persistance activée, la `log show` commande peut être utilisée pour exporter des éléments de journal.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-164">After persistence is enabled, the `log show` command can be used to export log items.</span></span> <span data-ttu-id="1ddc6-165">La commande fournit des options pour exporter les N derniers éléments, les éléments depuis un moment donné, ou des éléments dans un intervalle de temps donné.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-165">The command provides options for exporting the last N items, items since a given time, or items within a given time span.</span></span>

<span data-ttu-id="1ddc6-166">Par exemple, la commande suivante exporte des éléments depuis `9am on April 5 of 2018` :</span><span class="sxs-lookup"><span data-stu-id="1ddc6-166">For example, the following command exports items since `9am on April 5 of 2018`:</span></span>

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

<span data-ttu-id="1ddc6-167">Vous pouvez obtenir de l’aide pour `log` en exécutant `log show --help` pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-167">You can get help for `log` by running `log show --help` for additional details.</span></span>

> [!TIP]
> <span data-ttu-id="1ddc6-168">Quand vous exécutez l’une des commandes de journal à partir d’une invite ou d’un script PowerShell, utilisez des guillemets doubles autour de la chaîne de prédicat entière et des guillemets simples dans.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-168">When executing any of the log commands from a PowerShell prompt or script, use double quotes around the entire predicate string and single quotes within.</span></span> <span data-ttu-id="1ddc6-169">Cela évite de devoir échapper les caractères de guillemet double dans la chaîne de prédicat.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-169">This avoids the need to escape double quote characters within the predicate string.</span></span>

<span data-ttu-id="1ddc6-170">Vous pouvez également envisager d’enregistrer les journaux des événements dans un emplacement plus sécurisé, tel qu’un collecteur de journaux des événements centraux ou un agrégateur [Siem][] .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-170">You may also want to consider saving the event logs to a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="1ddc6-171">Vous pouvez configurer SIEM dans Azure.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-171">You can set up SIEM in Azure.</span></span> <span data-ttu-id="1ddc6-172">Pour plus d’informations, consultez [intégration Siem générique](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="1ddc6-172">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

## <a name="configuring-logging-on-a-non-windows-system"></a><span data-ttu-id="1ddc6-173">Configuration de la journalisation sur un système non-Windows</span><span class="sxs-lookup"><span data-stu-id="1ddc6-173">Configuring logging on a non-Windows system</span></span>

<span data-ttu-id="1ddc6-174">Sur Windows, la journalisation est configurée en créant des écouteurs de suivi ETW ou en utilisant le observateur d’événements pour activer la journalisation analytique.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-174">On Windows, logging is configured by creating ETW trace listeners or by using the Event Viewer to enable Analytic logging.</span></span> <span data-ttu-id="1ddc6-175">Sur Linux et macOS, la journalisation est configurée à l’aide du fichier `powershell.config.json` .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-175">On Linux and macOS, logging is configured using the file `powershell.config.json`.</span></span> <span data-ttu-id="1ddc6-176">Le reste de cette section traite de la configuration de la journalisation PowerShell sur un système non-Windows.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-176">The rest of this section will discuss configuring PowerShell logging on a non-Windows system.</span></span>

<span data-ttu-id="1ddc6-177">Par défaut, PowerShell active la journalisation d’informations sur le canal opérationnel.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-177">By default, PowerShell enables informational logging to the operational channel.</span></span> <span data-ttu-id="1ddc6-178">Cela signifie que toute sortie de journal produite par PowerShell marquée comme opérationnelle et dont le niveau de journalisation (suivi) est supérieur à information est consigné.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-178">What this means is any log output produced by PowerShell that is marked as operational and has a log (trace) level greater than informational will be logged.</span></span> <span data-ttu-id="1ddc6-179">Parfois, les diagnostics peuvent nécessiter une sortie de journal supplémentaire, par exemple une sortie de journal détaillée ou l’activation de la sortie de journal analytique.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-179">Occasionally, diagnoses may require additional log output, such as verbose log output or enabling analytic log output.</span></span>

<span data-ttu-id="1ddc6-180">Le fichier `powershell.config.json` est un fichier au format **JSON** résidant dans le `$PSHOME` répertoire PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-180">The file `powershell.config.json` is a **JSON** formatted file residing in the PowerShell `$PSHOME` directory.</span></span> <span data-ttu-id="1ddc6-181">Chaque installation de PowerShell utilise sa propre copie de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-181">Each installation of PowerShell uses its own copy of this file.</span></span> <span data-ttu-id="1ddc6-182">Pour un fonctionnement normal, ce fichier reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-182">For normal operation, this file is left unchanged.</span></span> <span data-ttu-id="1ddc6-183">Bien qu’il puisse être utile, pour modifier certains paramètres dans le fichier, pour le diagnostic ou pour distinguer plusieurs versions de PowerShell sur le même système ou même plusieurs copies de la même version (voir `LogIdentity` dans le tableau ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="1ddc6-183">Although it can be useful, to change some of the settings in the file, for diagnosis or for distinguishing between multiple PowerShell versions on the same system or even multiple copies of the same version (See `LogIdentity` in the table below).</span></span>

<span data-ttu-id="1ddc6-184">Le code suivant est un exemple de configuration :</span><span class="sxs-lookup"><span data-stu-id="1ddc6-184">The following code is an example configuration:</span></span>

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

<span data-ttu-id="1ddc6-185">Les propriétés de configuration de la journalisation PowerShell sont répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-185">The properties for configuring PowerShell logging are listed in the following table.</span></span> <span data-ttu-id="1ddc6-186">Les valeurs marquées d’un astérisque, telles que `Operational*` , indiquent la valeur par défaut quand aucune valeur n’est fournie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-186">Values marked with an asterisk, such as `Operational*`, indicate the default value when no value is provided in the file.</span></span>

|<span data-ttu-id="1ddc6-187">Propriété</span><span class="sxs-lookup"><span data-stu-id="1ddc6-187">Property</span></span>   |<span data-ttu-id="1ddc6-188">Valeurs</span><span class="sxs-lookup"><span data-stu-id="1ddc6-188">Values</span></span>        |<span data-ttu-id="1ddc6-189">Description</span><span class="sxs-lookup"><span data-stu-id="1ddc6-189">Description</span></span>                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|<span data-ttu-id="1ddc6-190">(nom de chaîne)</span><span class="sxs-lookup"><span data-stu-id="1ddc6-190">(string name)</span></span> |<span data-ttu-id="1ddc6-191">Nom à utiliser lors de la journalisation.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-191">The name to use when logging.</span></span> <span data-ttu-id="1ddc6-192">Par défaut,</span><span class="sxs-lookup"><span data-stu-id="1ddc6-192">By default,</span></span>  |
|           |<span data-ttu-id="1ddc6-193">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ddc6-193">powershell\*</span></span>   |<span data-ttu-id="1ddc6-194">PowerShell est l’identité.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-194">powershell is the identity.</span></span> <span data-ttu-id="1ddc6-195">Cette valeur peut être</span><span class="sxs-lookup"><span data-stu-id="1ddc6-195">This value can be</span></span>|
|           |              |<span data-ttu-id="1ddc6-196">permet d’indiquer la différence entre deux</span><span class="sxs-lookup"><span data-stu-id="1ddc6-196">used to tell the difference between two</span></span>      |
|           |              |<span data-ttu-id="1ddc6-197">les instances d’une installation PowerShell, telles que</span><span class="sxs-lookup"><span data-stu-id="1ddc6-197">instances of a PowerShell installation, such</span></span> |
|           |              |<span data-ttu-id="1ddc6-198">comme version bêta.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-198">as a release and beta version.</span></span> <span data-ttu-id="1ddc6-199">Cette valeur est</span><span class="sxs-lookup"><span data-stu-id="1ddc6-199">This value is</span></span> |
|           |              |<span data-ttu-id="1ddc6-200">également utilisé pour rediriger la sortie du journal vers un</span><span class="sxs-lookup"><span data-stu-id="1ddc6-200">also used to redirect log output to a</span></span>        |
|           |              |<span data-ttu-id="1ddc6-201">fichier distinct sur Linux.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-201">separate file on Linux.</span></span> <span data-ttu-id="1ddc6-202">Consultez la discussion sur</span><span class="sxs-lookup"><span data-stu-id="1ddc6-202">See the discussion of</span></span>|
|           |              |<span data-ttu-id="1ddc6-203">**rsyslog** ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-203">**rsyslog** above.</span></span>                           |
|`LogChannels`|<span data-ttu-id="1ddc6-204">Quotidiennes</span><span class="sxs-lookup"><span data-stu-id="1ddc6-204">Operational\*</span></span>  |<span data-ttu-id="1ddc6-205">Canaux à activer.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-205">The channels to enable.</span></span> <span data-ttu-id="1ddc6-206">Séparer les valeurs</span><span class="sxs-lookup"><span data-stu-id="1ddc6-206">Separate the values</span></span>|
|           |<span data-ttu-id="1ddc6-207">Analytiques</span><span class="sxs-lookup"><span data-stu-id="1ddc6-207">Analytic</span></span>      |<span data-ttu-id="1ddc6-208">avec une virgule quand vous spécifiez plusieurs.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-208">with a comma when specifying more than one.</span></span>  |
|`LogLevel`   |<span data-ttu-id="1ddc6-209">Toujours</span><span class="sxs-lookup"><span data-stu-id="1ddc6-209">Always</span></span>        |<span data-ttu-id="1ddc6-210">Spécifiez une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-210">Specify a single value.</span></span> <span data-ttu-id="1ddc6-211">La valeur active</span><span class="sxs-lookup"><span data-stu-id="1ddc6-211">The value enables</span></span>  |
|           |<span data-ttu-id="1ddc6-212">Critique</span><span class="sxs-lookup"><span data-stu-id="1ddc6-212">Critical</span></span>      |<span data-ttu-id="1ddc6-213">elle-même et toutes les valeurs qui la précèdent dans le</span><span class="sxs-lookup"><span data-stu-id="1ddc6-213">itself and all values above it in the</span></span>        |
|           |<span data-ttu-id="1ddc6-214">Error</span><span class="sxs-lookup"><span data-stu-id="1ddc6-214">Error</span></span>         |<span data-ttu-id="1ddc6-215">liste à gauche.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-215">list to the left.</span></span>                            |
|           |<span data-ttu-id="1ddc6-216">Avertissement</span><span class="sxs-lookup"><span data-stu-id="1ddc6-216">Warning</span></span>       |                                             |
|           |<span data-ttu-id="1ddc6-217">D’information</span><span class="sxs-lookup"><span data-stu-id="1ddc6-217">Informational\*</span></span>|                                             |
|           |<span data-ttu-id="1ddc6-218">Commentaires</span><span class="sxs-lookup"><span data-stu-id="1ddc6-218">Verbose</span></span>       |                                             |
|           |<span data-ttu-id="1ddc6-219">Débogage</span><span class="sxs-lookup"><span data-stu-id="1ddc6-219">Debug</span></span>         |                                             |
|`LogKeywords`|<span data-ttu-id="1ddc6-220">Instance d'exécution</span><span class="sxs-lookup"><span data-stu-id="1ddc6-220">Runspace</span></span>      |<span data-ttu-id="1ddc6-221">Les mots clés permettent de limiter la journalisation</span><span class="sxs-lookup"><span data-stu-id="1ddc6-221">Keywords provide the ability to limit logging</span></span>|
|           |<span data-ttu-id="1ddc6-222">Pipeline</span><span class="sxs-lookup"><span data-stu-id="1ddc6-222">Pipeline</span></span>      |<span data-ttu-id="1ddc6-223">à des composants spécifiques dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-223">to specific components within PowerShell.</span></span> <span data-ttu-id="1ddc6-224">par</span><span class="sxs-lookup"><span data-stu-id="1ddc6-224">By</span></span> |
|           |<span data-ttu-id="1ddc6-225">Protocole</span><span class="sxs-lookup"><span data-stu-id="1ddc6-225">Protocol</span></span>      |<span data-ttu-id="1ddc6-226">par défaut, tous les mots clés sont activés et modifiés</span><span class="sxs-lookup"><span data-stu-id="1ddc6-226">default, all keywords are enabled and change</span></span> |
|           |<span data-ttu-id="1ddc6-227">Transport</span><span class="sxs-lookup"><span data-stu-id="1ddc6-227">Transport</span></span>     |<span data-ttu-id="1ddc6-228">Cette valeur est utile uniquement pour les</span><span class="sxs-lookup"><span data-stu-id="1ddc6-228">this value is only useful for very</span></span>           |
|           |<span data-ttu-id="1ddc6-229">Host</span><span class="sxs-lookup"><span data-stu-id="1ddc6-229">Host</span></span>          |<span data-ttu-id="1ddc6-230">résolution des problèmes spécialisés.</span><span class="sxs-lookup"><span data-stu-id="1ddc6-230">specialized troubleshooting.</span></span>                |
|           |<span data-ttu-id="1ddc6-231">Applets de commande</span><span class="sxs-lookup"><span data-stu-id="1ddc6-231">Cmdlets</span></span>       |                                             |
|           |<span data-ttu-id="1ddc6-232">serializer</span><span class="sxs-lookup"><span data-stu-id="1ddc6-232">Serializer</span></span>    |                                             |
|           |<span data-ttu-id="1ddc6-233">Session</span><span class="sxs-lookup"><span data-stu-id="1ddc6-233">Session</span></span>       |                                             |
|           |<span data-ttu-id="1ddc6-234">ManagedPlugin</span><span class="sxs-lookup"><span data-stu-id="1ddc6-234">ManagedPlugin</span></span> |                                             |

## <a name="see-also"></a><span data-ttu-id="1ddc6-235">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ddc6-235">See also</span></span>

<span data-ttu-id="1ddc6-236">Pour les informations relatives à **syslog** et **rsyslog. conf** Linux, reportez-vous aux pages locales de l’ordinateur Linux `man` .</span><span class="sxs-lookup"><span data-stu-id="1ddc6-236">For Linux **syslog** and **rsyslog.conf** information, refer to the Linux computer's local `man` pages.</span></span>

<span data-ttu-id="1ddc6-237">Pour plus d’informations sur le **Os_log** MacOS, consultez [os_log documentation du développeur](https://developer.apple.com/documentation/os/os_log).</span><span class="sxs-lookup"><span data-stu-id="1ddc6-237">For macOS **os_log** information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

[<span data-ttu-id="1ddc6-238">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="1ddc6-238">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="1ddc6-239">Intégration de SIEM générique</span><span class="sxs-lookup"><span data-stu-id="1ddc6-239">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
