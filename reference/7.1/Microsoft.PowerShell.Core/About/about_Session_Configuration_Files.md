---
description: Décrit les fichiers de configuration de session, qui sont utilisés dans une configuration de session (également appelée « point de terminaison ») pour définir l’environnement des sessions qui utilisent la configuration de session.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 45c8a6e0ba8478e0a49cb287cd4311d7556a42ea
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206706"
---
# <a name="about-session-configuration-files"></a><span data-ttu-id="99531-104">À propos des fichiers de configuration de session</span><span class="sxs-lookup"><span data-stu-id="99531-104">About Session Configuration Files</span></span>

## <a name="short-description"></a><span data-ttu-id="99531-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="99531-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="99531-106">Décrit les fichiers de configuration de session, qui sont utilisés dans une configuration de session (également appelée « point de terminaison ») pour définir l’environnement des sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-106">Describes session configuration files, which are used in a session configuration (also known as an "endpoint") to define the environment of sessions that use the session configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="99531-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="99531-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="99531-108">Un « fichier de configuration de session » est un fichier texte avec une extension de nom de fichier. PSSC qui contient une table de hachage des propriétés et des valeurs de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-108">A "session configuration file" is a text file with a .pssc file name extension that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="99531-109">Vous pouvez utiliser un fichier de configuration de session pour définir les propriétés d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-109">You can use a session configuration file to set the properties of a session configuration.</span></span> <span data-ttu-id="99531-110">Cela définit l’environnement des sessions PowerShell qui utilisent cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-110">Doing so defines the environment of any PowerShell sessions that use that session configuration.</span></span>

<span data-ttu-id="99531-111">Les fichiers de configuration de session facilitent la création de configurations de session personnalisées sans utiliser d’assemblys ou de scripts C# complexes.</span><span class="sxs-lookup"><span data-stu-id="99531-111">Session configuration files make it easy to create custom session configurations without using complex C# assemblies or scripts.</span></span>

<span data-ttu-id="99531-112">Une « configuration de session » ou un « point de terminaison » est une collection de paramètres d’ordinateur local qui déterminent des éléments tels que les utilisateurs qui peuvent créer des sessions sur l’ordinateur. les commandes que les utilisateurs peuvent exécuter dans ces sessions ; et si la session doit s’exécuter en tant que compte virtuel privilégié.</span><span class="sxs-lookup"><span data-stu-id="99531-112">A "session configuration" or "endpoint" is a collection of local computer settings that determine such things as which users can create sessions on the computer; which commands users can run in those sessions; and whether the session should run as a privileged virtual account.</span></span> <span data-ttu-id="99531-113">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="99531-113">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

<span data-ttu-id="99531-114">Les configurations de session ont été introduites dans Windows PowerShell 2,0, et les fichiers de configuration de session ont été introduits dans Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="99531-114">Session configurations were introduced in Windows PowerShell 2.0, and session configuration files were introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="99531-115">Vous devez utiliser Windows PowerShell 3,0 pour inclure un fichier de configuration de session dans une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-115">You must use Windows PowerShell 3.0 to include a session configuration file in a session configuration.</span></span> <span data-ttu-id="99531-116">Toutefois, les utilisateurs de Windows PowerShell 2,0 (et versions ultérieures) sont affectés par les paramètres de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-116">However, users of Windows PowerShell 2.0 (and later) are affected by the settings in the session configuration.</span></span>

## <a name="creating-custom-sessions"></a><span data-ttu-id="99531-117">Création de sessions personnalisées</span><span class="sxs-lookup"><span data-stu-id="99531-117">Creating Custom Sessions</span></span>

<span data-ttu-id="99531-118">Vous pouvez personnaliser de nombreuses fonctionnalités d’une session PowerShell en spécifiant les propriétés de session dans une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-118">You can customize many features of a PowerShell session by specifying session properties in a session configuration.</span></span> <span data-ttu-id="99531-119">Vous pouvez personnaliser une session en écrivant un programme C# qui définit une instance d’exécution personnalisée, ou vous pouvez utiliser un fichier de configuration de session pour définir les propriétés des sessions créées à l’aide de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-119">You can customize a session by writing a C# program that defines a custom runspace, or you can use a session configuration file to define the properties of sessions created by using the session configuration.</span></span> <span data-ttu-id="99531-120">En règle générale, il est plus facile d’utiliser le fichier de configuration de session que d’écrire un programme C#.</span><span class="sxs-lookup"><span data-stu-id="99531-120">As a general rule, it is easier to use the session configuration file than to write a C# program.</span></span>

<span data-ttu-id="99531-121">Vous pouvez utiliser un fichier de configuration de session pour créer des éléments tels que des sessions entièrement opérationnelles pour des utilisateurs hautement fiables. sessions verrouillées qui autorisent un accès minimal ; sessions destinées à des particuliers et qui contiennent uniquement les modules requis pour ces tâches ; et les sessions où les utilisateurs non privilégiés peuvent uniquement exécuter des commandes spécifiques en tant que compte privilégié.</span><span class="sxs-lookup"><span data-stu-id="99531-121">You can use a session configuration file to create items such as fully-functioning sessions for highly trusted users; locked-down sessions that allow minimal access; sessions designed for particular and that contain only the modules required for those tasks; and sessions where unprivileged users can only run specific commands as a privileged account.</span></span>

<span data-ttu-id="99531-122">En outre, vous pouvez gérer si les utilisateurs de la session peuvent utiliser des éléments de langage PowerShell tels que des blocs de script ou s’ils peuvent uniquement exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="99531-122">In addition to that, you can manage whether users of the session can use PowerShell language elements such as script blocks, or whether they can only run commands.</span></span> <span data-ttu-id="99531-123">Vous pouvez gérer la version des utilisateurs PowerShell qui peuvent s’exécuter dans la session. gérer les modules importés dans la session ; et gèrent les applets de commande, fonctions et alias que les utilisateurs de session peuvent exécuter.</span><span class="sxs-lookup"><span data-stu-id="99531-123">You can manage the version of PowerShell users can run in the session; manage which modules are imported into the session; and manage which cmdlets, functions, and aliases session users can run.</span></span> <span data-ttu-id="99531-124">Lorsque vous utilisez le champ RoleDefinitions, vous pouvez fournir aux utilisateurs différentes fonctionnalités dans la session en fonction de l’appartenance à un groupe.</span><span class="sxs-lookup"><span data-stu-id="99531-124">When using the RoleDefinitions field, you can give users different capabilities in the session based on group membership.</span></span>

<span data-ttu-id="99531-125">Pour plus d’informations sur RoleDefinitions et sur la définition de cette valeur, consultez la rubrique d’aide de l’applet de commande New-PSRoleCapabilityFile.</span><span class="sxs-lookup"><span data-stu-id="99531-125">For more information about RoleDefinitions and how to define this Value, see the help topic for the New-PSRoleCapabilityFile Cmdlet.</span></span>

## <a name="creating-a-session-configuration-file"></a><span data-ttu-id="99531-126">Création d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="99531-126">Creating a Session Configuration File</span></span>

<span data-ttu-id="99531-127">Le moyen le plus simple de créer un fichier de configuration de session consiste à utiliser l’applet de commande New-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="99531-127">The easiest way to create a session configuration file is by using the New-PSSessionConfigurationFile cmdlet.</span></span> <span data-ttu-id="99531-128">Cette applet de commande génère un fichier qui utilise la syntaxe et le format corrects, et qui vérifie automatiquement la plupart des valeurs des propriétés du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="99531-128">This cmdlet generates a file that uses the correct syntax and format, and that automatically verifies many of the configuration file property values.</span></span>

<span data-ttu-id="99531-129">Pour obtenir une description détaillée des propriétés que vous pouvez définir dans un fichier de configuration de session, consultez la rubrique d’aide de l’applet de commande New-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="99531-129">For detailed descriptions of the properties that you can set in a session configuration file, see the help topic for the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="99531-130">La commande suivante crée un fichier de configuration de session qui utilise les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="99531-130">The following command creates a session configuration file that uses the default values.</span></span> <span data-ttu-id="99531-131">Le fichier de configuration résultant utilise uniquement les valeurs par défaut, car aucun paramètre autre que le paramètre Path (qui spécifie le chemin d’accès du fichier) n’est inclus :</span><span class="sxs-lookup"><span data-stu-id="99531-131">The resulting configuration file uses only the default values because no parameters other than the Path parameter (which specifies the file path) are included:</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

<span data-ttu-id="99531-132">Pour afficher le nouveau fichier de configuration dans votre éditeur de texte par défaut, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="99531-132">To view the new configuration file in your default text editor, use the following command:</span></span>

```powershell
Invoke-Item -Path .\Defaults.pssc
```

<span data-ttu-id="99531-133">Pour créer une configuration de session pour les sessions dans lesquelles l’utilisateur peut exécuter des commandes, mais pas utiliser d’autres éléments du langage PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="99531-133">To create a session configuration for sessions in which user can run commands, but not use other elements of the PowerShell language, type:</span></span>

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="99531-134">Dans la commande précédente, l’affectation de la valeur nolanguage au paramètre LanguageMode empêche les utilisateurs d’effectuer des opérations telles que l’écriture ou l’exécution de scripts ou l’utilisation de variables.</span><span class="sxs-lookup"><span data-stu-id="99531-134">In the preceding command, setting the LanguageMode parameter to NoLanguage prevents users from doing such things as writing or running scripts, or using variables.</span></span>

<span data-ttu-id="99531-135">Pour créer une configuration de session pour les sessions dans lesquelles les utilisateurs peuvent uniquement utiliser les applets de commande obtenir, tapez :</span><span class="sxs-lookup"><span data-stu-id="99531-135">To create a session configuration for sessions in which users can use only Get cmdlets, type:</span></span>

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

<span data-ttu-id="99531-136">Dans l’exemple précédent, la définition du paramètre VisibleCmdlets sur obtenir-\* limite les utilisateurs aux applets de commande dont les noms commencent par la valeur de chaîne « obtenir- ».</span><span class="sxs-lookup"><span data-stu-id="99531-136">In the preceding example, setting the VisibleCmdlets parameter to Get-\* limits users to cmdlets that have names that start with the string value "Get-".</span></span>

<span data-ttu-id="99531-137">Pour créer une configuration de session pour les sessions qui s’exécutent sous un compte virtuel privilégié au lieu des informations d’identification de l’utilisateur, tapez :</span><span class="sxs-lookup"><span data-stu-id="99531-137">To create a session configuration for sessions that run under a privileged virtual account instead of the user's credentials, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

<span data-ttu-id="99531-138">Pour créer une configuration de session pour les sessions dans lesquelles les commandes visibles par l’utilisateur sont spécifiées dans un fichier de capacités de rôle, tapez :</span><span class="sxs-lookup"><span data-stu-id="99531-138">To create a session configuration for sessions in which the commands visible to the user are specified in a role capabilities file, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a><span data-ttu-id="99531-139">Utilisation d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="99531-139">Using a Session Configuration File</span></span>

<span data-ttu-id="99531-140">Vous pouvez inclure un fichier de configuration de session lorsque vous créez une configuration de session ou ajoutez vous pouvez ajouter un fichier à la configuration de session ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="99531-140">You can include a session configuration file when you create a session configuration or add you can add a file to the session configuration at a later time.</span></span>

<span data-ttu-id="99531-141">Pour inclure un fichier de configuration de session lors de la création d’une configuration de session, utilisez le paramètre Path de l’applet de commande Register-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="99531-141">To include a session configuration file when creating a session configuration, use the Path parameter of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="99531-142">Par exemple, la commande suivante utilise le fichier nolanguage. PSSC lorsqu’il crée une configuration de session nolanguage.</span><span class="sxs-lookup"><span data-stu-id="99531-142">For example, the following command uses the NoLanguage.pssc file when it creates a NoLanguage session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="99531-143">Lors du démarrage d’une nouvelle session nolanguage, les utilisateurs n’ont accès qu’aux commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99531-143">When a new NoLanguage session starts, users will only have access to PowerShell commands.</span></span>

<span data-ttu-id="99531-144">Pour ajouter un fichier de configuration de session à une configuration de session existante, utilisez l’applet de commande Set-PSSessionConfiguration et le paramètre Path.</span><span class="sxs-lookup"><span data-stu-id="99531-144">To add a session configuration file to an existing session configuration, use the Set-PSSessionConfiguration cmdlet and the Path parameter.</span></span> <span data-ttu-id="99531-145">Cela affecte les nouvelles sessions créées avec la configuration de session spécifiée.</span><span class="sxs-lookup"><span data-stu-id="99531-145">This affects any new sessions created with the specified session configuration.</span></span> <span data-ttu-id="99531-146">Notez que l’applet de commande Set-PSSessionConfiguration modifie la session elle-même et ne modifie pas le fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-146">Note that the Set-PSSessionConfiguration cmdlet changes the session itself and does not modify the session configuration file.</span></span>

<span data-ttu-id="99531-147">Par exemple, la commande suivante ajoute le fichier nolanguage. PSSC à la configuration de session LockedDown.</span><span class="sxs-lookup"><span data-stu-id="99531-147">For example, the following command adds the NoLanguage.pssc file to the LockedDown session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

<span data-ttu-id="99531-148">Quand les utilisateurs utilisent la configuration de session LockedDown pour créer une session, ils peuvent exécuter des applets de commande, mais ils ne peuvent pas créer ou utiliser des variables, assigner des valeurs ou utiliser d’autres éléments de langage PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99531-148">When users use the LockedDown session configuration to create a session, they will be able to run cmdlets but they will not be able to create or use variables, assign values, or use other PowerShell language elements.</span></span>

<span data-ttu-id="99531-149">La commande suivante utilise l’applet de commande New-PSSession pour créer une session sur l’ordinateur Srv01 qui utilise la configuration de session LockedDown, en enregistrant une référence d’objet dans la session dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="99531-149">The following command uses the New-PSSession cmdlet to create a session on the computer Srv01 that uses the LockedDown session configuration, saving an object reference to the session in the $s variable.</span></span> <span data-ttu-id="99531-150">La liste de contrôle d’accès (ACL) de la configuration de session détermine qui peut l’utiliser pour créer une session.</span><span class="sxs-lookup"><span data-stu-id="99531-150">The ACL (access control list) of the session configuration determines who can use it to create a session.</span></span>

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

<span data-ttu-id="99531-151">Étant donné que les contraintes nolanguage ont été ajoutées à la configuration de session LockedDown, les utilisateurs dans les sessions LockedDown pourront uniquement exécuter des commandes et des applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99531-151">Because the NoLanguage constraints were added to the LockedDown session configuration, users in LockedDown sessions will only be able to run PowerShell commands and cmdlets.</span></span> <span data-ttu-id="99531-152">Par exemple, les deux commandes suivantes utilisent l’applet de commande Invoke-Command pour exécuter des commandes dans la session référencée dans la variable $s.</span><span class="sxs-lookup"><span data-stu-id="99531-152">For example, the following two commands use the Invoke-Command cmdlet to run commands in the session referenced in the $s variable.</span></span> <span data-ttu-id="99531-153">La première commande, qui exécute l’applet de commande Get-UICulture et n’utilise pas de variables, est réussie.</span><span class="sxs-lookup"><span data-stu-id="99531-153">The first command, which runs the Get-UICulture cmdlet and does not use any variables, succeeds.</span></span> <span data-ttu-id="99531-154">La deuxième commande, qui obtient la valeur de la variable $PSUICulture, échoue.</span><span class="sxs-lookup"><span data-stu-id="99531-154">The second command, which gets the value of the $PSUICulture variable, fails.</span></span>

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a><span data-ttu-id="99531-155">Modification d'un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="99531-155">Editing a Session Configuration File</span></span>

<span data-ttu-id="99531-156">Tous les paramètres d’une configuration de session, à l’exception de Runasvirtualaccount doit avoir et RunAsVirtualAccountGroups, peuvent être modifiés en modifiant le fichier de configuration de session utilisé par la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-156">All settings in a session configuration except for RunAsVirtualAccount and RunAsVirtualAccountGroups can be modified by editing the session configuration file used by the session configuration.</span></span> <span data-ttu-id="99531-157">Pour ce faire, commencez par Rechercher la copie active du fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-157">To do this, begin by locating the active copy of the session configuration file.</span></span>

<span data-ttu-id="99531-158">Quand vous utilisez un fichier de configuration de session dans une configuration de session, PowerShell crée une copie active du fichier de configuration de session et le stocke dans le \$ \\ répertoire pshome SessionConfig sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="99531-158">When you use a session configuration file in a session configuration, PowerShell creates an active copy of the session configuration file and stores it in the \$pshome\\SessionConfig directory on the local computer.</span></span>

<span data-ttu-id="99531-159">L’emplacement de la copie active d’un fichier de configuration de session est stocké dans la propriété ConfigFilePath de l’objet de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-159">The location of the active copy of a session configuration file is stored in the ConfigFilePath property of the session configuration object.</span></span>

<span data-ttu-id="99531-160">La commande suivante obtient l’emplacement du fichier de configuration de session pour la configuration de session nolanguage.</span><span class="sxs-lookup"><span data-stu-id="99531-160">The following command gets the location of the session configuration file for the NoLanguage session configuration.</span></span>

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

<span data-ttu-id="99531-161">Cette commande retourne un chemin d’accès de fichier similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="99531-161">That command returns a file path similar to the following:</span></span>

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="99531-162">Vous pouvez modifier le fichier. PSSC dans n’importe quel éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="99531-162">You can edit the .pssc file in any text editor.</span></span> <span data-ttu-id="99531-163">Une fois le fichier enregistré, il est utilisé par les nouvelles sessions qui utilisent la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-163">After the file is saved it will be employed by any new sessions that use the session configuration.</span></span>

<span data-ttu-id="99531-164">Si vous avez besoin de modifier les paramètres Runasvirtualaccount doit avoir ou RunAsVirtualAccountGroups, vous devez annuler l’inscription de la configuration de session et enregistrer à nouveau un fichier de configuration de session qui comprend les valeurs modifiées.</span><span class="sxs-lookup"><span data-stu-id="99531-164">If you need to modify the RunAsVirtualAccount or the RunAsVirtualAccountGroups settings, you must un-register the session configuration and re-register a session configuration file that includes the edited values.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="99531-165">Test d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="99531-165">Testing a Session Configuration File</span></span>

<span data-ttu-id="99531-166">Utilisez l’applet de commande Test-PSSessionConfigurationFile pour tester les fichiers de configuration de session modifiés manuellement.</span><span class="sxs-lookup"><span data-stu-id="99531-166">Use the Test-PSSessionConfigurationFile cmdlet to test manually edited session configuration files.</span></span> <span data-ttu-id="99531-167">Cela est important : si la syntaxe et les valeurs de fichier ne sont pas valides, les utilisateurs ne pourront pas utiliser la configuration de session pour créer une session.</span><span class="sxs-lookup"><span data-stu-id="99531-167">That's important: if the file syntax and values are not valid users will not be able to use the session configuration to create a session.</span></span>

<span data-ttu-id="99531-168">Par exemple, la commande suivante teste le fichier de configuration de session active de la configuration de session nolanguage.</span><span class="sxs-lookup"><span data-stu-id="99531-168">For example, the following command tests the active session configuration file of the NoLanguage session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="99531-169">Si la syntaxe et les valeurs du fichier de configuration sont valides Test-PSSessionConfigurationFile retourne la valeur true.</span><span class="sxs-lookup"><span data-stu-id="99531-169">If the syntax and values in the configuration file are valid Test-PSSessionConfigurationFile returns True.</span></span> <span data-ttu-id="99531-170">Si la syntaxe et les valeurs ne sont pas valides, l’applet de commande retourne false.</span><span class="sxs-lookup"><span data-stu-id="99531-170">If the syntax and values are not valid then the cmdlet returns False.</span></span>

<span data-ttu-id="99531-171">Vous pouvez utiliser Test-PSSessionConfigurationFile pour tester un fichier de configuration de session, y compris les fichiers créés par l’applet de commande New-PSSessionConfiguration.</span><span class="sxs-lookup"><span data-stu-id="99531-171">You can use Test-PSSessionConfigurationFile to test any session configuration file, including files that the New-PSSessionConfiguration cmdlet creates.</span></span> <span data-ttu-id="99531-172">Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande Test-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="99531-172">For more information, see the help topic for the Test-PSSessionConfigurationFile cmdlet.</span></span>

## <a name="removing-a-session-configuration-file"></a><span data-ttu-id="99531-173">Suppression d’un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="99531-173">Removing a Session Configuration File</span></span>

<span data-ttu-id="99531-174">Vous ne pouvez pas supprimer un fichier de configuration de session d’une configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-174">You cannot remove a session configuration file from a session configuration.</span></span>
<span data-ttu-id="99531-175">Toutefois, vous pouvez remplacer le fichier par un nouveau fichier qui utilise les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="99531-175">However, you can replace the file with a new file that uses the default settings.</span></span> <span data-ttu-id="99531-176">Cela a pour effet d’annuler les paramètres utilisés par le fichier de configuration d’origine.</span><span class="sxs-lookup"><span data-stu-id="99531-176">This effectively cancels the settings used by the original configuration file.</span></span>

<span data-ttu-id="99531-177">Pour remplacer un fichier de configuration de session, créez un fichier de configuration de session qui utilise les paramètres par défaut, puis utilisez l’applet de commande Set-PSSessionConfiguration pour remplacer le fichier de configuration de session personnalisé par le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="99531-177">To replace a session configuration file, create a new session configuration file that uses the default settings, then use the Set-PSSessionConfiguration cmdlet to replace the custom session configuration file with the new file.</span></span>

<span data-ttu-id="99531-178">Par exemple, les commandes suivantes créent un fichier de configuration de session par défaut, puis remplacent le fichier de configuration de session actif dans la configuration de session nolanguage.</span><span class="sxs-lookup"><span data-stu-id="99531-178">For example, the following commands create a Default session configuration file and then replace the active session configuration file in the NoLanguage session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

<span data-ttu-id="99531-179">Lorsque ces commandes sont terminées, la configuration de session nolanguage fournit en fait une prise en charge linguistique complète (paramètre par défaut) pour toutes les sessions créées avec cette configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-179">When these commands finish, the NoLanguage session configuration will actually provide full language support (the default setting) for all sessions created with that session configuration.</span></span>

<span data-ttu-id="99531-180">Affichage des propriétés d’une configuration de session les objets de configuration de session qui représentent des configurations de session à l’aide de fichiers de configuration de session ont des propriétés supplémentaires qui facilitent la découverte et l’analyse de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="99531-180">Viewing the Properties of a Session Configuration The session configuration objects that represent session configurations using session configuration files have additional properties that make it easy to discover and analyze the session configuration.</span></span> <span data-ttu-id="99531-181">(Notez que le nom de type indiqué ci-dessous comprend une définition de vue mise en forme.) Vous pouvez afficher les propriétés en exécutant l’applet de commande Get-PSSessionConfiguration et en canalisant les données renvoyées vers l’applet de commande Get-Member :</span><span class="sxs-lookup"><span data-stu-id="99531-181">(Note that the type name shown below includes a formatted view definition.) You can view the properties by running the Get-PSSessionConfiguration cmdlet and piping the returned data to the Get-Member cmdlet:</span></span>

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

<span data-ttu-id="99531-182">Ces propriétés facilitent la recherche de configurations de session spécifiques.</span><span class="sxs-lookup"><span data-stu-id="99531-182">These properties make it easy to search for specific session configurations.</span></span>
<span data-ttu-id="99531-183">Par exemple, vous pouvez utiliser la propriété ExecutionPolicy pour rechercher une configuration de session qui prend en charge les sessions avec la stratégie d’exécution RemoteSigned.</span><span class="sxs-lookup"><span data-stu-id="99531-183">For example, you can use the ExecutionPolicy property to find a session configuration that supports sessions with the RemoteSigned execution policy.</span></span>
<span data-ttu-id="99531-184">Notez que, étant donné que la propriété ExecutionPolicy existe uniquement sur les sessions qui utilisent des fichiers de configuration de session, la commande peut ne pas retourner toutes les configurations de session éligibles.</span><span class="sxs-lookup"><span data-stu-id="99531-184">Note that, because the ExecutionPolicy property exists only on sessions that use session configuration files, the command might not return all qualifying session configurations.</span></span>

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

<span data-ttu-id="99531-185">La commande suivante obtient les configurations de session dans lesquelles le nom_d’emprunt est l’administrateur Exchange.</span><span class="sxs-lookup"><span data-stu-id="99531-185">The following command gets session configurations in which the RunAsUser is the Exchange administrator.</span></span>

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

<span data-ttu-id="99531-186">Pour afficher des informations sur les définitions de rôles associées à une configuration, utilisez l’applet de commande Get-PSSessionCapability.</span><span class="sxs-lookup"><span data-stu-id="99531-186">To view information about the role definitions associated with a configuration use the Get-PSSessionCapability cmdlet.</span></span> <span data-ttu-id="99531-187">Cette applet de commande vous permet de déterminer les commandes et l’environnement disponibles pour des utilisateurs spécifiques dans des points de terminaison spécifiques.</span><span class="sxs-lookup"><span data-stu-id="99531-187">This cmdlet enables you to determine the commands and environment available to specific users in specific endpoints.</span></span>

## <a name="notes"></a><span data-ttu-id="99531-188">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="99531-188">NOTES</span></span>

<span data-ttu-id="99531-189">Les configurations de session prennent également en charge un type de session connu sous le nom de session « vide ».</span><span class="sxs-lookup"><span data-stu-id="99531-189">Session configurations also support a type of session known as an "empty" session.</span></span> <span data-ttu-id="99531-190">Un type de session vide vous permet de créer des sessions personnalisées avec des commandes sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="99531-190">An Empty session type enables you to create custom sessions with selected commands.</span></span> <span data-ttu-id="99531-191">Si vous n’ajoutez pas de modules, de fonctions ou de scripts à une session vide, la session est limitée aux expressions et peut ne pas être utilisée de façon pratique.</span><span class="sxs-lookup"><span data-stu-id="99531-191">If you do not add modules, functions, or scripts to an empty session, the session is limited to expressions and might not be of any practical use.</span></span> <span data-ttu-id="99531-192">La propriété SessionType vous indique si vous utilisez une session vide ou non.</span><span class="sxs-lookup"><span data-stu-id="99531-192">The SessionType property tells you whether or not you are working with an empty session.</span></span>

## <a name="see-also"></a><span data-ttu-id="99531-193">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="99531-193">SEE ALSO</span></span>

[<span data-ttu-id="99531-194">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="99531-194">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="99531-195">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="99531-195">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="99531-196">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99531-196">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="99531-197">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99531-197">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="99531-198">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99531-198">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="99531-199">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="99531-199">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="99531-200">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99531-200">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="99531-201">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99531-201">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="99531-202">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="99531-202">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="99531-203">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="99531-203">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[<span data-ttu-id="99531-204">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="99531-204">Get-PSSessionCapability</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[<span data-ttu-id="99531-205">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="99531-205">New-PSRoleCapabilityFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)

