---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Inscription de configurations JEA
description: Cette inscription auprès du système a pour effet de mettre le point de terminaison à la disposition des utilisateurs et des moteurs d’automatisation.
ms.openlocfilehash: 6e7f8cdc1e7a666bddaa42034d70fcbcf55c1972
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92499907"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="fcbb9-104">Inscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="fcbb9-104">Registering JEA Configurations</span></span>

<span data-ttu-id="fcbb9-105">Une fois les [capacités des rôles](role-capabilities.md) et le [fichier de configuration de session](session-configurations.md) créés, la dernière étape consiste à inscrire le point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="fcbb9-106">Cette inscription auprès du système a pour effet de mettre le point de terminaison à la disposition des utilisateurs et des moteurs d’automatisation.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="fcbb9-107">Configuration d’une machine unique</span><span class="sxs-lookup"><span data-stu-id="fcbb9-107">Single machine configuration</span></span>

<span data-ttu-id="fcbb9-108">Pour les environnements de petite taille, vous pouvez déployer JEA en inscrivant le fichier de configuration de session à l’aide de l’applet de commande [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="fcbb9-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="fcbb9-109">Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="fcbb9-109">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="fcbb9-110">Un ou plusieurs rôles ont été créés et placés dans le dossier **RoleCapabilities** d’un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-110">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="fcbb9-111">Un fichier de configuration de session a été créé et testé.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="fcbb9-112">L’utilisateur qui inscrit la configuration JEA dispose de droits d’administrateur sur le système.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-112">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="fcbb9-113">Vous avez sélectionné un nom pour votre point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-113">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="fcbb9-114">Le nom du point de terminaison JEA est nécessaire quand les utilisateurs se connectent au système avec JEA.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-114">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="fcbb9-115">L’applet de commande [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) liste les noms des points de terminaison sur un système.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-115">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="fcbb9-116">Les points de terminaison qui commencent par `microsoft` sont généralement livrés avec Windows.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-116">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="fcbb9-117">Le point de terminaison `microsoft.powershell` est le point de terminaison par défaut utilisé lors de la connexion à un point de terminaison PowerShell distant.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-117">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="fcbb9-118">Exécutez la commande suivante pour inscrire le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-118">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="fcbb9-119">La commande précédente redémarre le service WinRM sur le système.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-119">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="fcbb9-120">Ceci arrête toutes les sessions de communication à distance PowerShell ainsi que les éventuelles configurations DSC en cours.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-120">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="fcbb9-121">Nous vous recommandons de mettre les machines de production hors connexion avant d’exécuter la commande, de façon à éviter d’interrompre les opérations dans l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-121">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="fcbb9-122">Après l’inscription, vous êtes prêt à [utiliser JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="fcbb9-122">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="fcbb9-123">Vous pouvez supprimer le fichier de configuration de session à tout moment.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-123">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="fcbb9-124">Le fichier de configuration n’est plus utilisé après l’inscription du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-124">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="fcbb9-125">Configuration sur plusieurs machines avec DSC</span><span class="sxs-lookup"><span data-stu-id="fcbb9-125">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="fcbb9-126">Pour le déploiement de JEA sur plusieurs machines, le modèle de déploiement le plus simple utilise la ressource JEA [Configuration d’état souhaité](../../../dsc/overview/overview.md) (DSC, Desired State Configuration) pour déployer JEA de façon rapide et cohérente sur chaque machine.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-126">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="fcbb9-127">Voici les prérequis à respecter pour pouvoir déployer JEA avec DSC :</span><span class="sxs-lookup"><span data-stu-id="fcbb9-127">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="fcbb9-128">Une ou plusieurs capacités de rôle ont été créées et ajoutées dans un module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-128">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="fcbb9-129">Le module PowerShell contenant les rôles est stocké sur un partage de fichiers (en lecture seule) accessible depuis chaque machine.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-129">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="fcbb9-130">Les paramètres de la configuration de session ont été déterminés.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-130">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="fcbb9-131">Vous n’avez pas besoin de créer un fichier de configuration de session quand vous utilisez la ressource DSC JEA.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-131">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="fcbb9-132">Vous disposez d’informations d’identification permettant des actions d’administration sur chaque machine ou l’accès au serveur Pull DSC utilisé pour gérer les machines.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-132">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="fcbb9-133">Vous avez téléchargé la [ressource DSC JEA](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="fcbb9-133">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="fcbb9-134">Créez une configuration DSC pour votre point de terminaison JEA sur une machine ou un serveur Pull cible.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-134">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="fcbb9-135">Dans cette configuration, la ressource DSC **JustEnoughAdministration** définit le fichier de configuration de session et la ressource **File** copie les capacités de rôle depuis le partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-135">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="fcbb9-136">Les propriétés suivantes sont configurables à l’aide de la ressource DSC :</span><span class="sxs-lookup"><span data-stu-id="fcbb9-136">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="fcbb9-137">Définitions de rôle</span><span class="sxs-lookup"><span data-stu-id="fcbb9-137">Role Definitions</span></span>
- <span data-ttu-id="fcbb9-138">Groupes de comptes virtuels</span><span class="sxs-lookup"><span data-stu-id="fcbb9-138">Virtual account groups</span></span>
- <span data-ttu-id="fcbb9-139">Nom du compte de service géré de groupe</span><span class="sxs-lookup"><span data-stu-id="fcbb9-139">Group-managed service account name</span></span>
- <span data-ttu-id="fcbb9-140">Répertoire de transcription</span><span class="sxs-lookup"><span data-stu-id="fcbb9-140">Transcript directory</span></span>
- <span data-ttu-id="fcbb9-141">Lecteur utilisateur</span><span class="sxs-lookup"><span data-stu-id="fcbb9-141">User drive</span></span>
- <span data-ttu-id="fcbb9-142">Règles d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="fcbb9-142">Conditional access rules</span></span>
- <span data-ttu-id="fcbb9-143">Scripts de démarrage de la session JEA</span><span class="sxs-lookup"><span data-stu-id="fcbb9-143">Startup scripts for the JEA session</span></span>

<span data-ttu-id="fcbb9-144">La syntaxe pour chacune de ces propriétés dans une configuration DSC est cohérente avec le fichier de configuration de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-144">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="fcbb9-145">Voici un exemple de configuration DSC pour un module de maintenance générale des serveurs.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-145">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="fcbb9-146">Il suppose qu’un module PowerShell valide contenant les capacités de rôle se trouve sur le partage de fichiers `\\myfileshare\JEA`.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-146">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="fcbb9-147">Ensuite, cette configuration est appliquée à un système en appelant directement le [Gestionnaire de configuration local](/powershell/scripting/dsc/managing-nodes/metaConfig) ou en mettant à jour la [configuration du serveur Pull](/powershell/scripting/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="fcbb9-147">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="fcbb9-148">La ressource DSC vous permet également de remplacer le point de terminaison **Microsoft.PowerShell** par défaut.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-148">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="fcbb9-149">Après le remplacement, la ressource inscrit automatiquement un point de terminaison de sauvegarde nommé **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-149">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="fcbb9-150">Le point de terminaison de sauvegarde a la liste de contrôle d’accès WinRM par défaut, qui permet aux utilisateurs de la gestion à distance et aux membres du groupe Administrateurs locaux d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-150">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="fcbb9-151">Désinscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="fcbb9-151">Unregistering JEA configurations</span></span>

<span data-ttu-id="fcbb9-152">L’applet de commande [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) supprime un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-152">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="fcbb9-153">Le fait de désinscrire un point de terminaison JEA empêche les nouveaux utilisateurs de créer des sessions JEA sur le système.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-153">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="fcbb9-154">Elle permet également de mettre à jour une configuration JEA en réinscrivant un fichier de configuration de session mis à jour à l’aide du même nom de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-154">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="fcbb9-155">Le fait de désinscrire un point de terminaison JEA entraîne le redémarrage du service WinRM,</span><span class="sxs-lookup"><span data-stu-id="fcbb9-155">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="fcbb9-156">ce qui interrompt la plupart des opérations de gestion à distance en cours, notamment les autres sessions PowerShell, les appels WMI et certains outils de gestion.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-156">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="fcbb9-157">Ne désinscrivez des points de terminaison PowerShell que pendant les fenêtres de maintenance planifiée.</span><span class="sxs-lookup"><span data-stu-id="fcbb9-157">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcbb9-158">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fcbb9-158">Next steps</span></span>

[<span data-ttu-id="fcbb9-159">Tester le point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="fcbb9-159">Test the JEA endpoint</span></span>](using-jea.md)
