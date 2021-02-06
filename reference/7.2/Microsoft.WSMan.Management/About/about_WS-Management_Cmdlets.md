---
description: Fournit une vue d’ensemble de Web Services for Management (WS-Management) comme arrière-plan de l’utilisation des applets de commande WS-Management dans Windows PowerShell.
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: faf0f0b08d604f7568ac316557788eea21feea8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597983"
---
# <a name="about-ws-management-cmdlets"></a><span data-ttu-id="b9658-103">À propos des applets de commande WS-Management</span><span class="sxs-lookup"><span data-stu-id="b9658-103">About WS-Management Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="b9658-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="b9658-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b9658-105">Fournit une vue d’ensemble de Web Services for Management (WS-Management) comme arrière-plan de l’utilisation des applets de commande WS-Management dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9658-105">Provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b9658-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="b9658-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="b9658-107">Cette rubrique fournit une vue d’ensemble de la gestion des services Web (WS-Management) pour l’utilisation des applets de commande WS-Management dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9658-107">This topic provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span> <span data-ttu-id="b9658-108">Cette rubrique fournit également des liens vers des informations supplémentaires sur WS-Management.</span><span class="sxs-lookup"><span data-stu-id="b9658-108">This topic also provides links to more information about WS-Management.</span></span> <span data-ttu-id="b9658-109">L’implémentation Microsoft de WS-Management est également appelée Windows Remote Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="b9658-109">The Microsoft implementation of WS-Management is also known as Windows Remote Management (WinRM).</span></span>

## <a name="about-ws-management"></a><span data-ttu-id="b9658-110">À propos de WS-Management</span><span class="sxs-lookup"><span data-stu-id="b9658-110">About WS-Management</span></span>

<span data-ttu-id="b9658-111">Windows Remote Management est l’implémentation Microsoft du protocole WS-Management, un protocole standard SOAP, compatible avec un pare-feu qui permet l’interopérabilité du matériel et des systèmes d’exploitation de différents fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="b9658-111">Windows Remote Management is the Microsoft implementation of the WS-Management protocol, a standard SOAP-based, firewall-friendly protocol that allows hardware and operating systems from different vendors to interoperate.</span></span> <span data-ttu-id="b9658-112">La spécification de protocole WS-Management permet aux systèmes d’accéder et d’échanger des informations de gestion dans une infrastructure informatique de manière courante.</span><span class="sxs-lookup"><span data-stu-id="b9658-112">The WS-Management protocol specification provides a common way for systems to access and exchange management information across an information technology (IT) infrastructure.</span></span> <span data-ttu-id="b9658-113">WS-Management et Intelligent Platform Management Interface (IPMI), ainsi que le collecteur d’événements, sont des composants des fonctionnalités de gestion matérielle de Windows.</span><span class="sxs-lookup"><span data-stu-id="b9658-113">WS-Management and Intelligent Platform Management Interface (IPMI), along with the Event Collector, are components of the Windows Hardware Management features.</span></span>

<span data-ttu-id="b9658-114">Le protocole WS-Management est basé sur les spécifications de service Web standard suivantes : HTTPs, SOAP sur HTTP (profil WS-I), SOAP 1,2, WS-Addressing, WS-Transfer, WS-Enumeration et WS-Eventing.</span><span class="sxs-lookup"><span data-stu-id="b9658-114">The WS-Management protocol is based on the following standard Web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing.</span></span>

## <a name="ws-management-and-wmi"></a><span data-ttu-id="b9658-115">WS-Management et WMI</span><span class="sxs-lookup"><span data-stu-id="b9658-115">WS-Management and WMI</span></span>

<span data-ttu-id="b9658-116">WS-Management peut être utilisé pour récupérer les données exposées par Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="b9658-116">WS-Management can be used to retrieve data exposed by Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="b9658-117">Vous pouvez obtenir des données WMI avec des scripts ou des applications qui utilisent l’API de script WS-Management ou via l’outil en ligne de commande WinRM.</span><span class="sxs-lookup"><span data-stu-id="b9658-117">You can obtain WMI data with scripts or applications that use the WS-Management Scripting API or through the WinRM command-line tool.</span></span> <span data-ttu-id="b9658-118">WS-Management prend en charge la plupart des opérations et classes WMI familières, y compris les objets incorporés.</span><span class="sxs-lookup"><span data-stu-id="b9658-118">WS-Management supports most of the familiar WMI classes and operations, including embedded objects.</span></span> <span data-ttu-id="b9658-119">WS-Management pouvez tirer parti de WMI pour collecter des données sur les ressources ou pour gérer des ressources sur des ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="b9658-119">WS-Management can leverage WMI to collect data about resources or to manage resources on a Windows-based computers.</span></span> <span data-ttu-id="b9658-120">Cela signifie que vous pouvez obtenir des données sur des objets tels que des disques, des cartes réseau, des services ou des processus de votre entreprise par le biais de l’ensemble existant de classes WMI.</span><span class="sxs-lookup"><span data-stu-id="b9658-120">That means that you can obtain data about objects such as disks, network adapters, services, or processes in your enterprise through the existing set of WMI classes.</span></span> <span data-ttu-id="b9658-121">Vous pouvez également accéder aux données matérielles disponibles à partir du fournisseur IPMI WMI standard.</span><span class="sxs-lookup"><span data-stu-id="b9658-121">You can also access the hardware data that is available from the standard WMI IPMI provider.</span></span>

## <a name="ws-management-windows-powershell-provider-wsman"></a><span data-ttu-id="b9658-122">WS-Management fournisseur Windows PowerShell (WSMan)</span><span class="sxs-lookup"><span data-stu-id="b9658-122">WS-Management Windows PowerShell Provider (WSMan)</span></span>

<span data-ttu-id="b9658-123">Le fournisseur WSMan fournit une vue hiérarchique des paramètres de configuration WS-Management disponibles.</span><span class="sxs-lookup"><span data-stu-id="b9658-123">The WSMan provider provides a hierarchical view into the available WS-Management configuration settings.</span></span> <span data-ttu-id="b9658-124">Le fournisseur vous permet d’explorer et de définir les différentes options de configuration de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="b9658-124">The provider allows you to explore and set the various WS-Management configuration options.</span></span>

## <a name="ws-management-configuration"></a><span data-ttu-id="b9658-125">Configuration de WS-Management</span><span class="sxs-lookup"><span data-stu-id="b9658-125">WS-Management Configuration</span></span>

<span data-ttu-id="b9658-126">Si WS-Management n’est pas installé et configuré, la communication à distance Windows PowerShell n’est pas disponible, les applets de commande WS-Management ne s’exécutent pas, les scripts de WS-Management ne s’exécutent pas et le fournisseur WSMan ne peut pas effectuer d’opérations de données.</span><span class="sxs-lookup"><span data-stu-id="b9658-126">If WS-Management is not installed and configured, Windows PowerShell remoting is not available, the WS-Management cmdlets do not run, WS-Management scripts do not run, and the WSMan provider cannot perform data operations.</span></span> <span data-ttu-id="b9658-127">L’outil en ligne de commande WS-Management, WinRM et le transfert d’événements dépendent également de la configuration WS-Management.</span><span class="sxs-lookup"><span data-stu-id="b9658-127">The WS-Management command-line tool, WinRM, and event forwarding also depend on the WS-Management configuration.</span></span>

## <a name="ws-management-cmdlets"></a><span data-ttu-id="b9658-128">Applets de commande WS-Management</span><span class="sxs-lookup"><span data-stu-id="b9658-128">WS-Management Cmdlets</span></span>

<span data-ttu-id="b9658-129">WS-Management fonctionnalité est implémentée dans Windows PowerShell par le biais d’un module qui contient un ensemble d’applets de commande et le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="b9658-129">WS-Management functionality is implemented in Windows PowerShell through a module that contains a set of cmdlets and the WSMan provider.</span></span> <span data-ttu-id="b9658-130">Vous pouvez utiliser ces applets de commande pour effectuer les tâches de bout en bout nécessaires à la gestion des paramètres de WS-Management sur des ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="b9658-130">You can use these cmdlets to complete the end-to-end tasks necessary to manage WS-Management settings on local and remote computers.</span></span>

<span data-ttu-id="b9658-131">Les applets de commande WS-Management suivantes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="b9658-131">The following WS-Management cmdlets are available.</span></span>

## <a name="connection-cmdlets"></a><span data-ttu-id="b9658-132">Applets de commande de connexion</span><span class="sxs-lookup"><span data-stu-id="b9658-132">Connection Cmdlets</span></span>

- <span data-ttu-id="b9658-133">Connect-WSMan : connecte l’ordinateur local au service WS-Management (WinRM) sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b9658-133">Connect-WSMan: Connects the local computer to the WS-Management (WinRM) service on a remote computer.</span></span>

- <span data-ttu-id="b9658-134">Disconnect-WSMan : déconnecte l’ordinateur local du service WS-Management (WinRM) sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b9658-134">Disconnect-WSMan: Disconnects the local computer from the WS-Management (WinRM) service on a remote computer.</span></span>

## <a name="management-data-cmdlets"></a><span data-ttu-id="b9658-135">Applets de commande Management-Data</span><span class="sxs-lookup"><span data-stu-id="b9658-135">Management-Data Cmdlets</span></span>

- <span data-ttu-id="b9658-136">Obtenir-WSManInstance : affiche les informations de gestion d’une instance de ressource spécifiée par un URI de ressource.</span><span class="sxs-lookup"><span data-stu-id="b9658-136">Get-WSManInstance: Displays management information for a resource instance that is specified by a resource URI.</span></span>

- <span data-ttu-id="b9658-137">Invoke-WSManAction : appelle une action sur l’objet cible qui est spécifié par l’URI de ressource et par les sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="b9658-137">Invoke-WSManAction: Invokes an action on the target object that is specified by the resource URI and by the selectors.</span></span>

- <span data-ttu-id="b9658-138">New-WSManInstance : crée une nouvelle instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b9658-138">New-WSManInstance: Creates a new management resource instance.</span></span>

- <span data-ttu-id="b9658-139">Remove-WSManInstance : supprime une instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="b9658-139">Remove-WSManInstance: Deletes a management resource instance.</span></span>

- <span data-ttu-id="b9658-140">Set-WSManInstance : modifie les informations de gestion associées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="b9658-140">Set-WSManInstance: Modifies the management information that is related to a resource.</span></span>

## <a name="setup-and-configuration-cmdlets"></a><span data-ttu-id="b9658-141">Applets de commande d’installation et de configuration</span><span class="sxs-lookup"><span data-stu-id="b9658-141">Setup and Configuration Cmdlets</span></span>

- <span data-ttu-id="b9658-142">Set-WSManQuickConfig : configure l’ordinateur local pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="b9658-142">Set-WSManQuickConfig: Configures the local computer for remote management.</span></span>
  <span data-ttu-id="b9658-143">Vous pouvez utiliser l’applet de commande Set-WSManQuickConfig pour configurer WS-Management afin d’autoriser les connexions à distance au service WS-Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="b9658-143">You can use the Set-WSManQuickConfig cmdlet to configure WS-Management to allow remote connections to the WS-Management (WinRM) service.</span></span> <span data-ttu-id="b9658-144">L’applet de commande Set-WSManQuickConfig effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b9658-144">The Set-WSManQuickConfig cmdlet performs the following operations:</span></span>
  - <span data-ttu-id="b9658-145">Il détermine si le service WS-Management (WinRM) est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b9658-145">It determines whether the WS-Management (WinRM) service is running.</span></span> <span data-ttu-id="b9658-146">Si le service WinRM n’est pas en cours d’exécution, l’applet de commande Set-WSManQuickConfig démarre le service.</span><span class="sxs-lookup"><span data-stu-id="b9658-146">If the WinRM service is not running, the Set-WSManQuickConfig cmdlet starts the service.</span></span>
  - <span data-ttu-id="b9658-147">Il définit le type de démarrage du service WS-Management (WinRM) sur automatique.</span><span class="sxs-lookup"><span data-stu-id="b9658-147">It sets the WS-Management (WinRM) service startup type to automatic.</span></span>
  - <span data-ttu-id="b9658-148">Il crée un écouteur qui accepte les demandes émanant de n’importe quelle adresse IP.</span><span class="sxs-lookup"><span data-stu-id="b9658-148">It creates a listener that accepts requests from any IP address.</span></span> <span data-ttu-id="b9658-149">Le protocole de transport par défaut est HTTP.</span><span class="sxs-lookup"><span data-stu-id="b9658-149">The default transport protocol is HTTP.</span></span>
  - <span data-ttu-id="b9658-150">Il active une exception de pare-feu pour le trafic WS-Management.</span><span class="sxs-lookup"><span data-stu-id="b9658-150">It enables a firewall exception for WS-Management traffic.</span></span>

  <span data-ttu-id="b9658-151">Remarque : pour exécuter cette applet de commande dans Windows Vista, Windows Server 2008 et les versions ultérieures de Windows, vous devez démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="b9658-151">Note: To run this cmdlet in Windows Vista, Windows Server 2008, and later versions of Windows, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

- <span data-ttu-id="b9658-152">Test-WSMan : vérifie que WS-Management est installé et configuré.</span><span class="sxs-lookup"><span data-stu-id="b9658-152">Test-WSMan: Verifies that WS-Management is installed and configured.</span></span> <span data-ttu-id="b9658-153">L’applet de commande Test-WSMan teste si le service WS-Management (WinRM) est en cours d’exécution et configuré sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="b9658-153">The Test-WSMan cmdlet tests whether the WS-Management (WinRM) service is running and configured on a local or remote computer.</span></span>

- <span data-ttu-id="b9658-154">Disable-WSManCredSSP : désactive l’authentification CredSSP sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b9658-154">Disable-WSManCredSSP: Disables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="b9658-155">Enable-WSManCredSSP : active l’authentification CredSSP sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b9658-155">Enable-WSManCredSSP: Enables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="b9658-156">Obtenir-WSManCredSSP : obtient la configuration liée à CredSSP pour un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b9658-156">Get-WSManCredSSP: Gets the CredSSP-related configuration for a client computer.</span></span>

## <a name="ws-management-specific-cmdlets"></a><span data-ttu-id="b9658-157">Applets de commande spécifiques à WS-Management</span><span class="sxs-lookup"><span data-stu-id="b9658-157">WS-Management-Specific Cmdlets</span></span>

- <span data-ttu-id="b9658-158">New-WSManSessionOption : crée un objet WSManSessionOption à utiliser comme entrée pour un ou plusieurs paramètres d’une applet de commande WS-Management.</span><span class="sxs-lookup"><span data-stu-id="b9658-158">New-WSManSessionOption: Creates a WSManSessionOption object to use as input to one or more parameters of a WS-Management cmdlet.</span></span>

## <a name="additional-ws-management-information"></a><span data-ttu-id="b9658-159">Informations supplémentaires sur le WS-Management</span><span class="sxs-lookup"><span data-stu-id="b9658-159">Additional WS-Management Information</span></span>

<span data-ttu-id="b9658-160">Pour plus d’informations sur WS-Management, consultez les rubriques suivantes dans la documentation de Windows.</span><span class="sxs-lookup"><span data-stu-id="b9658-160">For more information about WS-Management, see the following topics in the Windows documentation.</span></span>

[<span data-ttu-id="b9658-161">Gestion à distance de Windows</span><span class="sxs-lookup"><span data-stu-id="b9658-161">Windows Remote Management</span></span>](/windows/win32/winrm/portal)

[<span data-ttu-id="b9658-162">À propos de Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="b9658-162">About Windows Remote Management</span></span>](/windows/win32/winrm/about-windows-remote-management)

[<span data-ttu-id="b9658-163">Installation et configuration de Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="b9658-163">Installation and Configuration for Windows Remote Management</span></span>](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[<span data-ttu-id="b9658-164">Architecture Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="b9658-164">Windows Remote Management Architecture</span></span>](/windows/win32/winrm/windows-remote-management-architecture)

[<span data-ttu-id="b9658-165">Protocole Gestion des services web</span><span class="sxs-lookup"><span data-stu-id="b9658-165">WS-Management Protocol</span></span>](/windows/win32/winrm/ws-management-protocol)

[<span data-ttu-id="b9658-166">Windows Remote Management et WMI</span><span class="sxs-lookup"><span data-stu-id="b9658-166">Windows Remote Management and WMI</span></span>](/windows/win32/winrm/windows-remote-management-and-wmi)

[<span data-ttu-id="b9658-167">URI de ressource</span><span class="sxs-lookup"><span data-stu-id="b9658-167">Resource URIs</span></span>](/windows/win32/winrm/resource-uris)

[<span data-ttu-id="b9658-168">Gestion matérielle à distance</span><span class="sxs-lookup"><span data-stu-id="b9658-168">Remote Hardware Management</span></span>](/windows/win32/winrm/remote-hardware-management)

[<span data-ttu-id="b9658-169">Événements</span><span class="sxs-lookup"><span data-stu-id="b9658-169">Events</span></span>](/windows/win32/winrm/events)

## <a name="see-also"></a><span data-ttu-id="b9658-170">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="b9658-170">SEE ALSO</span></span>

[<span data-ttu-id="b9658-171">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b9658-171">Connect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Connect-WSMan)

[<span data-ttu-id="b9658-172">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b9658-172">Disable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[<span data-ttu-id="b9658-173">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b9658-173">Disconnect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[<span data-ttu-id="b9658-174">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b9658-174">Enable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[<span data-ttu-id="b9658-175">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b9658-175">Get-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[<span data-ttu-id="b9658-176">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b9658-176">Get-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[<span data-ttu-id="b9658-177">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b9658-177">Invoke-WSManAction</span></span>](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[<span data-ttu-id="b9658-178">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b9658-178">New-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.New-WSManInstance)

[<span data-ttu-id="b9658-179">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b9658-179">Remove-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[<span data-ttu-id="b9658-180">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b9658-180">Set-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[<span data-ttu-id="b9658-181">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b9658-181">Set-WSManQuickConfig</span></span>](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[<span data-ttu-id="b9658-182">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="b9658-182">Test-WSMan</span></span>](xref:Microsoft.WSMan.Management.Test-WSMan)
