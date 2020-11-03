---
description: Explique comment utiliser l’outil en ligne de commande PowerShell_Ise.exe.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207957"
---
# <a name="about-powershell-iseexe"></a><span data-ttu-id="0c009-104">À propos des Ise.exe PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c009-104">About PowerShell Ise.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="0c009-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="0c009-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="0c009-106">Explique comment utiliser l’outil en ligne de commande PowerShell_Ise.exe.</span><span class="sxs-lookup"><span data-stu-id="0c009-106">Explains how to use the PowerShell_Ise.exe command-line tool.</span></span>

## <a name="long-description"></a><span data-ttu-id="0c009-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="0c009-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="0c009-108">PowerShell_Ise.exe démarre une session Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="0c009-108">PowerShell_Ise.exe starts a Windows PowerShell Integrated Scripting Environment (ISE) session.</span></span> <span data-ttu-id="0c009-109">Vous pouvez l’exécuter dans Cmd.exe et dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c009-109">You can run it in Cmd.exe and in Windows PowerShell.</span></span>

<span data-ttu-id="0c009-110">Pour exécuter PowerShell_ISE.exe, tapez PowerShell_ISE.exe, PowerShell_ISE ou ISE.</span><span class="sxs-lookup"><span data-stu-id="0c009-110">To run PowerShell_ISE.exe, type PowerShell_ISE.exe, PowerShell_ISE, or ISE.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c009-111">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0c009-111">SYNTAX</span></span>

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a><span data-ttu-id="0c009-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0c009-112">PARAMETERS</span></span>

### <a name="-file"></a><span data-ttu-id="0c009-113">-File</span><span class="sxs-lookup"><span data-stu-id="0c009-113">-File</span></span>

<span data-ttu-id="0c009-114">Ouvre les fichiers spécifiés dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0c009-114">Opens the specified files in Windows PowerShell ISE.</span></span> <span data-ttu-id="0c009-115">Le nom du paramètre (« -file ») est facultatif.</span><span class="sxs-lookup"><span data-stu-id="0c009-115">The parameter name ("-File") is optional.</span></span> <span data-ttu-id="0c009-116">Pour répertorier plusieurs fichiers, entrez une chaîne de texte entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="0c009-116">To list more than one file, enter one text string enclosed in quotation marks.</span></span> <span data-ttu-id="0c009-117">Utilisez des virgules pour séparer les noms de fichiers dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="0c009-117">Use commas to separate the file names within the string.</span></span>

<span data-ttu-id="0c009-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0c009-118">For example:</span></span>

<span data-ttu-id="0c009-119">PowerShell_ISE-file « File1.ps1, File2.ps1, File3.xml ».</span><span class="sxs-lookup"><span data-stu-id="0c009-119">PowerShell_ISE -File "File1.ps1,File2.ps1,File3.xml".</span></span>

<span data-ttu-id="0c009-120">Les espaces entre les noms de fichiers sont autorisés dans Windows PowerShell, mais ils peuvent ne pas être interprétés correctement par d’autres programmes, tels que Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="0c009-120">Spaces between the file names are permitted in Windows PowerShell, but might not be interpreted correctly by other programs, such as Cmd.exe.</span></span>

<span data-ttu-id="0c009-121">Vous pouvez utiliser ce paramètre pour ouvrir n’importe quel fichier texte, y compris les fichiers de script Windows PowerShell et les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="0c009-121">You can use this parameter to open any text file, including Windows PowerShell script files and XML files.</span></span>

### <a name="-mta"></a><span data-ttu-id="0c009-122">-Mta</span><span class="sxs-lookup"><span data-stu-id="0c009-122">-Mta</span></span>

<span data-ttu-id="0c009-123">Démarre Windows PowerShell ISE à l’aide d’un cloisonnement multithread.</span><span class="sxs-lookup"><span data-stu-id="0c009-123">Starts Windows PowerShell ISE using a multi-threaded apartment.</span></span> <span data-ttu-id="0c009-124">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0c009-124">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="0c009-125">Le cloisonnement (STA, Single-Threaded Apartment) est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0c009-125">Single-threaded apartment (STA) is the default.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="0c009-126">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="0c009-126">-NoProfile</span></span>

<span data-ttu-id="0c009-127">N’exécute pas les profils Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c009-127">Does not run Windows PowerShell profiles.</span></span> <span data-ttu-id="0c009-128">Par défaut, les profils Windows PowerShell sont exécutés dans chaque session.</span><span class="sxs-lookup"><span data-stu-id="0c009-128">By default, Windows PowerShell profiles are run in every session.</span></span>

<span data-ttu-id="0c009-129">Ce paramètre est recommandé lorsque vous écrivez du contenu partagé, comme des fonctions et des scripts qui seront exécutés sur des systèmes avec des profils différents.</span><span class="sxs-lookup"><span data-stu-id="0c009-129">This parameter is recommended when you are writing shared content, such as functions and scripts that will be run on systems with different profiles.</span></span>
<span data-ttu-id="0c009-130">Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0c009-130">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="-help---"></a><span data-ttu-id="0c009-131">-Help- ?,/ ?</span><span class="sxs-lookup"><span data-stu-id="0c009-131">-Help -?, /?</span></span>

<span data-ttu-id="0c009-132">Affiche l’aide pour PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="0c009-132">Displays help for PowerShell_ISE.exe.</span></span>

## <a name="examples"></a><span data-ttu-id="0c009-133">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="0c009-133">EXAMPLES</span></span>

<span data-ttu-id="0c009-134">Ces commandes démarrent Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0c009-134">These commands start Windows PowerShell ISE.</span></span> <span data-ttu-id="0c009-135">Les commandes sont équivalentes et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="0c009-135">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

<span data-ttu-id="0c009-136">Ces commandes ouvrent le script Get-Profile.ps1 dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0c009-136">These commands open the Get-Profile.ps1 script in Windows PowerShell ISE.</span></span>
<span data-ttu-id="0c009-137">Les commandes sont équivalentes et peuvent être utilisées indifféremment.</span><span class="sxs-lookup"><span data-stu-id="0c009-137">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

<span data-ttu-id="0c009-138">Cette commande ouvre les scripts Get-Backups.ps1 et Get-BackupInstance.ps1 dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0c009-138">This command opens the Get-Backups.ps1 and Get-BackupInstance.ps1 scripts in Windows PowerShell ISE.</span></span> <span data-ttu-id="0c009-139">Pour ouvrir plusieurs fichiers, utilisez une virgule pour séparer les noms de fichiers et placez la valeur de nom de fichier complète entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="0c009-139">To open more than one file, use a comma to separate the file names and enclose the entire file name value in quotation marks.</span></span>

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

<span data-ttu-id="0c009-140">Cette commande démarre Windows PowerShell ISE sans profil.</span><span class="sxs-lookup"><span data-stu-id="0c009-140">This command starts Windows PowerShell ISE with no profiles.</span></span>

```
PS C:> ISE -NoProfile
```

<span data-ttu-id="0c009-141">Cette commande obtient de l’aide pour PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="0c009-141">This command gets help for PowerShell_ISE.exe.</span></span>

```
PS C:> ISE -help
```

## <a name="see-also"></a><span data-ttu-id="0c009-142">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="0c009-142">SEE ALSO</span></span>

[<span data-ttu-id="0c009-143">about_PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="0c009-143">about_PowerShell.exe</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="0c009-144">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="0c009-144">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)

[<span data-ttu-id="0c009-145">Environnement d’écriture de scripts intégré de Windows PowerShell (ISE)</span><span class="sxs-lookup"><span data-stu-id="0c009-145">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
