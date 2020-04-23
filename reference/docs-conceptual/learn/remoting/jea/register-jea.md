---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Inscription de configurations JEA
ms.openlocfilehash: 7cc67e891bc14dd667c97e9a8b550b33b4c2b874
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "77706204"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="38dd2-103">Inscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="38dd2-103">Registering JEA Configurations</span></span>

<span data-ttu-id="38dd2-104">Une fois les [capacités des rôles](role-capabilities.md) et le [fichier de configuration de session](session-configurations.md) créés, la dernière étape consiste à inscrire le point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="38dd2-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="38dd2-105">Cette inscription auprès du système a pour effet de mettre le point de terminaison à la disposition des utilisateurs et des moteurs d’automatisation.</span><span class="sxs-lookup"><span data-stu-id="38dd2-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="38dd2-106">Configuration d’une machine unique</span><span class="sxs-lookup"><span data-stu-id="38dd2-106">Single machine configuration</span></span>

<span data-ttu-id="38dd2-107">Pour les environnements de petite taille, vous pouvez déployer JEA en inscrivant le fichier de configuration de session à l’aide de l’applet de commande [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="38dd2-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="38dd2-108">Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="38dd2-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="38dd2-109">Un ou plusieurs rôles ont été créés et placés dans le dossier **RoleCapabilities** d’un module PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38dd2-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="38dd2-110">Un fichier de configuration de session a été créé et testé.</span><span class="sxs-lookup"><span data-stu-id="38dd2-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="38dd2-111">L’utilisateur qui inscrit la configuration JEA dispose de droits d’administrateur sur le système.</span><span class="sxs-lookup"><span data-stu-id="38dd2-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="38dd2-112">Vous avez sélectionné un nom pour votre point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="38dd2-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="38dd2-113">Le nom du point de terminaison JEA est nécessaire quand les utilisateurs se connectent au système avec JEA.</span><span class="sxs-lookup"><span data-stu-id="38dd2-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="38dd2-114">L’applet de commande [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) liste les noms des points de terminaison sur un système.</span><span class="sxs-lookup"><span data-stu-id="38dd2-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="38dd2-115">Les points de terminaison qui commencent par `microsoft` sont généralement livrés avec Windows.</span><span class="sxs-lookup"><span data-stu-id="38dd2-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="38dd2-116">Le point de terminaison `microsoft.powershell` est le point de terminaison par défaut utilisé lors de la connexion à un point de terminaison PowerShell distant.</span><span class="sxs-lookup"><span data-stu-id="38dd2-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

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

<span data-ttu-id="38dd2-117">Exécutez la commande suivante pour inscrire le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="38dd2-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="38dd2-118">La commande précédente redémarre le service WinRM sur le système.</span><span class="sxs-lookup"><span data-stu-id="38dd2-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="38dd2-119">Ceci arrête toutes les sessions de communication à distance PowerShell ainsi que les éventuelles configurations DSC en cours.</span><span class="sxs-lookup"><span data-stu-id="38dd2-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="38dd2-120">Nous vous recommandons de mettre les machines de production hors connexion avant d’exécuter la commande, de façon à éviter d’interrompre les opérations dans l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="38dd2-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="38dd2-121">Après l’inscription, vous êtes prêt à [utiliser JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="38dd2-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="38dd2-122">Vous pouvez supprimer le fichier de configuration de session à tout moment.</span><span class="sxs-lookup"><span data-stu-id="38dd2-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="38dd2-123">Le fichier de configuration n’est plus utilisé après l’inscription du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="38dd2-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="38dd2-124">Configuration sur plusieurs machines avec DSC</span><span class="sxs-lookup"><span data-stu-id="38dd2-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="38dd2-125">Pour le déploiement de JEA sur plusieurs machines, le modèle de déploiement le plus simple utilise la ressource JEA [Configuration d’état souhaité](../../../dsc/overview/overview.md) (DSC, Desired State Configuration) pour déployer JEA de façon rapide et cohérente sur chaque machine.</span><span class="sxs-lookup"><span data-stu-id="38dd2-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="38dd2-126">Voici les prérequis à respecter pour pouvoir déployer JEA avec DSC :</span><span class="sxs-lookup"><span data-stu-id="38dd2-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="38dd2-127">Une ou plusieurs capacités de rôle ont été créées et ajoutées dans un module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="38dd2-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="38dd2-128">Le module PowerShell contenant les rôles est stocké sur un partage de fichiers (en lecture seule) accessible depuis chaque machine.</span><span class="sxs-lookup"><span data-stu-id="38dd2-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="38dd2-129">Les paramètres de la configuration de session ont été déterminés.</span><span class="sxs-lookup"><span data-stu-id="38dd2-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="38dd2-130">Vous n’avez pas besoin de créer un fichier de configuration de session quand vous utilisez la ressource DSC JEA.</span><span class="sxs-lookup"><span data-stu-id="38dd2-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="38dd2-131">Vous disposez d’informations d’identification permettant des actions d’administration sur chaque machine ou l’accès au serveur Pull DSC utilisé pour gérer les machines.</span><span class="sxs-lookup"><span data-stu-id="38dd2-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="38dd2-132">Vous avez téléchargé la [ressource DSC JEA](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="38dd2-132">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="38dd2-133">Créez une configuration DSC pour votre point de terminaison JEA sur une machine ou un serveur Pull cible.</span><span class="sxs-lookup"><span data-stu-id="38dd2-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="38dd2-134">Dans cette configuration, la ressource DSC **JustEnoughAdministration** définit le fichier de configuration de session et la ressource **File** copie les capacités de rôle depuis le partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="38dd2-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="38dd2-135">Les propriétés suivantes sont configurables à l’aide de la ressource DSC :</span><span class="sxs-lookup"><span data-stu-id="38dd2-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="38dd2-136">Définitions de rôles</span><span class="sxs-lookup"><span data-stu-id="38dd2-136">Role Definitions</span></span>
- <span data-ttu-id="38dd2-137">Groupes de comptes virtuels</span><span class="sxs-lookup"><span data-stu-id="38dd2-137">Virtual account groups</span></span>
- <span data-ttu-id="38dd2-138">Nom du compte de service géré de groupe</span><span class="sxs-lookup"><span data-stu-id="38dd2-138">Group-managed service account name</span></span>
- <span data-ttu-id="38dd2-139">Répertoire de transcription</span><span class="sxs-lookup"><span data-stu-id="38dd2-139">Transcript directory</span></span>
- <span data-ttu-id="38dd2-140">Lecteur utilisateur</span><span class="sxs-lookup"><span data-stu-id="38dd2-140">User drive</span></span>
- <span data-ttu-id="38dd2-141">Règles d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="38dd2-141">Conditional access rules</span></span>
- <span data-ttu-id="38dd2-142">Scripts de démarrage de la session JEA</span><span class="sxs-lookup"><span data-stu-id="38dd2-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="38dd2-143">La syntaxe pour chacune de ces propriétés dans une configuration DSC est cohérente avec le fichier de configuration de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38dd2-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="38dd2-144">Voici un exemple de configuration DSC pour un module de maintenance générale des serveurs.</span><span class="sxs-lookup"><span data-stu-id="38dd2-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="38dd2-145">Il suppose qu’un module PowerShell valide contenant les capacités de rôle se trouve sur le partage de fichiers `\\myfileshare\JEA`.</span><span class="sxs-lookup"><span data-stu-id="38dd2-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="38dd2-146">Ensuite, cette configuration est appliquée à un système en appelant directement le [Gestionnaire de configuration local](/powershell/scripting/dsc/managing-nodes/metaConfig) ou en mettant à jour la [configuration du serveur Pull](/powershell/scripting/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="38dd2-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="38dd2-147">La ressource DSC vous permet également de remplacer le point de terminaison **Microsoft.PowerShell** par défaut.</span><span class="sxs-lookup"><span data-stu-id="38dd2-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="38dd2-148">Après le remplacement, la ressource inscrit automatiquement un point de terminaison de sauvegarde nommé **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="38dd2-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="38dd2-149">Le point de terminaison de sauvegarde a la liste de contrôle d’accès WinRM par défaut, qui permet aux utilisateurs de la gestion à distance et aux membres du groupe Administrateurs locaux d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="38dd2-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="38dd2-150">Désinscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="38dd2-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="38dd2-151">L’applet de commande [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) supprime un point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="38dd2-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="38dd2-152">Le fait de désinscrire un point de terminaison JEA empêche les nouveaux utilisateurs de créer des sessions JEA sur le système.</span><span class="sxs-lookup"><span data-stu-id="38dd2-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="38dd2-153">Elle permet également de mettre à jour une configuration JEA en réinscrivant un fichier de configuration de session mis à jour à l’aide du même nom de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="38dd2-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="38dd2-154">Le fait de désinscrire un point de terminaison JEA entraîne le redémarrage du service WinRM,</span><span class="sxs-lookup"><span data-stu-id="38dd2-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="38dd2-155">ce qui interrompt la plupart des opérations de gestion à distance en cours, notamment les autres sessions PowerShell, les appels WMI et certains outils de gestion.</span><span class="sxs-lookup"><span data-stu-id="38dd2-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="38dd2-156">Ne désinscrivez des points de terminaison PowerShell que pendant les fenêtres de maintenance planifiée.</span><span class="sxs-lookup"><span data-stu-id="38dd2-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="38dd2-157">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="38dd2-157">Next steps</span></span>

[<span data-ttu-id="38dd2-158">Tester le point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="38dd2-158">Test the JEA endpoint</span></span>](using-jea.md)
