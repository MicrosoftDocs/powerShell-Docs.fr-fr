---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galerie,powershell,psgallery,RGPD
title: Conformité RGPD de PowerShell Gallery
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="8f648-103">Conformité RGPD de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="8f648-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="8f648-104">Overview</span></span>

<span data-ttu-id="8f648-105">En mai 2018, un règlement européen sur la confidentialité, le Règlement général sur la protection des données (RGPD), entre en vigueur.</span><span class="sxs-lookup"><span data-stu-id="8f648-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="8f648-106">Le RGPD impose de nouvelles règles aux entreprises, aux organismes publics, aux associations à but non lucratif et autres organisations qui proposent des biens et des services à des personnes de l’Union européenne, ou qui collectent et analysent des données relatives aux résidents de l’Union européenne.</span><span class="sxs-lookup"><span data-stu-id="8f648-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="8f648-107">Le RGPD s’applique indépendamment de l’endroit où vous vous trouvez.</span><span class="sxs-lookup"><span data-stu-id="8f648-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="8f648-108">Cet article explique comment supprimer des données personnelles à partir de PowerShell Gallery et peut être utilisé pour gérer vos obligations vis-à-vis du RGPD.</span><span class="sxs-lookup"><span data-stu-id="8f648-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="8f648-109">Si vous recherchez des informations générales sur le RGPD, consultez la [section RGPD du portail Service Trust](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="8f648-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="8f648-110">Données personnelles identifiables</span><span class="sxs-lookup"><span data-stu-id="8f648-110">Personally identifiable data</span></span>

<span data-ttu-id="8f648-111">PowerShell Gallery stocke les informations suivantes, susceptibles de provenir d’utilisateurs et donc de contenir des données personnelles :</span><span class="sxs-lookup"><span data-stu-id="8f648-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="8f648-112">Compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="8f648-113">Éléments publiés sur PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="8f648-114">Correspondance par e-mail avec l’équipe PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="8f648-115">La plupart des utilisateurs ne créent pas de compte PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="8f648-116">Un compte n’est pas obligatoire, sauf si vous vous apprêtez à publier un élément ou à utiliser la fonctionnalité « Contactez le propriétaire » dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="8f648-117">À part la correspondance par e-mail à l’initiative de l’utilisateur, PowerShell Gallery ne stocke pas de données personnelles identifiables pour les utilisateurs qui n’ont pas créé de compte.</span><span class="sxs-lookup"><span data-stu-id="8f648-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="8f648-118">Les utilisateurs qui créent un compte PowerShell Gallery peuvent publier des éléments sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="8f648-119">Ces éléments sont supposés être du code PowerShell, mais ils peuvent contenir d’autres informations, notamment des informations personnelles.</span><span class="sxs-lookup"><span data-stu-id="8f648-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="8f648-120">Les informations ci-dessous indiquent comment obtenir tous les éléments que vous avez publiés sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="8f648-121">Exportation DSR des données PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="8f648-122">Les sections suivantes décrivent comment PowerShell Gallery prend en charge les demandes DSR (Data Subject Request), en expliquant comment exporter des informations stockées dans PowerShell Gallery et comment demander la suppression de ces informations.</span><span class="sxs-lookup"><span data-stu-id="8f648-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="8f648-123">Courrier électronique</span><span class="sxs-lookup"><span data-stu-id="8f648-123">Email</span></span>

<span data-ttu-id="8f648-124">La correspondance par e-mail peut inclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8f648-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="8f648-125">E-mail envoyé aux propriétaires d’éléments de PowerShell Gallery si les examens d’analyse du code ont détecté un problème avec un élément qu’ils ont publié sur PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="8f648-126">E-mail envoyé par quelqu’un à l’équipe PowerShell Gallery en utilisant l’adresse e-mail de la page « Contactez-nous » (cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="8f648-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="8f648-127">Utilisateurs inscrits qui utilisent la fonctionnalité « Contactez le propriétaire » de PowerShell Gallery pour envoyer un e-mail au propriétaire d’un élément de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="8f648-128">Les e-mails envoyés par ou à PowerShell Gallery suivent une politique de conservation de 90 jours, ce qui permet d’effectuer d’éventuelles investigations sur la sécurité si du code malveillant devait être découvert dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="8f648-129">Conformément à cette politique, les e-mails sont supprimés après 90 jours.</span><span class="sxs-lookup"><span data-stu-id="8f648-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="8f648-130">Vous pouvez demander des copies de tous les e-mails envoyés à ou depuis votre adresse e-mail et PowerShell Gallery au cours des 90 jours qui ont précédé.</span><span class="sxs-lookup"><span data-stu-id="8f648-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="8f648-131">Pour demander cette correspondance, envoyez un e-mail à cgadmin@microsoft.com, avec le titre : « Demande DSR des e-mails relatifs à ce compte ».</span><span class="sxs-lookup"><span data-stu-id="8f648-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="8f648-132">Dans le corps du message, indiquez quelles informations vous demandez (par exemple : « Merci d’envoyer tous les e-mails envoyés ou reçus à cette adresse e-mail. »). Tous les e-mails impliquant votre adresse e-mail dans les 90 jours de la demande seront envoyés dans un délai de 7 jours ouvrés.</span><span class="sxs-lookup"><span data-stu-id="8f648-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="8f648-133">Informations du compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="8f648-134">Si vous avez créé un compte PowerShell Gallery, vous pouvez trouver toutes les informations personnelles qui ont été stockées dans PowerShell Gallery en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f648-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="8f648-135">Connectez-vous à PowerShell Gallery, puis cliquez sur votre nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8f648-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="8f648-136">La page qui s’affiche est la page Compte, qui montre l’adresse e-mail utilisée pour le compte PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="8f648-137">Si vous avez créé plusieurs comptes dans PowerShell Gallery, vous devez répéter ces étapes pour chaque compte.</span><span class="sxs-lookup"><span data-stu-id="8f648-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="8f648-138">Éléments dans PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="8f648-139">Pour faciliter l’exportation des éléments publiés sur PowerShell Gallery, nous avons publié le script « GetPSGalleryItemsForAuthor » sur PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="8f648-140">Ce script exporte une copie de chaque version de chaque élément placé dans PowerShell Gallery ; il est basé sur les informations relatives à l’auteur qui sont stockées dans l’élément.</span><span class="sxs-lookup"><span data-stu-id="8f648-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="8f648-141">L’auteur est stocké dans le manifeste de l’élément quand vous publiez votre élément.</span><span class="sxs-lookup"><span data-stu-id="8f648-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="8f648-142">Il n’est pas garanti que l’auteur représente la même identité que le compte que vous utilisez dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8f648-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="8f648-143">Si vous utilisez une autre valeur dans le champ Auteur, vous devez fournir cette valeur lors de l’utilisation de ce script.</span><span class="sxs-lookup"><span data-stu-id="8f648-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="8f648-144">Vous pouvez télécharger le script avec la commande PowerShell suivante :</span><span class="sxs-lookup"><span data-stu-id="8f648-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="8f648-145">Vous pouvez ensuite exécuter le script avec les commandes PowerShell suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f648-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="8f648-146">Vous serez invité à spécifier l’auteur et un dossier sur votre système où les éléments doivent être enregistrés.</span><span class="sxs-lookup"><span data-stu-id="8f648-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="8f648-147">Suppression des données personnelles de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="8f648-148">Pour supprimer votre compte PowerShell Gallery ou tout élément dont vous êtes propriétaire dans PowerShell Gallery, envoyez un e-mail à cgadmin@microsoft.com avec le titre : « Demande RGPD pour des éléments relatifs à ce compte ».</span><span class="sxs-lookup"><span data-stu-id="8f648-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="8f648-149">Dans le corps du message, indiquez les informations que vous voulez faire supprimer.</span><span class="sxs-lookup"><span data-stu-id="8f648-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="8f648-150">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8f648-150">For example:</span></span>

* <span data-ttu-id="8f648-151">Veuillez supprimer la version x.y.z de mon élément « nom de l’élément »</span><span class="sxs-lookup"><span data-stu-id="8f648-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="8f648-152">Veuillez supprimer toutes les versions de mon élément « nom de l’élément »</span><span class="sxs-lookup"><span data-stu-id="8f648-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="8f648-153">Veuillez supprimer mon compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="8f648-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="8f648-154">Les administrateurs de PowerShell Gallery répondent dans un délai de 7 jours ouvrés.</span><span class="sxs-lookup"><span data-stu-id="8f648-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="8f648-155">Les éléments spécifiés sont supprimés dans les 30 jours suivant l’envoi de la demande.</span><span class="sxs-lookup"><span data-stu-id="8f648-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
