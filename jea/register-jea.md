---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Inscription de configurations JEA
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084825"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="ad6db-103">Inscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="ad6db-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="ad6db-104">S'applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ad6db-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ad6db-105">Une fois les [fonctionnalités de rôles](role-capabilities.md) et le [fichier de configuration de session](session-configurations.md) créés, la dernière étape à suivre pour pouvoir utiliser JEA consiste à inscrire le point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="ad6db-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="ad6db-106">Cette inscription auprès du système a pour effet de mettre le point de terminaison à la disposition des utilisateurs et des moteurs d’automatisation.</span><span class="sxs-lookup"><span data-stu-id="ad6db-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="ad6db-107">Configuration d’une machine unique</span><span class="sxs-lookup"><span data-stu-id="ad6db-107">Single machine configuration</span></span>

<span data-ttu-id="ad6db-108">Pour les environnements de petite taille, vous pouvez déployer JEA en inscrivant le fichier de configuration de session à l’aide de l’applet de commande [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration).</span><span class="sxs-lookup"><span data-stu-id="ad6db-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="ad6db-109">Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="ad6db-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="ad6db-110">Un ou plusieurs rôles ont été créés et placés dans le dossier « RoleCapabilities » d’un module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="ad6db-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="ad6db-111">Un fichier de configuration de session a été créé et testé.</span><span class="sxs-lookup"><span data-stu-id="ad6db-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="ad6db-112">L’utilisateur qui inscrit la configuration JEA dispose de droits d’administrateur sur les systèmes.</span><span class="sxs-lookup"><span data-stu-id="ad6db-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="ad6db-113">Vous devez également sélectionner un nom pour votre point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="ad6db-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="ad6db-114">Le nom du point de terminaison JEA est requis lorsque les utilisateurs souhaitent se connecter au système avec JEA.</span><span class="sxs-lookup"><span data-stu-id="ad6db-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="ad6db-115">Vous pouvez utiliser l’applet de commande [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) pour vérifier les noms des points de terminaison qui existent sur le système.</span><span class="sxs-lookup"><span data-stu-id="ad6db-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="ad6db-116">Les points de terminaison qui commencent par « microsoft » sont généralement livrés avec Windows.</span><span class="sxs-lookup"><span data-stu-id="ad6db-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="ad6db-117">Le point de terminaison « microsoft.powershell » est le point de terminaison par défaut utilisé lors de la connexion à un point de terminaison PowerShell distant.</span><span class="sxs-lookup"><span data-stu-id="ad6db-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="ad6db-118">Lorsque vous avez déterminé un nom approprié pour votre point de terminaison JEA, exécutez la commande suivante pour inscrire le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ad6db-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="ad6db-119">La commande ci-dessus redémarre le service WinRM sur le système,</span><span class="sxs-lookup"><span data-stu-id="ad6db-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="ad6db-120">ce qui arrête toutes les sessions de communication à distance PowerShell, ainsi que les éventuelles configurations DSC en cours.</span><span class="sxs-lookup"><span data-stu-id="ad6db-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="ad6db-121">Il est recommandé de mettre toute machine de production hors connexion avant d’exécuter la commande pour éviter d’interrompre les opérations métier.</span><span class="sxs-lookup"><span data-stu-id="ad6db-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="ad6db-122">Si l’inscription a réussi, vous pouvez maintenant [utiliser JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="ad6db-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="ad6db-123">Vous pouvez à tout moment supprimer le fichier de configuration de session ; il n’est plus utilisé après l’inscription du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ad6db-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="ad6db-124">Configuration sur plusieurs machines avec DSC</span><span class="sxs-lookup"><span data-stu-id="ad6db-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="ad6db-125">Si vous déployez JEA sur plusieurs machines, le modèle de déploiement le plus simple consiste à utiliser la ressource JEA [Configuration d’état souhaité](https://msdn.microsoft.com/powershell/dsc/overview) pour déployer JEA rapidement et de manière cohérente sur chaque machine.</span><span class="sxs-lookup"><span data-stu-id="ad6db-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="ad6db-126">Voici les prérequis à respecter pour pouvoir déployer JEA avec DSC :</span><span class="sxs-lookup"><span data-stu-id="ad6db-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="ad6db-127">Une ou plusieurs fonctionnalités de rôles ont été créées et ajoutées à un module PowerShell valide.</span><span class="sxs-lookup"><span data-stu-id="ad6db-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="ad6db-128">Le module PowerShell contenant les rôles est stocké sur un partage de fichiers (en lecture seule) accessible depuis chaque machine.</span><span class="sxs-lookup"><span data-stu-id="ad6db-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="ad6db-129">Les paramètres de la configuration de session ont été déterminés.</span><span class="sxs-lookup"><span data-stu-id="ad6db-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="ad6db-130">Il est inutile de créer un fichier de configuration de session si la ressource DSC JEA est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ad6db-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="ad6db-131">Vous disposez d’identifiants qui vous permettent d’effectuer des actions administratives sur chaque machine, ou d’avoir accès à un serveur Pull DSC utilisé pour gérer les machines.</span><span class="sxs-lookup"><span data-stu-id="ad6db-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="ad6db-132">Vous avez téléchargé la [ressource DSC JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="ad6db-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="ad6db-133">Sur une machine cible (ou le serveur collecteur, si vous en utilisez un), créez une configuration DSC pour votre point de terminaison JEA.</span><span class="sxs-lookup"><span data-stu-id="ad6db-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="ad6db-134">Dans cette configuration, la ressource DSC JustEnoughAdministration permet de définir le fichier de configuration de session et la ressource Fichier à copier sur les fonctionnalités de rôle à partir du partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ad6db-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="ad6db-135">Les propriétés suivantes sont configurables à l’aide de la ressource DSC :</span><span class="sxs-lookup"><span data-stu-id="ad6db-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="ad6db-136">Définitions de rôle</span><span class="sxs-lookup"><span data-stu-id="ad6db-136">Role Definitions</span></span>
- <span data-ttu-id="ad6db-137">Groupes de compte virtuel</span><span class="sxs-lookup"><span data-stu-id="ad6db-137">Virtual Account groups</span></span>
- <span data-ttu-id="ad6db-138">Nom de compte de service administré de groupe</span><span class="sxs-lookup"><span data-stu-id="ad6db-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="ad6db-139">Répertoire de transcription</span><span class="sxs-lookup"><span data-stu-id="ad6db-139">Transcript directory</span></span>
- <span data-ttu-id="ad6db-140">Lecteur utilisateur</span><span class="sxs-lookup"><span data-stu-id="ad6db-140">User drive</span></span>
- <span data-ttu-id="ad6db-141">Règles d’accès conditionnel</span><span class="sxs-lookup"><span data-stu-id="ad6db-141">Conditional access rules</span></span>
- <span data-ttu-id="ad6db-142">Scripts de démarrage de la session JEA</span><span class="sxs-lookup"><span data-stu-id="ad6db-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="ad6db-143">La syntaxe pour chacune de ces propriétés dans une configuration DSC est cohérente avec le fichier de configuration de session PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad6db-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="ad6db-144">Voici un exemple de configuration DSC pour un module de maintenance générale des serveurs.</span><span class="sxs-lookup"><span data-stu-id="ad6db-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="ad6db-145">Il part du principe qu’un module PowerShell valide contenant des fonctionnalités de rôle dans un sous-dossier « RoleCapabilities » se trouve sur le partage de fichiers « \\\\myfileshare\\JEA ».</span><span class="sxs-lookup"><span data-stu-id="ad6db-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="ad6db-146">Cette configuration peut ensuite être appliquée à un système en [appelant directement le Gestionnaire de configuration Local](https://msdn.microsoft.com/powershell/dsc/metaconfig) ou en mettant à jour la [configuration du serveur collecteur](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="ad6db-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="ad6db-147">La ressource DSC vous permet également de remplacer le point de terminaison de communication à distance Microsoft.PowerShell par défaut.</span><span class="sxs-lookup"><span data-stu-id="ad6db-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="ad6db-148">Si vous procédez ainsi, la ressource inscrit automatiquement un point de terminaison de sauvegarde sans contrainte nommé « Microsoft.PowerShell.Restricted » qui a la liste ACL WinRM par défaut (permettant aux membres du groupe Utilisateurs de gestion à distance et du groupe Administrateurs local d’y accéder).</span><span class="sxs-lookup"><span data-stu-id="ad6db-148">If you do this, the resource automatically registers a backup unconstrained endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="ad6db-149">Désinscription de configurations JEA</span><span class="sxs-lookup"><span data-stu-id="ad6db-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="ad6db-150">Pour supprimer un point de terminaison JEA sur un système, utilisez l’applet de commande [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration).</span><span class="sxs-lookup"><span data-stu-id="ad6db-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="ad6db-151">Le fait de désinscrire un point de terminaison JEA empêche les nouveaux utilisateurs de créer des sessions JEA sur le système.</span><span class="sxs-lookup"><span data-stu-id="ad6db-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="ad6db-152">Elle permet également de mettre à jour une configuration JEA en réinscrivant un fichier de configuration de session mis à jour à l’aide du même nom de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ad6db-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="ad6db-153">Le fait de désinscrire un point de terminaison JEA entraîne le redémarrage du service WinRM,</span><span class="sxs-lookup"><span data-stu-id="ad6db-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="ad6db-154">ce qui interrompt la plupart des opérations de gestion à distance en cours, notamment les autres sessions PowerShell, les appels WMI et certains outils de gestion.</span><span class="sxs-lookup"><span data-stu-id="ad6db-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="ad6db-155">Ne désinscrivez des points de terminaison PowerShell que pendant les fenêtres de maintenance planifiée.</span><span class="sxs-lookup"><span data-stu-id="ad6db-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad6db-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ad6db-156">Next steps</span></span>

- [<span data-ttu-id="ad6db-157">Tester le point de terminaison JEA</span><span class="sxs-lookup"><span data-stu-id="ad6db-157">Test the JEA endpoint</span></span>](using-jea.md)
