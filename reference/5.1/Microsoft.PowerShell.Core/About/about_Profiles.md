---
description: Décrit comment créer et utiliser un profil PowerShell.
keywords: powershell,applet de commande
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 17b89df0ec0ce88127385287cee560996af7a628
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207606"
---
# <a name="about-profiles"></a><span data-ttu-id="01a2d-104">À propos des profils</span><span class="sxs-lookup"><span data-stu-id="01a2d-104">About Profiles</span></span>

## <a name="short-description"></a><span data-ttu-id="01a2d-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="01a2d-105">Short Description</span></span>
<span data-ttu-id="01a2d-106">Décrit comment créer et utiliser un profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-106">Describes how to create and use a PowerShell profile.</span></span>

## <a name="long-description"></a><span data-ttu-id="01a2d-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="01a2d-107">Long Description</span></span>

<span data-ttu-id="01a2d-108">Vous pouvez créer un profil PowerShell pour personnaliser votre environnement et ajouter des éléments spécifiques à la session à chaque session PowerShell que vous démarrez.</span><span class="sxs-lookup"><span data-stu-id="01a2d-108">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span>

<span data-ttu-id="01a2d-109">Un profil PowerShell est un script qui s’exécute au démarrage de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-109">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="01a2d-110">Vous pouvez utiliser le profil comme script d’ouverture de session pour personnaliser l’environnement.</span><span class="sxs-lookup"><span data-stu-id="01a2d-110">You can use the profile as a logon script to customize the environment.</span></span> <span data-ttu-id="01a2d-111">Vous pouvez ajouter des commandes, des alias, des fonctions, des variables, des composants logiciels enfichables, des modules et des lecteurs PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-111">You can add commands, aliases, functions, variables, snap-ins, modules, and PowerShell drives.</span></span> <span data-ttu-id="01a2d-112">Vous pouvez également ajouter d’autres éléments spécifiques à la session à votre profil afin qu’ils soient disponibles dans chaque session sans avoir à les importer ou à les recréer.</span><span class="sxs-lookup"><span data-stu-id="01a2d-112">You can also add other session-specific elements to your profile so they are available in every session without having to import or re-create them.</span></span>

<span data-ttu-id="01a2d-113">PowerShell prend en charge plusieurs profils pour les utilisateurs et les programmes hôtes.</span><span class="sxs-lookup"><span data-stu-id="01a2d-113">PowerShell supports several profiles for users and host programs.</span></span> <span data-ttu-id="01a2d-114">Toutefois, il ne crée pas les profils pour vous.</span><span class="sxs-lookup"><span data-stu-id="01a2d-114">However, it does not create the profiles for you.</span></span> <span data-ttu-id="01a2d-115">Cette rubrique décrit les profils et décrit comment créer et gérer des profils sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="01a2d-115">This topic describes the profiles, and it describes how to create and maintain profiles on your computer.</span></span>

<span data-ttu-id="01a2d-116">Il explique comment utiliser le paramètre **noprofile** de la console powershell (PowerShell.exe) pour démarrer PowerShell sans aucun profil.</span><span class="sxs-lookup"><span data-stu-id="01a2d-116">It explains how to use the **NoProfile** parameter of the PowerShell console (PowerShell.exe) to start PowerShell without any profiles.</span></span> <span data-ttu-id="01a2d-117">Et explique l’effet de la stratégie d’exécution de PowerShell sur les profils.</span><span class="sxs-lookup"><span data-stu-id="01a2d-117">And, it explains the effect of the PowerShell execution policy on profiles.</span></span>

## <a name="the-profile-files"></a><span data-ttu-id="01a2d-118">Fichiers de profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-118">The Profile Files</span></span>

<span data-ttu-id="01a2d-119">PowerShell prend en charge plusieurs fichiers de profil.</span><span class="sxs-lookup"><span data-stu-id="01a2d-119">PowerShell supports several profile files.</span></span> <span data-ttu-id="01a2d-120">En outre, les programmes hôtes PowerShell peuvent prendre en charge leurs propres profils propres à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="01a2d-120">Also, PowerShell host programs can support their own host-specific profiles.</span></span>

<span data-ttu-id="01a2d-121">Par exemple, la console PowerShell prend en charge les fichiers de profil de base suivants.</span><span class="sxs-lookup"><span data-stu-id="01a2d-121">For example, the PowerShell console supports the following basic profile files.</span></span> <span data-ttu-id="01a2d-122">Les profils sont répertoriés par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="01a2d-122">The profiles are listed in precedence order.</span></span> <span data-ttu-id="01a2d-123">Le premier profil a la priorité la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="01a2d-123">The first profile has the highest precedence.</span></span>

|<span data-ttu-id="01a2d-124">Description</span><span class="sxs-lookup"><span data-stu-id="01a2d-124">Description</span></span>               | <span data-ttu-id="01a2d-125">Path</span><span class="sxs-lookup"><span data-stu-id="01a2d-125">Path</span></span>                                          |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="01a2d-126">Tous les utilisateurs, tous les ordinateurs hôtes</span><span class="sxs-lookup"><span data-stu-id="01a2d-126">All Users, All Hosts</span></span>      |<span data-ttu-id="01a2d-127">$PSHOME \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="01a2d-127">$PSHOME\\Profile.ps1</span></span>                           |
|<span data-ttu-id="01a2d-128">Tous les utilisateurs, hôte actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-128">All Users, Current Host</span></span>   |<span data-ttu-id="01a2d-129">$PSHOME \\Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="01a2d-129">$PSHOME\\Microsoft.PowerShell_profile.ps1</span></span>      |
|<span data-ttu-id="01a2d-130">Utilisateur actuel, tous les ordinateurs hôtes</span><span class="sxs-lookup"><span data-stu-id="01a2d-130">Current User, All Hosts</span></span>   |<span data-ttu-id="01a2d-131">$Home \\ [My] documents \\ WindowsPowerShell \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="01a2d-131">$Home\\[My ]Documents\\WindowsPowerShell\\Profile.ps1</span></span> |
|<span data-ttu-id="01a2d-132">Utilisateur actuel, hôte actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-132">Current user, Current Host</span></span>|<span data-ttu-id="01a2d-133">$Home \\ [My] documents \\ WindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="01a2d-133">$Home\\[My ]Documents\\WindowsPowerShell</span></span>\\<br><span data-ttu-id="01a2d-134">Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="01a2d-134">Microsoft.PowerShell_profile.ps1</span></span> |

<span data-ttu-id="01a2d-135">Les chemins d’accès aux profils incluent les variables suivantes :</span><span class="sxs-lookup"><span data-stu-id="01a2d-135">The profile paths include the following variables:</span></span>

- <span data-ttu-id="01a2d-136">La `$PSHOME` variable, qui stocke le répertoire d’installation de PowerShell</span><span class="sxs-lookup"><span data-stu-id="01a2d-136">The `$PSHOME` variable, which stores the installation directory for PowerShell</span></span>
- <span data-ttu-id="01a2d-137">La `$Home` variable, qui stocke le répertoire de démarrage de l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-137">The `$Home` variable, which stores the current user's home directory</span></span>

<span data-ttu-id="01a2d-138">En outre, d’autres programmes qui hébergent PowerShell peuvent prendre en charge leurs propres profils.</span><span class="sxs-lookup"><span data-stu-id="01a2d-138">In addition, other programs that host PowerShell can support their own profiles.</span></span> <span data-ttu-id="01a2d-139">Par exemple, l’environnement d’écriture de scripts intégré (ISE) de PowerShell prend en charge les profils spécifiques à l’hôte suivants.</span><span class="sxs-lookup"><span data-stu-id="01a2d-139">For example, PowerShell Integrated Scripting Environment (ISE) supports the following host-specific profiles.</span></span>

|<span data-ttu-id="01a2d-140">Description</span><span class="sxs-lookup"><span data-stu-id="01a2d-140">Description</span></span>               | <span data-ttu-id="01a2d-141">Path</span><span class="sxs-lookup"><span data-stu-id="01a2d-141">Path</span></span>                                       |
|--------------------------|--------------------------------------------|
|<span data-ttu-id="01a2d-142">Tous les utilisateurs, hôte actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-142">All users, Current Host</span></span>   |<span data-ttu-id="01a2d-143">$PSHOME \\Microsoft.PowerShellISE_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="01a2d-143">$PSHOME\\Microsoft.PowerShellISE_profile.ps1</span></span>|
|<span data-ttu-id="01a2d-144">Utilisateur actuel, hôte actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-144">Current user, Current Host</span></span>|<span data-ttu-id="01a2d-145">$Home \\ [My] documents \\ WindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="01a2d-145">$Home\\[My ]Documents\\WindowsPowerShell</span></span>\\<br><span data-ttu-id="01a2d-146">Microsoft.PowerShellISE_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="01a2d-146">Microsoft.PowerShellISE_profile.ps1</span></span> |

<span data-ttu-id="01a2d-147">Dans l’aide PowerShell, le profil « CurrentUser, hôte actuel » est le profil le plus souvent appelé « votre profil PowerShell ».</span><span class="sxs-lookup"><span data-stu-id="01a2d-147">In PowerShell Help, the "CurrentUser, Current Host" profile is the profile most often referred to as "your PowerShell profile".</span></span>

## <a name="the-profile-variable"></a><span data-ttu-id="01a2d-148">La variable $PROFILE</span><span class="sxs-lookup"><span data-stu-id="01a2d-148">The $PROFILE variable</span></span>

<span data-ttu-id="01a2d-149">La `$PROFILE` variable automatique stocke les chemins d’accès aux profils PowerShell qui sont disponibles dans la session active.</span><span class="sxs-lookup"><span data-stu-id="01a2d-149">The `$PROFILE` automatic variable stores the paths to the PowerShell profiles that are available in the current session.</span></span>

<span data-ttu-id="01a2d-150">Pour afficher un chemin de profil, affichez la valeur de la `$PROFILE` variable.</span><span class="sxs-lookup"><span data-stu-id="01a2d-150">To view a profile path, display the value of the `$PROFILE` variable.</span></span> <span data-ttu-id="01a2d-151">Vous pouvez également utiliser la `$PROFILE` variable dans une commande pour représenter un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="01a2d-151">You can also use the `$PROFILE` variable in a command to represent a path.</span></span>

<span data-ttu-id="01a2d-152">La `$PROFILE` variable stocke le chemin d’accès au profil « utilisateur actuel, hôte actuel ».</span><span class="sxs-lookup"><span data-stu-id="01a2d-152">The `$PROFILE` variable stores the path to the "Current User, Current Host" profile.</span></span> <span data-ttu-id="01a2d-153">Les autres profils sont enregistrés dans les propriétés de note de la `$PROFILE` variable.</span><span class="sxs-lookup"><span data-stu-id="01a2d-153">The other profiles are saved in note properties of the `$PROFILE` variable.</span></span>

<span data-ttu-id="01a2d-154">Par exemple, la `$PROFILE` variable a les valeurs suivantes dans la console Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-154">For example, the `$PROFILE` variable has the following values in the Windows PowerShell console.</span></span>

|<span data-ttu-id="01a2d-155">Description</span><span class="sxs-lookup"><span data-stu-id="01a2d-155">Description</span></span>                |<span data-ttu-id="01a2d-156">Nom</span><span class="sxs-lookup"><span data-stu-id="01a2d-156">Name</span></span>                              |
|---------------------------|----------------------------------|
|<span data-ttu-id="01a2d-157">Utilisateur actuel, hôte actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-157">Current User, Current Host</span></span> |`$PROFILE`                        |
|<span data-ttu-id="01a2d-158">Utilisateur actuel, hôte actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-158">Current User, Current Host</span></span> |`$PROFILE.CurrentUserCurrentHost` |
|<span data-ttu-id="01a2d-159">Utilisateur actuel, tous les ordinateurs hôtes</span><span class="sxs-lookup"><span data-stu-id="01a2d-159">Current User, All Hosts</span></span>    |`$PROFILE.CurrentUserAllHosts`    |
|<span data-ttu-id="01a2d-160">Tous les utilisateurs, hôte actuel</span><span class="sxs-lookup"><span data-stu-id="01a2d-160">All Users, Current Host</span></span>    |`$PROFILE.AllUsersCurrentHost`    |
|<span data-ttu-id="01a2d-161">Tous les utilisateurs, tous les ordinateurs hôtes</span><span class="sxs-lookup"><span data-stu-id="01a2d-161">All Users, All Hosts</span></span>       |`$PROFILE.AllUsersAllHosts`       |

<span data-ttu-id="01a2d-162">Étant donné que les valeurs de la `$PROFILE` variable changent pour chaque utilisateur et dans chaque application hôte, assurez-vous d’afficher les valeurs des variables de profil dans chaque application hôte PowerShell que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="01a2d-162">Because the values of the `$PROFILE` variable change for each user and in each host application, ensure that you display the values of the profile variables in each PowerShell host application that you use.</span></span>

<span data-ttu-id="01a2d-163">Pour afficher les valeurs actuelles de la `$PROFILE` variable, tapez :</span><span class="sxs-lookup"><span data-stu-id="01a2d-163">To see the current values of the `$PROFILE` variable, type:</span></span>

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

<span data-ttu-id="01a2d-164">Vous pouvez utiliser la `$PROFILE` variable dans de nombreuses commandes.</span><span class="sxs-lookup"><span data-stu-id="01a2d-164">You can use the `$PROFILE` variable in many commands.</span></span> <span data-ttu-id="01a2d-165">Par exemple, la commande suivante ouvre le profil « utilisateur actuel, hôte actuel » dans le bloc-notes :</span><span class="sxs-lookup"><span data-stu-id="01a2d-165">For example, the following command opens the "Current User, Current Host" profile in Notepad:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="01a2d-166">La commande suivante détermine si un profil « tous les utilisateurs, tous les ordinateurs hôtes » a été créé sur l’ordinateur local :</span><span class="sxs-lookup"><span data-stu-id="01a2d-166">The following command determines whether an "All Users, All Hosts" profile has been created on the local computer:</span></span>

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a><span data-ttu-id="01a2d-167">Comment créer un profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-167">How to create a profile</span></span>

<span data-ttu-id="01a2d-168">Pour créer un profil PowerShell, utilisez le format de commande suivant :</span><span class="sxs-lookup"><span data-stu-id="01a2d-168">To create a PowerShell profile, use the following command format:</span></span>

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

<span data-ttu-id="01a2d-169">Par exemple, pour créer un profil pour l’utilisateur actuel dans l’application hôte PowerShell actuelle, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="01a2d-169">For example, to create a profile for the current user in the current PowerShell host application, use the following command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

<span data-ttu-id="01a2d-170">Dans cette commande, l' `If` instruction vous empêche de remplacer un profil existant.</span><span class="sxs-lookup"><span data-stu-id="01a2d-170">In this command, the `If` statement prevents you from overwriting an existing profile.</span></span> <span data-ttu-id="01a2d-171">Remplacez la valeur de l' \<profile-path\> espace réservé par le chemin d’accès au fichier de profil que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="01a2d-171">Replace the value of the \<profile-path\> placeholder with the path to the profile file that you want to create.</span></span>

> [!NOTE]
> <span data-ttu-id="01a2d-172">Pour créer des profils « tous les utilisateurs » dans Windows Vista et les versions ultérieures de Windows, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="01a2d-172">To create "All Users" profiles in Windows Vista and later versions of Windows, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="how-to-edit-a-profile"></a><span data-ttu-id="01a2d-173">Comment modifier un profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-173">How to edit a profile</span></span>

<span data-ttu-id="01a2d-174">Vous pouvez ouvrir n’importe quel profil PowerShell dans un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="01a2d-174">You can open any PowerShell profile in a text editor, such as Notepad.</span></span>

<span data-ttu-id="01a2d-175">Pour ouvrir le profil de l’utilisateur actuel dans l’application hôte PowerShell actuelle dans le bloc-notes, tapez :</span><span class="sxs-lookup"><span data-stu-id="01a2d-175">To open the profile of the current user in the current PowerShell host application in Notepad, type:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="01a2d-176">Pour ouvrir d’autres profils, spécifiez le nom du profil.</span><span class="sxs-lookup"><span data-stu-id="01a2d-176">To open other profiles, specify the profile name.</span></span> <span data-ttu-id="01a2d-177">Par exemple, pour ouvrir le profil pour tous les utilisateurs de toutes les applications hôtes, tapez :</span><span class="sxs-lookup"><span data-stu-id="01a2d-177">For example, to open the profile for all the users of all the host applications, type:</span></span>

```powershell
notepad $PROFILE.AllUsersAllHosts
```

<span data-ttu-id="01a2d-178">Pour appliquer les modifications, enregistrez le fichier de profil, puis redémarrez PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-178">To apply the changes, save the profile file, and then restart PowerShell.</span></span>

## <a name="how-to-choose-a-profile"></a><span data-ttu-id="01a2d-179">Comment choisir un profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-179">How to choose a profile</span></span>

<span data-ttu-id="01a2d-180">Si vous utilisez plusieurs applications hôtes, placez les éléments que vous utilisez dans toutes les applications hôtes dans votre `$PROFILE.CurrentUserAllHosts` profil.</span><span class="sxs-lookup"><span data-stu-id="01a2d-180">If you use multiple host applications, put the items that you use in all the host applications into your `$PROFILE.CurrentUserAllHosts` profile.</span></span> <span data-ttu-id="01a2d-181">Placez les éléments spécifiques à une application hôte, par exemple une commande qui définit la couleur d’arrière-plan d’une application hôte, dans un profil spécifique à cette application hôte.</span><span class="sxs-lookup"><span data-stu-id="01a2d-181">Put items that are specific to a host application, such as a command that sets the background color for a host application, in a profile that is specific to that host application.</span></span>

<span data-ttu-id="01a2d-182">Si vous êtes un administrateur qui personnalise PowerShell pour de nombreux utilisateurs, suivez ces instructions :</span><span class="sxs-lookup"><span data-stu-id="01a2d-182">If you are an administrator who is customizing PowerShell for many users, follow these guidelines:</span></span>

- <span data-ttu-id="01a2d-183">Stocker les éléments communs dans le `$PROFILE.AllUsersAllHosts` profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-183">Store the common items in the `$PROFILE.AllUsersAllHosts` profile</span></span>
- <span data-ttu-id="01a2d-184">Stocker des éléments spécifiques à une application hôte dans des `$PROFILE.AllUsersCurrentHost` profils spécifiques à l’application hôte</span><span class="sxs-lookup"><span data-stu-id="01a2d-184">Store items that are specific to a host application in `$PROFILE.AllUsersCurrentHost` profiles that are specific to the host application</span></span>
- <span data-ttu-id="01a2d-185">Stocker des éléments pour des utilisateurs particuliers dans les profils spécifiques à l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="01a2d-185">Store items for particular users in the user-specific profiles</span></span>

<span data-ttu-id="01a2d-186">Veillez à consulter la documentation de l’application hôte pour connaître toute implémentation spéciale des profils PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-186">Be sure to check the host application documentation for any special implementation of PowerShell profiles.</span></span>

## <a name="how-to-use-a-profile"></a><span data-ttu-id="01a2d-187">Comment utiliser un profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-187">How to use a profile</span></span>

<span data-ttu-id="01a2d-188">La plupart des éléments que vous créez dans PowerShell et la plupart des commandes que vous exécutez affectent uniquement la session active.</span><span class="sxs-lookup"><span data-stu-id="01a2d-188">Many of the items that you create in PowerShell and most commands that you run affect only the current session.</span></span> <span data-ttu-id="01a2d-189">Lorsque vous terminez la session, les éléments sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="01a2d-189">When you end the session, the items are deleted.</span></span>

<span data-ttu-id="01a2d-190">Les commandes et éléments spécifiques à la session incluent les variables, les variables de préférence, les alias, les fonctions, les commandes (à l’exception de [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) et les modules PowerShell que vous ajoutez à la session.</span><span class="sxs-lookup"><span data-stu-id="01a2d-190">The session-specific commands and items include variables, preference variables, aliases, functions, commands (except for [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)), and PowerShell modules that you add to the session.</span></span>

<span data-ttu-id="01a2d-191">Pour enregistrer ces éléments et les rendre disponibles dans toutes les sessions ultérieures, ajoutez-les à un profil PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-191">To save these items and make them available in all future sessions, add them to a PowerShell profile.</span></span>

<span data-ttu-id="01a2d-192">Une autre utilisation courante des profils consiste à enregistrer les fonctions, alias et variables fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="01a2d-192">Another common use for profiles is to save frequently-used functions, aliases, and variables.</span></span> <span data-ttu-id="01a2d-193">Lorsque vous enregistrez les éléments dans un profil, vous pouvez les utiliser dans n’importe quelle session applicable sans les recréer.</span><span class="sxs-lookup"><span data-stu-id="01a2d-193">When you save the items in a profile, you can use them in any applicable session without recreating them.</span></span>

## <a name="how-to-start-a-profile"></a><span data-ttu-id="01a2d-194">Comment démarrer un profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-194">How to start a profile</span></span>

<span data-ttu-id="01a2d-195">Lorsque vous ouvrez le fichier de profil, il est vide.</span><span class="sxs-lookup"><span data-stu-id="01a2d-195">When you open the profile file, it is blank.</span></span> <span data-ttu-id="01a2d-196">Toutefois, vous pouvez le remplir avec les variables, les alias et les commandes que vous utilisez fréquemment.</span><span class="sxs-lookup"><span data-stu-id="01a2d-196">However, you can fill it with the variables, aliases, and commands that you use frequently.</span></span>

<span data-ttu-id="01a2d-197">Voici quelques suggestions pour vous aider à démarrer.</span><span class="sxs-lookup"><span data-stu-id="01a2d-197">Here are a few suggestions to get you started.</span></span>

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a><span data-ttu-id="01a2d-198">Ajoutez des commandes qui facilitent l’ouverture de votre profil</span><span class="sxs-lookup"><span data-stu-id="01a2d-198">Add commands that make it easy to open your profile</span></span>

<span data-ttu-id="01a2d-199">Cela s’avère particulièrement utile si vous utilisez un profil autre que le profil « utilisateur actuel, hôte actuel ».</span><span class="sxs-lookup"><span data-stu-id="01a2d-199">This is especially useful if you use a profile other than the "Current User, Current Host" profile.</span></span> <span data-ttu-id="01a2d-200">Par exemple, ajoutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="01a2d-200">For example, add the following command:</span></span>

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a><span data-ttu-id="01a2d-201">Ajouter une fonction qui répertorie les alias de toute applet de commande</span><span class="sxs-lookup"><span data-stu-id="01a2d-201">Add a function that lists the aliases for any cmdlet</span></span>

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a><span data-ttu-id="01a2d-202">Personnaliser votre console</span><span class="sxs-lookup"><span data-stu-id="01a2d-202">Customize your console</span></span>

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a><span data-ttu-id="01a2d-203">Ajouter une invite PowerShell personnalisée</span><span class="sxs-lookup"><span data-stu-id="01a2d-203">Add a customized PowerShell prompt</span></span>

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

<span data-ttu-id="01a2d-204">Pour plus d’informations sur l’invite de PowerShell, consultez [about_Prompts](about_Prompts.md).</span><span class="sxs-lookup"><span data-stu-id="01a2d-204">For more information about the PowerShell prompt, see [about_Prompts](about_Prompts.md).</span></span>

## <a name="the-noprofile-parameter"></a><span data-ttu-id="01a2d-205">Paramètre noprofile</span><span class="sxs-lookup"><span data-stu-id="01a2d-205">The NoProfile parameter</span></span>

<span data-ttu-id="01a2d-206">Pour démarrer PowerShell sans profils, utilisez le paramètre **noprofile** de **PowerShell.exe** , le programme qui démarre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01a2d-206">To start PowerShell without profiles, use the **NoProfile** parameter of **PowerShell.exe** , the program that starts PowerShell.</span></span>

<span data-ttu-id="01a2d-207">Pour commencer, ouvrez un programme capable de Démarrer PowerShell, tel que Cmd.exe ou PowerShell lui-même.</span><span class="sxs-lookup"><span data-stu-id="01a2d-207">To begin, open a program that can start PowerShell, such as Cmd.exe or PowerShell itself.</span></span> <span data-ttu-id="01a2d-208">Vous pouvez également utiliser la boîte de dialogue Exécuter dans Windows.</span><span class="sxs-lookup"><span data-stu-id="01a2d-208">You can also use the Run dialog box in Windows.</span></span>

<span data-ttu-id="01a2d-209">Tapez :</span><span class="sxs-lookup"><span data-stu-id="01a2d-209">Type:</span></span>

```
PowerShell -NoProfile
```

<span data-ttu-id="01a2d-210">Pour obtenir la liste complète des paramètres de PowerShell.exe, tapez :</span><span class="sxs-lookup"><span data-stu-id="01a2d-210">For a complete list of the parameters of PowerShell.exe, type:</span></span>

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a><span data-ttu-id="01a2d-211">Profils et stratégie d’exécution</span><span class="sxs-lookup"><span data-stu-id="01a2d-211">Profiles and Execution Policy</span></span>

<span data-ttu-id="01a2d-212">La stratégie d’exécution de PowerShell détermine, en partie, si vous pouvez exécuter des scripts et charger des fichiers de configuration, y compris les profils.</span><span class="sxs-lookup"><span data-stu-id="01a2d-212">The PowerShell execution policy determines, in part, whether you can run scripts and load configuration files, including the profiles.</span></span> <span data-ttu-id="01a2d-213">La stratégie d’exécution **restreinte** est la stratégie par défaut.</span><span class="sxs-lookup"><span data-stu-id="01a2d-213">The **Restricted** execution policy is the default.</span></span> <span data-ttu-id="01a2d-214">Il empêche l’exécution de tous les scripts, y compris les profils.</span><span class="sxs-lookup"><span data-stu-id="01a2d-214">It prevents all scripts from running, including the profiles.</span></span> <span data-ttu-id="01a2d-215">Si vous utilisez la stratégie « Restricted », le profil ne s’exécute pas et son contenu n’est pas appliqué.</span><span class="sxs-lookup"><span data-stu-id="01a2d-215">If you use the "Restricted" policy, the profile does not run, and its contents are not applied.</span></span>

<span data-ttu-id="01a2d-216">Une `Set-ExecutionPolicy` commande définit et modifie votre stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="01a2d-216">A `Set-ExecutionPolicy` command sets and changes your execution policy.</span></span> <span data-ttu-id="01a2d-217">Il s’agit de l’une des quelques commandes qui s’appliquent à toutes les sessions PowerShell, car la valeur est enregistrée dans le registre.</span><span class="sxs-lookup"><span data-stu-id="01a2d-217">It is one of the few commands that applies in all PowerShell sessions because the value is saved in the registry.</span></span> <span data-ttu-id="01a2d-218">Vous n’avez pas besoin de la définir lorsque vous ouvrez la console, et vous n’avez pas besoin de stocker une `Set-ExecutionPolicy` commande dans votre profil.</span><span class="sxs-lookup"><span data-stu-id="01a2d-218">You do not have to set it when you open the console, and you do not have to store a `Set-ExecutionPolicy` command in your profile.</span></span>

## <a name="profiles-and-remote-sessions"></a><span data-ttu-id="01a2d-219">Profils et sessions à distance</span><span class="sxs-lookup"><span data-stu-id="01a2d-219">Profiles and remote sessions</span></span>

<span data-ttu-id="01a2d-220">Les profils PowerShell ne sont pas exécutés automatiquement dans les sessions à distance. par conséquent, les commandes ajoutées par les profils ne sont pas présentes dans la session à distance.</span><span class="sxs-lookup"><span data-stu-id="01a2d-220">PowerShell profiles are not run automatically in remote sessions, so the commands that the profiles add are not present in the remote session.</span></span> <span data-ttu-id="01a2d-221">En outre, la `$PROFILE` variable automatique n’est pas remplie dans les sessions à distance.</span><span class="sxs-lookup"><span data-stu-id="01a2d-221">In addition, the `$PROFILE` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="01a2d-222">Pour exécuter un profil dans une session, utilisez l’applet de [commande Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .</span><span class="sxs-lookup"><span data-stu-id="01a2d-222">To run a profile in a session, use the [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet.</span></span>

<span data-ttu-id="01a2d-223">Par exemple, la commande suivante exécute le profil « utilisateur actuel, hôte actuel » à partir de l’ordinateur local dans la session dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="01a2d-223">For example, the following command runs the "Current user, Current Host" profile from the local computer in the session in `$s`.</span></span>

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

<span data-ttu-id="01a2d-224">La commande suivante exécute le profil « utilisateur actuel, hôte actuel » à partir de l’ordinateur distant dans la session dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="01a2d-224">The following command runs the "Current user, Current Host" profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="01a2d-225">Étant donné que la `$PROFILE` variable n’est pas remplie, la commande utilise le chemin d’accès explicite au profil.</span><span class="sxs-lookup"><span data-stu-id="01a2d-225">Because the `$PROFILE` variable is not populated, the command uses the explicit path to the profile.</span></span> <span data-ttu-id="01a2d-226">Nous utilisons un opérateur d’approvisionnement en points pour que le profil s’exécute dans l’étendue actuelle sur l’ordinateur distant et non dans sa propre étendue.</span><span class="sxs-lookup"><span data-stu-id="01a2d-226">We use dot sourcing operator so that the profile executes in the current scope on the remote computer and not in its own scope.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="01a2d-227">Après l’exécution de cette commande, les commandes ajoutées par le profil à la session sont disponibles dans `$s` .</span><span class="sxs-lookup"><span data-stu-id="01a2d-227">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

## <a name="see-also"></a><span data-ttu-id="01a2d-228">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01a2d-228">See Also</span></span>

[<span data-ttu-id="01a2d-229">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="01a2d-229">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="01a2d-230">about_Functions</span><span class="sxs-lookup"><span data-stu-id="01a2d-230">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="01a2d-231">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="01a2d-231">about_Prompts</span></span>](about_Prompts.md)

[<span data-ttu-id="01a2d-232">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="01a2d-232">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="01a2d-233">about_Signing</span><span class="sxs-lookup"><span data-stu-id="01a2d-233">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="01a2d-234">about_Remote</span><span class="sxs-lookup"><span data-stu-id="01a2d-234">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="01a2d-235">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="01a2d-235">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="01a2d-236">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="01a2d-236">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
