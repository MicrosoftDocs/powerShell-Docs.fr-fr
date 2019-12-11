---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Conditions préalables pour JEA
ms.openlocfilehash: 1833bacf49eebcccefc10f7c85a39732559c1a97
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416733"
---
# <a name="prerequisites"></a>Conditions préalables

Just Enough Administration (JEA) est une fonctionnalité incluse dans PowerShell 5.0 et ultérieur. Cet article décrit les prérequis à satisfaire pour pouvoir commencer à utiliser JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Vérifier la version de PowerShell installée.

Pour vérifier la version de PowerShell installée sur votre système, consultez la variable `$PSVersionTable` dans une invite de Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA est disponible avec PowerShell 5.0 et ultérieur. Pour bénéficier des fonctionnalités complètes, il est recommandé d’installer la dernière version de PowerShell disponible pour votre système. Le tableau suivant décrit la disponibilité de JEA sur Windows Server :

| Système d’exploitation serveur |                Disponibilité de JEA                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | Préinstallé                                   |
| Windows Server 2012 R2  | Fonctionnalité complète avec WMF 5.1                |
| Windows Server 2012     | Fonctionnalité complète avec WMF 5.1                |
| Windows Server 2008 R2  | Fonctionnalités réduites<sup>1</sup> avec WMF 5.1 |

Vous pouvez également utiliser JEA sur un ordinateur personnel ou professionnel :

| Système d’exploitation client |                   Disponibilité de JEA                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Préinstallé                                         |
| Windows 10 1603, 1511   | Préinstallé, avec des fonctionnalités réduites<sup>2</sup> |
| Windows 10 1507         | Non disponible                                        |
| Windows 8, 8.1          | Fonctionnalité complète avec WMF 5.1                      |
| Windows 7               | Fonctionnalités réduites<sup>1</sup> avec WMF 5.1       |

- <sup>1</sup> Vous ne pouvez pas configurer JEA pour utiliser des comptes de service gérés de groupe sur Windows Server 2008 R2 ou Windows 7. Les comptes virtuels et les autres fonctionnalités JEA *sont* pris en charge.

- <sup>2</sup> Les fonctionnalités JEA suivantes ne sont pas prises en charge sur Windows 10 versions 1511 et 1603 :

  - Exécution en tant que compte de service géré de groupe
  - Règles d’accès conditionnel dans les configurations de session
  - Lecteur utilisateur
  - Octroi de l’accès aux comptes d’utilisateurs locaux

  Pour obtenir un support pour ces fonctionnalités, vous devez mettre à jour Windows à la version 1607 (Mise à jour anniversaire) ou à une version ultérieure.

### <a name="install-windows-management-framework"></a>Installer Windows Management Framework

Si vous exécutez une version antérieure de PowerShell, il peut être nécessaire de mettre à jour votre système avec la dernière mise à jour de Windows Management Framework (WMF). Pour plus d’informations, consultez la [Documentation WMF](/powershell/scripting/wmf/overview).

Il est recommandé de tester la compatibilité de votre charge de travail avec WMF avant de mettre à niveau tous vos serveurs.

Les utilisateurs Windows 10 doivent installer les dernières mises à jour de la fonctionnalité pour obtenir la version actuelle de Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Activer la communication à distance de PowerShell

La communication à distance PowerShell est la base de JEA. Il est nécessaire de vérifier que la communication à distance PowerShell est activée et correctement sécurisée avant de pouvoir utiliser JEA. Pour plus d’informations, consultez [Sécurité de WinRM](/powershell/scripting/learn/remoting/winrmsecurity).

La communication à distance PowerShell est activée par défaut dans Windows Server 2012, 2012 R2 et 2016. Vous pouvez activer la communication à distance PowerShell en exécutant la commande suivante dans une fenêtre PowerShell élevée.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Activer la journalisation des modules PowerShell et des blocs de script (facultatif)

Les étapes suivantes activent la journalisation de toutes les actions PowerShell sur votre système. La journalisation des modules PowerShell n’est pas obligatoire pour JEA. Cependant, il est recommandé de l’activer afin de garantir que les commandes exécutées par les utilisateurs sont journalisées à un emplacement central.

Vous pouvez configurer la stratégie de journalisation des modules PowerShell à l’aide de la stratégie de groupe.

1. Ouvrez l’éditeur d'objets de stratégie de groupe local sur une station de travail ou un objet de stratégie de groupe dans la console de gestion des stratégies de groupe sur un contrôleur de domaine Active Directory
2. Accédez à **Configuration ordinateur\\Modèles d’administration\\Composants Windows\\Windows PowerShell**.
3. Double cliquez sur **Activer l’enregistrement des modules**.
4. Cliquez sur **Activé**.
5. Dans la section Options, cliquez sur **Afficher** en regard des noms de module.
6. Tapez `*` dans la fenêtre contextuelle pour journaliser les commandes de tous les modules.
7. Cliquez sur **OK** pour définir la stratégie.
8. Double-cliquez sur **Activer la journalisation de blocs de scripts PowerShell**
9. Cliquez sur **Activé**.
10. Cliquez sur **OK** pour définir la stratégie.
11. (Sur les ordinateurs joints à un domaine uniquement) Exécutez `gpupdate` ou attendez que la stratégie de groupe traite la stratégie mise à jour et applique les paramètres.

Vous pouvez également activer la transcription PowerShell à l’échelle du système par le biais de la stratégie de groupe.

## <a name="next-steps"></a>Étapes suivantes

[Créer un fichier de fonctionnalité de rôle](role-capabilities.md)

[Créer un fichier de configuration de session](session-configurations.md)

## <a name="see-also"></a>Voir aussi

[Sécurité de WinRM](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ the Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
