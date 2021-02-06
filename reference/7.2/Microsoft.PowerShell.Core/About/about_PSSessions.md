---
description: Décrit les sessions PowerShell (sessions PSSession) et explique comment établir une connexion permanente à un ordinateur distant.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: edc7109f3f79376ac1d348d3c3cd65e3a8d3e69c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597945"
---
# <a name="about-pssessions"></a><span data-ttu-id="f393e-103">À propos de sessions PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-103">About PSSessions</span></span>

## <a name="short-description"></a><span data-ttu-id="f393e-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="f393e-104">Short Description</span></span>
<span data-ttu-id="f393e-105">Décrit les sessions PowerShell (sessions PSSession) et explique comment établir une connexion permanente à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f393e-105">Describes PowerShell sessions (PSSessions) and explains how to establish a persistent connection to a remote computer.</span></span>

## <a name="long-description"></a><span data-ttu-id="f393e-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="f393e-106">Long Description</span></span>

<span data-ttu-id="f393e-107">Pour exécuter des commandes PowerShell sur un ordinateur distant, vous pouvez utiliser le paramètre **ComputerName** d’une applet de commande, ou vous pouvez créer une session PowerShell (PSSession) et exécuter des commandes dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-107">To run PowerShell commands on a remote computer, you can use the **ComputerName** parameter of a cmdlet, or you can create a PowerShell session (PSSession) and run commands in the PSSession.</span></span>

<span data-ttu-id="f393e-108">Lorsque vous créez une session PSSession, PowerShell établit une connexion permanente à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f393e-108">When you create a PSSession, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="f393e-109">Utilisez une session PSSession pour exécuter une série de commandes associées sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f393e-109">Use a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="f393e-110">Les commandes qui s’exécutent dans la même session PSSession peuvent partager des données, telles que les valeurs des variables, des alias et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="f393e-110">Commands that run in the same PSSession can share data, such as the values of variables, aliases, and functions.</span></span>

<span data-ttu-id="f393e-111">Vous pouvez également créer une session PSSession sur l’ordinateur local et y exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="f393e-111">You can also create a PSSession on the local computer and run commands in it.</span></span>
<span data-ttu-id="f393e-112">Une session PSSession locale utilise l’infrastructure de communication à distance PowerShell pour créer et maintenir la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-112">A local PSSession uses the PowerShell remoting infrastructure to create and maintain the PSSession.</span></span>

<span data-ttu-id="f393e-113">À compter de Windows PowerShell 3,0, les sessions PSSession sont indépendants des sessions dans lesquelles ils sont créés.</span><span class="sxs-lookup"><span data-stu-id="f393e-113">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they are created.</span></span> <span data-ttu-id="f393e-114">Les sessions PSSession actifs sont conservés sur l’ordinateur distant (ou l’ordinateur situé à l’extrémité distante ou côté serveur de la connexion).</span><span class="sxs-lookup"><span data-stu-id="f393e-114">Active PSSessions are maintained on the remote computer (or the computer at the remote end or "server-side" of the connection).</span></span> <span data-ttu-id="f393e-115">Par conséquent, vous pouvez vous déconnecter de la session PSSession et vous y reconnecter ultérieurement à partir du même ordinateur ou d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f393e-115">As a result, you can disconnect from the PSSession and reconnect to it at a later time from the same computer or from a different computer.</span></span>

<span data-ttu-id="f393e-116">Cette rubrique explique comment créer, utiliser, récupérer et supprimer des sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-116">This topic explains how to create, use, get, and delete PSSessions.</span></span> <span data-ttu-id="f393e-117">Pour plus d’informations, consultez [about_PSSession_Details](about_PSSession_Details.md).</span><span class="sxs-lookup"><span data-stu-id="f393e-117">For more advanced information, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

<span data-ttu-id="f393e-118">Remarque : sessions PSSession utilise l’infrastructure de communication à distance PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f393e-118">Note: PSSessions use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="f393e-119">Pour utiliser sessions PSSession, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="f393e-119">To use PSSessions, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="f393e-120">Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f393e-120">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

<span data-ttu-id="f393e-121">Dans Windows Vista et les versions ultérieures de Windows, vous devez démarrer PowerShell avec l’option « Exécuter en tant qu’administrateur » pour créer une session PSSession sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f393e-121">In Windows Vista and later versions of Windows, to create a PSSession on a local computer, you must start PowerShell with the "Run as administrator" option.</span></span>

## <a name="what-is-a-session"></a><span data-ttu-id="f393e-122">Qu’est-ce qu’une session ?</span><span class="sxs-lookup"><span data-stu-id="f393e-122">What Is a Session?</span></span>

<span data-ttu-id="f393e-123">Une session est un environnement dans lequel PowerShell s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f393e-123">A session is an environment in which PowerShell runs.</span></span>

<span data-ttu-id="f393e-124">Chaque fois que vous démarrez PowerShell, une session est créée pour vous et vous pouvez exécuter des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="f393e-124">Each time you start PowerShell, a session is created for you, and you can run commands in the session.</span></span> <span data-ttu-id="f393e-125">Vous pouvez également ajouter des éléments à votre session, tels que des modules et des composants logiciels enfichables, et vous pouvez créer des éléments, tels que des variables, des fonctions et des alias.</span><span class="sxs-lookup"><span data-stu-id="f393e-125">You can also add items to your session, such as modules and snap-ins, and you can create items, such as variables, functions, and aliases.</span></span> <span data-ttu-id="f393e-126">Ces éléments existent uniquement dans la session et sont supprimés à la fin de la session.</span><span class="sxs-lookup"><span data-stu-id="f393e-126">These items exist only in the session and are deleted when the session ends.</span></span>

<span data-ttu-id="f393e-127">Vous pouvez également créer des sessions gérées par l’utilisateur, appelées « sessions PowerShell » ou « sessions PSSession », sur l’ordinateur local ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f393e-127">You can also create user-managed sessions, known as " PowerShell sessions" or "PSSessions," on the local computer or on a remote computer.</span></span> <span data-ttu-id="f393e-128">Comme pour la session par défaut, vous pouvez exécuter des commandes dans une session PSSession et ajouter et créer des éléments.</span><span class="sxs-lookup"><span data-stu-id="f393e-128">Like the default session, you can run commands in a PSSession and add and create items.</span></span> <span data-ttu-id="f393e-129">Toutefois, contrairement à la session qui démarre automatiquement, vous pouvez contrôler le sessions PSSession que vous créez.</span><span class="sxs-lookup"><span data-stu-id="f393e-129">However, unlike the session that starts automatically, you can control the PSSessions that you create.</span></span> <span data-ttu-id="f393e-130">Vous pouvez les récupérer, les créer, les configurer et les supprimer, vous déconnecter et vous y reconnecter, et exécuter plusieurs commandes dans la même session PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-130">You can get, create, configure, and remove them, disconnect and reconnect to them, and run multiple commands in the same PSSession.</span></span> <span data-ttu-id="f393e-131">La session PSSession reste disponible jusqu’à ce que vous la supprimiez ou expire.</span><span class="sxs-lookup"><span data-stu-id="f393e-131">The PSSession remains available until you delete it or it times out.</span></span>

<span data-ttu-id="f393e-132">En général, vous créez une session PSSession pour exécuter une série de commandes associées sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f393e-132">Typically, you create a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="f393e-133">Lorsque vous créez une session PSSession sur un ordinateur distant, PowerShell établit une connexion permanente à l’ordinateur distant pour prendre en charge la session.</span><span class="sxs-lookup"><span data-stu-id="f393e-133">When you create a PSSession on a remote computer, PowerShell establishes a persistent connection to the remote computer to support the session.</span></span>

<span data-ttu-id="f393e-134">Si vous utilisez le paramètre **ComputerName** de l' `Invoke-Command` applet de `Enter-PSSession` commande ou pour exécuter une commande à distance ou démarrer une session interactive, PowerShell crée une session temporaire sur l’ordinateur distant et ferme la session dès que la commande est terminée ou dès la fin de la session interactive.</span><span class="sxs-lookup"><span data-stu-id="f393e-134">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlet to run a remote command or to start an interactive session, PowerShell creates a temporary session on the remote computer and closes the session as soon as the command is complete or as soon as the interactive session ends.</span></span> <span data-ttu-id="f393e-135">Vous ne pouvez pas contrôler ces sessions temporaires et vous ne pouvez pas les utiliser pour plusieurs commandes ou une seule session interactive.</span><span class="sxs-lookup"><span data-stu-id="f393e-135">You cannot control these temporary sessions, and you cannot use them for more than a single command or a single interactive session.</span></span>

<span data-ttu-id="f393e-136">Dans PowerShell, la « session active » correspond à la session dans laquelle vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="f393e-136">In PowerShell, the "current session" is the session that you are working in.</span></span> <span data-ttu-id="f393e-137">La « session active » peut faire référence à n’importe quelle session, y compris une session temporaire ou une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-137">The "current session" can refer to any session, including a temporary session or a PSSession.</span></span>

## <a name="why-use-a-pssession"></a><span data-ttu-id="f393e-138">Pourquoi utiliser une session PSSession ?</span><span class="sxs-lookup"><span data-stu-id="f393e-138">Why Use a PSSession?</span></span>

<span data-ttu-id="f393e-139">Utilisez une session PSSession lorsque vous avez besoin d’une connexion permanente à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f393e-139">Use a PSSession when you need a persistent connection to a remote computer.</span></span>
<span data-ttu-id="f393e-140">Avec PSSession, vous pouvez exécuter une série de commandes qui partagent des données, telles que la valeur des variables, le contenu d’une fonction ou la définition d’un alias.</span><span class="sxs-lookup"><span data-stu-id="f393e-140">With a PSSession, you can run a series of commands that share data, such as the value of variables, the contents of a function, or the definition of an alias.</span></span>

<span data-ttu-id="f393e-141">Vous pouvez exécuter des commandes distantes sans créer de session PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-141">You can run remote commands without creating a PSSession.</span></span> <span data-ttu-id="f393e-142">Utilisez le paramètre **ComputerName** des cmdlets distantes pour exécuter une seule commande ou une série de commandes non liées sur un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f393e-142">Use the **ComputerName** parameter of remote-enabled cmdlets to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="f393e-143">Quand vous utilisez le paramètre **ComputerName** de `Invoke-Command` ou `Enter-PSSession` , PowerShell établit une connexion temporaire à l’ordinateur distant, puis ferme la connexion dès que la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="f393e-143">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection to the remote computer and then closes the connection as soon as the command is complete.</span></span> <span data-ttu-id="f393e-144">Tout élément de données que vous créez est perdu lorsque la connexion est fermée.</span><span class="sxs-lookup"><span data-stu-id="f393e-144">Any data elements that you create are lost when the connection is closed.</span></span>

<span data-ttu-id="f393e-145">D’autres applets de commande ayant un paramètre **ComputerName** , telles que `Get-Eventlog` et `Get-WmiObject` , utilisent différentes technologies de communication à distance pour collecter des données.</span><span class="sxs-lookup"><span data-stu-id="f393e-145">Other cmdlets that have a **ComputerName** parameter, such as `Get-Eventlog` and `Get-WmiObject`, use different remoting technologies to gather data.</span></span> <span data-ttu-id="f393e-146">Aucun crée une connexion persistante comme une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-146">None create a persistent connection like a PSSession.</span></span>

## <a name="how-to-create-a-pssession"></a><span data-ttu-id="f393e-147">Comment créer une session PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-147">How to Create a PSSession</span></span>

<span data-ttu-id="f393e-148">Pour créer une session PSSession, utilisez l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f393e-148">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="f393e-149">Pour créer la session PSSession sur un ordinateur distant, utilisez le paramètre **ComputerName** de l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f393e-149">To create the PSSession on a remote computer, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="f393e-150">Par exemple, la commande suivante crée une session PSSession sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="f393e-150">For example, the following command creates a new PSSession on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

<span data-ttu-id="f393e-151">Lorsque vous envoyez la commande, `New-PSSession` crée la session PSSession et retourne un objet qui représente la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="f393e-151">When you submit the command, `New-PSSession` creates the PSSession and returns an object that represents the PSSession.</span></span> <span data-ttu-id="f393e-152">Vous pouvez enregistrer l’objet dans une variable lorsque vous créez la session PSSession, ou vous pouvez utiliser une `Get-PSSession` commande pour obtenir la session PSSession ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="f393e-152">You can save the object in a variable when you create the PSSession, or you can use a `Get-PSSession` command to get the PSSession at a later time.</span></span>

<span data-ttu-id="f393e-153">Par exemple, la commande suivante crée une session PSSession sur l’ordinateur SERVEUR01 et enregistre l’objet résultant dans la variable $ps.</span><span class="sxs-lookup"><span data-stu-id="f393e-153">For example, the following command creates a new PSSession on the Server01 computer and saves the resulting object in the $ps variable.</span></span>

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a><span data-ttu-id="f393e-154">Comment créer des sessions PSSession sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="f393e-154">How to Create PSSessions on Multiple Computers</span></span>

<span data-ttu-id="f393e-155">Pour créer des sessions PSSession sur plusieurs ordinateurs, utilisez le paramètre **ComputerName** de l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f393e-155">To create PSSessions on multiple computers, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="f393e-156">Tapez les noms des ordinateurs distants dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="f393e-156">Type the names of the remote computers in a comma-separated list.</span></span>

<span data-ttu-id="f393e-157">Par exemple, pour créer des sessions PSSession sur les ordinateurs Serveur01, Server02 et Server03, tapez :</span><span class="sxs-lookup"><span data-stu-id="f393e-157">For example, to create PSSessions on the Server01, Server02, and Server03 computers, type:</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="f393e-158">`New-PSSession` crée une session PSSession sur chacun des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="f393e-158">`New-PSSession` creates one PSSession on each of the remote computers.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="f393e-159">Obtention de sessions PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-159">How to Get PSSessions</span></span>

<span data-ttu-id="f393e-160">Pour récupérer les sessions PSSession qui ont été créés dans votre session active, utilisez l’applet de commande `Get-PSSession` sans le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="f393e-160">To get the PSSessions that were created in your current session, use the `Get-PSSession` cmdlet without the **ComputerName** parameter.</span></span> <span data-ttu-id="f393e-161">`Get-PSSession` retourne le même type d’objet que celui `New-PSSession` retourné par.</span><span class="sxs-lookup"><span data-stu-id="f393e-161">`Get-PSSession` returns the same type of object that `New-PSSession` returns.</span></span>

<span data-ttu-id="f393e-162">La commande suivante obtient toutes les sessions PSSession qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f393e-162">The following command gets all the PSSessions that were created in the current session.</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="f393e-163">L’affichage par défaut de l’sessions PSSession affiche son ID et un nom d’affichage par défaut.</span><span class="sxs-lookup"><span data-stu-id="f393e-163">The default display of the PSSessions shows their ID and a default display name.</span></span> <span data-ttu-id="f393e-164">Vous pouvez attribuer un autre nom d’affichage lorsque vous créez la session.</span><span class="sxs-lookup"><span data-stu-id="f393e-164">You can assign an alternate display name when you create the session.</span></span>

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

<span data-ttu-id="f393e-165">Vous pouvez également enregistrer le sessions PSSession dans une variable.</span><span class="sxs-lookup"><span data-stu-id="f393e-165">You can also save the PSSessions in a variable.</span></span> <span data-ttu-id="f393e-166">La commande suivante obtient le sessions PSSession et les enregistre dans la \$ variable ps123.</span><span class="sxs-lookup"><span data-stu-id="f393e-166">The following command gets the PSSessions and saves them in the \$ps123 variable.</span></span>

```powershell
$ps123 = Get-PSSession
```

<span data-ttu-id="f393e-167">Lorsque vous utilisez les applets de commande PSSession, vous pouvez faire référence à une session PSSession par son ID, son nom ou son ID d’instance (GUID).</span><span class="sxs-lookup"><span data-stu-id="f393e-167">When using the PSSession cmdlets, you can refer to a PSSession by its ID, by its name, or by its instance ID (a GUID).</span></span> <span data-ttu-id="f393e-168">La commande suivante obtient une session PSSession par son ID et l’enregistre dans la \$ variable PS01.</span><span class="sxs-lookup"><span data-stu-id="f393e-168">The following command gets a PSSession by its ID and saves it in the \$ps01 variable.</span></span>

```powershell
$ps01 = Get-PSSession -Id 1
```

<span data-ttu-id="f393e-169">À compter de Windows PowerShell 3,0, les sessions PSSession sont conservés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="f393e-169">Beginning in Windows PowerShell 3.0, PSSessions are maintained on the remote computer.</span></span> <span data-ttu-id="f393e-170">Pour accéder à des sessions PSSession que vous avez créés sur des ordinateurs distants particuliers, utilisez le paramètre **ComputerName** de l’applet de commande `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f393e-170">To get PSSessions that you created on particular remote computers, use the **ComputerName** parameter of the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="f393e-171">La commande suivante obtient les sessions PSSession que vous avez créés sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="f393e-171">The following command gets the PSSessions that you created on the Server01 remote computer.</span></span> <span data-ttu-id="f393e-172">Cela comprend les sessions PSSession créés dans la session active et dans d’autres sessions sur l’ordinateur local ou d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="f393e-172">This includes PSSessions created in the current session and in other sessions on the local computer or other computers.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

<span data-ttu-id="f393e-173">Dans Windows PowerShell 2,0, `Get-PSSession` obtient uniquement les sessions PSSession qui ont été créés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="f393e-173">In Windows PowerShell 2.0, `Get-PSSession` gets only the PSSessions that were created in the current session.</span></span> <span data-ttu-id="f393e-174">Il n’obtient pas les sessions PSSession qui ont été créés dans d’autres sessions ou sur d’autres ordinateurs, même si les sessions sont connectées à et exécutent des commandes sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f393e-174">It does not get PSSessions that were created in other sessions or on other computers, even if the sessions are connected to and are running commands on the local computer.</span></span>

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="f393e-175">Comment exécuter des commandes dans une session PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-175">How to Run Commands in a PSSession</span></span>

<span data-ttu-id="f393e-176">Pour exécuter une commande dans un ou plusieurs sessions PSSession, utilisez l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f393e-176">To run a command in one or more PSSessions, use the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="f393e-177">Utilisez le paramètre session pour spécifier sessions PSSession et le paramètre **scriptblock** pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="f393e-177">Use the Session parameter to specify the PSSessions and the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="f393e-178">Par exemple, pour exécuter une `Get-ChildItem` commande (« dir ») dans chacun des trois sessions PSSession enregistrés dans la variable $ps 123, tapez :</span><span class="sxs-lookup"><span data-stu-id="f393e-178">For example, to run a `Get-ChildItem` ("dir") command in each of the three PSSessions saved in the $ps123 variable, type:</span></span>

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a><span data-ttu-id="f393e-179">Comment supprimer des sessions PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-179">How to Delete PSSessions</span></span>

<span data-ttu-id="f393e-180">Lorsque vous avez terminé avec la session PSSession, utilisez l' `Remove-PSSession` applet de commande pour supprimer la session PSSession et libérer les ressources qu’elle utilisait.</span><span class="sxs-lookup"><span data-stu-id="f393e-180">When you are finished with the PSSession, use the `Remove-PSSession` cmdlet to delete the PSSession and to release the resources that it was using.</span></span>

```powershell
Remove-PSSession -Session $ps
```

<span data-ttu-id="f393e-181">ou</span><span class="sxs-lookup"><span data-stu-id="f393e-181">or</span></span>

```powershell
Remove-PSSession -Id 1
```

<span data-ttu-id="f393e-182">Pour supprimer une session PSSession d’un ordinateur distant, utilisez le paramètre **ComputerName** de l’applet de commande `Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="f393e-182">To remove a PSSession from a remote computer, use the **ComputerName** parameter of the `Remove-PSSession` cmdlet.</span></span>

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

<span data-ttu-id="f393e-183">Si vous ne supprimez pas la session PSSession, la session PSSession reste disponible pour être utilisée jusqu’à expiration.</span><span class="sxs-lookup"><span data-stu-id="f393e-183">If you do not delete the PSSession, the PSSession remains available for use until it times out.</span></span>

<span data-ttu-id="f393e-184">Vous pouvez également utiliser le paramètre **IdleTimeout** de l' `New-PSSessionOption` applet de commande pour définir une heure d’expiration pour une session PSSession inactive.</span><span class="sxs-lookup"><span data-stu-id="f393e-184">You can also use the **IdleTimeout** parameter of the `New-PSSessionOption` cmdlet to set an expiration time for an idle PSSession.</span></span> <span data-ttu-id="f393e-185">Pour plus d’informations, consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="f393e-185">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="the-pssession-cmdlets"></a><span data-ttu-id="f393e-186">Applets de commande PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-186">The PSSession Cmdlets</span></span>

<span data-ttu-id="f393e-187">Pour obtenir la liste des applets de commande PSSession, tapez :</span><span class="sxs-lookup"><span data-stu-id="f393e-187">For a list of PSSession cmdlets, type:</span></span>

```powershell
Get-Help *-PSSession
```

- <span data-ttu-id="f393e-188">Connect-PSSession : connecte une session PSSession à la session active</span><span class="sxs-lookup"><span data-stu-id="f393e-188">Connect-PSSession: Connects a PSSession to the current session</span></span>
- <span data-ttu-id="f393e-189">Disconnect-PSSession : déconnecte une session PSSession de la session active</span><span class="sxs-lookup"><span data-stu-id="f393e-189">Disconnect-PSSession: Disconnects a PSSession from the current session</span></span>
- <span data-ttu-id="f393e-190">Enter-PSSession : démarre une session interactive</span><span class="sxs-lookup"><span data-stu-id="f393e-190">Enter-PSSession: Starts an interactive session</span></span>
- <span data-ttu-id="f393e-191">Exit-PSSession : met fin à une session interactive</span><span class="sxs-lookup"><span data-stu-id="f393e-191">Exit-PSSession: Ends an interactive session</span></span>
- <span data-ttu-id="f393e-192">Obtenir-PSSession : obtient le sessions PSSession dans la session active</span><span class="sxs-lookup"><span data-stu-id="f393e-192">Get-PSSession: Gets the PSSessions in the current session</span></span>
- <span data-ttu-id="f393e-193">New-PSSession : crée une session PSSession sur un ordinateur local ou distant</span><span class="sxs-lookup"><span data-stu-id="f393e-193">New-PSSession: Creates a new PSSession on a local or remote computer</span></span>
- <span data-ttu-id="f393e-194">Receive-PSSession : obtient les résultats des commandes exécutées dans une session déconnectée</span><span class="sxs-lookup"><span data-stu-id="f393e-194">Receive-PSSession: Gets the results of commands that ran in a disconnected session</span></span>
- <span data-ttu-id="f393e-195">Remove-PSSession : supprime le sessions PSSession dans la session active</span><span class="sxs-lookup"><span data-stu-id="f393e-195">Remove-PSSession: Deletes the PSSessions in the current session</span></span>

## <a name="for-more-information"></a><span data-ttu-id="f393e-196">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="f393e-196">For More Information</span></span>

<span data-ttu-id="f393e-197">Pour plus d’informations sur sessions PSSession, consultez [about_PSSession_Details](about_PSSession_Details.md).</span><span class="sxs-lookup"><span data-stu-id="f393e-197">For more information about PSSessions, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f393e-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f393e-198">See Also</span></span>

[<span data-ttu-id="f393e-199">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f393e-199">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="f393e-200">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="f393e-200">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="f393e-201">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="f393e-201">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="f393e-202">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-202">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="f393e-203">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-203">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="f393e-204">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-204">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="f393e-205">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-205">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="f393e-206">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-206">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="f393e-207">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f393e-207">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="f393e-208">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-208">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="f393e-209">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="f393e-209">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)

