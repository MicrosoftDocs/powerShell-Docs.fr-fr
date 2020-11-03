---
description: Décrit les sessions Windows PowerShell (sessions PSSession) et explique comment établir une connexion permanente à un ordinateur distant.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: 0bf3e24ca11108b5ab4739abd9be530243c50f11
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207985"
---
# <a name="about-pssessions"></a><span data-ttu-id="7d455-104">À propos de sessions PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-104">About PSSessions</span></span>

## <a name="short-description"></a><span data-ttu-id="7d455-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="7d455-105">Short Description</span></span>

<span data-ttu-id="7d455-106">Décrit les sessions Windows PowerShell (sessions PSSession) et explique comment établir une connexion permanente à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d455-106">Describes Windows PowerShell sessions (PSSessions) and explains how to establish a persistent connection to a remote computer.</span></span>

## <a name="long-description"></a><span data-ttu-id="7d455-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="7d455-107">Long Description</span></span>

<span data-ttu-id="7d455-108">Pour exécuter des commandes Windows PowerShell sur un ordinateur distant, vous pouvez utiliser le paramètre **ComputerName** d’une applet de commande, ou vous pouvez créer une session Windows PowerShell (PSSession) et exécuter des commandes dans la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-108">To run Windows PowerShell commands on a remote computer, you can use the **ComputerName** parameter of a cmdlet, or you can create a Windows PowerShell session (PSSession) and run commands in the PSSession.</span></span>

<span data-ttu-id="7d455-109">Quand vous créez une session PSSession, Windows PowerShell établit une connexion permanente à l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d455-109">When you create a PSSession, Windows PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="7d455-110">Utilisez une session PSSession pour exécuter une série de commandes associées sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d455-110">Use a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="7d455-111">Les commandes qui s’exécutent dans la même session PSSession peuvent partager des données, telles que les valeurs des variables, des alias et des fonctions.</span><span class="sxs-lookup"><span data-stu-id="7d455-111">Commands that run in the same PSSession can share data, such as the values of variables, aliases, and functions.</span></span>

<span data-ttu-id="7d455-112">Vous pouvez également créer une session PSSession sur l’ordinateur local et y exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="7d455-112">You can also create a PSSession on the local computer and run commands in it.</span></span>
<span data-ttu-id="7d455-113">Une session PSSession locale utilise l’infrastructure de communication à distance Windows PowerShell pour créer et maintenir la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-113">A local PSSession uses the Windows PowerShell remoting infrastructure to create and maintain the PSSession.</span></span>

<span data-ttu-id="7d455-114">À compter de Windows PowerShell 3,0, les sessions PSSession sont indépendants des sessions dans lesquelles ils sont créés.</span><span class="sxs-lookup"><span data-stu-id="7d455-114">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they are created.</span></span> <span data-ttu-id="7d455-115">Les sessions PSSession actifs sont conservés sur l’ordinateur distant (ou l’ordinateur situé à l’extrémité distante ou côté serveur de la connexion).</span><span class="sxs-lookup"><span data-stu-id="7d455-115">Active PSSessions are maintained on the remote computer (or the computer at the remote end or "server-side" of the connection).</span></span> <span data-ttu-id="7d455-116">Par conséquent, vous pouvez vous déconnecter de la session PSSession et vous y reconnecter ultérieurement à partir du même ordinateur ou d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7d455-116">As a result, you can disconnect from the PSSession and reconnect to it at a later time from the same computer or from a different computer.</span></span>

<span data-ttu-id="7d455-117">Cette rubrique explique comment créer, utiliser, récupérer et supprimer des sessions PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-117">This topic explains how to create, use, get, and delete PSSessions.</span></span> <span data-ttu-id="7d455-118">Pour plus d’informations, consultez [about_PSSession_Details](about_PSSession_Details.md).</span><span class="sxs-lookup"><span data-stu-id="7d455-118">For more advanced information, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

<span data-ttu-id="7d455-119">Remarque : sessions PSSession utilise l’infrastructure de communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d455-119">Note: PSSessions use the Windows PowerShell remoting infrastructure.</span></span> <span data-ttu-id="7d455-120">Pour utiliser sessions PSSession, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="7d455-120">To use PSSessions, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="7d455-121">Pour plus d'informations, consultez [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d455-121">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

<span data-ttu-id="7d455-122">Dans Windows Vista et les versions ultérieures de Windows, vous devez démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur » pour créer une session PSSession sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7d455-122">In Windows Vista and later versions of Windows, to create a PSSession on a local computer, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

## <a name="what-is-a-session"></a><span data-ttu-id="7d455-123">Qu’est-ce qu’une session ?</span><span class="sxs-lookup"><span data-stu-id="7d455-123">What Is a Session?</span></span>

<span data-ttu-id="7d455-124">Une session est un environnement dans lequel Windows PowerShell s’exécute.</span><span class="sxs-lookup"><span data-stu-id="7d455-124">A session is an environment in which Windows PowerShell runs.</span></span>

<span data-ttu-id="7d455-125">Chaque fois que vous démarrez Windows PowerShell, une session est créée pour vous et vous pouvez exécuter des commandes dans la session.</span><span class="sxs-lookup"><span data-stu-id="7d455-125">Each time you start Windows PowerShell, a session is created for you, and you can run commands in the session.</span></span> <span data-ttu-id="7d455-126">Vous pouvez également ajouter des éléments à votre session, tels que des modules et des composants logiciels enfichables, et vous pouvez créer des éléments, tels que des variables, des fonctions et des alias.</span><span class="sxs-lookup"><span data-stu-id="7d455-126">You can also add items to your session, such as modules and snap-ins, and you can create items, such as variables, functions, and aliases.</span></span> <span data-ttu-id="7d455-127">Ces éléments existent uniquement dans la session et sont supprimés à la fin de la session.</span><span class="sxs-lookup"><span data-stu-id="7d455-127">These items exist only in the session and are deleted when the session ends.</span></span>

<span data-ttu-id="7d455-128">Vous pouvez également créer des sessions gérées par l’utilisateur, appelées « sessions Windows PowerShell » ou « sessions PSSession », sur l’ordinateur local ou sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d455-128">You can also create user-managed sessions, known as " Windows PowerShell sessions" or "PSSessions," on the local computer or on a remote computer.</span></span> <span data-ttu-id="7d455-129">Comme pour la session par défaut, vous pouvez exécuter des commandes dans une session PSSession et ajouter et créer des éléments.</span><span class="sxs-lookup"><span data-stu-id="7d455-129">Like the default session, you can run commands in a PSSession and add and create items.</span></span> <span data-ttu-id="7d455-130">Toutefois, contrairement à la session qui démarre automatiquement, vous pouvez contrôler le sessions PSSession que vous créez.</span><span class="sxs-lookup"><span data-stu-id="7d455-130">However, unlike the session that starts automatically, you can control the PSSessions that you create.</span></span> <span data-ttu-id="7d455-131">Vous pouvez les récupérer, les créer, les configurer et les supprimer, vous déconnecter et vous y reconnecter, et exécuter plusieurs commandes dans la même session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-131">You can get, create, configure, and remove them, disconnect and reconnect to them, and run multiple commands in the same PSSession.</span></span> <span data-ttu-id="7d455-132">La session PSSession reste disponible jusqu’à ce que vous la supprimiez ou expire.</span><span class="sxs-lookup"><span data-stu-id="7d455-132">The PSSession remains available until you delete it or it times out.</span></span>

<span data-ttu-id="7d455-133">En général, vous créez une session PSSession pour exécuter une série de commandes associées sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d455-133">Typically, you create a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="7d455-134">Lorsque vous créez une session PSSession sur un ordinateur distant, Windows PowerShell établit une connexion permanente à l’ordinateur distant pour prendre en charge la session.</span><span class="sxs-lookup"><span data-stu-id="7d455-134">When you create a PSSession on a remote computer, Windows PowerShell establishes a persistent connection to the remote computer to support the session.</span></span>

<span data-ttu-id="7d455-135">Si vous utilisez le paramètre **ComputerName** de l' `Invoke-Command` applet de `Enter-PSSession` commande ou pour exécuter une commande à distance ou démarrer une session interactive, Windows PowerShell crée une session temporaire sur l’ordinateur distant et ferme la session dès que la commande est terminée ou dès la fin de la session interactive.</span><span class="sxs-lookup"><span data-stu-id="7d455-135">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlet to run a remote command or to start an interactive session, Windows PowerShell creates a temporary session on the remote computer and closes the session as soon as the command is complete or as soon as the interactive session ends.</span></span> <span data-ttu-id="7d455-136">Vous ne pouvez pas contrôler ces sessions temporaires et vous ne pouvez pas les utiliser pour plusieurs commandes ou une seule session interactive.</span><span class="sxs-lookup"><span data-stu-id="7d455-136">You cannot control these temporary sessions, and you cannot use them for more than a single command or a single interactive session.</span></span>

<span data-ttu-id="7d455-137">Dans Windows PowerShell, la « session active » correspond à la session dans laquelle vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="7d455-137">In Windows PowerShell, the "current session" is the session that you are working in.</span></span> <span data-ttu-id="7d455-138">La « session active » peut faire référence à n’importe quelle session, y compris une session temporaire ou une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-138">The "current session" can refer to any session, including a temporary session or a PSSession.</span></span>

## <a name="why-use-a-pssession"></a><span data-ttu-id="7d455-139">Pourquoi utiliser une session PSSession ?</span><span class="sxs-lookup"><span data-stu-id="7d455-139">Why Use a PSSession?</span></span>

<span data-ttu-id="7d455-140">Utilisez une session PSSession lorsque vous avez besoin d’une connexion permanente à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d455-140">Use a PSSession when you need a persistent connection to a remote computer.</span></span>
<span data-ttu-id="7d455-141">Avec PSSession, vous pouvez exécuter une série de commandes qui partagent des données, telles que la valeur des variables, le contenu d’une fonction ou la définition d’un alias.</span><span class="sxs-lookup"><span data-stu-id="7d455-141">With a PSSession, you can run a series of commands that share data, such as the value of variables, the contents of a function, or the definition of an alias.</span></span>

<span data-ttu-id="7d455-142">Vous pouvez exécuter des commandes distantes sans créer de session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-142">You can run remote commands without creating a PSSession.</span></span> <span data-ttu-id="7d455-143">Utilisez le paramètre **ComputerName** des cmdlets distantes pour exécuter une seule commande ou une série de commandes non liées sur un ou plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="7d455-143">Use the **ComputerName** parameter of remote-enabled cmdlets to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="7d455-144">Quand vous utilisez le paramètre **ComputerName** de `Invoke-Command` ou `Enter-PSSession` , Windows PowerShell établit une connexion temporaire à l’ordinateur distant, puis ferme la connexion dès que la commande est terminée.</span><span class="sxs-lookup"><span data-stu-id="7d455-144">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, Windows PowerShell establishes a temporary connection to the remote computer and then closes the connection as soon as the command is complete.</span></span> <span data-ttu-id="7d455-145">Tout élément de données que vous créez est perdu lorsque la connexion est fermée.</span><span class="sxs-lookup"><span data-stu-id="7d455-145">Any data elements that you create are lost when the connection is closed.</span></span>

<span data-ttu-id="7d455-146">D’autres applets de commande ayant un paramètre **ComputerName** , telles que `Get-Eventlog` et `Get-WmiObject` , utilisent différentes technologies de communication à distance pour collecter des données.</span><span class="sxs-lookup"><span data-stu-id="7d455-146">Other cmdlets that have a **ComputerName** parameter, such as `Get-Eventlog` and `Get-WmiObject`, use different remoting technologies to gather data.</span></span> <span data-ttu-id="7d455-147">Aucun crée une connexion persistante comme une session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-147">None create a persistent connection like a PSSession.</span></span>

## <a name="how-to-create-a-pssession"></a><span data-ttu-id="7d455-148">Comment créer une session PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-148">How to Create a PSSession</span></span>

<span data-ttu-id="7d455-149">Pour créer une session PSSession, utilisez l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7d455-149">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="7d455-150">Pour créer la session PSSession sur un ordinateur distant, utilisez le paramètre **ComputerName** de l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7d455-150">To create the PSSession on a remote computer, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="7d455-151">Par exemple, la commande suivante crée une session PSSession sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="7d455-151">For example, the following command creates a new PSSession on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

<span data-ttu-id="7d455-152">Lorsque vous envoyez la commande, `New-PSSession` crée la session PSSession et retourne un objet qui représente la session PSSession.</span><span class="sxs-lookup"><span data-stu-id="7d455-152">When you submit the command, `New-PSSession` creates the PSSession and returns an object that represents the PSSession.</span></span> <span data-ttu-id="7d455-153">Vous pouvez enregistrer l’objet dans une variable lorsque vous créez la session PSSession, ou vous pouvez utiliser une `Get-PSSession` commande pour obtenir la session PSSession ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="7d455-153">You can save the object in a variable when you create the PSSession, or you can use a `Get-PSSession` command to get the PSSession at a later time.</span></span>

<span data-ttu-id="7d455-154">Par exemple, la commande suivante crée une session PSSession sur l’ordinateur SERVEUR01 et enregistre l’objet résultant dans la variable $ps.</span><span class="sxs-lookup"><span data-stu-id="7d455-154">For example, the following command creates a new PSSession on the Server01 computer and saves the resulting object in the $ps variable.</span></span>

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a><span data-ttu-id="7d455-155">Comment créer des sessions PSSession sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="7d455-155">How to Create PSSessions on Multiple Computers</span></span>

<span data-ttu-id="7d455-156">Pour créer des sessions PSSession sur plusieurs ordinateurs, utilisez le paramètre **ComputerName** de l’applet de commande `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7d455-156">To create PSSessions on multiple computers, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="7d455-157">Tapez les noms des ordinateurs distants dans une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7d455-157">Type the names of the remote computers in a comma-separated list.</span></span>

<span data-ttu-id="7d455-158">Par exemple, pour créer des sessions PSSession sur les ordinateurs Serveur01, Server02 et Server03, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d455-158">For example, to create PSSessions on the Server01, Server02, and Server03 computers, type:</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="7d455-159">`New-PSSession` crée une session PSSession sur chacun des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="7d455-159">`New-PSSession` creates one PSSession on each of the remote computers.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="7d455-160">Obtention de sessions PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-160">How to Get PSSessions</span></span>

<span data-ttu-id="7d455-161">Pour récupérer les sessions PSSession qui ont été créés dans votre session active, utilisez l’applet de commande `Get-PSSession` sans le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="7d455-161">To get the PSSessions that were created in your current session, use the `Get-PSSession` cmdlet without the **ComputerName** parameter.</span></span> <span data-ttu-id="7d455-162">`Get-PSSession` retourne le même type d’objet que celui `New-PSSession` retourné par.</span><span class="sxs-lookup"><span data-stu-id="7d455-162">`Get-PSSession` returns the same type of object that `New-PSSession` returns.</span></span>

<span data-ttu-id="7d455-163">La commande suivante obtient toutes les sessions PSSession qui ont été créées dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7d455-163">The following command gets all the PSSessions that were created in the current session.</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="7d455-164">L’affichage par défaut de l’sessions PSSession affiche son ID et un nom d’affichage par défaut.</span><span class="sxs-lookup"><span data-stu-id="7d455-164">The default display of the PSSessions shows their ID and a default display name.</span></span> <span data-ttu-id="7d455-165">Vous pouvez attribuer un autre nom d’affichage lorsque vous créez la session.</span><span class="sxs-lookup"><span data-stu-id="7d455-165">You can assign an alternate display name when you create the session.</span></span>

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

<span data-ttu-id="7d455-166">Vous pouvez également enregistrer le sessions PSSession dans une variable.</span><span class="sxs-lookup"><span data-stu-id="7d455-166">You can also save the PSSessions in a variable.</span></span> <span data-ttu-id="7d455-167">La commande suivante obtient le sessions PSSession et les enregistre dans la \$ variable ps123.</span><span class="sxs-lookup"><span data-stu-id="7d455-167">The following command gets the PSSessions and saves them in the \$ps123 variable.</span></span>

```powershell
$ps123 = Get-PSSession
```

<span data-ttu-id="7d455-168">Lorsque vous utilisez les applets de commande PSSession, vous pouvez faire référence à une session PSSession par son ID, son nom ou son ID d’instance (GUID).</span><span class="sxs-lookup"><span data-stu-id="7d455-168">When using the PSSession cmdlets, you can refer to a PSSession by its ID, by its name, or by its instance ID (a GUID).</span></span> <span data-ttu-id="7d455-169">La commande suivante obtient une session PSSession par son ID et l’enregistre dans la \$ variable PS01.</span><span class="sxs-lookup"><span data-stu-id="7d455-169">The following command gets a PSSession by its ID and saves it in the \$ps01 variable.</span></span>

```powershell
$ps01 = Get-PSSession -Id 1
```

<span data-ttu-id="7d455-170">À compter de Windows PowerShell 3,0, les sessions PSSession sont conservés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d455-170">Beginning in Windows PowerShell 3.0, PSSessions are maintained on the remote computer.</span></span> <span data-ttu-id="7d455-171">Pour accéder à des sessions PSSession que vous avez créés sur des ordinateurs distants particuliers, utilisez le paramètre **ComputerName** de l’applet de commande `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7d455-171">To get PSSessions that you created on particular remote computers, use the **ComputerName** parameter of the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="7d455-172">La commande suivante obtient les sessions PSSession que vous avez créés sur l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="7d455-172">The following command gets the PSSessions that you created on the Server01 remote computer.</span></span> <span data-ttu-id="7d455-173">Cela comprend les sessions PSSession créés dans la session active et dans d’autres sessions sur l’ordinateur local ou d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="7d455-173">This includes PSSessions created in the current session and in other sessions on the local computer or other computers.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

<span data-ttu-id="7d455-174">Dans Windows PowerShell 2,0, `Get-PSSession` obtient uniquement les sessions PSSession qui ont été créés dans la session active.</span><span class="sxs-lookup"><span data-stu-id="7d455-174">In Windows PowerShell 2.0, `Get-PSSession` gets only the PSSessions that were created in the current session.</span></span> <span data-ttu-id="7d455-175">Il n’obtient pas les sessions PSSession qui ont été créés dans d’autres sessions ou sur d’autres ordinateurs, même si les sessions sont connectées à et exécutent des commandes sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7d455-175">It does not get PSSessions that were created in other sessions or on other computers, even if the sessions are connected to and are running commands on the local computer.</span></span>

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="7d455-176">Comment exécuter des commandes dans une session PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-176">How to Run Commands in a PSSession</span></span>

<span data-ttu-id="7d455-177">Pour exécuter une commande dans un ou plusieurs sessions PSSession, utilisez l' `Invoke-Command` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="7d455-177">To run a command in one or more PSSessions, use the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="7d455-178">Utilisez le paramètre session pour spécifier sessions PSSession et le paramètre **scriptblock** pour spécifier la commande.</span><span class="sxs-lookup"><span data-stu-id="7d455-178">Use the Session parameter to specify the PSSessions and the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="7d455-179">Par exemple, pour exécuter une `Get-ChildItem` commande (« dir ») dans chacun des trois sessions PSSession enregistrés dans la variable $ps 123, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d455-179">For example, to run a `Get-ChildItem` ("dir") command in each of the three PSSessions saved in the $ps123 variable, type:</span></span>

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a><span data-ttu-id="7d455-180">Comment supprimer des sessions PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-180">How to Delete PSSessions</span></span>

<span data-ttu-id="7d455-181">Lorsque vous avez terminé avec la session PSSession, utilisez l' `Remove-PSSession` applet de commande pour supprimer la session PSSession et libérer les ressources qu’elle utilisait.</span><span class="sxs-lookup"><span data-stu-id="7d455-181">When you are finished with the PSSession, use the `Remove-PSSession` cmdlet to delete the PSSession and to release the resources that it was using.</span></span>

```powershell
Remove-PSSession -Session $ps
```

<span data-ttu-id="7d455-182">ou</span><span class="sxs-lookup"><span data-stu-id="7d455-182">or</span></span>

```powershell
Remove-PSSession -Id 1
```

<span data-ttu-id="7d455-183">Pour supprimer une session PSSession d’un ordinateur distant, utilisez le paramètre **ComputerName** de l’applet de commande `Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7d455-183">To remove a PSSession from a remote computer, use the **ComputerName** parameter of the `Remove-PSSession` cmdlet.</span></span>

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

<span data-ttu-id="7d455-184">Si vous ne supprimez pas la session PSSession, la session PSSession reste disponible pour être utilisée jusqu’à expiration.</span><span class="sxs-lookup"><span data-stu-id="7d455-184">If you do not delete the PSSession, the PSSession remains available for use until it times out.</span></span>

<span data-ttu-id="7d455-185">Vous pouvez également utiliser le paramètre **IdleTimeout** de l' `New-PSSessionOption` applet de commande pour définir une heure d’expiration pour une session PSSession inactive.</span><span class="sxs-lookup"><span data-stu-id="7d455-185">You can also use the **IdleTimeout** parameter of the `New-PSSessionOption` cmdlet to set an expiration time for an idle PSSession.</span></span> <span data-ttu-id="7d455-186">Pour plus d’informations, consultez [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="7d455-186">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="the-pssession-cmdlets"></a><span data-ttu-id="7d455-187">Applets de commande PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-187">The PSSession Cmdlets</span></span>

<span data-ttu-id="7d455-188">Pour obtenir la liste des applets de commande PSSession, tapez :</span><span class="sxs-lookup"><span data-stu-id="7d455-188">For a list of PSSession cmdlets, type:</span></span>

```powershell
Get-Help *-PSSession
```

- <span data-ttu-id="7d455-189">Connect-PSSession : connecte une session PSSession à la session active</span><span class="sxs-lookup"><span data-stu-id="7d455-189">Connect-PSSession: Connects a PSSession to the current session</span></span>
- <span data-ttu-id="7d455-190">Disconnect-PSSession : déconnecte une session PSSession de la session active</span><span class="sxs-lookup"><span data-stu-id="7d455-190">Disconnect-PSSession: Disconnects a PSSession from the current session</span></span>
- <span data-ttu-id="7d455-191">Enter-PSSession : démarre une session interactive</span><span class="sxs-lookup"><span data-stu-id="7d455-191">Enter-PSSession: Starts an interactive session</span></span>
- <span data-ttu-id="7d455-192">Exit-PSSession : met fin à une session interactive</span><span class="sxs-lookup"><span data-stu-id="7d455-192">Exit-PSSession: Ends an interactive session</span></span>
- <span data-ttu-id="7d455-193">Obtenir-PSSession : obtient le sessions PSSession dans la session active</span><span class="sxs-lookup"><span data-stu-id="7d455-193">Get-PSSession: Gets the PSSessions in the current session</span></span>
- <span data-ttu-id="7d455-194">New-PSSession : crée une session PSSession sur un ordinateur local ou distant</span><span class="sxs-lookup"><span data-stu-id="7d455-194">New-PSSession: Creates a new PSSession on a local or remote computer</span></span>
- <span data-ttu-id="7d455-195">Receive-PSSession : obtient les résultats des commandes exécutées dans une session déconnectée</span><span class="sxs-lookup"><span data-stu-id="7d455-195">Receive-PSSession: Gets the results of commands that ran in a disconnected session</span></span>
- <span data-ttu-id="7d455-196">Remove-PSSession : supprime le sessions PSSession dans la session active</span><span class="sxs-lookup"><span data-stu-id="7d455-196">Remove-PSSession: Deletes the PSSessions in the current session</span></span>

## <a name="for-more-information"></a><span data-ttu-id="7d455-197">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="7d455-197">For More Information</span></span>

<span data-ttu-id="7d455-198">Pour plus d’informations sur sessions PSSession, consultez [about_PSSession_Details](about_PSSession_Details.md).</span><span class="sxs-lookup"><span data-stu-id="7d455-198">For more information about PSSessions, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d455-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d455-199">See Also</span></span>

[<span data-ttu-id="7d455-200">about_Remote</span><span class="sxs-lookup"><span data-stu-id="7d455-200">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="7d455-201">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="7d455-201">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="7d455-202">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="7d455-202">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="7d455-203">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-203">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="7d455-204">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-204">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="7d455-205">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-205">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="7d455-206">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-206">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="7d455-207">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-207">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="7d455-208">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7d455-208">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="7d455-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-209">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="7d455-210">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7d455-210">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)
