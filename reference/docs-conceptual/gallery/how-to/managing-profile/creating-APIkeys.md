---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,applet de commande,psgallery
title: Gestion des clés API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328290"
---
# <a name="managing-api-keys"></a><span data-ttu-id="9cf6b-103">Gestion des clés API</span><span class="sxs-lookup"><span data-stu-id="9cf6b-103">Managing API keys</span></span>

<span data-ttu-id="9cf6b-104">PowerShell Gallery permet la création de plusieurs clés API de façon à prendre en charge diverses contraintes de publication.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="9cf6b-105">Une clé API peut s’appliquer à un ou plusieurs packages, accorde des privilèges spécifiques et présente une date d’expiration.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9cf6b-106">Les utilisateurs qui ont publié dans PowerShell Gallery avant l’introduction des clés API étendues ont une « clé API d’accès total ».</span><span class="sxs-lookup"><span data-stu-id="9cf6b-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="9cf6b-107">Les clés d’accès total n’intègrent pas les améliorations de sécurité inhérentes aux clés API étendues.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="9cf6b-108">Les clés d’accès total n’expirent jamais et s’appliquent à tous les éléments qui appartiennent à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="9cf6b-109">Si vous supprimez cette clé, elle ne peut pas être recréée.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="9cf6b-110">L’illustration suivante montre les options disponibles pendant la création d’une clé API étendue.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-110">The following image shows the options available when creating a scoped API key.</span></span>

![Création de clés API](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="9cf6b-112">Dans cet exemple, nous avons créé une clé API nommée **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="9cf6b-113">La valeur de cette clé peut être utilisée pour envoyer (push) des packages avec des noms qui commencent par « AzureRM.DataFactory » et qui sont valides pendant 365 jours.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="9cf6b-114">Il s’agit d’un scénario classique quand différentes équipes au sein d’une même entreprise travaillent sur différents packages.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="9cf6b-115">Les membres d’une équipe disposent d’une clé qui leur accorde des privilèges pour le package sur lequel ils travaillent.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="9cf6b-116">La valeur d’expiration évite que des clés obsolètes ou oubliées soient utilisées.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="9cf6b-117">Utilisation de modèles Glob</span><span class="sxs-lookup"><span data-stu-id="9cf6b-117">Using glob patterns</span></span>

<span data-ttu-id="9cf6b-118">Si vous travaillez sur plusieurs packages, vous pouvez utiliser des modèles Glob pour établir des correspondances avec eux en tant que groupe.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="9cf6b-119">Les autorisations d’une clé API s’appliquent à tous les nouveaux packages présentant une correspondance avec le modèle Glob.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="9cf6b-120">Ainsi, dans l’exemple précédent, le **modèle Glob** a la valeur « AzureRM.DataFactory\* ».</span><span class="sxs-lookup"><span data-stu-id="9cf6b-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="9cf6b-121">Vous pouvez envoyer (push) un package nommé « AzureRm.DataFactoryV2.Netcore » en utilisant cette clé dans la mesure où le package correspond au modèle Glob.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="9cf6b-122">Créer des clés API en toute sécurité</span><span class="sxs-lookup"><span data-stu-id="9cf6b-122">Create API keys securely</span></span>

<span data-ttu-id="9cf6b-123">Par mesure de sécurité, une valeur de clé qui vient d’être créée n’est jamais affichée à l’écran et n’est accessible qu’à partir du bouton Copier, comme illustré ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Obtention de la nouvelle valeur de clé API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="9cf6b-125">Vous ne pouvez copier la valeur d’une clé API que de suite après l’avoir créée ou actualisée.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="9cf6b-126">Elle ne s’affiche pas et n’est plus accessible une fois que la page a été actualisée.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="9cf6b-127">Si vous perdez la valeur de la clé, vous devez cliquer sur Regénérer et copier la clé une fois qu’elle a été regénérée.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="9cf6b-128">Autorisations et expiration des clés</span><span class="sxs-lookup"><span data-stu-id="9cf6b-128">Key permissions and expiration</span></span>

<span data-ttu-id="9cf6b-129">Les clés API étendues peuvent attribuer l’une des autorisations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9cf6b-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="9cf6b-130">Envoi (push) de nouveaux packages</span><span class="sxs-lookup"><span data-stu-id="9cf6b-130">Push new packages</span></span>
- <span data-ttu-id="9cf6b-131">Envoi (push) de nouveaux packages ou de packages de mises à jour</span><span class="sxs-lookup"><span data-stu-id="9cf6b-131">Push new or update packages</span></span>
- <span data-ttu-id="9cf6b-132">Retrait de packages de la liste</span><span class="sxs-lookup"><span data-stu-id="9cf6b-132">Unlist packages</span></span>

<span data-ttu-id="9cf6b-133">Chaque nouvelle clé est assortie d’un délai d’expiration.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-133">Every new key has an expiration.</span></span> <span data-ttu-id="9cf6b-134">La valeur du délai d’expiration est exprimée en jours.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-134">The expiration value is measured in days.</span></span> <span data-ttu-id="9cf6b-135">Les valeurs possibles du délai d’expiration sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9cf6b-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="9cf6b-136">1 jour</span><span class="sxs-lookup"><span data-stu-id="9cf6b-136">1 day</span></span>
- <span data-ttu-id="9cf6b-137">90 jours</span><span class="sxs-lookup"><span data-stu-id="9cf6b-137">90 days</span></span>
- <span data-ttu-id="9cf6b-138">180 jours</span><span class="sxs-lookup"><span data-stu-id="9cf6b-138">180 days</span></span>
- <span data-ttu-id="9cf6b-139">270 jours</span><span class="sxs-lookup"><span data-stu-id="9cf6b-139">270 days</span></span>
- <span data-ttu-id="9cf6b-140">365 jours (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="9cf6b-140">365 days (default)</span></span>

<span data-ttu-id="9cf6b-141">Ces paramètres ne peuvent pas être modifiés une fois que la clé est créée.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="9cf6b-142">Vous ne pouvez pas créer une clé qui n’expire jamais.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="9cf6b-143">Modification et suppression de clés API existantes</span><span class="sxs-lookup"><span data-stu-id="9cf6b-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="9cf6b-144">Vous pouvez modifier certains paramètres d’une clé existante.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="9cf6b-145">Comme indiqué précédemment, vous ne pouvez ni modifier l’étendue de sécurité d’une clé API existante, ni modifier son délai d’expiration.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="9cf6b-146">Les options que vous pouvez modifier figurent dans la capture d’écran suivante :</span><span class="sxs-lookup"><span data-stu-id="9cf6b-146">The changeable options are shown in the following screenshot:</span></span>

![Obtention d’une nouvelle valeur de clé API](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="9cf6b-148">Pour modifier les packages contrôlés par une clé, vous pouvez choisir individuellement les packages dans la liste ou modifier le modèle Glob.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="9cf6b-149">En cliquant sur **Regénérer**, vous créez une nouvelle valeur de clé.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="9cf6b-150">Comme à l’étape initiale de création de la clé, vous devez **Copier** la valeur de la clé de suite après l’avoir mise à jour.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="9cf6b-151">L’option **Copier** n’est plus disponible une fois que vous quittez cette page.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="9cf6b-152">Quand vous cliquez sur **Supprimer**, un message de confirmation s’affiche.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="9cf6b-153">Dès lors qu’une clé est supprimée, elle ne peut plus être utilisée.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="9cf6b-154">Expiration des clés</span><span class="sxs-lookup"><span data-stu-id="9cf6b-154">Key expiration</span></span>

<span data-ttu-id="9cf6b-155">Dix jours avant la date d’expiration, PowerShell Gallery envoie un e-mail d’avertissement au titulaire du compte de la clé API.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="9cf6b-156">Une fois arrivée à expiration, la clé est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="9cf6b-157">Un message d’avertissement s’affiche en haut de la page de gestion des clés API en répertoriant les clés qui ne sont plus valides.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="9cf6b-158">Vous pouvez générer une nouvelle valeur de clé.</span><span class="sxs-lookup"><span data-stu-id="9cf6b-158">You can generate a new key value.</span></span>
