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
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366988"
---
# <a name="updatable-help-authoring-step-by-step"></a>Création d’aide actualisable : pas à pas

Ce document répertorie les étapes du processus de création de l’aide actualisable.

## <a name="authoring-updatable-help-step-by-step"></a>Création de l’aide actualisable : pas à pas

L’aide pouvant être mise à jour est conçue pour les utilisateurs finaux, mais elle offre également des avantages significatifs pour les auteurs de modules et les créateurs d’aide, y compris la possibilité d’ajouter du contenu, de corriger des erreurs, de fournir dans plusieurs cultures d’interface utilisateur et de répondre aux commentaires et aux demandes des utilisateurs, longtemps après le module a été expédié. Cette rubrique explique comment empaqueter et télécharger des fichiers d’aide afin que les utilisateurs puissent les télécharger et les installer à l’aide des applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Les étapes suivantes fournissent une vue d’ensemble du processus de prise en charge de l’aide actualisable.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Étape 1 : Rechercher un site Internet pour vos fichiers d’aide

La première étape de création de l’aide actualisable consiste à rechercher un emplacement Internet pour les fichiers d’aide de votre module. En fait, vous pouvez utiliser deux emplacements différents. Vous pouvez conserver le fichier d’informations d’aide de votre module (HelpInfo XML-décrit ci-dessous) à un emplacement Internet et les fichiers CAB du contenu d’aide à un autre emplacement Internet. Tous les fichiers CAB du contenu d’aide pour un module doivent se trouver au même emplacement. Vous pouvez placer des fichiers CAB de contenu d’aide pour différents modules au même emplacement.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Étape 2 : ajouter une clé HelpInfoURI à votre manifeste de module

Ajoutez une clé **HelpInfoURI** à votre manifeste de module. La valeur de la clé est le Uniform Resource Identifier (URI) de l’emplacement du fichier d’informations XML HelpInfo pour votre module. Pour des fins de sécurité, l’adresse doit commencer par « http » ou « HTTPS ». L’URI doit spécifier un emplacement Internet, mais il ne doit pas inclure le nom de fichier XML HelpInfo.

Par exemple :

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Étape 3 : créer un fichier XML HelpInfo

Le fichier d’informations XML HelpInfo contient l’URI de l’emplacement Internet de vos fichiers d’aide et les numéros de version des fichiers d’aide les plus récents pour votre module dans chaque culture d’interface utilisateur prise en charge. Chaque module Windows PowerShell dispose d’un fichier XML HelpInfo. Lorsque vous mettez à jour vos fichiers d’aide, vous modifiez ou remplacez le fichier XML HelpInfo ; vous n’en ajoutez pas une autre. Pour plus d’informations, voir [How to Create a HELPINFO XML file](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Étape 4 : signer vos fichiers d’aide

Les signatures numériques ne sont pas requises, mais elles sont recommandées à chaque fois que vous partagez des fichiers.

### <a name="step-5-create-cab-files"></a>Étape 5 : créer des fichiers CAB

Utilisez un outil qui crée des fichiers Cabinet (. cab), tels que MakeCab. exe, pour créer un. Fichier CAB qui contient les fichiers d’aide de votre module. Créez un fichier CAB distinct pour les fichiers d’aide dans chaque culture d’interface utilisateur prise en charge. Pour plus d’informations, consultez [Comment préparer des fichiers CAB d’aide pouvant être mis à jour](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Étape 6 : télécharger vos fichiers

Pour publier des fichiers d’aide nouveaux ou mis à jour, téléchargez les fichiers CAB vers l’emplacement Internet spécifié par l’élément **HelpContentUri** dans le fichier XML HelpInfo. Ensuite, chargez le fichier XML HelpInfo à l’emplacement Internet spécifié par la valeur de la clé **HelpInfoUri** dans le manifeste de module.
