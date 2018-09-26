---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Inscription de configurations JEA
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522849"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="0dfd1-103">Inscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="0dfd1-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="0dfd1-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0dfd1-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0dfd1-105">La dernière étape avant de pouvoir utiliser JEA une fois les [fonctionnalités de rôles](role-capabilities.md) et le [fichier de configuration de session](session-configurations.md) créés consiste à inscrire le point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="0dfd1-106">Ce processus applique les informations de configuration de session au système et rend le point de terminaison disponible pour une utilisation par des utilisateurs et des moteurs d’automatisation (Automation).</span><span class="sxs-lookup"><span data-stu-id="0dfd1-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="0dfd1-107">Configuration d’une machine unique</span><span class="sxs-lookup"><span data-stu-id="0dfd1-107">Single machine configuration</span></span>

<span data-ttu-id="0dfd1-108">Pour les environnements de petite taille, vous pouvez déployer JEA en inscrivant le fichier de configuration de session à l’aide de l’applet de commande [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="0dfd1-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="0dfd1-109">Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="0dfd1-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="0dfd1-110">Un ou plusieurs rôles ont été créés et placés dans le dossier « RoleCapabilities » d’un module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="0dfd1-111">Un fichier de configuration de session a été créé et testé.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="0dfd1-112">L’utilisateur qui inscrit la configuration JEA dispose de droits d’administrateur sur les systèmes.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="0dfd1-113">Vous devez également sélectionner un nom pour votre point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="0dfd1-114">Le nom du point de terminaison JEA est nécessaire lorsque les utilisateurs souhaitent se connecter au système à l’aide de JEA.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="0dfd1-115">Vous pouvez utiliser l’applet de commande [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) pour vérifier les noms des points de terminaison qui existent sur le système.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="0dfd1-116">Les points de terminaison qui commencent par « microsoft » sont généralement livrés avec Windows.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="0dfd1-117">Le point de terminaison « microsoft.powershell » est le point de terminaison par défaut utilisé lors de la connexion à un point de terminaison PowerShell distant.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="0dfd1-118">Lorsque vous avez déterminé un nom approprié pour votre point de terminaison JEA, exécutez la commande suivante pour inscrire le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="0dfd1-119">La commande ci-dessus redémarre le service WinRM sur le système.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="0dfd1-120">Cela arrête toutes les sessions de communication à distance PowerShell, ainsi que toute configuration DSC en cours.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="0dfd1-121">Il est recommandé de mettre toute machine de production hors connexion avant d’exécuter la commande pour éviter d’interrompre les opérations métier.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="0dfd1-122">Si l’inscription a réussi, vous êtes prêt à [utiliser JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="0dfd1-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="0dfd1-123">Vous pouvez supprimer le fichier de configuration de session à tout moment. Il n’est pas utilisé après l’inscription.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="0dfd1-124">Configuration sur plusieurs machines avec DSC</span><span class="sxs-lookup"><span data-stu-id="0dfd1-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="0dfd1-125">Si vous déployez JEA sur plusieurs machines, le modèle de déploiement le plus simple consiste à utiliser la ressource JEA [Configuration d’état souhaité](https://msdn.microsoft.com/powershell/dsc/overview) pour déployer JEA rapidement et de manière cohérente sur chaque machine.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="0dfd1-126">Pour déployer JEA avec DSC, vous devez garantir que les conditions préalables suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="0dfd1-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="0dfd1-127">Une ou plusieurs fonctionnalités de rôles ont été créées et ajoutées à un module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="0dfd1-128">Le module PowerShell contenant les rôles est stocké sur un partage de fichiers (en lecture seule) accessible depuis chaque machine.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="0dfd1-129">Les paramètres de la configuration de session ont été déterminés.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="0dfd1-130">Il est inutile de créer un fichier de configuration de session si la ressource DSC JEA est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="0dfd1-131">Vous disposez des informations d’identification qui vous permettent d’effectuer des actions administratives sur chaque machine, ou d’avoir accès à un serveur collecteur DSC utilisé pour gérer les machines.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="0dfd1-132">Vous avez téléchargé la [ressource DSC JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="0dfd1-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="0dfd1-133">Sur une machine cible (ou le serveur collecteur, si vous en utilisez un), créez une configuration DSC pour votre point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="0dfd1-134">Dans cette configuration, vous utilisez la ressource DSC JustEnoughAdministration pour définir le fichier de configuration de session et la ressource Fichier à copier sur les fonctionnalités de rôle à partir du partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="0dfd1-135">Les propriétés suivantes sont configurables à l’aide de la ressource DSC :</span><span class="sxs-lookup"><span data-stu-id="0dfd1-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="0dfd1-136">Définitions de rôle</span><span class="sxs-lookup"><span data-stu-id="0dfd1-136">Role Definitions</span></span>
- <span data-ttu-id="0dfd1-137">Groupes de compte virtuel</span><span class="sxs-lookup"><span data-stu-id="0dfd1-137">Virtual Account groups</span></span>
- <span data-ttu-id="0dfd1-138">Nom de compte de service administré de groupe</span><span class="sxs-lookup"><span data-stu-id="0dfd1-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="0dfd1-139">Répertoire de transcription</span><span class="sxs-lookup"><span data-stu-id="0dfd1-139">Transcript directory</span></span>
- <span data-ttu-id="0dfd1-140">Lecteur utilisateur</span><span class="sxs-lookup"><span data-stu-id="0dfd1-140">User drive</span></span>
- <span data-ttu-id="0dfd1-141">Règles d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="0dfd1-141">Conditional access rules</span></span>
- <span data-ttu-id="0dfd1-142">Scripts de démarrage de la session JEA</span><span class="sxs-lookup"><span data-stu-id="0dfd1-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="0dfd1-143">La syntaxe pour chacune de ces propriétés dans une configuration DSC est cohérente avec le fichier de configuration de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="0dfd1-144">Voici un exemple de configuration DSC pour un module de maintenance générale des serveurs.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="0dfd1-145">Il part du principe qu’un module PowerShell valide contenant des fonctionnalités de rôle dans un sous-dossier « RoleCapabilities » se trouve sur le partage de fichiers « \\\\myfileshare\\JEA ».</span><span class="sxs-lookup"><span data-stu-id="0dfd1-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="0dfd1-146">Cette configuration peut ensuite être appliquée à un système en [appelant directement le Gestionnaire de configuration Local](https://msdn.microsoft.com/powershell/dsc/metaconfig) ou en mettant à jour la [configuration du serveur collecteur](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="0dfd1-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="0dfd1-147">La ressource DSC vous permet également de remplacer le point de terminaison de communication à distance Microsoft.PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="0dfd1-148">Si vous procédez ainsi, la ressource inscrit automatiquement un point de terminaison de sauvegarde sans contrainte nommé « Microsoft.PowerShell.Restricted » qui a la valeur par défaut des listes de contrôle d’accès WinRM (permettant aux groupes Utilisateurs de gestion à distance et Administrateurs locaux d’y accéder).</span><span class="sxs-lookup"><span data-stu-id="0dfd1-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="0dfd1-149">Désinscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="0dfd1-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="0dfd1-150">Pour supprimer un point de terminaison JEA sur un système, utilisez l’applet de commande [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).</span><span class="sxs-lookup"><span data-stu-id="0dfd1-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="0dfd1-151">La désinscription d’un point de terminaison JEA empêche les nouveaux utilisateurs de créer de nouvelles sessions JEA sur le système.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="0dfd1-152">Elle permet également de mettre à jour une configuration JEA en réinscrivant un fichier de configuration de session mis à jour à l’aide du même nom de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="0dfd1-153">La désinscription d’un point de terminaison JEA entraîne le redémarrage du service WinRM.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="0dfd1-154">Elle interrompt la plupart des opérations de gestion à distance en cours, notamment les autres sessions PowerShell, les appels WMI et certains outils de gestion.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="0dfd1-155">Ne désinscrivez des points de terminaison PowerShell que pendant les fenêtres de maintenance planifiée.</span><span class="sxs-lookup"><span data-stu-id="0dfd1-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0dfd1-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0dfd1-156">Next steps</span></span>

- [<span data-ttu-id="0dfd1-157">Tester le point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="0dfd1-157">Test the JEA endpoint</span></span>](using-jea.md)