---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 0bc085588190f134c4a687c952509aa256b5f840
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085199"
---
# <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)
Just Enough Administration est une nouvelle fonctionnalité de WMF 5.0 qui autorise l’administration basée sur des rôles par le biais de l’accès distant PowerShell.  Elle étend l’infrastructure de point de terminaison contrainte existante en autorisant les utilisateurs non-administrateurs à exécuter des commandes, des scripts et des exécutables spécifiques en tant qu’administrateur.  Cela vous permet de réduire le nombre d’administrateurs complets dans votre environnement et d’améliorer la sécurité.  JEA fonctionne pour tout ce que vous gérez par le biais de PowerShell. Si vous pouvez gérer quelque chose avec PowerShell, JEA peut vous aider à le faire de manière plus sécurisée.  Pour découvrir Just Enough Administration de manière détaillée, consultez le [guide d’expérience](http://aka.ms/JEA).

Contrairement aux anciens points de terminaison contraints, JEA est à la fois puissant et facile à configurer.  Les fonctionnalités utilisateur dans JEA peuvent être contrôlées de manière granulaire, jusqu’à limiter les jeux de paramètres et les valeurs qui peuvent être fournis à une commande spécifique. Les actions de l’utilisateur sont exécutées dans le contexte d’un compte virtuel ponctuel qui est autorisé à effectuer les actions d’administrateur.  Vous pouvez enregistrer les commandes appelées par l’utilisateur dans un journal afin d’effectuer un audit de sécurité.

JEA vous permet de créer des points de terminaison contraints spécialement configurés.  Ces points de terminaison ont quelques caractéristiques importantes :

1. Les utilisateurs qui s’y connectent « s’exécutent en tant que » compte privilégié virtuel qui existe uniquement pendant la durée de la session à distance.  Par défaut, ce compte virtuel est membre du groupe Administrateurs intégré, et également administrateur de domaine sur les contrôleurs de domaine (notez que ces autorisations sont configurables). Le fait de se connecter sous un utilisateur et de s’exécuter en tant qu’autre utilisateur privilégié permet aux utilisateurs sans privilèges d’effectuer des tâches administratives spécifiques sans que des droits d’administration leur soient accordés sur vos systèmes.
2. Le point de terminaison est verrouillé.  Cela signifie que PowerShell s’exécute en mode sans langage.  Seuls des commandes, scripts et exécutables spécifiques sont visibles par l’utilisateur.
3. Des ensembles de capacités différents sont présentés aux utilisateurs qui se connectent en fonction de l’appartenance au groupe.  Vous pouvez fournir différentes capacités à différents rôles sur le même point de terminaison.
