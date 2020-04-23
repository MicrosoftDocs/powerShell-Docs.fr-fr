---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galerie,powershell,psgallery,RGPD
title: Conformité RGPD de PowerShell Gallery
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328320"
---
# <a name="powershell-gallery-gdpr-compliance"></a>Conformité RGPD de PowerShell Gallery

## <a name="overview"></a>Vue d’ensemble

En mai 2018, un règlement européen sur la confidentialité, le Règlement général sur la protection des données (RGPD), est entré en vigueur.
Le RGPD impose de nouvelles règles aux entreprises, aux organismes publics, aux associations à but non lucratif et autres organisations qui proposent des biens et des services à des personnes de l’Union européenne, ou qui collectent et analysent des données relatives aux résidents de l’Union européenne.
Le RGPD s’applique indépendamment de l’endroit où vous vous trouvez.

> [!NOTE]
> Cet article explique comment supprimer des données personnelles à partir de PowerShell Gallery et peut être utilisé pour gérer vos obligations vis-à-vis du RGPD. Si vous recherchez des informations générales sur le RGPD, consultez la [section RGPD du portail Service Trust](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Données personnelles identifiables

PowerShell Gallery stocke les informations suivantes, susceptibles de provenir d’utilisateurs et donc de contenir des données personnelles :

- Compte PowerShell Gallery
- Packages publiés sur PowerShell Gallery
- Correspondance par e-mail avec l’équipe PowerShell Gallery

La plupart des utilisateurs ne créent pas de compte PowerShell Gallery.
Un compte n’est pas obligatoire, sauf si vous vous apprêtez à publier un package ou à utiliser la fonctionnalité « Contactez le propriétaire » dans PowerShell Gallery.
À part la correspondance par e-mail à l’initiative de l’utilisateur, PowerShell Gallery ne stocke pas de données personnelles identifiables pour les utilisateurs qui n’ont pas créé de compte.

Les utilisateurs qui créent un compte PowerShell Gallery peuvent publier des packages sur PowerShell Gallery.
Ces packages sont supposés être du code PowerShell, mais ils peuvent contenir d’autres informations, notamment des informations personnelles.
Les informations ci-dessous indiquent comment obtenir tous les packages que vous avez publiés sur PowerShell Gallery.

## <a name="dsr-export-of-powershell-gallery-data"></a>Exportation DSR des données PowerShell Gallery

Les sections suivantes décrivent comment PowerShell Gallery prend en charge les demandes DSR (Data Subject Request), en expliquant comment exporter des informations stockées dans PowerShell Gallery et comment demander la suppression de ces informations.

### <a name="email"></a>E-mail

La correspondance par e-mail peut inclure les éléments suivants :

- E-mail envoyé aux propriétaires de packages de PowerShell Gallery si les examens d’analyse du code ont détecté un problème avec un package qu’ils ont publié sur PowerShell Gallery
- E-mail envoyé par quelqu’un à l’équipe PowerShell Gallery en utilisant l’adresse e-mail de la page « Contactez-nous » [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Utilisateurs inscrits qui utilisent la fonctionnalité « Contactez le propriétaire » de PowerShell Gallery pour envoyer un e-mail au propriétaire d’un package de PowerShell Gallery

Les e-mails envoyés par ou à PowerShell Gallery suivent une politique de conservation de 90 jours, ce qui permet d’effectuer d’éventuelles investigations sur la sécurité si du code malveillant devait être découvert dans PowerShell Gallery.
Conformément à cette politique, les e-mails sont supprimés après 90 jours.

Vous pouvez demander des copies de tous les e-mails envoyés à ou depuis votre adresse e-mail et PowerShell Gallery au cours des 90 jours qui ont précédé.
Pour demander cette correspondance, envoyez un e-mail à [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), avec le titre : « Demande DSR des e-mails relatifs à ce compte ».
Dans le corps du message, indiquez quelles informations vous demandez (par exemple : « Merci d’envoyer tous les e-mails envoyés ou reçus à cette adresse e-mail. »). Tous les e-mails impliquant votre adresse e-mail dans les 90 jours de la demande seront envoyés dans un délai de 7 jours ouvrés.

### <a name="powershell-gallery-account-information"></a>Informations du compte PowerShell Gallery

Si vous avez créé un compte PowerShell Gallery, vous pouvez trouver toutes les informations personnelles qui ont été stockées dans PowerShell Gallery en effectuant les étapes suivantes :

1. Connectez-vous à PowerShell Gallery, puis cliquez sur votre nom d’utilisateur.
2. La page qui s’affiche est la page Compte, qui montre l’adresse e-mail utilisée pour le compte PowerShell Gallery.

Si vous avez créé plusieurs comptes dans PowerShell Gallery, vous devez répéter ces étapes pour chaque compte.

### <a name="packages-in-the-powershell-gallery"></a>Packages dans PowerShell Gallery

Pour faciliter l’exportation des packages publiés sur PowerShell Gallery, nous avons publié le script « GetPSGalleryItemsForAuthor » sur PowerShell Gallery.
Ce script exporte une copie de chaque version de chaque package placé dans PowerShell Gallery ; il est basé sur les informations relatives à l’auteur qui sont stockées dans le package.

> [!NOTE]
> L’auteur est stocké dans le manifeste du package quand vous publiez votre package.
> Il n’est pas garanti que l’auteur représente la même identité que le compte que vous utilisez dans PowerShell Gallery.
> Si vous utilisez une autre valeur dans le champ Auteur, vous devez fournir cette valeur lors de l’utilisation de ce script.

Vous pouvez télécharger le script avec la commande PowerShell suivante :

```powershell
Save-Script Get-repository psgallery
```

Vous pouvez ensuite exécuter le script avec les commandes PowerShell suivantes :

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Vous serez invité à spécifier l’auteur et un dossier sur votre système où les packages doivent être enregistrés.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Suppression des données personnelles de PowerShell Gallery

Pour supprimer votre compte PowerShell Gallery ou tout package dont vous êtes propriétaire dans PowerShell Gallery, envoyez un e-mail à cgadmin@microsoft.com avec le titre : « Demande RGPD pour des éléments relatifs à ce compte ».
Dans le corps du message, indiquez les informations que vous voulez faire supprimer. Par exemple :

- Veuillez supprimer la version x.y.z de mon package « nom du package »
- Veuillez supprimer toutes les versions de mon package « nom du package »
- Veuillez supprimer mon compte PowerShell Gallery

Les administrateurs de PowerShell Gallery répondent dans un délai de 7 jours ouvrés.
Les packages spécifiés sont supprimés dans les 30 jours suivant l’envoi de la demande.
