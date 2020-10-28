---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Présentation de JEA (Just Enough Administration)
description: JEA est une technologie de sécurité qui permet une administration déléguée de tout ce qui est géré avec PowerShell.
ms.openlocfilehash: cc1c49960e274b58635c1ca4e6769a54c3c7ded6
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501709"
---
# <a name="just-enough-administration"></a>Administration suffisante

Just Enough Administration (JEA) est une technologie de sécurité qui permet une administration déléguée de tout ce qui est géré avec PowerShell. Avec JEA, vous pouvez :

- **Réduire le nombre d’administrateurs sur vos machines** en utilisant des comptes virtuels ou des comptes de service gérés de groupe pour effectuer des actions privilégiées au nom d’utilisateurs normaux.
- **Limiter les opérations réalisables par les utilisateurs** en spécifiant les applets de commande, fonctions et commandes externes qu’ils peuvent exécuter.
- **Mieux comprendre ce que font vos utilisateurs** avec des transcriptions et des journaux qui vous montrent exactement quelles commandes un utilisateur a exécutées pendant sa session.

**Pourquoi JEA est-il important ?**

Les comptes à privilèges élevés utilisés pour administrer vos serveurs posent un important risque de sécurité. Si une personne malveillante compromet l’un de ces comptes, elle peut lancer des [attaques latérales](https://aka.ms/pth) au sein de votre organisation. Chaque compte compromis donne à un attaquant l’accès à encore plus de comptes et de ressources, et le rapproche donc de la possibilité de voler des secrets de l’entreprise, de lancer une attaque par déni de service, etc.

Il n’est pas non plus toujours facile de supprimer des privilèges d’administration. Envisagez le scénario courant dans lequel le rôle DNS est installé sur la même machine que votre contrôleur de domaine Active Directory. Vos administrateurs DNS nécessitent des privilèges d’administrateur local pour résoudre les problèmes rencontrés avec le serveur DNS. Mais pour cela, vous devez en faire des membres du groupe de sécurité avec privilèges élevés **Admins du domaine** . Cette approche permet effectivement aux administrateurs DNS de contrôler tout votre domaine et d’accéder à toutes les ressources situées sur cet ordinateur.

JEA résout ce problème via le principe de **moindre privilège** . Avec JEA, vous pouvez configurer un point de terminaison de gestion pour les administrateurs DNS qui leur donne accès seulement aux commandes PowerShell dont ils ont besoin pour faire leur travail. Cela signifie que vous pouvez leur octroyer un accès approprié pour réparer un cache DNS empoisonné ou redémarrer le serveur DNS sans leur donner par inadvertance des droits sur Active Directory, parcourir le système de fichiers, ou exécuter des scripts potentiellement dangereux. Mieux encore, quand la session JEA est configurée pour utiliser des comptes virtuels privilégiés temporaires, vos administrateurs DNS peuvent se connecter au serveur en utilisant des informations d’identification d’utilisateurs **non-administrateurs** et exécuter quand même des commandes qui exigent généralement des privilèges d’administrateur. JEA vous permet de supprimer des utilisateurs dans des rôles d’administrateur local ou de domaine largement privilégiés, et de contrôler soigneusement ce qu’ils peuvent faire sur chaque machine.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la configuration requise pour utiliser JEA, consultez l’article [Prérequis](prerequisites.md).

## <a name="samples-and-dsc-resource"></a>Exemples et ressources DSC

Vous trouverez des exemples de configurations JEA et la ressource DSC JEA dans le [référentiel GitHub JEA](https://github.com/PowerShell/JEA).
