---
ms.date: 08/23/2017
keywords: powershell,applet de commande
title: résolution des problèmes d’accès dans Accès Web Windows PowerShell
ms.openlocfilehash: 818beffaf7df55ae36a154b7b751f9201c5b4299
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870181"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="7d1ca-103">Résolution des problèmes d’accès dans Accès Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d1ca-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="7d1ca-104">Mise à jour : 24 juin 2013 (révisée le 23 août 2017)</span><span class="sxs-lookup"><span data-stu-id="7d1ca-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="7d1ca-105">S’applique à : Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7d1ca-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="7d1ca-106">Les sections suivantes identifient certains problèmes courants que les utilisateurs peuvent rencontrer quand ils essaient de se connecter à un ordinateur distant à l’aide d’Accès Web Windows PowerShell. Elles incluent des suggestions pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="7d1ca-107">Échec de connexion</span><span class="sxs-lookup"><span data-stu-id="7d1ca-107">Sign-in failure</span></span>

<span data-ttu-id="7d1ca-108">L’échec peut avoir les causes suivantes.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="7d1ca-109">Il n’existe aucune règle d’autorisation qui autorise l’utilisateur à accéder à l’ordinateur, ni configuration de session spécifique sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="7d1ca-110">La sécurité d’Accès Web Windows PowerShell est restrictive ; les utilisateurs doivent recevoir un accès explicite aux ordinateurs distants à l’aide de règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="7d1ca-111">Pour plus d’informations sur la création de règles d’autorisation, consultez [Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="7d1ca-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="7d1ca-112">L’utilisateur n’est pas autorisé à accéder à l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="7d1ca-113">Cet accès est déterminé par des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="7d1ca-114">Pour plus d’informations, consultez [Connexion à Accès Web Windows PowerShell](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) ou le Blog de l’équipe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="7d1ca-115">La gestion à distance Windows PowerShell n’est peut-être pas activée sur l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="7d1ca-116">Vérifiez que la gestion à distance est activée sur l’ordinateur auquel l’utilisateur essaie de se connecter.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="7d1ca-117">Pour plus d’informations, consultez [Comment configurer votre ordinateur pour la communication à distance](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="7d1ca-117">For more information, see [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="7d1ca-118">Erreur interne du serveur</span><span class="sxs-lookup"><span data-stu-id="7d1ca-118">Internal Server Error</span></span>

<span data-ttu-id="7d1ca-119">Quand des utilisateurs essaient de se connecter à Accès Web Windows PowerShell dans une fenêtre Internet Explorer, une page **Erreur de serveur interne** leur est présentée ou *Internet Explorer* cesse de répondre.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="7d1ca-120">Ce problème est propre à Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="7d1ca-121">Cause probable</span><span class="sxs-lookup"><span data-stu-id="7d1ca-121">Possible cause</span></span>

<span data-ttu-id="7d1ca-122">Il peut survenir pour les utilisateurs qui se sont connectés avec un nom de domaine contenant des caractères chinois ou si un ou plusieurs caractères chinois font partie du nom du serveur de passerelle.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="7d1ca-123">Solution de contournement</span><span class="sxs-lookup"><span data-stu-id="7d1ca-123">Workaround</span></span>

1. <span data-ttu-id="7d1ca-124">Installer et exécuter Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="7d1ca-124">Install and run Internet Explorer 10</span></span>
1. <span data-ttu-id="7d1ca-125">Remplacez le paramètre Internet Explorer **Mode de document** par *Normes Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="7d1ca-126">Appuyez sur **F12** pour ouvrir la console Outils de développement.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="7d1ca-127">Dans Internet Explorer 10, cliquez sur **Mode navigateur**, puis sélectionnez *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="7d1ca-128">Cliquez sur **Mode de document**, puis sur *Normes Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="7d1ca-129">Appuyez de nouveau sur **F12** pour fermer la console Outils de développement.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="7d1ca-130">Désactivez la configuration automatique du proxy dans Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="7d1ca-131">Cliquez sur **Outils**, puis sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="7d1ca-132">Dans la boîte de dialogue **Options Internet**, sous l’onglet **Connexions**, cliquez sur **Paramètres réseau**.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="7d1ca-133">Décochez la case **Détecter automatiquement les paramètres de connexion**.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="7d1ca-134">Cliquez sur **OK**, puis de nouveau sur **OK** pour fermer la boîte de dialogue *Options Internet*.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="7d1ca-135">Impossible de se connecter à un ordinateur de groupe de travail distant</span><span class="sxs-lookup"><span data-stu-id="7d1ca-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="7d1ca-136">Si l’ordinateur de destination est membre d’un groupe de travail, utilisez la syntaxe suivante pour fournir votre nom d’utilisateur et vous connecter à l’ordinateur : `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="7d1ca-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="7d1ca-137">Impossible de trouver les outils de gestion de serveur web (IIS) bien que le rôle ait été installé</span><span class="sxs-lookup"><span data-stu-id="7d1ca-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="7d1ca-138">Si vous avez installé Windows PowerShell Web Access à l’aide de la cmdlet `Install-WindowsFeature`, les outils de gestion ne sont pas installés, sauf si le paramètre **IncludeManagementTools** est ajouté à la cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the **IncludeManagementTools** parameter is added to the cmdlet.</span></span>

<span data-ttu-id="7d1ca-139">Pour obtenir un exemple, consultez [Pour installer Accès Web Windows PowerShell à l’aide des applets de commande Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="7d1ca-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="7d1ca-140">Vous pouvez ajouter la console du Gestionnaire des services Internet et d’autres outils de gestion IIS dont vous avez besoin en sélectionnant les outils dans une session de l’**Assistant Ajout de rôles et de fonctionnalités** qui cible le serveur de passerelle.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span> <span data-ttu-id="7d1ca-141">Vous pouvez ouvrir l’Assistant Ajout de rôles et de fonctionnalités à partir du Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="7d1ca-142">Le site web Accès Web Windows PowerShell n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="7d1ca-143">Si la Configuration de sécurité renforcée est activée dans Internet Explorer (IE ESC), vous pouvez ajouter le site web Accès Web Windows PowerShell à la liste des sites de confiance.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="7d1ca-144">Une approche moins recommandée en raison des risques de sécurité est de désactiver IE ESC.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span> <span data-ttu-id="7d1ca-145">Vous pouvez désactiver IE ESC dans la vignette Propriétés de la page Serveur local dans le Gestionnaire de serveur.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="7d1ca-146">Un échec d’autorisation s’est produit.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-146">An authorization failure occurred.</span></span> <span data-ttu-id="7d1ca-147">Vérifiez que vous êtes autorisé à vous connecter à l’ordinateur de destination.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="7d1ca-148">Le message d’erreur suivant s’affiche lors d’une tentative de connexion quand le serveur de passerelle est l’ordinateur de destination et qu’il se trouve également dans un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="7d1ca-149">Quand le serveur de passerelle est également le serveur de destination et qu’il se trouve dans un groupe de travail, spécifiez le nom d’utilisateur, le nom d’ordinateur et le nom du groupe d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span> <span data-ttu-id="7d1ca-150">N’utilisez pas de point (.) tout seul pour représenter le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="7d1ca-151">Scénarios et valeurs appropriées</span><span class="sxs-lookup"><span data-stu-id="7d1ca-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="7d1ca-152">Tous les cas</span><span class="sxs-lookup"><span data-stu-id="7d1ca-152">All cases</span></span>

  <span data-ttu-id="7d1ca-153">Paramètre</span><span class="sxs-lookup"><span data-stu-id="7d1ca-153">Parameter</span></span>   |                                        <span data-ttu-id="7d1ca-154">Valeur</span><span class="sxs-lookup"><span data-stu-id="7d1ca-154">Value</span></span>
------------- | -----------------------------------------------------------------------------------
<span data-ttu-id="7d1ca-155">UserName</span><span class="sxs-lookup"><span data-stu-id="7d1ca-155">UserName</span></span>      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
<span data-ttu-id="7d1ca-156">UserGroup</span><span class="sxs-lookup"><span data-stu-id="7d1ca-156">UserGroup</span></span>     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
<span data-ttu-id="7d1ca-157">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="7d1ca-157">ComputerGroup</span></span> | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="7d1ca-158">Serveur de passerelle dans un domaine</span><span class="sxs-lookup"><span data-stu-id="7d1ca-158">Gateway server is in a domain</span></span>

 <span data-ttu-id="7d1ca-159">Paramètre</span><span class="sxs-lookup"><span data-stu-id="7d1ca-159">Parameter</span></span>   |                        <span data-ttu-id="7d1ca-160">Valeur</span><span class="sxs-lookup"><span data-stu-id="7d1ca-160">Value</span></span>
------------ | ----------------------------------------------------
<span data-ttu-id="7d1ca-161">ComputerName</span><span class="sxs-lookup"><span data-stu-id="7d1ca-161">ComputerName</span></span> | <span data-ttu-id="7d1ca-162">Nom complet du serveur de passerelle ou Localhost</span><span class="sxs-lookup"><span data-stu-id="7d1ca-162">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="7d1ca-163">Serveur de passerelle dans un groupe de travail</span><span class="sxs-lookup"><span data-stu-id="7d1ca-163">Gateway server is in a workgroup</span></span>

 <span data-ttu-id="7d1ca-164">Paramètre</span><span class="sxs-lookup"><span data-stu-id="7d1ca-164">Parameter</span></span>   |    <span data-ttu-id="7d1ca-165">Valeur</span><span class="sxs-lookup"><span data-stu-id="7d1ca-165">Value</span></span>
------------ | -----------
<span data-ttu-id="7d1ca-166">ComputerName</span><span class="sxs-lookup"><span data-stu-id="7d1ca-166">ComputerName</span></span> | <span data-ttu-id="7d1ca-167">Nom du serveur</span><span class="sxs-lookup"><span data-stu-id="7d1ca-167">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="7d1ca-168">Informations d’identification de la passerelle</span><span class="sxs-lookup"><span data-stu-id="7d1ca-168">Gateway credentials</span></span>

<span data-ttu-id="7d1ca-169">Connectez-vous à un serveur de passerelle en tant qu’ordinateur cible à l’aide d’informations d’identification formatées de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-169">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="7d1ca-170">Un identificateur de sécurité (SID) est affiché dans une règle d’autorisation</span><span class="sxs-lookup"><span data-stu-id="7d1ca-170">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="7d1ca-171">Un identificateur de sécurité (SID) est affiché dans une règle d’autorisation au lieu de la syntaxe `user_name/computer_name`.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-171">A security identifier (SID) is displayed in an authorization rule instead of the syntax `user_name/computer_name`.</span></span>

<span data-ttu-id="7d1ca-172">Soit la règle n’est plus valide, soit la requête des services de domaine Active Directory a échoué.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-172">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="7d1ca-173">Une règle d’autorisation n’est généralement pas valide dans les scénarios où le serveur de passerelle était à un moment donné dans un groupe de travail, puis a par la suite joint un domaine.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-173">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="7d1ca-174">Impossible de se connecter avec la règle en tant qu’adresse IPv6 avec un domaine</span><span class="sxs-lookup"><span data-stu-id="7d1ca-174">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="7d1ca-175">Impossible de se connecter à un ordinateur cible spécifié dans des règles d’autorisation sous forme d’adresse IPv6 avec un domaine.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-175">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="7d1ca-176">Les règles d’autorisation ne prennent pas en charge une adresse IPv6 sous forme de nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-176">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="7d1ca-177">Pour spécifier un ordinateur de destination à l’aide d’une adresse IPv6, utilisez l’adresse IPv6 d’origine (qui contient des deux-points) dans la règle d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-177">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="7d1ca-178">Les adresses IPv6 de domaine et numériques (avec des signes deux-points) sont prises en charge en tant que nom d’ordinateur cible dans la page de connexion à Accès Web Windows PowerShell, mais pas dans les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="7d1ca-178">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="7d1ca-179">Pour plus d’informations sur les adresses IPv6, consultez [Fonctionnement d’IPv6](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="7d1ca-179">For more information about IPv6 addresses, see [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d1ca-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d1ca-180">See Also</span></span>

- <span data-ttu-id="7d1ca-181">[Règles d’autorisation et fonctionnalités de sécurité d’Accès Web Windows PowerShell](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="7d1ca-181">[Authorization Rules and Security Features of Windows PowerShell Web Access](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))</span></span>
- <span data-ttu-id="7d1ca-182">[Utiliser la console web Windows PowerShell](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="7d1ca-182">[Use the Web-based Windows PowerShell Console](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))</span></span>
- [<span data-ttu-id="7d1ca-183">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="7d1ca-183">about_Remote_Requirements</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
