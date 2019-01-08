---
ms.date: 10/13/2017
keywords: dsc,powershell,configuration,setup
title: Présentation de la configuration de l’état souhaité pour les ingénieurs
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401846"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Présentation de la configuration de l’état souhaité pour les ingénieurs

Ce document est destiné à faire découvrir aux développeurs et équipes opérationnelles les avantages de la configuration d’état souhaité (DSC) PowerShell.
Pour une vision plus globale des avantages offerts par DSC, consultez la section [Présentation de la configuration de l’état souhaité pour les décideurs](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Avantages de la configuration de l’état souhaité

Objectifs de DSC :

- Réduire la complexité des scripts dans Windows
- Accélérer la vitesse d’itération

Le concept de « déploiement continu » gagne en importance.
Grâce au déploiement continu, il est possible de procéder à des déploiements fréquents, potentiellement plusieurs fois par jour.
L’objectif de ces déploiements n’est pas de réparer quoi que ce soit, mais de permettre des publications plus rapides.
En développant de nouvelles fonctionnalités et en les rendant opérationnelles aussi rapidement et efficacement que possible, vous accélérez le retour sur investissement de cette nouvelle logique métier.

Le passage au cloud computing implique une solution de déploiement qui utilise un modèle « déclaratif », où un environnement final est déclaré en tant que texte et publié sur un moteur de déploiement.
Cette technique de déploiement permet des modifications rapides à grande échelle, avec une résilience contre les menaces de défaillance, puisque le déploiement peut être répété à tout moment de manière cohérente pour garantir un état final.
La création d’outils et de services prenant en charge ce type d’opérations par le biais de l’automatisation est une réponse à ces modifications.

DSC est une plateforme assurant des opérations de déploiement, de configuration et de conformité déclaratives et idempotentes (reproductibles).
La plateforme DSC permet de garantir que les composants de votre centre de données sont configurés correctement, ce qui évite des erreurs et de coûteux échecs de déploiement.
En traitant les configurations DSC dans le cadre du code de l’application, DSC permet un déploiement continu.
La configuration DSC doit être mise à jour directement dans l’application, en veillant à ce que les données nécessaires au déploiement de l’application soient toujours à jour et prêtes à être utilisées.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>« Je dispose de PowerShell, pourquoi ai-je besoin de la configuration de l’état souhaité ? »

Les configurations DSC font la distinction entre l’intention (« Ce que je veux effectuer » et l’exécution (« Comment je veux l’effectuer »).
Cela signifie que la logique d’exécution est contenue dans les ressources.
Les utilisateurs n’ont pas besoin de savoir implémenter ou déployer une fonctionnalité lorsqu’une ressource DSC pour cette fonctionnalité est disponible.
Cela permet à l’utilisateur de se concentrer sur la structure de son déploiement.

Par exemple, les scripts PowerShell doivent ressembler à ceci :
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Ce script est simple, aisément compréhensible et direct.
Toutefois, si vous tentez de mettre ce script en production, vous rencontrerez plusieurs problèmes.
Que se passe-t-il si ce script est exécuté deux fois de suite ?
Que se passe-t-il si Bob avait précédemment un accès complet au partage ?

Pour compenser ces problèmes, une version « réelle » du script ressemblera davantage à ceci :
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Ce script est plus complexe, avec une grande quantité de logiques et d’erreurs à gérer.
Le script est plus complexe, car vous n’indiquez plus ce que vous voulez effectuer, mais *comment l’effectuer*.

DSC vous permet de dire ce que vous voulez effectuer, et il est fait abstraction de la logique sous-jacente.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Ce script est mis en forme proprement et facile à lire.
Les chemins d’accès logiques et la gestion des erreurs sont toujours présents dans l’implémentation des [ressources](../resources/resources.md), mais invisibles pour le créateur du script.

## <a name="separating-environment-from-structure"></a>Distinction entre environnement et structure

Dans DevOps, un schéma fréquent consiste à disposer de plusieurs environnements pour le déploiement.
Par exemple, un environnement de développement peut être utilisé pour créer rapidement le prototype d’un nouveau code.
Le code de l’environnement de développement se retrouve dans un environnement de test, où d’autres personnes vérifient les nouvelles fonctionnalités.
Enfin, le code passe en production, autrement dit dans l’environnement de production du site en ligne.

Les configurations DSC s’adaptent à ce système développement-test-production par l’utilisation des [données de configuration](../configurations/configData.md).
Cela précise encore davantage la distinction entre la structure de la configuration et les nœuds gérés.
Par exemple, vous pouvez définir une configuration qui nécessite un serveur SQL, un serveur IIS et un serveur de couche intermédiaire.
Quels que soient les nœuds qui reçoivent les différents éléments de cette configuration, ces trois éléments seront toujours présents.
Vous pouvez utiliser des données de configuration pour pointer les trois éléments vers le même ordinateur d’un environnement de développement, séparer ces trois éléments sur trois ordinateurs différents d’un environnement de test et enfin transférer l’ensemble de vos serveurs de production pour l’environnement de production.
Pour effectuer un déploiement sur les différents environnements, vous pouvez appeler **Start-DscConfiguration** avec les données de configuration appropriées à l’environnement que vous souhaitez cibler.

## <a name="see-also"></a>Voir aussi

[Configurations](../configurations/configurations.md)

[Données de configuration](../configurations/configData.md)

[Ressources](../resources/resources.md)
