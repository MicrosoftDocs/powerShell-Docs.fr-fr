---
ms.date: 09/11/2018
title: Création d’un compte PowerShell Gallery
description: Cet article décrit la configuration requise du compte d’utilisateur pour PowerShell Gallery
ms.openlocfilehash: 24c7531e61128415a284d1b438b43f3af0d1053a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662608"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="76a87-103">Création d’un compte PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="76a87-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="76a87-104">Vous devez créer un compte PowerShell Gallery avant de publier quoi que ce soit dans PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="76a87-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="76a87-105">Les comptes PowerShell Gallery doivent être liés à un compte de connexion à extension messagerie.</span><span class="sxs-lookup"><span data-stu-id="76a87-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="76a87-106">Ce compte peut être un compte Azure Active Directory ou un ID Microsoft, comme un compte de messagerie outlook.com ou hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="76a87-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="76a87-107">Pour créer un compte PowerShell Gallery, accédez à [https://PowerShellGallery.com](https://PowerShellGallery.com) et cliquez sur **Se connecter** (voir l’illustration suivante).</span><span class="sxs-lookup"><span data-stu-id="76a87-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Créer un nouveau compte](media/creating-an-account/CreateAccount-Register.png)

<span data-ttu-id="76a87-109">Pour utiliser un compte Azure Active Directory, sélectionnez **Compte professionnel ou scolaire** , puis connectez-vous avec votre compte.</span><span class="sxs-lookup"><span data-stu-id="76a87-109">To use an Azure Active Directory account, select **Work or School Account** , and sign in with your account.</span></span> <span data-ttu-id="76a87-110">Pour utiliser un ID Microsoft, choisissez **Compte personnel** et connectez-vous.</span><span class="sxs-lookup"><span data-stu-id="76a87-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="76a87-111">Vous êtes ensuite invité à créer un nom d’utilisateur pour PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="76a87-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="76a87-112">Examinez les conditions d’utilisation et la politique de confidentialité, entrez un nom d’utilisateur, puis cliquez sur **S’inscrire**.</span><span class="sxs-lookup"><span data-stu-id="76a87-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="76a87-113">Le nom de compte ne peut pas être modifié une fois qu’il est créé.</span><span class="sxs-lookup"><span data-stu-id="76a87-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="76a87-114">Pour plus d’informations, voir [Gérer les propriétaires de packages](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="76a87-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="76a87-115">Pratiques recommandées pour les comptes PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="76a87-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="76a87-116">Il est important de superviser activement le compte de messagerie utilisé avec votre compte PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="76a87-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="76a87-117">Toutes les communications avec les propriétaires de packages PowerShell Gallery se font par cette adresse e-mail.</span><span class="sxs-lookup"><span data-stu-id="76a87-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="76a87-118">Si l’équipe chargée des opérations PowerShell Gallery ne parvient pas à contacter le propriétaire d’un package, nous serons peut-être contraints de supprimer le package.</span><span class="sxs-lookup"><span data-stu-id="76a87-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="76a87-119">Les organisations qui publient dans PowerShell Gallery créent souvent un compte externe unique à cet effet.</span><span class="sxs-lookup"><span data-stu-id="76a87-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="76a87-120">Nous vous recommandons d’utiliser la fonctionnalité de transfert de courrier pour transférer les notifications à une adresse au sein de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="76a87-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="76a87-121">Quand plusieurs propriétaires sont associés à un package, toutes les notifications PowerShell Gallery sont envoyées à l’ensemble des propriétaires.</span><span class="sxs-lookup"><span data-stu-id="76a87-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="76a87-122">Pour plus d’informations, voir [Gérer les propriétaires de packages](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="76a87-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
