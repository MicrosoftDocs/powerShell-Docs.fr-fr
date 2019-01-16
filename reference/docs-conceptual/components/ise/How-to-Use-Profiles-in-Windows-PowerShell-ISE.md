---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Comment utiliser des profils dans Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401648"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="edab6-103">Comment utiliser des profils dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="edab6-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="edab6-104">Cette rubrique explique comment utiliser des profils dans l’environnement d’écriture de scripts intégré de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="edab6-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="edab6-105">Avant d’effectuer les tâches décrites dans cette section, nous vous recommandons de consulter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) ou, dans le volet Console, tapez `Get-Help about_Profiles` et appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="edab6-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="edab6-106">Un profil est un script Windows PowerShell ISE qui s’exécute automatiquement quand vous démarrez une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="edab6-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="edab6-107">Vous pouvez créer un ou plusieurs profils Windows PowerShell pour Windows PowerShell ISE, et les utiliser pour ajouter la configuration à l’environnement Windows PowerShell ou Windows PowerShell ISE, en le préparant pour votre utilisation, avec les variables, alias, fonctions et préférences de police et de couleur dont vous voulez disposer.</span><span class="sxs-lookup"><span data-stu-id="edab6-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="edab6-108">Un profil affecte chaque session Windows PowerShell ISE que vous démarrez.</span><span class="sxs-lookup"><span data-stu-id="edab6-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="edab6-109">La stratégie d’exécution de Windows PowerShell détermine si vous pouvez exécuter des scripts et charger un profil.</span><span class="sxs-lookup"><span data-stu-id="edab6-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="edab6-110">La stratégie d’exécution par défaut, « Restricted », empêche l’exécution de tous les scripts, y compris des profils.</span><span class="sxs-lookup"><span data-stu-id="edab6-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="edab6-111">Si vous utilisez la stratégie « Restricted », le profil ne peut pas se charger.</span><span class="sxs-lookup"><span data-stu-id="edab6-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="edab6-112">Pour plus d’informations sur la stratégie d’exécution, voir [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="edab6-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="edab6-113">Sélection d’un profil à utiliser dans Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="edab6-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="edab6-114">Windows PowerShell ISE prend en charge les profils pour l’utilisateur actuel et tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="edab6-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="edab6-115">Il prend également en charge les profils Windows PowerShell qui s’appliquent à tous les ordinateurs hôtes.</span><span class="sxs-lookup"><span data-stu-id="edab6-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="edab6-116">Le profil que vous utilisez est déterminé par la façon dont vous utilisez Windows PowerShell et Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="edab6-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="edab6-117">Si vous utilisez uniquement Windows PowerShell ISE pour exécuter Windows PowerShell, enregistrez tous vos éléments dans un des profils spécifiques d’ISE, tel le profil CurrentUserCurrentHost pour Windows PowerShell ISE, ou le profil AllUsersCurrentHost pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="edab6-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="edab6-118">Si vous utilisez plusieurs programmes hôtes pour exécuter Windows PowerShell, enregistrez vos fonctions, alias, variables et commandes dans un profil qui affecte tous les programmes hôtes, tel le profil CurrentUserAllHosts ou le profil AllUsersAllHosts, et enregistrez les fonctionnalités spécifiques d’ISE, telle la personnalisation de la couleur et de la police, dans le profil CurrentUserCurrentHost pour Windows PowerShell ISE ou le profil AllUsersCurrentHost pour Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="edab6-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="edab6-119">Les éléments suivants sont des profils qui peuvent être créés et utilisés dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="edab6-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="edab6-120">Chaque profil est enregistré dans son chemin d’accès spécifique.</span><span class="sxs-lookup"><span data-stu-id="edab6-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="edab6-121">Type de profil</span><span class="sxs-lookup"><span data-stu-id="edab6-121">Profile Type</span></span> | <span data-ttu-id="edab6-122">Chemin d’accès du profil</span><span class="sxs-lookup"><span data-stu-id="edab6-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="edab6-123">**Utilisateur actuel, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="edab6-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="edab6-124">`$PROFILE.CurrentUserCurrentHost`, ou `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="edab6-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="edab6-125">**Tous les utilisateurs, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="edab6-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="edab6-126">**Utilisateur actuel, Tous les ordinateurs hôtes**</span><span class="sxs-lookup"><span data-stu-id="edab6-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="edab6-127">**Tous les utilisateurs, Tous les ordinateurs hôtes**</span><span class="sxs-lookup"><span data-stu-id="edab6-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="edab6-128">Pour créer un profil</span><span class="sxs-lookup"><span data-stu-id="edab6-128">To create a new profile</span></span>

<span data-ttu-id="edab6-129">Pour créer un profil « Utilisateur actuel, Windows PowerShell ISE », exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="edab6-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="edab6-130">Pour créer un profil « Tous les utilisateurs, Windows PowerShell ISE », exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="edab6-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="edab6-131">Pour créer un profil « Utilisateur actuel, Tous les ordinateurs hôtes », exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="edab6-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="edab6-132">Pour créer un profil « Tous les utilisateurs, Tous les ordinateurs hôtes », tapez :</span><span class="sxs-lookup"><span data-stu-id="edab6-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="edab6-133">Pour modifier un profil</span><span class="sxs-lookup"><span data-stu-id="edab6-133">To edit a profile</span></span>

1. <span data-ttu-id="edab6-134">Pour ouvrir le profil, exécutez la commande psedit avec la variable qui spécifie le profil que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="edab6-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="edab6-135">Par exemple, pour ouvrir le profil « Utilisateur actuel, Windows PowerShell ISE », tapez : `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="edab6-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="edab6-136">Ajoutez des éléments à votre profil.</span><span class="sxs-lookup"><span data-stu-id="edab6-136">Add some items to your profile.</span></span> <span data-ttu-id="edab6-137">Voici quelques exemples pour vous aider à démarrer :</span><span class="sxs-lookup"><span data-stu-id="edab6-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="edab6-138">Pour modifier la couleur d’arrière-plan par défaut du volet Console en bleu, dans le type de fichier de profil : `$psISE.Options.OutputPaneBackground = 'blue'`.</span><span class="sxs-lookup"><span data-stu-id="edab6-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="edab6-139">Pour plus d’informations sur la variable $psISE, voir [Référence de modèle objet Windows PowerShell ISE](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="edab6-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="edab6-140">Pour modifier la taille de police en 20, dans le type de fichier de profil : `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="edab6-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="edab6-141">Pour enregistrer votre fichier de profil, dans le menu **Fichier**, cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="edab6-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="edab6-142">À l’ouverture suivante de Windows PowerShell ISE, vos personnalisations sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="edab6-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="edab6-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edab6-143">See Also</span></span>

- [<span data-ttu-id="edab6-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="edab6-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="edab6-145">Présentation de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="edab6-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)