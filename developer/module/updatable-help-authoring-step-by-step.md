---
title: 'Création d’une aide actualisable : Pas à pas | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860315"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="6cf59-102">Création d’une aide actualisable : procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="6cf59-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="6cf59-103">Ce documents répertorie les étapes du processus de création de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="6cf59-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="6cf59-104">Création d’aide actualisable : procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="6cf59-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="6cf59-105">Aide actualisable est conçu pour les utilisateurs finaux, mais il fournit également des avantages significatifs pour les auteurs de modules et les writers d’aide, y compris la possibilité d’ajouter du contenu, de corriger les erreurs, d’offrir dans plusieurs cultures d’interface utilisateur et de répondent aux commentaires des utilisateurs et des demandes, délai après le module a été expédiée.</span><span class="sxs-lookup"><span data-stu-id="6cf59-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="6cf59-106">Cette rubrique explique comment vous en package et les fichiers d’aide de téléchargement afin que les utilisateurs peuvent télécharger et les installer à l’aide de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applets de commande.</span><span class="sxs-lookup"><span data-stu-id="6cf59-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="6cf59-107">Les étapes suivantes fournissent une vue d’ensemble du processus de prise en charge de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="6cf59-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="6cf59-108">Étape 1 : Trouver un site Internet pour vos fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="6cf59-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="6cf59-109">La première étape de création d’aide actualisable consiste à trouver un emplacement Internet pour les fichiers d’aide de votre module.</span><span class="sxs-lookup"><span data-stu-id="6cf59-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="6cf59-110">En fait, vous pouvez utiliser deux emplacements différents.</span><span class="sxs-lookup"><span data-stu-id="6cf59-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="6cf59-111">Vous pouvez conserver le fichier d’informations de votre module aide (HelpInfo XML - décrits ci-dessous) à un emplacement Internet et les fichiers CAB contenus d’aide à un autre emplacement Internet.</span><span class="sxs-lookup"><span data-stu-id="6cf59-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="6cf59-112">Aide de tous les fichiers CAB en contenu pour un module doivent être dans le même emplacement.</span><span class="sxs-lookup"><span data-stu-id="6cf59-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="6cf59-113">Vous pouvez placer des fichiers CAB contenus d’aide pour les différents modules dans le même emplacement.</span><span class="sxs-lookup"><span data-stu-id="6cf59-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="6cf59-114">Étape 2 : Ajouter une clé HelpInfoURI dans le manifeste de module</span><span class="sxs-lookup"><span data-stu-id="6cf59-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="6cf59-115">Ajouter un **HelpInfoURI** clés dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="6cf59-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="6cf59-116">La valeur de la clé est l’identificateur URI (Uniform Resource) de l’emplacement du fichier d’informations HelpInfo XML pour votre module.</span><span class="sxs-lookup"><span data-stu-id="6cf59-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="6cf59-117">Pour la sécurité, l’adresse doit commencer par « http » ou « https ».</span><span class="sxs-lookup"><span data-stu-id="6cf59-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="6cf59-118">L’URI doit spécifier un emplacement Internet, mais ne doit pas inclure le nom de fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6cf59-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="6cf59-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6cf59-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="6cf59-120">Étape 3 : Créez un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="6cf59-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="6cf59-121">Le fichier d’informations HelpInfo XML contient l’URI de l’emplacement Internet de vos fichiers d’aide et les numéros de version les plus récente des fichiers d’aide pour votre module dans chaque culture d’interface utilisateur pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6cf59-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="6cf59-122">Chaque module Windows PowerShell a un fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6cf59-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="6cf59-123">Lorsque vous mettez à jour vos fichiers d’aide, modifier ou de remplacer le fichier XML HelpInfo ; vous n’ajoutez pas d’un autre.</span><span class="sxs-lookup"><span data-stu-id="6cf59-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="6cf59-124">Pour plus d’informations, consultez [comment créer un fichier XML de HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="6cf59-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="6cf59-125">Étape 4 : Se connecter à vos fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="6cf59-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="6cf59-126">Signatures numériques ne sont pas nécessaires, mais ils sont une recommandation de meilleures pratiques, chaque fois que vous partagez des fichiers.</span><span class="sxs-lookup"><span data-stu-id="6cf59-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="6cf59-127">Étape 5 : Créer des fichiers CAB</span><span class="sxs-lookup"><span data-stu-id="6cf59-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="6cf59-128">Utiliser un outil qui crée des fichiers CAB (.cab), telles que MakeCab.exe, pour créer un. Fichier CAB qui contient les fichiers d’aide pour votre module.</span><span class="sxs-lookup"><span data-stu-id="6cf59-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="6cf59-129">Créer un fichier CAB distinct pour les fichiers d’aide dans chaque culture d’interface utilisateur pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6cf59-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="6cf59-130">Pour plus d’informations, consultez [comment préparer actualisable CAB fichiers d’aide](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="6cf59-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="6cf59-131">Étape 6 : Charger vos fichiers</span><span class="sxs-lookup"><span data-stu-id="6cf59-131">Step 6: Upload your files</span></span>

<span data-ttu-id="6cf59-132">Pour publier des fichiers d’aide nouveaux ou mis à jour, télécharger les fichiers CAB à l’emplacement Internet spécifié par le **HelpContentUri** élément dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6cf59-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="6cf59-133">Ensuite, chargez le fichier XML HelpInfo à l’emplacement Internet spécifié par la valeur de la **HelpInfoUri** clés dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="6cf59-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
