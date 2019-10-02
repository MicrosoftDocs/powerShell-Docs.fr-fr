---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Paramètres de compte PowerShell Gallery
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328030"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="f1210-103">Paramètres de compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f1210-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="f1210-104">Votre compte PowerShell Gallery est un nom visible publiquement qui est lié à une identité.</span><span class="sxs-lookup"><span data-stu-id="f1210-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="f1210-105">Cette identité est soit un ID Microsoft, comme `user@hotmail.com` ou `user@outlook.com`, soit un compte Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="f1210-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="f1210-106">PowerShell Gallery présente les paramètres de compte suivants :</span><span class="sxs-lookup"><span data-stu-id="f1210-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="f1210-107">Le compte de messagerie associé à votre compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f1210-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="f1210-108">Les options de notifications par e-mail envoyées à partir de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f1210-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="f1210-109">Le compte d’utilisateur associé à votre compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f1210-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="f1210-110">L’image associée à votre compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f1210-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="f1210-111">Adresse de messagerie</span><span class="sxs-lookup"><span data-stu-id="f1210-111">Email address</span></span>

<span data-ttu-id="f1210-112">L’adresse e-mail est la destination des notifications de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f1210-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="f1210-113">Elle ne doit pas nécessairement correspondre au compte de connexion.</span><span class="sxs-lookup"><span data-stu-id="f1210-113">It does not have to match the login account.</span></span> <span data-ttu-id="f1210-114">Vous pouvez utiliser n’importe quel compte de messagerie auquel vous avez accès.</span><span class="sxs-lookup"><span data-stu-id="f1210-114">You may use any email account you have access to.</span></span> <span data-ttu-id="f1210-115">PowerShell Gallery ne communique jamais directement votre adresse e-mail à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f1210-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Changement d’adresse e-mail](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="f1210-117">Quand vous entrez une nouvelle adresse e-mail, PowerShell Gallery envoie un message de vérification à cette adresse.</span><span class="sxs-lookup"><span data-stu-id="f1210-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="f1210-118">Ce message contient un lien vers PowerShell Gallery pour terminer le processus de modification.</span><span class="sxs-lookup"><span data-stu-id="f1210-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="f1210-119">Tant que le processus de vérification n’est pas terminé, toutes les notifications sont envoyées à l’adresse précédente.</span><span class="sxs-lookup"><span data-stu-id="f1210-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="f1210-120">Notifications par e-mail</span><span class="sxs-lookup"><span data-stu-id="f1210-120">Email notifications</span></span>

<span data-ttu-id="f1210-121">PowerShell Gallery propose les options de notification suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1210-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="f1210-122">Les utilisateurs peuvent me contacter via PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f1210-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="f1210-123">M’avertir quand un package est envoyé (push) sur PowerShell Gallery avec mon compte</span><span class="sxs-lookup"><span data-stu-id="f1210-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![Changement d’adresse e-mail](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="f1210-125">Comme indiqué dans la page, les notifications critiques de PowerShell Gallery ne peuvent pas être désactivées.</span><span class="sxs-lookup"><span data-stu-id="f1210-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="f1210-126">Ces paramètres sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="f1210-126">These include:</span></span>

- <span data-ttu-id="f1210-127">Notifications de sécurité</span><span class="sxs-lookup"><span data-stu-id="f1210-127">Security notifications</span></span>
- <span data-ttu-id="f1210-128">Notifications de gestion de compte des administrateurs PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f1210-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="f1210-129">Notifications sur les tests exécutés par PowerShell Gallery pour vos soumissions</span><span class="sxs-lookup"><span data-stu-id="f1210-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="f1210-130">Modifier votre compte de connexion</span><span class="sxs-lookup"><span data-stu-id="f1210-130">Change your login account</span></span>

<span data-ttu-id="f1210-131">Pour modifier le compte de connexion, vous devez être connecté avec le compte actif.</span><span class="sxs-lookup"><span data-stu-id="f1210-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="f1210-132">Effectuez les étapes suivantes pour effectuer la modification.</span><span class="sxs-lookup"><span data-stu-id="f1210-132">Use the following steps to complete the change.</span></span>

![Paramètres de compte de connexion](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="f1210-134">Cliquez sur **Changer de compte**.</span><span class="sxs-lookup"><span data-stu-id="f1210-134">Click on **Change Account**.</span></span> <span data-ttu-id="f1210-135">Une fenêtre contextuelle explique que la modification du compte de connexion s’applique à toutes les utilisations de ce compte dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f1210-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="f1210-136">Vérifiez les informations, puis cliquez sur **OK** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="f1210-136">Review the information, then click **OK** to continue.</span></span>

   ![Paramètres de compte de connexion](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="f1210-138">Vous êtes ensuite invité à vous connecter en utilisant le _nouveau compte_.</span><span class="sxs-lookup"><span data-stu-id="f1210-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Paramètres de compte de connexion](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="f1210-140">Quand vous cliquez sur **Suivant**, un message s’affiche pour vous indiquer que vous êtes connecté avec le compte actif.</span><span class="sxs-lookup"><span data-stu-id="f1210-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="f1210-141">Cliquez sur **Se déconnecter et se connecter avec un autre compte**.</span><span class="sxs-lookup"><span data-stu-id="f1210-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Paramètres de compte de connexion](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="f1210-143">Entrez le mot de passe du nouveau compte.</span><span class="sxs-lookup"><span data-stu-id="f1210-143">Enter the password of the new account.</span></span> <span data-ttu-id="f1210-144">Après avoir entré le mot de passe, la page Paramètres du compte s’affiche à nouveau et vous indique que le compte de connexion a été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="f1210-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="f1210-145">Activer l’authentification à 2 facteurs (2FA)</span><span class="sxs-lookup"><span data-stu-id="f1210-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="f1210-146">L’authentification à deux facteurs est recommandée pour tous les utilisateurs qui publient manuellement dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f1210-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="f1210-147">Pour activer l’authentification à deux facteurs, au moins deux formes d’authentification doivent être inscrites pour le compte de connexion.</span><span class="sxs-lookup"><span data-stu-id="f1210-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="f1210-148">La première doit être un mot de passe et les autres l’une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f1210-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="f1210-149">Un numéro de téléphone pouvant recevoir des SMS</span><span class="sxs-lookup"><span data-stu-id="f1210-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="f1210-150">Une application d’authentification agréée, comme Microsoft Authenticator, pour votre téléphone mobile</span><span class="sxs-lookup"><span data-stu-id="f1210-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="f1210-151">Ces formes d’authentification doivent être configurées dans les informations de votre compte AAD ou dans les paramètres de sécurité de votre compte ID Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f1210-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="f1210-152">Une fois que l’authentification 2FA est activée, vous devez vous authentifier en utilisant les formes d’authentification configurées chaque fois que vous vous connectez à PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="f1210-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1210-153">Le fait d’activer l’authentification à deux facteurs pour le site PowerShell Gallery ne vous oblige pas à activer 2FA pour toutes les utilisations de votre compte de connexion.</span><span class="sxs-lookup"><span data-stu-id="f1210-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="f1210-154">Pour plus d’informations, consultez [À propos de la vérification en deux étapes](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="f1210-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="f1210-155">Changer votre image de profil</span><span class="sxs-lookup"><span data-stu-id="f1210-155">Change your profile picture</span></span>

<span data-ttu-id="f1210-156">PowerShell Gallery utilise Gravatar pour stocker et afficher l’image associée à votre profil.</span><span class="sxs-lookup"><span data-stu-id="f1210-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="f1210-157">Pour mettre à jour votre image de profil, accédez à [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="f1210-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
