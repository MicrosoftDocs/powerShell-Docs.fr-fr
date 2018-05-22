---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Création d’un compte PowerShell Gallery
ms.openlocfilehash: 4a44b51967ea8acdd331f6b3c682fc5884bd2f54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
## <a name="creating-a-powershell-gallery-account"></a>Création d’un compte PowerShell Gallery

Un compte PowerShell Gallery doit être créé avant de publier quoi que ce soit dessus.
Les comptes PowerShell Gallery doivent être liés à un compte de messagerie compatible Azure Active Directory ou un compte de messagerie Microsoft (avec un domaine outlook.com, hotmail.com, etc.)

Pour créer un compte PowerShell Gallery, accédez à https://PowerShellGallery.com et cliquez sur « S’inscrire » (voir l’image ci-dessous).

![Créer un nouveau compte](../../Images/CreatingAccount-Register.png)

Sur la page suivante, sélectionnez « Compte professionnel ou scolaire » pour utiliser un compte Azure Active Directory et connectez-vous avec votre compte.
Pour utiliser un compte Microsoft, par exemple avec un domaine Hotmail.com ou Outlook.com, choisissez « Compte personnel », puis connectez-vous.

Une fois que vous êtes connecté, il vous est demandé de créer un nom d’utilisateur pour PowerShell Gallery.
Passez en revue les liens des conditions d’utilisation et de la politique de confidentialité, saisissez un nom d’utilisateur, puis cliquez sur S’inscrire.

Remarque : Ce nom de compte ne peut pas être modifié une fois qu’il est créé.
Consultez [Gestion des propriétaires d’éléments](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) pour plus d’informations à ce sujet.

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Pratiques recommandées pour les comptes PowerShell Gallery

Il est important que le compte de messagerie utilisé avec votre compte PowerShell Gallery soit surveillé activement.
Toutes les communications avec les propriétaires des éléments PowerShell Gallery passent par l’adresse de messagerie associée à votre compte PowerShell Gallery.
Si nous ne pouvons pas contacter un propriétaire d’élément, il peut être demandé à l’équipe des opérations de supprimer un élément dans certaines circonstances.

Les organisations qui publient sur PowerShell Gallery créent souvent un compte unique à cet effet sur Outlook.com, ou un autre domaine de compte Microsoft.
Dans de nombreux cas, ce compte n’est pas surveillé régulièrement.
Dans ce cas, il est recommandé d’utiliser le transfert d’Outlook pour envoyer un courrier électronique à une autre adresse, appartenant généralement à l’organisation, qui est surveillée par les propriétaires de l’élément.

S’il existe plusieurs propriétaires associés un élément, toutes les communications provenant de PowerShell Gallery seront transmises à tous les propriétaires.
Consultez [Gestion des propriétaires d’éléments](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) pour plus d’informations sur l’ajout de propriétaires à un élément.