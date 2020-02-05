---
title: 'Création d’une aide actualisable : pas à pas | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: a5290265f3d729504983b95195c793b88c4a2613
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995987"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="78038-102">Création d’aide actualisable : pas à pas</span><span class="sxs-lookup"><span data-stu-id="78038-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="78038-103">Ce document répertorie les étapes du processus de création de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="78038-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="78038-104">Création de l’aide actualisable : pas à pas</span><span class="sxs-lookup"><span data-stu-id="78038-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="78038-105">L’aide pouvant être mise à jour est conçue pour les utilisateurs finaux, mais elle offre également des avantages significatifs pour les auteurs de modules et les créateurs d’aide, y compris la possibilité d’ajouter du contenu, de corriger des erreurs, de fournir dans plusieurs cultures d’interface utilisateur et de répondre aux commentaires et aux demandes des utilisateurs, longtemps après le module a été expédié.</span><span class="sxs-lookup"><span data-stu-id="78038-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="78038-106">Cette rubrique explique comment empaqueter et télécharger des fichiers d’aide afin que les utilisateurs puissent les télécharger et les installer à l’aide des applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="78038-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="78038-107">Les étapes suivantes fournissent une vue d’ensemble du processus de prise en charge de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="78038-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="78038-108">Étape 1 : Rechercher un site Internet pour vos fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="78038-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="78038-109">La première étape de création de l’aide actualisable consiste à rechercher un emplacement Internet pour les fichiers d’aide de votre module.</span><span class="sxs-lookup"><span data-stu-id="78038-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="78038-110">En fait, vous pouvez utiliser deux emplacements différents.</span><span class="sxs-lookup"><span data-stu-id="78038-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="78038-111">Vous pouvez conserver le fichier d’informations d’aide de votre module (HelpInfo XML-décrit ci-dessous) à un emplacement Internet et les fichiers CAB du contenu d’aide à un autre emplacement Internet.</span><span class="sxs-lookup"><span data-stu-id="78038-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="78038-112">Tous les fichiers CAB du contenu d’aide pour un module doivent se trouver au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="78038-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="78038-113">Vous pouvez placer des fichiers CAB de contenu d’aide pour différents modules au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="78038-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="78038-114">Étape 2 : ajouter une clé HelpInfoURI à votre manifeste de module</span><span class="sxs-lookup"><span data-stu-id="78038-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="78038-115">Ajoutez une clé **HelpInfoURI** à votre manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="78038-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="78038-116">La valeur de la clé est le Uniform Resource Identifier (URI) de l’emplacement du fichier d’informations XML HelpInfo pour votre module.</span><span class="sxs-lookup"><span data-stu-id="78038-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="78038-117">Pour des fins de sécurité, l’adresse doit commencer par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="78038-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="78038-118">L’URI doit spécifier un emplacement Internet, mais il ne doit pas inclure le nom de fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="78038-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="78038-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="78038-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="78038-120">Étape 3 : créer un fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="78038-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="78038-121">Le fichier d’informations XML HelpInfo contient l’URI de l’emplacement Internet de vos fichiers d’aide et les numéros de version des fichiers d’aide les plus récents pour votre module dans chaque culture d’interface utilisateur prise en charge.</span><span class="sxs-lookup"><span data-stu-id="78038-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="78038-122">Chaque module Windows PowerShell dispose d’un fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="78038-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="78038-123">Lorsque vous mettez à jour vos fichiers d’aide, vous modifiez ou remplacez le fichier XML HelpInfo ; vous n’en ajoutez pas une autre.</span><span class="sxs-lookup"><span data-stu-id="78038-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="78038-124">Pour plus d’informations, voir [How to Create a HELPINFO XML file](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="78038-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="78038-125">Étape 4 : signer vos fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="78038-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="78038-126">Les signatures numériques ne sont pas requises, mais elles sont recommandées à chaque fois que vous partagez des fichiers.</span><span class="sxs-lookup"><span data-stu-id="78038-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="78038-127">Étape 5 : créer des fichiers CAB</span><span class="sxs-lookup"><span data-stu-id="78038-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="78038-128">Utilisez un outil qui crée des fichiers Cabinet (. cab), tels que MakeCab. exe, pour créer un. Fichier CAB qui contient les fichiers d’aide de votre module.</span><span class="sxs-lookup"><span data-stu-id="78038-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="78038-129">Créez un fichier CAB distinct pour les fichiers d’aide dans chaque culture d’interface utilisateur prise en charge.</span><span class="sxs-lookup"><span data-stu-id="78038-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="78038-130">Pour plus d’informations, consultez [Comment préparer des fichiers CAB d’aide pouvant être mis à jour](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="78038-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="78038-131">Étape 6 : télécharger vos fichiers</span><span class="sxs-lookup"><span data-stu-id="78038-131">Step 6: Upload your files</span></span>

<span data-ttu-id="78038-132">Pour publier des fichiers d’aide nouveaux ou mis à jour, téléchargez les fichiers CAB vers l’emplacement Internet spécifié par l’élément **HelpContentUri** dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="78038-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="78038-133">Ensuite, chargez le fichier XML HelpInfo à l’emplacement Internet spécifié par la valeur de la clé **HelpInfoUri** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="78038-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
