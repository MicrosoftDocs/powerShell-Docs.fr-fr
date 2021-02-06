---
title: Bien démarrer avec la contribution à la documentation de PowerShell
description: Cet article explique dans les grandes lignes comment bien démarrer en tant que contributeur de la documentation de PowerShell.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: ddcbf79de1ab05b901ce1abd67f65b2524ed164d
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99595462"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Bien démarrer avec la contribution à la documentation de PowerShell

Cet article explique dans les grandes lignes comment bien démarrer en tant que contributeur de la documentation de PowerShell.

## <a name="powershell-docs-structure"></a>Structure de PowerShell-Docs

Le [référentiel PowerShell-docs][psdocs] est divisé en deux groupes de contenu : référence et conceptuel.

### <a name="reference-content"></a>Contenu de référence

Le contenu de référence est la référence des applets de commande PowerShell pour les applets de commande fournies avec PowerShell.
La [référence][ref] est collectée dans les dossiers de versions (5,1, 7,0, 7,1 et 7,2). Ce contenu contient une référence d’applet de commande uniquement pour les modules fournis avec PowerShell. Ce contenu est également utilisé pour créer les informations d’aide affichées par l’applet de commande `Get-Help` .

### <a name="conceptual-content"></a>Contenu conceptuel

La documentation conceptuelle comprend le contenu suivant :

- Notes de publication
- Instructions de configuration
- Exemples de scripts et Articles de procédure
- Documentation DSC
- Documentation du kit de développement logiciel (SDK)

La [documentation conceptuelle][conceptual] n’est pas organisée par version. Tous les articles sont affichés pour chaque version de PowerShell. Nous travaillons actuellement à la création d’articles spécifiques à la version. Lorsque cette fonctionnalité est disponible dans notre documentation, ce guide est mis à jour avec les informations appropriées.

> [!NOTE]
> Chaque fois qu’un article conceptuel est ajouté, supprimé ou renommé, la table des matières doit être mise à jour et incluse dans la requête de tirage (pull request).

## <a name="creating-new-articles"></a>Création de nouveaux Articles

Un problème GitHub doit être créé pour tout nouveau document que vous souhaitez verser. Recherchez les problèmes existants pour vous assurer de ne pas dupliquer les efforts. Les problèmes affectés sont considérés comme étant `in progress` . Si vous souhaitez collaborer sur un problème, contactez la personne affectée au problème.

À l’instar du [processus PowerShell RFC][rfc], créez un problème avant d’écrire le contenu. Le problème vous évite de perdre du temps et des efforts sur le travail qui est rejeté par l’équipe PowerShell-Docs. Le problème nous permet de vous renseigner sur l’étendue du contenu et son emplacement dans la documentation PowerShell. Tous les articles doivent être inclus dans la table des matières (TOC). L’emplacement de la table des matières proposée doit être inclus dans la discussion du problème.

> [!NOTE]
> La table des matières pour le contenu de référence est générée automatiquement par le système de publication. Vous n’avez pas besoin de mettre à jour la table des matières.

## <a name="updating-existing-articles"></a>Mise à jour d’articles existants

Le cas échéant, les Articles de référence sur les applets de commande sont dupliqués dans toutes les versions de PowerShell conservées dans ce référentiel. Lorsque vous signalez un problème concernant une référence d’applet de commande ou un `About_` article, vous devez spécifier les versions qui sont affectées par le problème. Le modèle de problème dans GitHub comprend une liste de contrôle des versions. Utilisez les cases à cocher pour spécifier les versions du contenu qui sont affectées.

Vérifiez la version de l’article pour voir si la même modification est nécessaire dans les autres versions. Appliquez la modification appropriée à chaque version du fichier.

## <a name="localized-content"></a>Contenu localisé

La documentation PowerShell est écrite en anglais et traduite en 17 autres langages. Le contenu en anglais est stocké dans le référentiel GitHub nommé `MicrosoftDocs/PowerShell-Docs` . Le contenu localisé est stocké dans un référentiel distinct pour chaque langue. Les référentiels utilisent le même nom de répertoire, mais ajoutent le nom des paramètres régionaux à la fin. Par exemple, `MicrosoftDocs/PowerShell-Docs.de-de` contient le contenu qui a été traduit en allemand.

En général, les problèmes et les modifications doivent être soumis au référentiel anglais. Toutes les traductions commencent d’abord à partir du contenu en anglais. Nous utilisons la traduction humaine et la traduction automatique.

| Méthode de traduction  |                              Languages                               |
| ------------------- | -------------------------------------------------------------------- |
| Traduction humaine   | de-DE, es-ES, fr-FR, IT-IT, ja-JP, ko-KR, PT-BR, ru-RU, zh-CN, zh-TW |
| Traduction automatique | CS-CZ, HU-HU, NL-NL, PL-PL, PT-PT, SV-SE, TR-TR                      |

Le contenu traduit par la traduction automatique peut ne pas toujours aboutir à des choix de mots et à une grammaire corrects. Si vous trouvez une erreur dans la traduction pour n’importe quelle langue, plutôt que dans les détails techniques de l’article, ouvrez un problème dans le référentiel localisé. Expliquez pourquoi vous pensez que la traduction est incorrecte. Notre équipe de localisation révise et répond à ces problèmes.

## <a name="next-steps"></a>Étapes suivantes

Il existe deux façons courantes de soumettre des modifications dans GitHub. Les deux méthodes sont décrites dans le Guide du contributeur central :

1. Vous pouvez apporter des [modifications rapides aux documents existants](/contribute/#quick-edits-to-existing-documents) dans l’interface Web github.
1. Utilisez le [flux de travail complet GitHub][making-changes] pour ajouter de nouveaux articles, mettre à jour plusieurs fichiers ou d’autres modifications importantes.

Avant de commencer les modifications, vous devez créer une fourche du référentiel PowerShell-Docs. Les modifications doivent être apportées dans une branche de travail dans votre copie de PowerShell-docs. Si vous utilisez la méthode de **modification rapide** dans GitHub, ces étapes sont gérées pour vous. Si vous utilisez le flux de travail **GitHub complet**, vous devez être configuré pour [travailler localement][fork].

Les deux méthodes se terminent par la création d’une demande de tirage (pull request). Pour plus d’informations et pour connaître les meilleures pratiques, consultez [soumission d’une demande de tirage (pull Request](pull-requests.md) ).

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
