---
title: Accès distant à WS-Management (WSMan) dans PowerShell Core
description: Accès distant dans PowerShell Core à l’aide de WSMan
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402047"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="3a3c6-103">Accès distant à WS-Management (WSMan) dans PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3a3c6-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="3a3c6-104">Instructions pour créer un point de terminaison de communication à distance</span><span class="sxs-lookup"><span data-stu-id="3a3c6-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="3a3c6-105">Le package PowerShell Core pour Windows inclut un plug-in WinRM (`pwrshplugin.dll`) et un script d’installation (`Install-PowerShellRemoting.ps1`) dans `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="3a3c6-106">Ces fichiers permettent à PowerShell d’accepter les connexions à distance PowerShell entrantes quand son point de terminaison est spécifié.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="3a3c6-107">Motivation</span><span class="sxs-lookup"><span data-stu-id="3a3c6-107">Motivation</span></span>

<span data-ttu-id="3a3c6-108">Une installation de PowerShell peut établir des sessions PowerShell sur des ordinateurs distants avec `New-PSSession` et `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="3a3c6-109">Pour lui permettre d’accepter les connexions à distance PowerShell, l’utilisateur doit créer un point de terminaison d’accès distant WinRM.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="3a3c6-110">Il s’agit d’un scénario à choisir explicitement là où l’utilisateur exécute Install-PowerShellRemoting.ps1 pour créer le point de terminaison WinRM.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="3a3c6-111">Le script d’installation est une solution à court terme jusqu’à ce que nous ajoutions une fonctionnalité supplémentaire à `Enable-PSRemoting` pour effectuer la même action.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="3a3c6-112">Pour plus d’informations, reportez-vous au problème [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="3a3c6-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="3a3c6-113">Actions du script</span><span class="sxs-lookup"><span data-stu-id="3a3c6-113">Script Actions</span></span>

<span data-ttu-id="3a3c6-114">Le script</span><span class="sxs-lookup"><span data-stu-id="3a3c6-114">The script</span></span>

1. <span data-ttu-id="3a3c6-115">Crée un répertoire pour le plug-in dans %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a3c6-115">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="3a3c6-116">Copie pwrshplugin.dll à cet emplacement</span><span class="sxs-lookup"><span data-stu-id="3a3c6-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="3a3c6-117">Génère un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="3a3c6-117">Generates a configuration file</span></span>
1. <span data-ttu-id="3a3c6-118">Inscrit ce plug-in auprès de WinRM</span><span class="sxs-lookup"><span data-stu-id="3a3c6-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="3a3c6-119">Inscription</span><span class="sxs-lookup"><span data-stu-id="3a3c6-119">Registration</span></span>

<span data-ttu-id="3a3c6-120">Le script doit être exécuté dans une session PowerShell de niveau administrateur et il s’exécute dans deux modes.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="3a3c6-121">Exécuté par l’instance de PowerShell qu’il inscrira</span><span class="sxs-lookup"><span data-stu-id="3a3c6-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="3a3c6-122">Exécuté par une autre instance de PowerShell pour le compte de l’instance qu’il inscrira</span><span class="sxs-lookup"><span data-stu-id="3a3c6-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="3a3c6-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3a3c6-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="3a3c6-124">**REMARQUE :** Le script d’inscription de communication à distance doit redémarrer WinRM. Toutes les sessions PSRP existantes seront donc terminées immédiatement après l’exécution du script.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="3a3c6-125">S’il est exécuté pendant une session à distance, ceci mettra fin à la connexion.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="3a3c6-126">Comment se connecter à un nouveau point de terminaison</span><span class="sxs-lookup"><span data-stu-id="3a3c6-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="3a3c6-127">Créez une session PowerShell sur le nouveau point de terminaison PowerShell en spécifiant `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="3a3c6-128">Pour vous connecter à l’instance PowerShell de l’exemple ci-dessus, utilisez :</span><span class="sxs-lookup"><span data-stu-id="3a3c6-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="3a3c6-129">Notez que les appels de `New-PSSession` et de `Enter-PSSession` qui ne spécifient pas `-ConfigurationName` ciblent le point de terminaison PowerShell par défaut, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="3a3c6-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>