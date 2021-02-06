---
description: Décrit les configurations de session qui déterminent les utilisateurs pouvant se connecter à distance à l'ordinateur et les commandes qu'ils peuvent exécuter.
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 4c6d5494f49bc271a7fe128fbce7b27c9d1f675f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598372"
---
# <a name="about-session-configurations"></a><span data-ttu-id="60a9b-103">À propos des configurations de session</span><span class="sxs-lookup"><span data-stu-id="60a9b-103">About Session Configurations</span></span>

## <a name="short-description"></a><span data-ttu-id="60a9b-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="60a9b-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="60a9b-105">Décrit les configurations de session qui déterminent les utilisateurs pouvant se connecter à distance à l'ordinateur et les commandes qu'ils peuvent exécuter.</span><span class="sxs-lookup"><span data-stu-id="60a9b-105">Describes session configurations, which determine the users who can connect to the computer remotely and the commands they can run.</span></span>

## <a name="long-description"></a><span data-ttu-id="60a9b-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="60a9b-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="60a9b-107">Une configuration de session, également appelée « point de terminaison », est un groupe de paramètres sur l’ordinateur local qui définissent l’environnement des sessions PowerShell qui sont créées lorsque des utilisateurs distants ou locaux se connectent à PowerShell sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60a9b-107">A session configuration, also known as an "endpoint" is a group of settings on the local computer that define the environment for the PowerShell sessions that are created when remote or local users connect to PowerShell on the local computer.</span></span>

<span data-ttu-id="60a9b-108">Les administrateurs de l’ordinateur peuvent utiliser des configurations de session pour protéger l’ordinateur et définir des environnements personnalisés pour les utilisateurs qui se connectent à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-108">Administrators of the computer can use session configurations to protect the computer and to define custom environments for users who connect to the computer.</span></span>

<span data-ttu-id="60a9b-109">Les administrateurs peuvent également utiliser des configurations de session pour déterminer les autorisations requises pour se connecter à l’ordinateur à distance.</span><span class="sxs-lookup"><span data-stu-id="60a9b-109">Administrators can also use session configurations to determine the permissions that are required to connect to the computer remotely.</span></span> <span data-ttu-id="60a9b-110">Par défaut, seuls les membres du groupe administrateurs sont autorisés à utiliser la configuration de session pour se connecter à distance, mais vous pouvez modifier les paramètres par défaut pour permettre à tous les utilisateurs, ou aux utilisateurs sélectionnés, de se connecter à distance à votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-110">By default, only members of the Administrators group have permission to use the session configuration to connect remotely, but you can change the default settings to allow all users, or selected users, to connect remotely to your computer.</span></span>

<span data-ttu-id="60a9b-111">À compter de PowerShell 3,0, vous pouvez utiliser un fichier de configuration de session pour définir les éléments d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-111">Beginning in PowerShell 3.0, you can use a session configuration file to define the elements of a session configuration.</span></span> <span data-ttu-id="60a9b-112">Cette fonctionnalité permet de personnaliser facilement les sessions sans écrire de code et de découvrir les propriétés d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-112">This feature makes it easy to customize sessions without writing code and to discover the properties of a session configuration.</span></span> <span data-ttu-id="60a9b-113">Pour créer un fichier de configuration de session, utilisez l’applet de commande New-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-113">To create a session configuration file, use the New-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="60a9b-114">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="60a9b-114">For more information about session configuration files, see [about_Session_Configuration_Files](about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="60a9b-115">Les configurations de session sont une fonctionnalité de la communication à distance PowerShell basée sur les services Web for Management (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="60a9b-115">Session configurations are a feature of Web Services for Management (WS-Management) based PowerShell remoting.</span></span> <span data-ttu-id="60a9b-116">Ils sont utilisés uniquement lorsque vous utilisez les applets de commande New-PSSession, Invoke-Command ou Enter-PSSession pour vous connecter à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="60a9b-116">They are used only when you use the New-PSSession, Invoke-Command, or Enter-PSSession cmdlets to connect to a remote computer.</span></span>

<span data-ttu-id="60a9b-117">Remarque : pour gérer les configurations de session, démarrez PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="60a9b-117">Note: To manage the session configurations, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="60a9b-118">À propos des configurations de session</span><span class="sxs-lookup"><span data-stu-id="60a9b-118">About Session Configurations</span></span>

<span data-ttu-id="60a9b-119">Chaque session PowerShell utilise une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-119">Every PowerShell session uses a session configuration.</span></span> <span data-ttu-id="60a9b-120">Cela comprend les sessions persistantes que vous créez à l’aide des applets de commande New-PSSession ou Enter-PSSession, et les sessions temporaires que PowerShell crée lorsque vous utilisez le paramètre ComputerName d’une applet de commande qui utilise la technologie de communication à distance basée sur WS-Management, comme Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="60a9b-120">This includes persistent sessions that you create by using the New-PSSession or Enter-PSSession cmdlets, and the temporary sessions that PowerShell creates when you use the ComputerName parameter of a cmdlet that uses WS-Management-based remoting technology, such as Invoke-Command.</span></span>

<span data-ttu-id="60a9b-121">Les administrateurs peuvent utiliser des configurations de session pour protéger les ressources de l’ordinateur et créer des environnements personnalisés pour les utilisateurs qui se connectent à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-121">Administrators can use session configurations to protect the resources of the computer and to create custom environments for users who connect to the computer.</span></span> <span data-ttu-id="60a9b-122">Par exemple, vous pouvez utiliser une configuration de session pour limiter la taille des objets que l’ordinateur reçoit dans la session, pour définir le mode de langue de la session et pour spécifier les applets de commande, fournisseurs et fonctions disponibles dans la session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-122">For example, you can use a session configuration to limit the size of objects that the computer receives in the session, to define the language mode of the session, and to specify the cmdlets, providers, and functions that are available in the session.</span></span>

<span data-ttu-id="60a9b-123">En configurant le descripteur de sécurité d’une configuration de session, vous déterminez qui peut utiliser la configuration de session pour se connecter à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-123">By configuring the security descriptor of a session configuration, you determine who can use the session configuration to connect to the computer.</span></span>
<span data-ttu-id="60a9b-124">Les utilisateurs doivent disposer de l’autorisation EXECUTE sur une configuration de session pour pouvoir l’utiliser dans une session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-124">Users must have Execute permission to a session configuration to use it in a session.</span></span> <span data-ttu-id="60a9b-125">Si un utilisateur ne dispose pas des autorisations nécessaires pour utiliser l’une des configurations de session sur un ordinateur, il ne peut pas se connecter à distance à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-125">If a user does not have the required permissions to use any of the session configurations on a computer, the user cannot connect to the computer remotely.</span></span>

<span data-ttu-id="60a9b-126">Par défaut, seuls les administrateurs de l’ordinateur sont autorisés à utiliser les configurations de session par défaut.</span><span class="sxs-lookup"><span data-stu-id="60a9b-126">By default, only Administrators of the computer have permission to use the default session configurations.</span></span> <span data-ttu-id="60a9b-127">Toutefois, vous pouvez modifier les descripteurs de sécurité pour autoriser tout le monde, personne ou uniquement les utilisateurs sélectionnés à utiliser les configurations de session sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-127">But, you can change the security descriptors to allow everyone, no one, or only selected users to use the session configurations on your computer.</span></span>

<span data-ttu-id="60a9b-128">Configurations de session intégrées</span><span class="sxs-lookup"><span data-stu-id="60a9b-128">Built-in Session Configurations</span></span>

<span data-ttu-id="60a9b-129">PowerShell 3,0 comprend des configurations de session intégrées nommées Microsoft. PowerShell et Microsoft. PowerShell. Workflow.</span><span class="sxs-lookup"><span data-stu-id="60a9b-129">PowerShell 3.0 includes built-in session configurations named Microsoft.PowerShell and Microsoft.PowerShell.Workflow.</span></span> <span data-ttu-id="60a9b-130">Sur les ordinateurs exécutant des versions 64 bits de Windows, PowerShell fournit également Microsoft. PowerShell32, une configuration de session 32 bits.</span><span class="sxs-lookup"><span data-stu-id="60a9b-130">On computers running 64-bit versions of Windows, PowerShell also provides Microsoft.PowerShell32, a 32-bit session configuration.</span></span>

<span data-ttu-id="60a9b-131">La configuration de session Microsoft. PowerShell est utilisée pour les sessions par défaut, autrement dit, quand une commande permettant de créer une session n’inclut pas le paramètre ConfigurationName de l’applet de commande New-PSSession, Enter-PSSession ou Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="60a9b-131">The Microsoft.PowerShell session configuration is used for sessions by default, that is, when a command to create a session does not include the ConfigurationName parameter of the New-PSSession, Enter-PSSession, or Invoke-Command cmdlet.</span></span>

<span data-ttu-id="60a9b-132">Les descripteurs de sécurité pour les configurations de session par défaut autorisent uniquement les membres du groupe Administrateurs sur l’ordinateur local à les utiliser.</span><span class="sxs-lookup"><span data-stu-id="60a9b-132">The security descriptors for the default session configurations allow only members of the Administrators group on the local computer to use them.</span></span> <span data-ttu-id="60a9b-133">Ainsi, seuls les membres du groupe administrateurs peuvent se connecter à l’ordinateur à distance, sauf si vous modifiez les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="60a9b-133">As such, only members of the Administrators group can connect to the computer remotely unless you change the default settings.</span></span>

<span data-ttu-id="60a9b-134">Vous pouvez modifier les configurations de session par défaut à l’aide de la variable de préférence $PSSessionConfigurationName.</span><span class="sxs-lookup"><span data-stu-id="60a9b-134">You can change the default session configurations by using the $PSSessionConfigurationName preference variable.</span></span> <span data-ttu-id="60a9b-135">Pour plus d'informations, consultez about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="60a9b-135">For more information, see about_Preference_Variables.</span></span>

<span data-ttu-id="60a9b-136">Affichage des configurations de session sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="60a9b-136">Viewing Session Configurations on the Local Computer</span></span>

<span data-ttu-id="60a9b-137">Pour récupérer les configurations de session sur votre ordinateur local, utilisez l’applet de commande Get-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-137">To get the session configurations on your local computer, use the Get-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="60a9b-138">Par exemple, entrez :</span><span class="sxs-lookup"><span data-stu-id="60a9b-138">For example, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="60a9b-139">L’objet de configuration de session est développé dans PowerShell 3,0 pour afficher les propriétés de la configuration de session configurées à l’aide d’un fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-139">The session configuration object is expanded in PowerShell 3.0 to display the properties of the session configuration that are configured by using a session configuration file.</span></span>

<span data-ttu-id="60a9b-140">Par exemple, pour afficher toutes les propriétés d’un objet de configuration de session, tapez :</span><span class="sxs-lookup"><span data-stu-id="60a9b-140">For example, to see all of the properties of a session configuration object, type:</span></span>

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

<span data-ttu-id="60a9b-141">Vous pouvez également utiliser le fournisseur WSMan dans PowerShell pour afficher les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-141">You can also use the WSMan provider in PowerShell to view session configurations.</span></span> <span data-ttu-id="60a9b-142">Le fournisseur WSMan crée un lecteur WSMAN : dans votre session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-142">The WSMan provider creates a WSMAN: drive in your session.</span></span>

<span data-ttu-id="60a9b-143">Dans le lecteur WSMAN :, les configurations de session se trouvent dans le nœud de plug-in.</span><span class="sxs-lookup"><span data-stu-id="60a9b-143">In the WSMAN: drive, session configurations are in the Plugin node.</span></span> <span data-ttu-id="60a9b-144">(Toutes les configurations de session se trouvent dans le nœud de plug-in, mais il existe des éléments dans le nœud de plug-in qui ne sont pas des configurations de session.)</span><span class="sxs-lookup"><span data-stu-id="60a9b-144">(All session configurations are in the Plugin node, but there are items in the Plugin node that are not session configurations.)</span></span>

<span data-ttu-id="60a9b-145">Par exemple, pour afficher les configurations de session sur l’ordinateur local, tapez :</span><span class="sxs-lookup"><span data-stu-id="60a9b-145">For example, to view the session configurations on the local computer, type:</span></span>

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

<span data-ttu-id="60a9b-146">Affichage des configurations de session sur un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="60a9b-146">Viewing Session Configurations on a Remote Computer</span></span>

<span data-ttu-id="60a9b-147">Pour afficher les configurations de session sur un ordinateur distant, utilisez l’applet de commande Connect-WSMan pour ajouter une note pour l’ordinateur distant au lecteur WSMAN : sur votre ordinateur local, puis utilisez le lecteur WSMAN : pour afficher les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-147">To view the session configurations on a remote computer, use the Connect-WSMan cmdlet to add a note for the remote computer to the WSMAN: drive on your local computer, and then use the WSMAN: drive to view the session configurations.</span></span>

<span data-ttu-id="60a9b-148">Par exemple, la commande suivante ajoute un nœud pour l’ordinateur distant SERVEUR01 au lecteur WSMAN : sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="60a9b-148">For example, the following command adds a node for the Server01 remote computer to the WSMAN: drive on the local computer.</span></span>

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

<span data-ttu-id="60a9b-149">Une fois la commande terminée, vous pouvez accéder au nœud de l’ordinateur SERVEUR01 pour afficher les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="60a9b-149">When the command is complete, you can navigate to the node for the Server01 computer to view the session configurations.</span></span>

<span data-ttu-id="60a9b-150">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60a9b-150">For example:</span></span>

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

<span data-ttu-id="60a9b-151">Modification du descripteur de sécurité d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="60a9b-151">Changing the Security Descriptor of a Session Configuration</span></span>

<span data-ttu-id="60a9b-152">Dans Windows Server 2012 et les versions plus récentes de Windows Server, les configurations de session intégrées sont activées par défaut pour les utilisateurs distants.</span><span class="sxs-lookup"><span data-stu-id="60a9b-152">In Windows Server 2012 and newer releases of Windows Server, the built-in session configurations are enabled for remote users by default.</span></span> <span data-ttu-id="60a9b-153">Dans les autres versions prises en charge de Windows, vous devez modifier les descripteurs de sécurité des configurations de session pour autoriser l’accès à distance.</span><span class="sxs-lookup"><span data-stu-id="60a9b-153">In other supported versions of Windows, you must change the security descriptors of the session configurations to allow remote access.</span></span>

<span data-ttu-id="60a9b-154">Pour activer l’accès à distance aux configurations de session sur l’ordinateur, utilisez l’applet de commande Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="60a9b-154">To enable remote access to the session configurations on the computer, use the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="60a9b-155">Cette applet de commande crée deux configurations de session :</span><span class="sxs-lookup"><span data-stu-id="60a9b-155">This cmdlet creates two session configurations:</span></span>

- <span data-ttu-id="60a9b-156">avec le nom défini en tant que : « PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="60a9b-156">with the name defined as: "PowerShell."</span></span> <span data-ttu-id="60a9b-157">+ « version actuelle de PowerShell »</span><span class="sxs-lookup"><span data-stu-id="60a9b-157">+ "current PowerShell version"</span></span>
- <span data-ttu-id="60a9b-158">avec le nom « PowerShell. 6 », qui n’est pas lié à une version spécifique de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60a9b-158">with name "PowerShell.6", untied to any specific PowerShell version.</span></span>

<span data-ttu-id="60a9b-159">De même, par défaut, seuls les membres du groupe Administrateurs sur l’ordinateur ont l’autorisation EXECUTE sur les configurations de session par défaut, mais vous pouvez modifier les descripteurs de sécurité sur les configurations de session par défaut et sur toutes les configurations de session que vous créez.</span><span class="sxs-lookup"><span data-stu-id="60a9b-159">Also, by default, only members of the Administrators group on the computer have Execute permission to the default session configurations, but you can change the security descriptors on the default session configurations and on any session configurations that you create.</span></span>

<span data-ttu-id="60a9b-160">Pour accorder à d’autres utilisateurs l’autorisation de se connecter à distance à l’ordinateur, utilisez l’applet de commande Set-PSSessionConfiguration pour ajouter des autorisations « exécuter » pour ces utilisateurs aux descripteurs de sécurité des configurations de session Microsoft. PowerShell et Microsoft. PowerShell32.</span><span class="sxs-lookup"><span data-stu-id="60a9b-160">To give other users permission to connect to the computer remotely, use the Set-PSSessionConfiguration cmdlet to add "Execute" permissions for those users to the security descriptors of the Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span>

<span data-ttu-id="60a9b-161">Par exemple, la commande suivante ouvre une page de propriétés qui vous permet de modifier le descripteur de sécurité pour la configuration de session Microsoft. PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="60a9b-161">For example, the following command opens a property page that lets you change the security descriptor for the Microsoft.PowerShell default session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="60a9b-162">Pour refuser l’autorisation tout le monde à toutes les configurations de session sur l’ordinateur, utilisez l’applet de commande Disable-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-162">To deny everyone permission to all the session configurations on the computer, use the Disable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="60a9b-163">Par exemple, la commande suivante désactive les configurations de session par défaut sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-163">For example, the following command disables the default session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

<span data-ttu-id="60a9b-164">Pour empêcher les utilisateurs distants de se connecter à l’ordinateur, mais autoriser les utilisateurs locaux à se connecter, utilisez l’applet de commande Disable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="60a9b-164">To prevent remote users from connecting to the computer, but allow local users to connect, use the Disable-PSRemoting cmdlet.</span></span> <span data-ttu-id="60a9b-165">Disable-PSRemoting ajoute une entrée « Network_Deny_All » à toutes les configurations de session sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-165">Disable-PSRemoting adds a "Network_Deny_All" entry to all session configurations on the computer.</span></span>

```powershell
PS C:> Disable-PSRemoting
```

<span data-ttu-id="60a9b-166">Pour permettre aux utilisateurs distants d’utiliser toutes les configurations de session sur l’ordinateur, utilisez l’applet de commande Enable-PSRemoting ou Enable-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-166">To allow remote users to use all session configurations on the computer, use the Enable-PSRemoting or Enable-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="60a9b-167">Par exemple, la commande suivante active l’accès à distance aux configurations de session intégrées.</span><span class="sxs-lookup"><span data-stu-id="60a9b-167">For example, the following command enables remote access to the built-in session configurations.</span></span>

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

<span data-ttu-id="60a9b-168">Pour apporter d’autres modifications au descripteur de sécurité d’une configuration de session, utilisez l’applet de commande Set-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-168">To make other changes to the security descriptor of a session configuration, use the Set-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="60a9b-169">Utilisez le paramètre SecurityDescriptorSDDL pour envoyer une valeur de chaîne SDDL.</span><span class="sxs-lookup"><span data-stu-id="60a9b-169">Use the SecurityDescriptorSDDL parameter to submit an SDDL string value.</span></span> <span data-ttu-id="60a9b-170">Utilisez le paramètre ShowSecurityDescriptorUI pour afficher une feuille de propriétés de l’interface utilisateur qui vous aide à créer un nouveau SDDL.</span><span class="sxs-lookup"><span data-stu-id="60a9b-170">Use the ShowSecurityDescriptorUI parameter to display a user interface property sheet that helps you to create a new SDDL.</span></span>

<span data-ttu-id="60a9b-171">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60a9b-171">For example:</span></span>

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

<span data-ttu-id="60a9b-172">Création d’une nouvelle configuration de session</span><span class="sxs-lookup"><span data-stu-id="60a9b-172">Creating a New Session Configuration</span></span>

<span data-ttu-id="60a9b-173">Pour créer une nouvelle configuration de session sur l’ordinateur local, utilisez l’applet de commande Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-173">To create a new session configuration on the local computer, use the Register-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="60a9b-174">Pour définir la nouvelle configuration de session, vous pouvez utiliser un assembly C#, un script PowerShell et les paramètres de l’applet de commande Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-174">To define the new session configuration, you can use a C# assembly, a PowerShell script, and the parameters of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="60a9b-175">Par exemple, la commande suivante crée une configuration de session qui est identique à la configuration de session Microsoft. PowerShell, à ceci près qu’elle limite les données reçues d’une commande à distance à 20 mégaoctets (Mo).</span><span class="sxs-lookup"><span data-stu-id="60a9b-175">For example, the following command creates a session configuration that is identical the Microsoft.PowerShell session configuration, except that it limits the data received from a remote command to 20 megabytes (MB).</span></span> <span data-ttu-id="60a9b-176">(La valeur par défaut est 50 Mo).</span><span class="sxs-lookup"><span data-stu-id="60a9b-176">(The default is 50 MB).</span></span>

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

<span data-ttu-id="60a9b-177">Lorsque vous créez une configuration de session, vous pouvez la gérer à l’aide des autres applets de commande de configuration de session, et elle apparaît dans le lecteur WSMAN :.</span><span class="sxs-lookup"><span data-stu-id="60a9b-177">When you create a session configuration, you can manage it by using the other session configuration cmdlets, and it appears in the WSMAN: drive.</span></span>

<span data-ttu-id="60a9b-178">Pour plus d’informations, consultez Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-178">For more information, see Register-PSSessionConfiguration.</span></span>

<span data-ttu-id="60a9b-179">Suppression d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="60a9b-179">Removing a Session Configuration</span></span>

<span data-ttu-id="60a9b-180">Pour supprimer une configuration de session de l’ordinateur local, utilisez l’applet de commande Unregister-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-180">To remove a session configuration from the local computer, use the Unregister-PSSessionConfiguration cmdlet.</span></span> <span data-ttu-id="60a9b-181">Par exemple, la commande suivante supprime la configuration de session NewConfig de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-181">For example, the following command removes the NewConfig session configuration from the computer.</span></span>

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

<span data-ttu-id="60a9b-182">Pour plus d’informations, consultez Unregister-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="60a9b-182">For more information, see Unregister-PSSessionConfiguration.</span></span>

<span data-ttu-id="60a9b-183">Restauration d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="60a9b-183">Restoring a Session Configuration</span></span>

<span data-ttu-id="60a9b-184">Pour restaurer une configuration de session par défaut qui a été supprimée (désinscrite) accidentellement, utilisez l’applet de commande Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="60a9b-184">To restore a default session configuration that was deleted (unregistered) accidentally, use the Enable-PSRemoting cmdlet.</span></span>

<span data-ttu-id="60a9b-185">L’applet de commande Enable-PSRemoting recrée toutes les configurations de sessions par défaut qui n’existent pas sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-185">The Enable-PSRemoting cmdlet recreates all default sessions configurations that do not exist on the computer.</span></span> <span data-ttu-id="60a9b-186">Elle ne remplace pas ou ne modifie pas les valeurs des propriétés des configurations de session existantes.</span><span class="sxs-lookup"><span data-stu-id="60a9b-186">It does not overwrite or change the property values of existing session configurations.</span></span>

<span data-ttu-id="60a9b-187">Pour restaurer les valeurs de propriété d’origine d’une configuration de session par défaut, utilisez la Unregister-PSSessionConfiguration pour supprimer la configuration de session, puis utilisez l’applet de commande Enable-PSRemoting pour la recréer.</span><span class="sxs-lookup"><span data-stu-id="60a9b-187">To restore the original property values of a default session configuration, use the Unregister-PSSessionConfiguration to delete the session configuration and then use the Enable-PSRemoting cmdlet to recreate it.</span></span>

<span data-ttu-id="60a9b-188">Sélection d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="60a9b-188">Selecting a Session Configuration</span></span>

<span data-ttu-id="60a9b-189">Pour sélectionner une configuration de session particulière pour une session, utilisez le paramètre ConfigurationName de New-PSSession, Enter-PSSession ou Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="60a9b-189">To select a particular session configuration for a session, use the ConfigurationName parameter of New-PSSession, Enter-PSSession, or Invoke-Command.</span></span>

<span data-ttu-id="60a9b-190">Par exemple, cette commande utilise l’applet de commande New-PSSession pour démarrer une session PSSession sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="60a9b-190">For example, this command uses the New-PSSession cmdlet to start a PSSession on the Server01 computer.</span></span> <span data-ttu-id="60a9b-191">La commande utilise le paramètre ConfigurationName pour sélectionner la configuration WithProfile sur l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="60a9b-191">The command uses the ConfigurationName parameter to select the WithProfile configuration on the Server01 computer.</span></span>

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

<span data-ttu-id="60a9b-192">Cette commande ne fonctionnera que si l’utilisateur actuel est autorisé à utiliser la configuration de session WithProfile ou peut fournir les informations d’identification d’un utilisateur disposant des autorisations requises.</span><span class="sxs-lookup"><span data-stu-id="60a9b-192">This command will succeed only if the current user has permission to use the WithProfile session configuration or can supply the credentials of a user who has the required permissions.</span></span>

<span data-ttu-id="60a9b-193">Vous pouvez également utiliser la variable de préférence $PSSessionConfigurationName pour modifier la configuration de session par défaut sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60a9b-193">You can also use the $PSSessionConfigurationName preference variable to change the default session configuration on the computer.</span></span> <span data-ttu-id="60a9b-194">Pour plus d’informations sur la variable de préférence $PSSessionConfigurationName, consultez about_Preference_Variables.</span><span class="sxs-lookup"><span data-stu-id="60a9b-194">For more information about the $PSSessionConfigurationName preference variable, see about_Preference_Variables.</span></span>

## <a name="keywords"></a><span data-ttu-id="60a9b-195">MOT</span><span class="sxs-lookup"><span data-stu-id="60a9b-195">KEYWORDS</span></span>

<span data-ttu-id="60a9b-196">about_Endpoints about_SessionConfigurations</span><span class="sxs-lookup"><span data-stu-id="60a9b-196">about_Endpoints about_SessionConfigurations</span></span>

## <a name="see-also"></a><span data-ttu-id="60a9b-197">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="60a9b-197">SEE ALSO</span></span>

[<span data-ttu-id="60a9b-198">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="60a9b-198">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="60a9b-199">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="60a9b-199">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="60a9b-200">about_Remote</span><span class="sxs-lookup"><span data-stu-id="60a9b-200">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="60a9b-201">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="60a9b-201">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)

[<span data-ttu-id="60a9b-202">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="60a9b-202">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="60a9b-203">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="60a9b-203">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="60a9b-204">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="60a9b-204">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="60a9b-205">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="60a9b-205">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="60a9b-206">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="60a9b-206">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="60a9b-207">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="60a9b-207">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="60a9b-208">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="60a9b-208">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="60a9b-209">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="60a9b-209">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="60a9b-210">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="60a9b-210">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

