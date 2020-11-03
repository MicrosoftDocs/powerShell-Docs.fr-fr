---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202317"
---
# <span data-ttu-id="5bc7d-103">Export-Console</span><span class="sxs-lookup"><span data-stu-id="5bc7d-103">Export-Console</span></span>

## <span data-ttu-id="5bc7d-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5bc7d-104">SYNOPSIS</span></span>
<span data-ttu-id="5bc7d-105">Exporte les noms des composants logiciels enfichables de la session active dans un fichier de console.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-105">Exports the names of snap-ins in the current session to a console file.</span></span>

## <span data-ttu-id="5bc7d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5bc7d-106">SYNTAX</span></span>

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5bc7d-107">Description</span><span class="sxs-lookup"><span data-stu-id="5bc7d-107">DESCRIPTION</span></span>
<span data-ttu-id="5bc7d-108">L’applet de commande **Export-Console** exporte les noms des composants logiciels enfichables Windows PowerShell de la session active dans un fichier de console Windows PowerShell (. psc1).</span><span class="sxs-lookup"><span data-stu-id="5bc7d-108">The **Export-Console** cmdlet exports the names of the Windows PowerShell snap-ins in the current session to a Windows PowerShell console file (.psc1).</span></span>
<span data-ttu-id="5bc7d-109">Vous pouvez utiliser cette applet de commande pour enregistrer les composants logiciels enfichables à utiliser plus tard dans d'autres sessions.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-109">You can use this cmdlet to save the snap-ins for use in future sessions.</span></span>

<span data-ttu-id="5bc7d-110">Pour ajouter les composants logiciels enfichables du fichier de console. psc1 à une session, démarrez Windows PowerShell (Powershell.exe) sur la ligne de commande à l’aide de Cmd.exe ou d’une autre session Windows PowerShell, puis utilisez le paramètre *PSConsoleFile* de Powershell.exe pour spécifier le fichier de console.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-110">To add the snap-ins in the .psc1 console file to a session, start Windows PowerShell (Powershell.exe) at the command line by using Cmd.exe or another Windows PowerShell session, and then use the *PSConsoleFile* parameter of Powershell.exe to specify the console file.</span></span>

<span data-ttu-id="5bc7d-111">Pour plus d'informations sur les composants logiciels enfichables Windows PowerShell, consultez about_PSSnapins.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-111">For more information about Windows PowerShell snap-ins, see about_PSSnapins.</span></span>

## <span data-ttu-id="5bc7d-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5bc7d-112">EXAMPLES</span></span>

### <span data-ttu-id="5bc7d-113">Exemple 1 : exporter les noms des composants logiciels enfichables dans la session active</span><span class="sxs-lookup"><span data-stu-id="5bc7d-113">Example 1: Export the names of snap-ins in the current session</span></span>

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

<span data-ttu-id="5bc7d-114">Cette commande exporte les noms des composants logiciels enfichables Windows PowerShell de la session active dans le fichier ConsoleS1. psc1 dans le dossier consoles du dossier d’installation de Windows PowerShell, $pshome.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-114">This command exports the names of Windows PowerShell snap-ins in the current session to the ConsoleS1.psc1 file in the Consoles folder of the Windows PowerShell installation folder, $pshome.</span></span>

### <span data-ttu-id="5bc7d-115">Exemple 2 : exporter les noms des composants logiciels enfichables vers le fichier de console le plus récent</span><span class="sxs-lookup"><span data-stu-id="5bc7d-115">Example 2: Export the names of snap-ins to the most recent console file</span></span>

```
PS C:\> Export-Console
```

<span data-ttu-id="5bc7d-116">Cette commande exporte les noms des composants logiciels enfichables Windows PowerShell de la session active dans le dernier fichier de console Windows PowerShell utilisé dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-116">This command exports the names of Windows PowerShell snap-ins from current session to the Windows PowerShell console file that was most recently used in the current session.</span></span>
<span data-ttu-id="5bc7d-117">Elle remplace le contenu précédent du fichier.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-117">It overwrites the previous file contents.</span></span>

<span data-ttu-id="5bc7d-118">Si vous n'avez pas exporté de fichier de console pendant la session active, vous êtes invité à autoriser la poursuite de l'opération et à entrer un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-118">If you have not exported a console file during the current session, you are prompted for permission to continue and then prompted for a file name.</span></span>

### <span data-ttu-id="5bc7d-119">Exemple 3 : ajouter un composant logiciel enfichable et exporter les noms des composants logiciels enfichables</span><span class="sxs-lookup"><span data-stu-id="5bc7d-119">Example 3: Add a snap-in and export the names of snap-ins</span></span>

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

<span data-ttu-id="5bc7d-120">Ces commandes ajoutent le composant logiciel enfichable Windows PowerShell NewPSSnapin à la session active, exportent les noms des composants logiciels enfichables Windows PowerShell de la session active dans un fichier de console, puis démarrent une session Windows PowerShell avec le fichier de console.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-120">These commands add the NewPSSnapin Windows PowerShell snap-in to the current session, export the names of Windows PowerShell snap-ins in the current session to a console file, and then start a Windows PowerShell session with the console file.</span></span>

<span data-ttu-id="5bc7d-121">La première commande utilise l’applet de commande **Add-PSSnapin** pour ajouter le composant logiciel enfichable NewPSSnapin à la session active.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-121">The first command uses the **Add-PSSnapin** cmdlet to add the NewPSSnapin snap-in to the current session.</span></span>
<span data-ttu-id="5bc7d-122">Vous ne pouvez ajouter que les composants logiciels enfichables Windows PowerShell inscrits sur votre système.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-122">You can only add Windows PowerShell snap-ins that are registered on your system.</span></span>

<span data-ttu-id="5bc7d-123">La deuxième commande exporte les noms des composants logiciels enfichables Windows PowerShell dans le fichier NewPSSnapinConsole.psc1.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-123">The second command exports the Windows PowerShell snap-in names to the NewPSSnapinConsole.psc1 file.</span></span>

<span data-ttu-id="5bc7d-124">La troisième commande démarre Windows PowerShell avec le fichier NewPSSnapinConsole.psc1.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-124">The third command starts Windows PowerShell with the NewPSSnapinConsole.psc1 file.</span></span>
<span data-ttu-id="5bc7d-125">Étant donné que le fichier de console inclut le nom du composant logiciel enfichable Windows PowerShell, les applets de commande et les fournisseurs du composant logiciel enfichable sont disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-125">Because the console file includes the Windows PowerShell snap-in name, the cmdlets and providers in the snap-in are available in the current session.</span></span>

### <span data-ttu-id="5bc7d-126">Exemple 4 : exporter les noms des composants logiciels enfichables vers un emplacement spécifié</span><span class="sxs-lookup"><span data-stu-id="5bc7d-126">Example 4: Export names of snap-ins to a specified location</span></span>

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

<span data-ttu-id="5bc7d-127">Cette commande exporte les noms des composants logiciels enfichables Windows PowerShell de la session active vers le fichier Console01.psc1 dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-127">This command exports the names of the Windows PowerShell snap-ins in the current session to the Console01.psc1 file in the current directory.</span></span>

<span data-ttu-id="5bc7d-128">La deuxième commande affiche le contenu du fichier Console01.psc1 dans le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-128">The second command displays the contents of the Console01.psc1 file in Notepad.</span></span>

### <span data-ttu-id="5bc7d-129">Exemple 5 : déterminer le fichier de console à mettre à jour</span><span class="sxs-lookup"><span data-stu-id="5bc7d-129">Example 5: Determine the console file to update</span></span>

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

<span data-ttu-id="5bc7d-130">Cet exemple montre comment utiliser la variable automatique $ConsoleFileName pour déterminer le fichier de console qui sera mis à jour si vous utilisez **Export-Console** sans valeur de paramètre *path* .</span><span class="sxs-lookup"><span data-stu-id="5bc7d-130">This example shows how to use the $ConsoleFileName automatic variable to determine the console file that will be updated if you use **Export-Console** without a *Path* parameter value.</span></span>

<span data-ttu-id="5bc7d-131">La première commande utilise le paramètre *PSConsoleFile* de PowerShell.exe pour ouvrir Windows PowerShell avec le fichier fichier Console01. psc1.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-131">The first command uses the *PSConsoleFile* parameter of PowerShell.exe to open Windows PowerShell with the Console01.psc1 file.</span></span>

<span data-ttu-id="5bc7d-132">La deuxième commande utilise l’applet de commande **Add-PSSnapin** pour ajouter le composant logiciel enfichable Windows PowerShell MySnapin à la session active.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-132">The second command uses the **Add-PSSnapin** cmdlet to add the MySnapin Windows PowerShell snap-in to the current session.</span></span>

<span data-ttu-id="5bc7d-133">La troisième commande utilise l’applet de commande **Export-Console** pour exporter les noms de tous les composants logiciels enfichables Windows PowerShell de la session dans le fichier NewConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-133">The third command uses the **Export-Console** cmdlet to export the names of all the Windows PowerShell snap-ins in the session to the NewConsole.psc1 file.</span></span>

<span data-ttu-id="5bc7d-134">La quatrième commande affiche la variable $ConsoleFileName.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-134">The fourth command displays the $ConsoleFileName variable.</span></span>
<span data-ttu-id="5bc7d-135">Il contient le dernier fichier de console utilisé.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-135">It contains the most recently used console file.</span></span>
<span data-ttu-id="5bc7d-136">L'exemple de sortie montre que NewConsole.ps1 est le dernier fichier utilisé.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-136">The sample output shows that NewConsole.ps1 is the most recently used file.</span></span>

<span data-ttu-id="5bc7d-137">La cinquième commande ajoute SnapIn03 à la console actuelle.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-137">The fifth command adds SnapIn03 to the current console.</span></span>

<span data-ttu-id="5bc7d-138">La sixième commande utilise l’applet de commande **Export-Console** sans paramètre *path* .</span><span class="sxs-lookup"><span data-stu-id="5bc7d-138">The sixth command uses the **Export-Console** cmdlet without a *Path* parameter.</span></span>
<span data-ttu-id="5bc7d-139">Cette commande exporte les noms de tous les composants logiciels enfichables Windows PowerShell de la session active dans le dernier fichier utilisé, NewConsole.psc1.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-139">This command exports the names of all the Windows PowerShell snap-ins in the current session to the most recently used file, NewConsole.psc1.</span></span>

## <span data-ttu-id="5bc7d-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5bc7d-140">PARAMETERS</span></span>

### <span data-ttu-id="5bc7d-141">-Force</span><span class="sxs-lookup"><span data-stu-id="5bc7d-141">-Force</span></span>
<span data-ttu-id="5bc7d-142">Indique que cette applet de commande remplace les données dans un fichier de console sans avertissement, même si le fichier a l’attribut de lecture seule.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-142">Indicates that this cmdlet overwrites the data in a console file without warning, even if the file has the read-only attribute.</span></span>
<span data-ttu-id="5bc7d-143">L’attribut de lecture seule est modifié et n’est pas réinitialisé à la fin de l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-143">The read-only attribute is changed and is not reset when the command finishes.</span></span>

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

### <span data-ttu-id="5bc7d-144">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="5bc7d-144">-NoClobber</span></span>
<span data-ttu-id="5bc7d-145">Indique que cette applet de commande ne remplace pas un fichier de console existant.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-145">Indicates that this cmdlet does not overwrite  an existing console file.</span></span>
<span data-ttu-id="5bc7d-146">Par défaut, si un fichier se trouve dans le chemin d’accès spécifié, **Export-Console** remplace le fichier sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-146">By default, if a file occurs in the specified path, **Export-Console** overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5bc7d-147">-Path</span><span class="sxs-lookup"><span data-stu-id="5bc7d-147">-Path</span></span>
<span data-ttu-id="5bc7d-148">Spécifie un chemin d'accès et un nom de fichier pour le fichier de console (\*.psc1).</span><span class="sxs-lookup"><span data-stu-id="5bc7d-148">Specifies a path and file name for the console file (\*.psc1).</span></span>
<span data-ttu-id="5bc7d-149">Entrez un chemin d’accès et un nom facultatifs.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-149">Enter an optional path and name.</span></span>
<span data-ttu-id="5bc7d-150">Les caractères génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-150">Wildcard characters are not permitted.</span></span>

<span data-ttu-id="5bc7d-151">Si vous spécifiez uniquement un nom de fichier, **Export-Console** crée un fichier portant ce nom et l’extension de nom de fichier. psc1 dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-151">If you specify only a file name, **Export-Console** creates a file that has that name and the .psc1 file name extension in the current directory.</span></span>

<span data-ttu-id="5bc7d-152">Ce paramètre est obligatoire, sauf si vous avez ouvert Windows PowerShell avec le paramètre *PSConsoleFile* ou exporté un fichier de console pendant la session active.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-152">This parameter is required unless you have opened Windows PowerShell with the *PSConsoleFile* parameter or exported a console file during the current session.</span></span>
<span data-ttu-id="5bc7d-153">Elle est également requise quand vous utilisez le paramètre *NoClobber* pour empêcher le fichier de console actif d’être remplacé.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-153">It is also required when you use the *NoClobber* parameter to prevent the current console file from being overwritten.</span></span>

<span data-ttu-id="5bc7d-154">Si vous omettez ce paramètre, **Export-Console** remplace le fichier de console qui a été utilisé le plus récemment dans cette session.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-154">If you omit this parameter, **Export-Console** overwrites the console file that was used most recently in this session.</span></span>
<span data-ttu-id="5bc7d-155">Le chemin d’accès du dernier fichier de console utilisé est stocké dans la valeur de la variable automatique $ConsoleFileName.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-155">The path of the most recently used console file is stored in the value of the $ConsoleFileName automatic variable.</span></span>
<span data-ttu-id="5bc7d-156">Pour plus d'informations, consultez about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-156">For more information, see about_Automatic_Variables.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5bc7d-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5bc7d-157">-Confirm</span></span>
<span data-ttu-id="5bc7d-158">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5bc7d-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5bc7d-159">-WhatIf</span></span>
<span data-ttu-id="5bc7d-160">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5bc7d-161">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5bc7d-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5bc7d-162">CommonParameters</span></span>
<span data-ttu-id="5bc7d-163">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5bc7d-164">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5bc7d-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5bc7d-165">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5bc7d-165">INPUTS</span></span>

### <span data-ttu-id="5bc7d-166">System.String</span><span class="sxs-lookup"><span data-stu-id="5bc7d-166">System.String</span></span>
<span data-ttu-id="5bc7d-167">Vous pouvez diriger une chaîne de chemin d’accès vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-167">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="5bc7d-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5bc7d-168">OUTPUTS</span></span>

### <span data-ttu-id="5bc7d-169">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="5bc7d-169">System.IO.FileInfo</span></span>
<span data-ttu-id="5bc7d-170">Cette applet de commande crée un fichier qui contient les alias exportés.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-170">This cmdlet creates a file that contains the exported aliases.</span></span>

## <span data-ttu-id="5bc7d-171">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5bc7d-171">NOTES</span></span>

* <span data-ttu-id="5bc7d-172">Quand un fichier de console (.psc1) est utilisé pour démarrer la session, son nom est automatiquement stocké dans la variable automatique $ConsoleFileName.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-172">When a console file (.psc1) is used to start the session, the name of the console file is automatically stored in the $ConsoleFileName automatic variable.</span></span> <span data-ttu-id="5bc7d-173">La valeur de $ConsoleFileName est mise à jour quand vous utilisez le paramètre *path* de **Export-Console** pour spécifier un nouveau fichier de console.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-173">The value of $ConsoleFileName is updated when you use the *Path* parameter of **Export-Console** to specify a new console file.</span></span> <span data-ttu-id="5bc7d-174">Quand aucun fichier de console n’est utilisé, $ConsoleFileName n’a aucune valeur ($Null).</span><span class="sxs-lookup"><span data-stu-id="5bc7d-174">When no console file is used, $ConsoleFileName has no value ($Null).</span></span>

  <span data-ttu-id="5bc7d-175">Pour utiliser un fichier de console Windows PowerShell dans une nouvelle session, employez la syntaxe suivante pour démarrer Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5bc7d-175">To use a Windows PowerShell console file in a new session, use the following syntax to start Windows PowerShell:</span></span>

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  <span data-ttu-id="5bc7d-176">Vous pouvez également enregistrer les composants logiciels enfichables Windows PowerShell pour des sessions futures en ajoutant une commande Add-PSSnapin à votre profil Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-176">You can also save Windows PowerShell snap-ins for future sessions by adding an Add-PSSnapin command to your Windows PowerShell profile.</span></span>
<span data-ttu-id="5bc7d-177">Pour plus d'informations, consultez about_Providers.</span><span class="sxs-lookup"><span data-stu-id="5bc7d-177">For more information, see about_Profiles.</span></span>


## <span data-ttu-id="5bc7d-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5bc7d-178">RELATED LINKS</span></span>

[<span data-ttu-id="5bc7d-179">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="5bc7d-179">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="5bc7d-180">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="5bc7d-180">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="5bc7d-181">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="5bc7d-181">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
