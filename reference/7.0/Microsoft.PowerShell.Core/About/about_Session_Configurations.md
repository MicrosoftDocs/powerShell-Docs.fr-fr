---
description: Décrit les configurations de session qui déterminent les utilisateurs pouvant se connecter à distance à l'ordinateur et les commandes qu'ils peuvent exécuter.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 5b59d8fb05ee118f5b2d7b5b859efad9be75814a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206585"
---
# <a name="about-session-configurations"></a><span data-ttu-id="a4eb6-104">À propos des configurations de session</span><span class="sxs-lookup"><span data-stu-id="a4eb6-104">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="a4eb6-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="a4eb6-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a4eb6-106">Décrit les configurations de session qui déterminent les utilisateurs pouvant se connecter à distance à l'ordinateur et les commandes qu'ils peuvent exécuter.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-106">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="a4eb6-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="a4eb6-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a4eb6-108">Une configuration de session, également appelée « point de terminaison », est un groupe de paramètres sur l’ordinateur local qui définissent l’environnement des sessions PowerShell qui sont créées lorsque des utilisateurs distants ou locaux se connectent à PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-108">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="a4eb6-109">Les administrateurs de l’ordinateur peuvent utiliser des configurations de session pour protéger l’ordinateur et définir des environnements personnalisés pour les utilisateurs qui se connectent à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-109">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="a4eb6-110">Les administrateurs peuvent également utiliser des configurations de session pour déterminer les autorisations requises pour se connecter à l’ordinateur à distance.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-110">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="a4eb6-111">Par défaut, seuls les membres du groupe administrateurs sont autorisés à utiliser la configuration de session pour se connecter à distance, mais vous pouvez modifier les paramètres par défaut pour permettre à tous les utilisateurs, ou aux utilisateurs sélectionnés, de se connecter à distance à votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-111">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="a4eb6-112">À compter de PowerShell 3,0, vous pouvez utiliser un fichier de configuration de session pour définir les éléments d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-112">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="a4eb6-113">Cette fonctionnalité permet de personnaliser facilement les sessions sans écrire de code et de découvrir les propriétés d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-113">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="a4eb6-114">Pour créer un fichier de configuration de session, utilisez l’applet de commande New-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-114">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a4eb6-115">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="a4eb6-115">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="a4eb6-116">Les configurations de session sont une fonctionnalité de la communication à distance PowerShell basée sur les services Web for Management (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="a4eb6-116">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="a4eb6-117">Ils sont utilisés uniquement lorsque vous utilisez les applets de commande New-PSSession, Invoke-Command ou Enter-PSSession pour vous connecter à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-117">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="a4eb6-118">Remarque : pour gérer les configurations de session, démarrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="a4eb6-118">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="a4eb6-119">À propos des configurations de session</span><span class="sxs-lookup"><span data-stu-id="a4eb6-119">About Session Configurations</span></span>

<span data-ttu-id="a4eb6-120">Chaque session PowerShell utilise une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-120">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="a4eb6-121">Cela comprend les sessions persistantes que vous créez à l’aide des applets de commande New-PSSession ou Enter-PSSession, et les sessions temporaires que PowerShell crée lorsque vous utilisez le paramètre ComputerName d’une applet de commande qui utilise la technologie de communication à distance basée sur WS-Management, comme Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-121">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="a4eb6-122">Les administrateurs peuvent utiliser des configurations de session pour protéger les ressources de l’ordinateur et créer des environnements personnalisés pour les utilisateurs qui se connectent à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-122">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="a4eb6-123">Par exemple, vous pouvez utiliser une configuration de session pour limiter la taille des objets que l’ordinateur reçoit dans la session, pour définir le mode de langue de la session et pour spécifier les applets de commande, fournisseurs et fonctions disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-123">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="a4eb6-124">En configurant le descripteur de sécurité d’une configuration de session, vous déterminez qui peut utiliser la configuration de session pour se connecter à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-124">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="a4eb6-125">Les utilisateurs doivent disposer de l’autorisation EXECUTE sur une configuration de session pour pouvoir l’utiliser dans une session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-125">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="a4eb6-126">Si un utilisateur ne dispose pas des autorisations nécessaires pour utiliser l’une des configurations de session sur un ordinateur, il ne peut pas se connecter à distance à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-126">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="a4eb6-127">Par défaut, seuls les administrateurs de l’ordinateur sont autorisés à utiliser les configurations de session par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-127">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="a4eb6-128">Toutefois, vous pouvez modifier les descripteurs de sécurité pour autoriser tout le monde, personne ou uniquement les utilisateurs sélectionnés à utiliser les configurations de session sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-128">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="a4eb6-129">Configurations de session intégrées</span><span class="sxs-lookup"><span data-stu-id="a4eb6-129">Built-in Session Configurations</span></span>

<span data-ttu-id="a4eb6-130">PowerShell 3,0 comprend des configurations de session intégrées nommées Microsoft. PowerShell et Microsoft. PowerShell. Workflow.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-130">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="a4eb6-131">Sur les ordinateurs exécutant des versions 64 bits de Windows, PowerShell fournit également Microsoft. PowerShell32, une configuration de session 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-131">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="a4eb6-132">La configuration de session Microsoft. PowerShell est utilisée pour les sessions par défaut, autrement dit, quand une commande permettant de créer une session n’inclut pas le paramètre ConfigurationName de l’applet de commande New-PSSession, Enter-PSSession ou Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-132">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="a4eb6-133">Les descripteurs de sécurité pour les configurations de session par défaut autorisent uniquement les membres du groupe Administrateurs sur l’ordinateur local à les utiliser.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-133">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="a4eb6-134">Ainsi, seuls les membres du groupe administrateurs peuvent se connecter à l’ordinateur à distance, sauf si vous modifiez les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-134">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="a4eb6-135">Vous pouvez modifier les configurations de session par défaut à l’aide de la variable de préférence $PSSessionConfigurationName.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-135">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="a4eb6-136">Pour plus d'informations, consultez about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-136">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="a4eb6-137">Affichage des configurations de session sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="a4eb6-137">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="a4eb6-138">Pour récupérer les configurations de session sur votre ordinateur local, utilisez l’applet de commande Get-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-138">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="a4eb6-139">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="a4eb6-139">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="a4eb6-140">L’objet de configuration de session est développé dans PowerShell 3,0 pour afficher les propriétés de la configuration de session configurées à l’aide d’un fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-140">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="a4eb6-141">Par exemple, pour afficher toutes les propriétés d’un objet de configuration de session, tapez :</span><span class="sxs-lookup"><span data-stu-id="a4eb6-141">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="a4eb6-142">Vous pouvez également utiliser le fournisseur WSMan dans PowerShell pour afficher les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-142">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="a4eb6-143">Le fournisseur WSMan crée un lecteur WSMAN : dans votre session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-143">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="a4eb6-144">Dans le lecteur WSMAN :, les configurations de session se trouvent dans le nœud de plug-in.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-144">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="a4eb6-145">(Toutes les configurations de session se trouvent dans le nœud de plug-in, mais il existe des éléments dans le nœud de plug-in qui ne sont pas des configurations de session.)</span><span class="sxs-lookup"><span data-stu-id="a4eb6-145">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="a4eb6-146">Par exemple, pour afficher les configurations de session sur l’ordinateur local, tapez :</span><span class="sxs-lookup"><span data-stu-id="a4eb6-146">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="a4eb6-147">Affichage des configurations de session sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="a4eb6-147">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="a4eb6-148">Pour afficher les configurations de session sur un ordinateur distant, utilisez l’applet de commande Connect-WSMan pour ajouter une note pour l’ordinateur distant au lecteur WSMAN : sur votre ordinateur local, puis utilisez le lecteur WSMAN : pour afficher les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-148">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="a4eb6-149">Par exemple, la commande suivante ajoute un nœud pour l’ordinateur distant SERVEUR01 au lecteur WSMAN : sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-149">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="a4eb6-150">Une fois la commande terminée, vous pouvez accéder au nœud de l’ordinateur SERVEUR01 pour afficher les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-150">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="a4eb6-151">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a4eb6-151">For example:</span></span>

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="a4eb6-152">Modification du descripteur de sécurité d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="a4eb6-152">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="a4eb6-153">Dans Windows Server 2012 et les versions plus récentes de Windows Server, les configurations de session intégrées sont activées par défaut pour les utilisateurs distants.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-153">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="a4eb6-154">Dans les autres versions prises en charge de Windows, vous devez modifier les descripteurs de sécurité des configurations de session pour autoriser l’accès à distance.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-154">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="a4eb6-155">Pour activer l’accès à distance aux configurations de session sur l’ordinateur, utilisez l’applet de commande Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-155">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="a4eb6-156">Cette applet de commande crée deux configurations de session :</span><span class="sxs-lookup"><span data-stu-id="a4eb6-156">This cmdlet creates two session configurations:</span></span>

- <span data-ttu-id="a4eb6-157">avec le nom défini en tant que : « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="a4eb6-157">with the name defined as: "PowerShell."</span></span> <span data-ttu-id="a4eb6-158">+ « version actuelle de PowerShell »</span><span class="sxs-lookup"><span data-stu-id="a4eb6-158">+ "current PowerShell version"</span></span>
- <span data-ttu-id="a4eb6-159">avec le nom « PowerShell. 6 », qui n’est pas lié à une version spécifique de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-159">with name "PowerShell.6", untied to any specific PowerShell version.</span></span>

<span data-ttu-id="a4eb6-160">De même, par défaut, seuls les membres du groupe Administrateurs sur l’ordinateur ont l’autorisation EXECUTE sur les configurations de session par défaut, mais vous pouvez modifier les descripteurs de sécurité sur les configurations de session par défaut et sur toutes les configurations de session que vous créez.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-160">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="a4eb6-161">Pour accorder à d’autres utilisateurs l’autorisation de se connecter à distance à l’ordinateur, utilisez l’applet de commande Set-PSSessionConfiguration pour ajouter des autorisations « exécuter » pour ces utilisateurs aux descripteurs de sécurité des configurations de session Microsoft. PowerShell et Microsoft. PowerShell32.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-161">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="a4eb6-162">Par exemple, la commande suivante ouvre une page de propriétés qui vous permet de modifier le descripteur de sécurité pour la configuration de session Microsoft. PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-162">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="a4eb6-163">Pour refuser l’autorisation tout le monde à toutes les configurations de session sur l’ordinateur, utilisez l’applet de commande Disable-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-163">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a4eb6-164">Par exemple, la commande suivante désactive les configurations de session par défaut sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-164">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="a4eb6-165">Pour empêcher les utilisateurs distants de se connecter à l’ordinateur, mais autoriser les utilisateurs locaux à se connecter, utilisez l’applet de commande Disable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-165">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="a4eb6-166">Disable-PSRemoting ajoute une entrée « Network_Deny_All » à toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-166">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="a4eb6-167">Pour permettre aux utilisateurs distants d’utiliser toutes les configurations de session sur l’ordinateur, utilisez l’applet de commande Enable-PSRemoting ou Enable-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-167">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a4eb6-168">Par exemple, la commande suivante active l’accès à distance aux configurations de session intégrées.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-168">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="a4eb6-169">Pour apporter d’autres modifications au descripteur de sécurité d’une configuration de session, utilisez l’applet de commande Set-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-169">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a4eb6-170">Utilisez le paramètre SecurityDescriptorSDDL pour envoyer une valeur de chaîne SDDL.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-170">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="a4eb6-171">Utilisez le paramètre ShowSecurityDescriptorUI pour afficher une feuille de propriétés de l’interface utilisateur qui vous aide à créer un nouveau SDDL.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-171">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="a4eb6-172">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a4eb6-172">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="a4eb6-173">Création d’une nouvelle configuration de session</span><span class="sxs-lookup"><span data-stu-id="a4eb6-173">Creating a New Session Configuration</span></span>

<span data-ttu-id="a4eb6-174">Pour créer une nouvelle configuration de session sur l’ordinateur local, utilisez l’applet de commande Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-174">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a4eb6-175">Pour définir la nouvelle configuration de session, vous pouvez utiliser un assembly C#, un script PowerShell et les paramètres de l’applet de commande Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-175">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="a4eb6-176">Par exemple, la commande suivante crée une configuration de session qui est identique à la configuration de session Microsoft. PowerShell, à ceci près qu’elle limite les données reçues d’une commande à distance à 20 mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="a4eb6-176">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="a4eb6-177">(La valeur par défaut est 50 Mo).</span><span class="sxs-lookup"><span data-stu-id="a4eb6-177">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="a4eb6-178">Lorsque vous créez une configuration de session, vous pouvez la gérer à l’aide des autres applets de commande de configuration de session, et elle apparaît dans le lecteur WSMAN :.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-178">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="a4eb6-179">Pour plus d’informations, consultez Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-179">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="a4eb6-180">Suppression d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="a4eb6-180">Removing a Session Configuration</span></span>

<span data-ttu-id="a4eb6-181">Pour supprimer une configuration de session de l’ordinateur local, utilisez l’applet de commande Unregister-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-181">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="a4eb6-182">Par exemple, la commande suivante supprime la configuration de session NewConfig de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-182">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="a4eb6-183">Pour plus d’informations, consultez Unregister-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-183">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="a4eb6-184">Restauration d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="a4eb6-184">Restoring a Session Configuration</span></span>

<span data-ttu-id="a4eb6-185">Pour restaurer une configuration de session par défaut qui a été supprimée (désinscrite) accidentellement, utilisez l’applet de commande Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-185">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="a4eb6-186">L’applet de commande Enable-PSRemoting recrée toutes les configurations de sessions par défaut qui n’existent pas sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-186">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="a4eb6-187">Elle ne remplace pas ou ne modifie pas les valeurs des propriétés des configurations de session existantes.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-187">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="a4eb6-188">Pour restaurer les valeurs de propriété d’origine d’une configuration de session par défaut, utilisez la Unregister-PSSessionConfiguration pour supprimer la configuration de session, puis utilisez l’applet de commande Enable-PSRemoting pour la recréer.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-188">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="a4eb6-189">Sélection d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="a4eb6-189">Selecting a Session Configuration</span></span>

<span data-ttu-id="a4eb6-190">Pour sélectionner une configuration de session particulière pour une session, utilisez le paramètre ConfigurationName de New-PSSession, Enter-PSSession ou Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-190">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="a4eb6-191">Par exemple, cette commande utilise l’applet de commande New-PSSession pour démarrer une session PSSession sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-191">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="a4eb6-192">La commande utilise le paramètre ConfigurationName pour sélectionner la configuration WithProfile sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-192">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="a4eb6-193">Cette commande ne fonctionnera que si l’utilisateur actuel est autorisé à utiliser la configuration de session WithProfile ou peut fournir les informations d’identification d’un utilisateur disposant des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-193">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="a4eb6-194">Vous pouvez également utiliser la variable de préférence $PSSessionConfigurationName pour modifier la configuration de session par défaut sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-194">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="a4eb6-195">Pour plus d’informations sur la variable de préférence $PSSessionConfigurationName, consultez about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="a4eb6-195">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="a4eb6-196">MOT</span><span class="sxs-lookup"><span data-stu-id="a4eb6-196">KEYWORDS</span></span>

<span data-ttu-id="a4eb6-197">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="a4eb6-197">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="a4eb6-198">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="a4eb6-198">SEE ALSO</span></span>

[<span data-ttu-id="a4eb6-199">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="a4eb6-199">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="a4eb6-200">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a4eb6-200">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="a4eb6-201">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a4eb6-201">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="a4eb6-202">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="a4eb6-202">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="a4eb6-203">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a4eb6-203">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="a4eb6-204">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4eb6-204">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="a4eb6-205">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4eb6-205">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="a4eb6-206">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4eb6-206">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="a4eb6-207">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a4eb6-207">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="a4eb6-208">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4eb6-208">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="a4eb6-209">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4eb6-209">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="a4eb6-210">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a4eb6-210">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="a4eb6-211">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4eb6-211">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)
