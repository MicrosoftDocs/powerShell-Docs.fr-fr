---
ms.date: 08/23/2017
keywords: powershell,applet de commande
title: résolution des problèmes d’accès dans Accès Web Windows PowerShell
ms.openlocfilehash: 314e4a8098988111739705d55b68ff5ed2f5eff3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086593"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="68d44-103">Résolution des problèmes d’accès dans Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="68d44-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="68d44-104">Mise à jour : 24 juin 2013 (révisée le 23 août 2017)</span><span class="sxs-lookup"><span data-stu-id="68d44-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="68d44-105">S’applique à : Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="68d44-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="68d44-106">Les sections suivantes identifient certains problèmes courants que les utilisateurs peuvent rencontrer quand ils essaient de se connecter à un ordinateur distant à l’aide d’Accès Web Windows PowerShell. Elles incluent des suggestions pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="68d44-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="68d44-107">Échec de connexion</span><span class="sxs-lookup"><span data-stu-id="68d44-107">Sign-in failure</span></span>

<span data-ttu-id="68d44-108">L’échec peut avoir les causes suivantes.</span><span class="sxs-lookup"><span data-stu-id="68d44-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="68d44-109">Il n’existe aucune règle d’autorisation qui autorise l’utilisateur à accéder à l’ordinateur, ni configuration de session spécifique sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="68d44-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="68d44-110">La sécurité d’Accès Web Windows PowerShell est restrictive ; les utilisateurs doivent recevoir un accès explicite aux ordinateurs distants à l’aide de règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="68d44-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="68d44-111">Pour plus d’informations sur la création de règles d’autorisation, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="68d44-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="68d44-112">L’utilisateur n’est pas autorisé à accéder à l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="68d44-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="68d44-113">Cet accès est déterminé par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="68d44-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="68d44-114">Pour plus d’informations, consultez [Connexion à Accès Web Windows PowerShell](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) ou le Blog de l’équipe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68d44-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="68d44-115">La gestion à distance Windows PowerShell n’est peut-être pas activée sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="68d44-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="68d44-116">Vérifiez que la gestion à distance est activée sur l’ordinateur auquel l’utilisateur essaie de se connecter.</span><span class="sxs-lookup"><span data-stu-id="68d44-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="68d44-117">Pour plus d’informations, consultez [Comment configurer votre ordinateur pour la communication à distance](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="68d44-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="68d44-118">Erreur de serveur interne</span><span class="sxs-lookup"><span data-stu-id="68d44-118">Internal Server Error</span></span>

<span data-ttu-id="68d44-119">Quand des utilisateurs essaient de se connecter à Accès Web Windows PowerShell dans une fenêtre Internet Explorer, une page **Erreur de serveur interne** leur est présentée ou *Internet Explorer* cesse de répondre.</span><span class="sxs-lookup"><span data-stu-id="68d44-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="68d44-120">Ce problème est propre à Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="68d44-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="68d44-121">Cause possible</span><span class="sxs-lookup"><span data-stu-id="68d44-121">Possible cause</span></span>

<span data-ttu-id="68d44-122">Il peut survenir pour les utilisateurs qui se sont connectés avec un nom de domaine contenant des caractères chinois ou si un ou plusieurs caractères chinois font partie du nom du serveur de passerelle.</span><span class="sxs-lookup"><span data-stu-id="68d44-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="68d44-123">Solution de contournement</span><span class="sxs-lookup"><span data-stu-id="68d44-123">Workaround</span></span>

1. [<span data-ttu-id="68d44-124">Installer et exécuter Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="68d44-124">Install and run Internet Explorer 10</span></span>](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="68d44-125">Remplacez le paramètre Internet Explorer **Mode de document** par *Normes Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="68d44-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="68d44-126">Appuyez sur **F12** pour ouvrir la console Outils de développement.</span><span class="sxs-lookup"><span data-stu-id="68d44-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="68d44-127">Dans Internet Explorer 10, cliquez sur **Mode navigateur**, puis sélectionnez *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="68d44-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="68d44-128">Cliquez sur **Mode de document**, puis sur *Normes Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="68d44-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="68d44-129">Appuyez de nouveau sur **F12** pour fermer la console Outils de développement.</span><span class="sxs-lookup"><span data-stu-id="68d44-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="68d44-130">Désactivez la configuration automatique du proxy dans Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="68d44-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="68d44-131">Cliquez sur **Outils**, puis sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="68d44-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="68d44-132">Dans la boîte de dialogue **Options Internet**, sous l’onglet **Connexions**, cliquez sur **Paramètres réseau**.</span><span class="sxs-lookup"><span data-stu-id="68d44-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="68d44-133">Décochez la case **Détecter automatiquement les paramètres de connexion**.</span><span class="sxs-lookup"><span data-stu-id="68d44-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="68d44-134">Cliquez sur **OK**, puis de nouveau sur **OK** pour fermer la boîte de dialogue *Options Internet*.</span><span class="sxs-lookup"><span data-stu-id="68d44-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="68d44-135">Impossible de se connecter à un ordinateur de groupe de travail distant</span><span class="sxs-lookup"><span data-stu-id="68d44-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="68d44-136">Si l’ordinateur de destination est membre d’un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="68d44-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="68d44-137">Impossible de trouver les outils de gestion de serveur web (IIS) bien que le rôle ait été installé</span><span class="sxs-lookup"><span data-stu-id="68d44-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="68d44-138">Si vous avez installé Accès Web Windows PowerShell en utilisant l’applet de commande `Install-WindowsFeature`, les outils de gestion ne sont pas installés, sauf si le paramètre `-IncludeManagementTools` est ajouté à l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="68d44-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="68d44-139">Pour obtenir un exemple, consultez [Pour installer Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="68d44-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="68d44-140">Vous pouvez ajouter la console du Gestionnaire des services Internet et d’autres outils de gestion IIS dont vous avez besoin en sélectionnant les outils dans une session de l’**Assistant Ajout de rôles et de fonctionnalités** qui cible le serveur de passerelle.</span><span class="sxs-lookup"><span data-stu-id="68d44-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="68d44-141">Vous pouvez ouvrir l’Assistant Ajout de rôles et de fonctionnalités à partir du Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="68d44-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="68d44-142">Le site web Accès Web Windows PowerShell n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="68d44-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="68d44-143">Si la Configuration de sécurité renforcée est activée dans Internet Explorer (IE ESC), vous pouvez ajouter le site web Accès Web Windows PowerShell à la liste des sites de confiance.</span><span class="sxs-lookup"><span data-stu-id="68d44-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="68d44-144">Une approche moins recommandée en raison des risques de sécurité est de désactiver IE ESC.</span><span class="sxs-lookup"><span data-stu-id="68d44-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="68d44-145">Vous pouvez désactiver IE ESC dans la vignette Propriétés de la page Serveur local dans le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="68d44-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="68d44-146">Un échec d’autorisation s’est produit.</span><span class="sxs-lookup"><span data-stu-id="68d44-146">An authorization failure occurred.</span></span> <span data-ttu-id="68d44-147">Vérifiez que vous êtes autorisé à vous connecter à l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="68d44-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="68d44-148">Le message d’erreur suivant s’affiche lors d’une tentative de connexion quand le serveur de passerelle est l’ordinateur de destination et qu’il se trouve également dans un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="68d44-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="68d44-149">Quand le serveur de passerelle est également le serveur de destination et qu’il se trouve dans un groupe de travail, spécifiez le nom d’utilisateur, le nom d’ordinateur et le nom du groupe d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="68d44-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="68d44-150">N’utilisez pas de point (.) tout seul pour représenter le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="68d44-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="68d44-151">Scénarios et valeurs appropriées</span><span class="sxs-lookup"><span data-stu-id="68d44-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="68d44-152">Tous les cas</span><span class="sxs-lookup"><span data-stu-id="68d44-152">All cases</span></span>

<span data-ttu-id="68d44-153">Paramètre</span><span class="sxs-lookup"><span data-stu-id="68d44-153">Parameter</span></span> | <span data-ttu-id="68d44-154">Valeur</span><span class="sxs-lookup"><span data-stu-id="68d44-154">Value</span></span>
-- | --
<span data-ttu-id="68d44-155">UserName</span><span class="sxs-lookup"><span data-stu-id="68d44-155">UserName</span></span> | <span data-ttu-id="68d44-156">Nom\_serveur\\nom\_utilisateur</span><span class="sxs-lookup"><span data-stu-id="68d44-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="68d44-157">Localhost\\nom\_utilisateur</span><span class="sxs-lookup"><span data-stu-id="68d44-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="68d44-158">.\\nom\_utilisateur</span><span class="sxs-lookup"><span data-stu-id="68d44-158">.\\user\_name</span></span>
<span data-ttu-id="68d44-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="68d44-159">UserGroup</span></span> | <span data-ttu-id="68d44-160">Nom\_serveur\\groupe\_utilisateurs</span><span class="sxs-lookup"><span data-stu-id="68d44-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="68d44-161">Localhost\\groupe\_s</span><span class="sxs-lookup"><span data-stu-id="68d44-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="68d44-162">.\\groupe\_utilisateurs</span><span class="sxs-lookup"><span data-stu-id="68d44-162">.\\user\_group</span></span>
<span data-ttu-id="68d44-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="68d44-163">ComputerGroup</span></span> | <span data-ttu-id="68d44-164">Nom\_serveur\\groupe\_ordinateurs</span><span class="sxs-lookup"><span data-stu-id="68d44-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="68d44-165">Localhost\\groupe\_ordinateurs</span><span class="sxs-lookup"><span data-stu-id="68d44-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="68d44-166">.\\groupe\_ordinateurs</span><span class="sxs-lookup"><span data-stu-id="68d44-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="68d44-167">Serveur de passerelle dans un domaine</span><span class="sxs-lookup"><span data-stu-id="68d44-167">Gateway server is in a domain</span></span>

<span data-ttu-id="68d44-168">Paramètre</span><span class="sxs-lookup"><span data-stu-id="68d44-168">Parameter</span></span> | <span data-ttu-id="68d44-169">Valeur</span><span class="sxs-lookup"><span data-stu-id="68d44-169">Value</span></span>
-- | --
<span data-ttu-id="68d44-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="68d44-170">ComputerName</span></span> | <span data-ttu-id="68d44-171">Nom complet du serveur de passerelle ou Localhost</span><span class="sxs-lookup"><span data-stu-id="68d44-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="68d44-172">Serveur de passerelle dans un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="68d44-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="68d44-173">Paramètre</span><span class="sxs-lookup"><span data-stu-id="68d44-173">Parameter</span></span> | <span data-ttu-id="68d44-174">Valeur</span><span class="sxs-lookup"><span data-stu-id="68d44-174">Value</span></span>
-- | --
<span data-ttu-id="68d44-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="68d44-175">ComputerName</span></span> | <span data-ttu-id="68d44-176">Nom du serveur</span><span class="sxs-lookup"><span data-stu-id="68d44-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="68d44-177">Informations d’identification de la passerelle</span><span class="sxs-lookup"><span data-stu-id="68d44-177">Gateway credentials</span></span>

<span data-ttu-id="68d44-178">Connectez-vous à un serveur de passerelle en tant qu’ordinateur cible à l’aide d’informations d’identification formatées de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="68d44-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="68d44-179">Nom\_serveur\\nom\_utilisateur</span><span class="sxs-lookup"><span data-stu-id="68d44-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="68d44-180">Localhost\\nom\_utilisateur</span><span class="sxs-lookup"><span data-stu-id="68d44-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="68d44-181">.\\nom\_utilisateur</span><span class="sxs-lookup"><span data-stu-id="68d44-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="68d44-182">Un identificateur de sécurité (SID) est affiché dans une règle d’autorisation</span><span class="sxs-lookup"><span data-stu-id="68d44-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="68d44-183">Un identificateur de sécurité (SID) est affiché dans une règle d’autorisation au lieu de la syntaxe nom\_utilisateur/nom\_ordinateur.</span><span class="sxs-lookup"><span data-stu-id="68d44-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="68d44-184">Soit la règle n’est plus valide, soit la requête des services de domaine Active Directory a échoué.</span><span class="sxs-lookup"><span data-stu-id="68d44-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="68d44-185">Une règle d’autorisation n’est généralement pas valide dans les scénarios où le serveur de passerelle était à un moment donné dans un groupe de travail, puis a par la suite joint un domaine.</span><span class="sxs-lookup"><span data-stu-id="68d44-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="68d44-186">Impossible de se connecter avec la règle en tant qu’adresse IPv6 avec un domaine</span><span class="sxs-lookup"><span data-stu-id="68d44-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="68d44-187">Impossible de se connecter à un ordinateur cible spécifié dans des règles d’autorisation sous forme d’adresse IPv6 avec un domaine.</span><span class="sxs-lookup"><span data-stu-id="68d44-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="68d44-188">Les règles d’autorisation ne prennent pas en charge une adresse IPv6 sous forme de nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="68d44-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="68d44-189">Pour spécifier un ordinateur de destination à l’aide d’une adresse IPv6, utilisez l’adresse IPv6 d’origine (qui contient des deux-points) dans la règle d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="68d44-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="68d44-190">Les adresses IPv6 de domaine et numériques (avec des signes deux-points) sont prises en charge en tant que nom d’ordinateur cible dans la page de connexion à Accès Web Windows PowerShell, mais pas dans les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="68d44-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="68d44-191">Pour plus d’informations sur les adresses IPv6, consultez [Fonctionnement d’IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="68d44-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="68d44-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68d44-192">See Also</span></span>

- <span data-ttu-id="68d44-193">[Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="68d44-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="68d44-194">[Utiliser la console web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="68d44-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="68d44-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="68d44-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)