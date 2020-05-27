---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Paramètres de compte PowerShell Gallery
ms.openlocfilehash: 7f67311b42123f247a00a9c7a5bf775685b64d48
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560455"
---
# <a name="powershell-gallery-account-settings"></a>Paramètres de compte PowerShell Gallery

Votre compte PowerShell Gallery est un nom visible publiquement qui est lié à une identité. Cette identité est soit un ID Microsoft, comme `user@hotmail.com` ou `user@outlook.com`, soit un compte Azure Active Directory (AAD).

PowerShell Gallery présente les paramètres de compte suivants :

- Le compte de messagerie associé à votre compte PowerShell Gallery
- Les options de notifications par e-mail envoyées à partir de PowerShell Gallery
- Le compte d’utilisateur associé à votre compte PowerShell Gallery
- L’image associée à votre compte PowerShell Gallery

## <a name="email-address"></a>Adresse de messagerie

L’adresse e-mail est la destination des notifications de PowerShell Gallery. Elle ne doit pas nécessairement correspondre au compte de connexion. Vous pouvez utiliser n’importe quel compte de messagerie auquel vous avez accès. PowerShell Gallery ne communique jamais directement votre adresse e-mail à d’autres utilisateurs.

![Changement d’adresse e-mail](media/managing-account/PSGallery_AcccountEmailAddress.png)

Quand vous entrez une nouvelle adresse e-mail, PowerShell Gallery envoie un message de vérification à cette adresse. Ce message contient un lien vers PowerShell Gallery pour terminer le processus de modification. Tant que le processus de vérification n’est pas terminé, toutes les notifications sont envoyées à l’adresse précédente.

## <a name="email-notifications"></a>Notifications par e-mail

PowerShell Gallery propose les options de notification suivantes :

- Les utilisateurs peuvent me contacter via PowerShell Gallery
- M’avertir quand un package est envoyé (push) sur PowerShell Gallery avec mon compte

![Changement d’adresse e-mail](media/managing-account/PSGallery_AccountEmailOptions.png)

Comme indiqué dans la page, les notifications critiques de PowerShell Gallery ne peuvent pas être désactivées.
notamment :

- Notifications de sécurité
- Notifications de gestion de compte des administrateurs PowerShell Gallery
- Notifications sur les tests exécutés par PowerShell Gallery pour vos soumissions

## <a name="change-your-login-account"></a>Modifier votre compte de connexion

Pour modifier le compte de connexion, vous devez être connecté avec le compte actif. Effectuez les étapes suivantes pour effectuer la modification.

![Paramètres de compte de connexion](media/managing-account/PSGallery_LoginAccountSettings.png)

1. Cliquez sur **Changer de compte**. Une fenêtre contextuelle explique que la modification du compte de connexion s’applique à toutes les utilisations de ce compte dans PowerShell Gallery. Vérifiez les informations, puis cliquez sur **OK** pour continuer.

   ![Paramètres de compte de connexion](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. Vous êtes ensuite invité à vous connecter en utilisant le _nouveau compte_.

   ![Paramètres de compte de connexion](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. Quand vous cliquez sur **Suivant**, un message s’affiche pour vous indiquer que vous êtes connecté avec le compte actif.
   Cliquez sur **Se déconnecter et se connecter avec un autre compte**.

   ![Paramètres de compte de connexion](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. Entrez le mot de passe du nouveau compte. Après avoir entré le mot de passe, la page Paramètres du compte s’affiche à nouveau et vous indique que le compte de connexion a été mis à jour.

## <a name="enable-two-factor-authentication-2fa"></a>Activer l’authentification à 2 facteurs (2FA)

L’authentification à deux facteurs est recommandée pour tous les utilisateurs qui publient manuellement dans PowerShell Gallery. Pour activer l’authentification à deux facteurs, au moins deux formes d’authentification doivent être inscrites pour le compte de connexion. La première doit être un mot de passe et les autres l’une des formes suivantes :

- Un numéro de téléphone pouvant recevoir des SMS
- Une application d’authentification agréée, comme Microsoft Authenticator, pour votre téléphone mobile

Ces formes d’authentification doivent être configurées dans les informations de votre compte AAD ou dans les paramètres de sécurité de votre compte ID Microsoft.

Une fois que l’authentification 2FA est activée, vous devez vous authentifier en utilisant les formes d’authentification configurées chaque fois que vous vous connectez à PowerShell Gallery.

> [!IMPORTANT]
> Le fait d’activer l’authentification à deux facteurs pour le site PowerShell Gallery ne vous oblige pas à activer 2FA pour toutes les utilisations de votre compte de connexion. Pour plus d’informations, consultez [À propos de la vérification en deux étapes](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Changer votre image de profil

PowerShell Gallery utilise Gravatar pour stocker et afficher l’image associée à votre profil. Pour mettre à jour votre image de profil, accédez à [Gravatar.com](http://www.gravatar.com/).
