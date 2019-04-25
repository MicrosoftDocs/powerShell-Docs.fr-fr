---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Création d’un compte PowerShell Gallery
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084202"
---
# <a name="creating-a-powershell-gallery-account"></a>Création d’un compte PowerShell Gallery

Vous devez créer un compte PowerShell Gallery avant de publier quoi que ce soit dans PowerShell Gallery.
Les comptes PowerShell Gallery doivent être liés à un compte de connexion à extension messagerie. Ce compte peut être un compte Azure Active Directory ou un ID Microsoft, comme un compte de messagerie outlook.com ou hotmail.com.

Pour créer un compte PowerShell Gallery, accédez à [https://PowerShellGallery.com](https://PowerShellGallery.com) et cliquez sur **Se connecter** (voir l’illustration suivante).

![Créer un nouveau compte](../../Images/CreateAccount-Register.png)

Pour utiliser un compte Azure Active Directory, sélectionnez **Compte professionnel ou scolaire**, puis connectez-vous avec votre compte. Pour utiliser un ID Microsoft, choisissez **Compte personnel** et connectez-vous.

Vous êtes ensuite invité à créer un nom d’utilisateur pour PowerShell Gallery. Examinez les conditions d’utilisation et la politique de confidentialité, entrez un nom d’utilisateur, puis cliquez sur **S’inscrire**.

> [!NOTE]
> Le nom de compte ne peut pas être modifié une fois qu’il est créé. Pour plus d’informations, voir [Gérer les propriétaires de packages](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Pratiques recommandées pour les comptes PowerShell Gallery

Il est important de superviser activement le compte de messagerie utilisé avec votre compte PowerShell Gallery. Toutes les communications avec les propriétaires de packages PowerShell Gallery se font par cette adresse e-mail. Si l’équipe chargée des opérations PowerShell Gallery ne parvient pas à contacter le propriétaire d’un package, nous serons peut-être contraints de supprimer le package.

Les organisations qui publient dans PowerShell Gallery créent souvent un compte externe unique à cet effet. Nous vous recommandons d’utiliser la fonctionnalité de transfert de courrier pour transférer les notifications à une adresse au sein de votre organisation.

Quand plusieurs propriétaires sont associés à un package, toutes les notifications PowerShell Gallery sont envoyées à l’ensemble des propriétaires. Pour plus d’informations, voir [Gérer les propriétaires de packages](managing-package-owners.md).
