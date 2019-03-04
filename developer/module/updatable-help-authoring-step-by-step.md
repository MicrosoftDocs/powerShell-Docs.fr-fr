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
# <a name="updatable-help-authoring-step-by-step"></a>Création d’une aide actualisable : procédure pas à pas

Ce documents répertorie les étapes du processus de création de l’aide actualisable.

## <a name="authoring-updatable-help-step-by-step"></a>Création d’aide actualisable : procédure pas à pas

Aide actualisable est conçu pour les utilisateurs finaux, mais il fournit également des avantages significatifs pour les auteurs de modules et les writers d’aide, y compris la possibilité d’ajouter du contenu, de corriger les erreurs, d’offrir dans plusieurs cultures d’interface utilisateur et de répondent aux commentaires des utilisateurs et des demandes, délai après le module a été expédiée. Cette rubrique explique comment vous en package et les fichiers d’aide de téléchargement afin que les utilisateurs peuvent télécharger et les installer à l’aide de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applets de commande.

Les étapes suivantes fournissent une vue d’ensemble du processus de prise en charge de l’aide actualisable.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Étape 1 : Trouver un site Internet pour vos fichiers d’aide

La première étape de création d’aide actualisable consiste à trouver un emplacement Internet pour les fichiers d’aide de votre module. En fait, vous pouvez utiliser deux emplacements différents. Vous pouvez conserver le fichier d’informations de votre module aide (HelpInfo XML - décrits ci-dessous) à un emplacement Internet et les fichiers CAB contenus d’aide à un autre emplacement Internet. Aide de tous les fichiers CAB en contenu pour un module doivent être dans le même emplacement. Vous pouvez placer des fichiers CAB contenus d’aide pour les différents modules dans le même emplacement.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Étape 2 : Ajouter une clé HelpInfoURI dans le manifeste de module

Ajouter un **HelpInfoURI** clés dans le manifeste de module. La valeur de la clé est l’identificateur URI (Uniform Resource) de l’emplacement du fichier d’informations HelpInfo XML pour votre module. Pour la sécurité, l’adresse doit commencer par « http » ou « https ». L’URI doit spécifier un emplacement Internet, mais ne doit pas inclure le nom de fichier XML HelpInfo.

Par exemple :

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Étape 3 : Créez un fichier XML HelpInfo

Le fichier d’informations HelpInfo XML contient l’URI de l’emplacement Internet de vos fichiers d’aide et les numéros de version les plus récente des fichiers d’aide pour votre module dans chaque culture d’interface utilisateur pris en charge. Chaque module Windows PowerShell a un fichier XML HelpInfo. Lorsque vous mettez à jour vos fichiers d’aide, modifier ou de remplacer le fichier XML HelpInfo ; vous n’ajoutez pas d’un autre. Pour plus d’informations, consultez [comment créer un fichier XML de HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Étape 4 : Se connecter à vos fichiers d’aide

Signatures numériques ne sont pas nécessaires, mais ils sont une recommandation de meilleures pratiques, chaque fois que vous partagez des fichiers.

### <a name="step-5-create-cab-files"></a>Étape 5 : Créer des fichiers CAB

Utiliser un outil qui crée des fichiers CAB (.cab), telles que MakeCab.exe, pour créer un. Fichier CAB qui contient les fichiers d’aide pour votre module. Créer un fichier CAB distinct pour les fichiers d’aide dans chaque culture d’interface utilisateur pris en charge. Pour plus d’informations, consultez [comment préparer actualisable CAB fichiers d’aide](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Étape 6 : Charger vos fichiers

Pour publier des fichiers d’aide nouveaux ou mis à jour, télécharger les fichiers CAB à l’emplacement Internet spécifié par le **HelpContentUri** élément dans le fichier XML HelpInfo. Ensuite, chargez le fichier XML HelpInfo à l’emplacement Internet spécifié par la valeur de la **HelpInfoUri** clés dans le manifeste de module.
