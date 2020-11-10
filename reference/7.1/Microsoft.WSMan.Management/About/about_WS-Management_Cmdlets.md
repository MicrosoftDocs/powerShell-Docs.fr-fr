---
description: Fournit une vue d’ensemble de Web Services for Management (WS-Management) comme arrière-plan de l’utilisation des applets de commande WS-Management dans Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: c9d89d0559bf844927976c78bde6fca58ffa8855
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390505"
---
# <a name="about-ws-management-cmdlets"></a><span data-ttu-id="e0bf4-104">À propos des applets de commande WS-Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-104">About WS-Management Cmdlets</span></span>

## <a name="short-description"></a><span data-ttu-id="e0bf4-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="e0bf4-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e0bf4-106">Fournit une vue d’ensemble de Web Services for Management (WS-Management) comme arrière-plan de l’utilisation des applets de commande WS-Management dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-106">Provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e0bf4-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="e0bf4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e0bf4-108">Cette rubrique fournit une vue d’ensemble de la gestion des services Web (WS-Management) pour l’utilisation des applets de commande WS-Management dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-108">This topic provides an overview of Web Services for Management (WS-Management) as background for using the WS-Management cmdlets in Windows PowerShell.</span></span> <span data-ttu-id="e0bf4-109">Cette rubrique fournit également des liens vers des informations supplémentaires sur WS-Management.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-109">This topic also provides links to more information about WS-Management.</span></span> <span data-ttu-id="e0bf4-110">L’implémentation Microsoft de WS-Management est également appelée Windows Remote Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="e0bf4-110">The Microsoft implementation of WS-Management is also known as Windows Remote Management (WinRM).</span></span>

## <a name="about-ws-management"></a><span data-ttu-id="e0bf4-111">À propos de WS-Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-111">About WS-Management</span></span>

<span data-ttu-id="e0bf4-112">Windows Remote Management est l’implémentation Microsoft du protocole WS-Management, un protocole standard SOAP, compatible avec un pare-feu qui permet l’interopérabilité du matériel et des systèmes d’exploitation de différents fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-112">Windows Remote Management is the Microsoft implementation of the WS-Management protocol, a standard SOAP-based, firewall-friendly protocol that allows hardware and operating systems from different vendors to interoperate.</span></span> <span data-ttu-id="e0bf4-113">La spécification de protocole WS-Management permet aux systèmes d’accéder et d’échanger des informations de gestion dans une infrastructure informatique de manière courante.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-113">The WS-Management protocol specification provides a common way for systems to access and exchange management information across an information technology (IT) infrastructure.</span></span> <span data-ttu-id="e0bf4-114">WS-Management et Intelligent Platform Management Interface (IPMI), ainsi que le collecteur d’événements, sont des composants des fonctionnalités de gestion matérielle de Windows.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-114">WS-Management and Intelligent Platform Management Interface (IPMI), along with the Event Collector, are components of the Windows Hardware Management features.</span></span>

<span data-ttu-id="e0bf4-115">Le protocole WS-Management est basé sur les spécifications de service Web standard suivantes : HTTPs, SOAP sur HTTP (profil WS-I), SOAP 1,2, WS-Addressing, WS-Transfer, WS-Enumeration et WS-Eventing.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-115">The WS-Management protocol is based on the following standard Web service specifications: HTTPS, SOAP over HTTP (WS-I profile), SOAP 1.2, WS-Addressing, WS-Transfer, WS-Enumeration, and WS-Eventing.</span></span>

## <a name="ws-management-and-wmi"></a><span data-ttu-id="e0bf4-116">WS-Management et WMI</span><span class="sxs-lookup"><span data-stu-id="e0bf4-116">WS-Management and WMI</span></span>

<span data-ttu-id="e0bf4-117">WS-Management peut être utilisé pour récupérer les données exposées par Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="e0bf4-117">WS-Management can be used to retrieve data exposed by Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="e0bf4-118">Vous pouvez obtenir des données WMI avec des scripts ou des applications qui utilisent l’API de script WS-Management ou via l’outil en ligne de commande WinRM.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-118">You can obtain WMI data with scripts or applications that use the WS-Management Scripting API or through the WinRM command-line tool.</span></span> <span data-ttu-id="e0bf4-119">WS-Management prend en charge la plupart des opérations et classes WMI familières, y compris les objets incorporés.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-119">WS-Management supports most of the familiar WMI classes and operations, including embedded objects.</span></span> <span data-ttu-id="e0bf4-120">WS-Management pouvez tirer parti de WMI pour collecter des données sur les ressources ou pour gérer des ressources sur des ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-120">WS-Management can leverage WMI to collect data about resources or to manage resources on a Windows-based computers.</span></span> <span data-ttu-id="e0bf4-121">Cela signifie que vous pouvez obtenir des données sur des objets tels que des disques, des cartes réseau, des services ou des processus de votre entreprise par le biais de l’ensemble existant de classes WMI.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-121">That means that you can obtain data about objects such as disks, network adapters, services, or processes in your enterprise through the existing set of WMI classes.</span></span> <span data-ttu-id="e0bf4-122">Vous pouvez également accéder aux données matérielles disponibles à partir du fournisseur IPMI WMI standard.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-122">You can also access the hardware data that is available from the standard WMI IPMI provider.</span></span>

## <a name="ws-management-windows-powershell-provider-wsman"></a><span data-ttu-id="e0bf4-123">WS-Management fournisseur Windows PowerShell (WSMan)</span><span class="sxs-lookup"><span data-stu-id="e0bf4-123">WS-Management Windows PowerShell Provider (WSMan)</span></span>

<span data-ttu-id="e0bf4-124">Le fournisseur WSMan fournit une vue hiérarchique des paramètres de configuration WS-Management disponibles.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-124">The WSMan provider provides a hierarchical view into the available WS-Management configuration settings.</span></span> <span data-ttu-id="e0bf4-125">Le fournisseur vous permet d’explorer et de définir les différentes options de configuration de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-125">The provider allows you to explore and set the various WS-Management configuration options.</span></span>

## <a name="ws-management-configuration"></a><span data-ttu-id="e0bf4-126">Configuration de WS-Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-126">WS-Management Configuration</span></span>

<span data-ttu-id="e0bf4-127">Si WS-Management n’est pas installé et configuré, la communication à distance Windows PowerShell n’est pas disponible, les applets de commande WS-Management ne s’exécutent pas, les scripts de WS-Management ne s’exécutent pas et le fournisseur WSMan ne peut pas effectuer d’opérations de données.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-127">If WS-Management is not installed and configured, Windows PowerShell remoting is not available, the WS-Management cmdlets do not run, WS-Management scripts do not run, and the WSMan provider cannot perform data operations.</span></span> <span data-ttu-id="e0bf4-128">L’outil en ligne de commande WS-Management, WinRM et le transfert d’événements dépendent également de la configuration WS-Management.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-128">The WS-Management command-line tool, WinRM, and event forwarding also depend on the WS-Management configuration.</span></span>

## <a name="ws-management-cmdlets"></a><span data-ttu-id="e0bf4-129">Applets de commande WS-Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-129">WS-Management Cmdlets</span></span>

<span data-ttu-id="e0bf4-130">WS-Management fonctionnalité est implémentée dans Windows PowerShell par le biais d’un module qui contient un ensemble d’applets de commande et le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-130">WS-Management functionality is implemented in Windows PowerShell through a module that contains a set of cmdlets and the WSMan provider.</span></span> <span data-ttu-id="e0bf4-131">Vous pouvez utiliser ces applets de commande pour effectuer les tâches de bout en bout nécessaires à la gestion des paramètres de WS-Management sur des ordinateurs locaux et distants.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-131">You can use these cmdlets to complete the end-to-end tasks necessary to manage WS-Management settings on local and remote computers.</span></span>

<span data-ttu-id="e0bf4-132">Les applets de commande WS-Management suivantes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-132">The following WS-Management cmdlets are available.</span></span>

## <a name="connection-cmdlets"></a><span data-ttu-id="e0bf4-133">Applets de commande de connexion</span><span class="sxs-lookup"><span data-stu-id="e0bf4-133">Connection Cmdlets</span></span>

- <span data-ttu-id="e0bf4-134">Connect-WSMan : connecte l’ordinateur local au service WS-Management (WinRM) sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-134">Connect-WSMan: Connects the local computer to the WS-Management (WinRM) service on a remote computer.</span></span>

- <span data-ttu-id="e0bf4-135">Disconnect-WSMan : déconnecte l’ordinateur local du service WS-Management (WinRM) sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-135">Disconnect-WSMan: Disconnects the local computer from the WS-Management (WinRM) service on a remote computer.</span></span>

## <a name="management-data-cmdlets"></a><span data-ttu-id="e0bf4-136">Applets de commande Management-Data</span><span class="sxs-lookup"><span data-stu-id="e0bf4-136">Management-Data Cmdlets</span></span>

- <span data-ttu-id="e0bf4-137">Obtenir-WSManInstance : affiche les informations de gestion d’une instance de ressource spécifiée par un URI de ressource.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-137">Get-WSManInstance: Displays management information for a resource instance that is specified by a resource URI.</span></span>

- <span data-ttu-id="e0bf4-138">Invoke-WSManAction : appelle une action sur l’objet cible qui est spécifié par l’URI de ressource et par les sélecteurs.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-138">Invoke-WSManAction: Invokes an action on the target object that is specified by the resource URI and by the selectors.</span></span>

- <span data-ttu-id="e0bf4-139">New-WSManInstance : crée une nouvelle instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-139">New-WSManInstance: Creates a new management resource instance.</span></span>

- <span data-ttu-id="e0bf4-140">Remove-WSManInstance : supprime une instance de ressource de gestion.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-140">Remove-WSManInstance: Deletes a management resource instance.</span></span>

- <span data-ttu-id="e0bf4-141">Set-WSManInstance : modifie les informations de gestion associées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-141">Set-WSManInstance: Modifies the management information that is related to a resource.</span></span>

## <a name="setup-and-configuration-cmdlets"></a><span data-ttu-id="e0bf4-142">Applets de commande d’installation et de configuration</span><span class="sxs-lookup"><span data-stu-id="e0bf4-142">Setup and Configuration Cmdlets</span></span>

- <span data-ttu-id="e0bf4-143">Set-WSManQuickConfig : configure l’ordinateur local pour la gestion à distance.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-143">Set-WSManQuickConfig: Configures the local computer for remote management.</span></span>
  <span data-ttu-id="e0bf4-144">Vous pouvez utiliser l’applet de commande Set-WSManQuickConfig pour configurer WS-Management afin d’autoriser les connexions à distance au service WS-Management (WinRM).</span><span class="sxs-lookup"><span data-stu-id="e0bf4-144">You can use the Set-WSManQuickConfig cmdlet to configure WS-Management to allow remote connections to the WS-Management (WinRM) service.</span></span> <span data-ttu-id="e0bf4-145">L’applet de commande Set-WSManQuickConfig effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0bf4-145">The Set-WSManQuickConfig cmdlet performs the following operations:</span></span>
  - <span data-ttu-id="e0bf4-146">Il détermine si le service WS-Management (WinRM) est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-146">It determines whether the WS-Management (WinRM) service is running.</span></span> <span data-ttu-id="e0bf4-147">Si le service WinRM n’est pas en cours d’exécution, l’applet de commande Set-WSManQuickConfig démarre le service.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-147">If the WinRM service is not running, the Set-WSManQuickConfig cmdlet starts the service.</span></span>
  - <span data-ttu-id="e0bf4-148">Il définit le type de démarrage du service WS-Management (WinRM) sur automatique.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-148">It sets the WS-Management (WinRM) service startup type to automatic.</span></span>
  - <span data-ttu-id="e0bf4-149">Il crée un écouteur qui accepte les demandes émanant de n’importe quelle adresse IP.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-149">It creates a listener that accepts requests from any IP address.</span></span> <span data-ttu-id="e0bf4-150">Le protocole de transport par défaut est HTTP.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-150">The default transport protocol is HTTP.</span></span>
  - <span data-ttu-id="e0bf4-151">Il active une exception de pare-feu pour le trafic WS-Management.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-151">It enables a firewall exception for WS-Management traffic.</span></span>

  <span data-ttu-id="e0bf4-152">Remarque : pour exécuter cette applet de commande dans Windows Vista, Windows Server 2008 et les versions ultérieures de Windows, vous devez démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».</span><span class="sxs-lookup"><span data-stu-id="e0bf4-152">Note: To run this cmdlet in Windows Vista, Windows Server 2008, and later versions of Windows, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

- <span data-ttu-id="e0bf4-153">Test-WSMan : vérifie que WS-Management est installé et configuré.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-153">Test-WSMan: Verifies that WS-Management is installed and configured.</span></span> <span data-ttu-id="e0bf4-154">L’applet de commande Test-WSMan teste si le service WS-Management (WinRM) est en cours d’exécution et configuré sur un ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-154">The Test-WSMan cmdlet tests whether the WS-Management (WinRM) service is running and configured on a local or remote computer.</span></span>

- <span data-ttu-id="e0bf4-155">Disable-WSManCredSSP : désactive l’authentification CredSSP sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-155">Disable-WSManCredSSP: Disables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="e0bf4-156">Enable-WSManCredSSP : active l’authentification CredSSP sur un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-156">Enable-WSManCredSSP: Enables CredSSP authentication on a client computer.</span></span>

- <span data-ttu-id="e0bf4-157">Obtenir-WSManCredSSP : obtient la configuration liée à CredSSP pour un ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-157">Get-WSManCredSSP: Gets the CredSSP-related configuration for a client computer.</span></span>

## <a name="ws-management-specific-cmdlets"></a><span data-ttu-id="e0bf4-158">Applets de commande spécifiques à WS-Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-158">WS-Management-Specific Cmdlets</span></span>

- <span data-ttu-id="e0bf4-159">New-WSManSessionOption : crée un objet WSManSessionOption à utiliser comme entrée pour un ou plusieurs paramètres d’une applet de commande WS-Management.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-159">New-WSManSessionOption: Creates a WSManSessionOption object to use as input to one or more parameters of a WS-Management cmdlet.</span></span>

## <a name="additional-ws-management-information"></a><span data-ttu-id="e0bf4-160">Informations supplémentaires sur le WS-Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-160">Additional WS-Management Information</span></span>

<span data-ttu-id="e0bf4-161">Pour plus d’informations sur WS-Management, consultez les rubriques suivantes dans la documentation de Windows.</span><span class="sxs-lookup"><span data-stu-id="e0bf4-161">For more information about WS-Management, see the following topics in the Windows documentation.</span></span>

[<span data-ttu-id="e0bf4-162">Gestion à distance de Windows</span><span class="sxs-lookup"><span data-stu-id="e0bf4-162">Windows Remote Management</span></span>](/windows/win32/winrm/portal)

[<span data-ttu-id="e0bf4-163">À propos de Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-163">About Windows Remote Management</span></span>](/windows/win32/winrm/about-windows-remote-management)

[<span data-ttu-id="e0bf4-164">Installation et configuration de Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-164">Installation and Configuration for Windows Remote Management</span></span>](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[<span data-ttu-id="e0bf4-165">Architecture Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="e0bf4-165">Windows Remote Management Architecture</span></span>](/windows/win32/winrm/windows-remote-management-architecture)

[<span data-ttu-id="e0bf4-166">Protocole Gestion des services web</span><span class="sxs-lookup"><span data-stu-id="e0bf4-166">WS-Management Protocol</span></span>](/windows/win32/winrm/ws-management-protocol)

[<span data-ttu-id="e0bf4-167">Windows Remote Management et WMI</span><span class="sxs-lookup"><span data-stu-id="e0bf4-167">Windows Remote Management and WMI</span></span>](/windows/win32/winrm/windows-remote-management-and-wmi)

[<span data-ttu-id="e0bf4-168">URI de ressource</span><span class="sxs-lookup"><span data-stu-id="e0bf4-168">Resource URIs</span></span>](/windows/win32/winrm/resource-uris)

[<span data-ttu-id="e0bf4-169">Gestion matérielle à distance</span><span class="sxs-lookup"><span data-stu-id="e0bf4-169">Remote Hardware Management</span></span>](/windows/win32/winrm/remote-hardware-management)

[<span data-ttu-id="e0bf4-170">Événements</span><span class="sxs-lookup"><span data-stu-id="e0bf4-170">Events</span></span>](/windows/win32/winrm/events)

## <a name="see-also"></a><span data-ttu-id="e0bf4-171">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="e0bf4-171">SEE ALSO</span></span>

[<span data-ttu-id="e0bf4-172">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e0bf4-172">Connect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Connect-WSMan)

[<span data-ttu-id="e0bf4-173">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e0bf4-173">Disable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[<span data-ttu-id="e0bf4-174">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e0bf4-174">Disconnect-WSMan</span></span>](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[<span data-ttu-id="e0bf4-175">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e0bf4-175">Enable-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[<span data-ttu-id="e0bf4-176">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e0bf4-176">Get-WSManCredSSP</span></span>](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[<span data-ttu-id="e0bf4-177">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e0bf4-177">Get-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[<span data-ttu-id="e0bf4-178">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="e0bf4-178">Invoke-WSManAction</span></span>](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[<span data-ttu-id="e0bf4-179">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e0bf4-179">New-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.New-WSManInstance)

[<span data-ttu-id="e0bf4-180">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e0bf4-180">Remove-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[<span data-ttu-id="e0bf4-181">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e0bf4-181">Set-WSManInstance</span></span>](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[<span data-ttu-id="e0bf4-182">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="e0bf4-182">Set-WSManQuickConfig</span></span>](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[<span data-ttu-id="e0bf4-183">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="e0bf4-183">Test-WSMan</span></span>](xref:Microsoft.WSMan.Management.Test-WSMan)
