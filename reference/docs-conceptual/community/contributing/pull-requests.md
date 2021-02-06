---
title: Guide pratique pour envoyer des demandes de tirage
description: Cet article explique comment envoyer des demandes de tirage au référentiel PowerShell-Docs.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "99595896"
---
# <a name="how-to-submit-pull-requests"></a>Guide pratique pour envoyer des demandes de tirage

Pour apporter des modifications au contenu, envoyez une demande de tirage (pull request) à partir de votre duplication (fork). Une requête de tirage doit être vérifiée avant de pouvoir être fusionnée. Pour de meilleurs résultats, passez en revue la [liste de contrôle éditoriale](editorial-checklist.md) avant de soumettre votre demande de tirage.

## <a name="using-git-branches"></a>Utilisation de branches git

La branche par défaut pour PowerShell-Docs est la `staging` branche. Les modifications apportées aux branches de travail sont fusionnées dans la `staging` branche avant d’être publiées. La `staging` branche est fusionnée dans la `live` branche tous les jours ouvrables à 3:00 h 00 (heure du Pacifique). La `live` branche contient le contenu publié sur docs.Microsoft.com.

Avant de commencer les modifications, créez une branche de travail dans votre copie locale du référentiel PowerShell-Docs. Lorsque vous travaillez localement, veillez à synchroniser votre dépôt local avant de créer votre branche de travail. La branche de travail doit être créée à partir d’une copie mise à jour de la `staging` branche.

Toutes les demandes de tirage doivent porter sur la branche `staging`. N’envoyez pas de modification à la `live` branche.
Les modifications apportées à la branche `staging` sont fusionnées dans `live`, remplaçant toutes les modifications apportées à `live`.

## <a name="make-the-pull-request-process-work-better-for-everyone"></a>Amélioration du processus de demande de tirage pour tout le monde

Plus la demande de tirage est simple et précise, plus vite elle peut être vérifiée et fusionnée.

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a>Évitez les requêtes de tirage qui mettent à jour un grand nombre de fichiers ou qui contiennent des modifications non liées

Évitez de créer des demandes de tirage qui contiennent des modifications sans lien les unes avec les autres. Séparez les mises à jour mineures d’articles existants des nouveaux articles et réécritures majeures. Travaillez sur ces modifications dans des branches de travail distinctes.

Les modifications en bloc créent des demandes de tirage avec modification d’un grand nombre de fichiers. Limitez votre demandes de tirage à 50 fichiers modifiés maximum. Les grandes demandes de tirage sont difficiles à vérifier et plus sujettes aux erreurs.

### <a name="renaming-or-deleting-files"></a>Renommer ou supprimer des fichiers

Lorsque vous renommez ou supprimez des fichiers, il doit y avoir un problème lié à la demande de tirage. qui aborde le caractère nécessaire du renommage ou de la suppression.

Évitez de mélanger les ajouts et modifications de contenu avec des changements de nom et suppressions de fichiers. Tout fichier renommé ou supprimé doit être ajouté au fichier de redirection globale. Lorsque cela est possible, mettez à jour tous les fichiers qui sont liés au contenu renommé ou supprimé, y compris les fichiers TOC.

## <a name="docs-pr-validation-service"></a>Service de validation des demandes de tirage Docs

Le service de validation docs PR est une application GitHub qui exécute des règles de validation sur vos modifications. Vous devez corriger toutes les erreurs ou tous les avertissements signalés par le service de validation.

Le comportement se présente ainsi :

1. Vous soumettez une demande de tirage.
1. Le commentaire GitHub indiquant l’état de votre demande de tirage présente l’état des « vérifications » activées sur le dépôt. Dans cet exemple, deux vérifications sont activées, « validation validée » et « OpenPublishing. Build » :

   ![État de validation : certaines vérifications ont échoué](media/pull-requests/validation-failed.png)

   Le build peut aboutir même si la validation commit échoue.

1. Pour plus d’informations, cliquez sur **Détails**.
1. Sur la page Détails figurent tous les contrôles de validation qui ont échoué, avec des informations indiquant comment résoudre les problèmes.
1. Une fois la validation réussie, le commentaire suivant est ajouté à la demande de tirage :

   ![État de validation : réussite](media/pull-requests/build-validation.png)

> [!NOTE]
> Si vous êtes un contributeur externe (et non un employé Microsoft), vous n’avez pas accès aux rapports de build détaillés ni aux liens d’aperçu.

Une fois la demande de tirage vérifiée, vous pouvez être invité à apporter des modifications ou à corriger les messages d’avertissement de validation. L’équipe PowerShell-Docs peut vous aider à comprendre les erreurs de validation et les exigences éditoriales.

## <a name="next-steps"></a>Étapes suivantes

[Guide de style PowerShell-Docs](powershell-style-guide.md)

## <a name="additional-resources"></a>Ressources supplémentaires

[Processus de gestion des demandes de tirage](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
