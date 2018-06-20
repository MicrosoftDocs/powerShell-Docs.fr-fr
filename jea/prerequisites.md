---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Conditions préalables pour JEA
ms.openlocfilehash: a5cf5519b30b24d44c12bdeedcf4cd763e2edbde
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189769"
---
# <a name="prerequisites"></a>Conditions préalables

> S’applique à : Windows PowerShell 5.0

Just Enough Administration est une fonctionnalité incluse dans Windows PowerShell 5.0 et versions ultérieures.
Cette rubrique décrit les conditions préalables à satisfaire pour pouvoir commencer à utiliser JEA.

## <a name="install-jea"></a>Installer JEA

JEA est disponible avec Windows PowerShell 5.0 et versions ultérieures. Mais, pour les fonctionnalités complètes, il est recommandé d’installer la dernière version de PowerShell disponible pour votre système.
Le tableau suivant décrit la disponibilité de JEA sur Windows Server :

Système d’exploitation serveur   | Disponibilité de JEA
--------------------------|--------------------------------
Windows Server 2016       | Préinstallé
Windows Server 2012 R2    | Fonctionnalité complète avec WMF 5.1
Windows Server 2012       | Fonctionnalité complète avec WMF 5.1
Windows Server 2008 R2    | Fonctionnalités réduites<sup>1</sup> avec WMF 5.1

Vous pouvez également utiliser JEA sur un ordinateur personnel ou professionnel :

Système d’exploitation client   | Disponibilité de JEA
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Préinstallé
Windows 10 1603, 1511     | Préinstallé, avec des fonctionnalités réduites<sup>2</sup>
Windows 10 1507           | Non disponible
Windows 8, 8.1            | Fonctionnalité complète avec WMF 5.1
Windows 7                 | Fonctionnalités réduites<sup>1</sup> avec WMF 5.1

<sup>1</sup> Vous ne pouvez pas configurer JEA pour utiliser des comptes de service géré de groupe sur Windows Server 2008 R2 ou Windows 7.
Les comptes virtuels et les autres fonctionnalités JEA *sont* pris en charge.

<sup>2</sup> Les versions Windows 10 1511 et 1603 ne prennent pas en charge les fonctionnalités JEA suivantes : exécution en tant que compte de service administré de groupe, les règles d’accès conditionnel dans des configurations de session, le lecteur utilisateur et l’octroi de l’accès à des comptes d’utilisateurs locaux.
Pour obtenir un support pour ces fonctionnalités, vous devez mettre à jour Windows à la version 1607 (Mise à jour anniversaire) ou à une version ultérieure.

### <a name="check-which-version-of-powershell-is-installed"></a>Vérifier la version de PowerShell installée.

Pour vérifier la version de PowerShell installée sur votre système, consultez la variable `$PSVersionTable` dans une invite de Windows PowerShell.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Vous êtes prêt à utiliser JEA si la version *principale* est supérieure ou égale à **5**.
Pour optimiser l’expérience et accéder à toutes les fonctionnalités les plus récentes, il est recommandé de mettre à niveau vers la version de PowerShell **5.1** lorsque cela est possible.

### <a name="install-windows-management-framework"></a>Installer Windows Management Framework

Si vous exécutez une version antérieure de PowerShell, vous devez mettre à jour votre système avec la dernière mise à jour de Windows Management Framework (WMF).
Les packages de mise à jour et un lien vers les dernières notes de publication de WMF sont disponibles dans le [Centre de téléchargement](https://aka.ms/WMF5).

Il est fortement recommandé de tester la compatibilité de votre charge de travail avec WMF avant de mettre à niveau tous vos serveurs.

Les utilisateurs Windows 10 doivent installer les dernières mises à jour de la fonctionnalité pour obtenir la version actuelle de Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Activer la communication à distance de PowerShell

La communication à distance PowerShell est la base de JEA.
Il est donc important d’assurer que la communication à distance PowerShell est activée et [correctement sécurisée](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) sur votre système avant de pouvoir utiliser JEA.

La communication à distance PowerShell est activée par défaut dans Windows Server 2012, 2012 R2 et 2016.
Vous pouvez activer la communication à distance PowerShell en exécutant la commande suivante dans une fenêtre PowerShell élevée.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Activer la journalisation des modules PowerShell et des blocs de script (facultatif)

Les étapes suivantes activent la journalisation de toutes les actions PowerShell sur votre système.
La journalisation des modules PowerShell n’est pas obligatoire pour JEA. Cependant, il est fortement recommandé de l’activer afin de vous assurer que les commandes utilisées par les utilisateurs sont journalisées dans un emplacement central.

Vous pouvez configurer la stratégie de journalisation des modules PowerShell à l’aide de la stratégie de groupe.

1. Ouvrez l’éditeur d'objets de stratégie de groupe local sur une station de travail ou un objet de stratégie de groupe dans la console de gestion des stratégies de groupe sur un contrôleur de domaine Active Directory
2. Accédez à **Configuration ordinateur\\Modèles d’administration\\Composants Windows\\Windows PowerShell**.
3. Double cliquez sur **Activer l’enregistrement des modules**.
4. Cliquez sur **Activé**.
5. Dans la section Options, cliquez sur **Afficher** en regard des noms de module.
6. Tapez « **\*** » dans la fenêtre contextuelle. Cette commande ordonne à PowerShell de journaliser les commandes de tous les modules.
7. Cliquez sur **OK** pour définir la stratégie.
8. Double-cliquez sur **Activer la journalisation de blocs de scripts PowerShell**
9. Cliquez sur **Activé**.
10. Cliquez sur **OK** pour définir la stratégie.
11. (sur les ordinateurs joints à un domaine uniquement). Exécutez **gpupdate** ou attendez que la stratégie de groupe traite la stratégie mise à jour et applique les paramètres.

Vous pouvez également activer la transcription PowerShell à l’échelle du système par le biais de la stratégie de groupe.

## <a name="next-steps"></a>Étapes suivantes

- [Créer un fichier de fonctionnalité de rôle](role-capabilities.md)
- [Créer un fichier de configuration de session](session-configurations.md)

## <a name="see-also"></a>Voir aussi

- [Informations supplémentaires sur la sécurité de la communication à distance PowerShell et WinRM](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [*PowerShell ♥ the Blue Team*, billet de blog sur la sécurité](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)