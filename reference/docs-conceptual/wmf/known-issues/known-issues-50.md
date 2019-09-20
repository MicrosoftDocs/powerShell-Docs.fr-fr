---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Problèmes connus dans WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147739"
---
# <a name="known-issues-in-wmf-50"></a>Problèmes connus dans WMF 5.0

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>Les raccourcis PowerShell sont rompus lors de la première utilisation

**Résolution :** Effectuez l’une des opérations suivantes :

1. Cliquez avec le bouton droit sur le raccourci PowerShell. Sélectionnez « Windows PowerShell » pour le lancer sans élévation de privilèges.
2. Cliquez avec le bouton droit sur le raccourci PowerShell. Cliquez avec le bouton droit sur « Windows PowerShell » et sélectionnez « Exécuter en tant qu’administrateur » pour le lancer avec élévation de privilèges.

Les raccourcis PowerShell fonctionneront une fois que vous aurez effectué l’une des actions ci-dessus. Vous ne devez effectuer ces actions qu’une seule fois.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>Les modules PowerShell et les ressources DSC signalent des erreurs concernant ExecutionPolicy sur Windows 7

Sur Windows 7, l’utilisation de modules PowerShell et de ressources DSC risque de provoquer des erreurs liées à ExecutionPolicy.

**Résolution :** Donnez la valeur **RemoteSigned** à ExecutionPolicy en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>La connexion à un ancien point de terminaison Exchange distant provoque un blocage

L’ancien point de terminaison Exchange redirige vers un nouveau point de terminaison. Un bogue dans la logique de redirection provoque un blocage.

**Résolution :** Connectez-vous directement au nouveau point de terminaison.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>La fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation de WMF 5.0 sur Windows Server 2012 R2

Quand vous installez WMF 5.0 sur un ordinateur Windows Server 2012 R2 qui exécute déjà SIL, la fonctionnalité de journalisation de l’inventaire logiciel est arrêtée de manière erronée après l’installation.

**Résolution :** Exécutez une fois la cmdlet `Start-SilLogging` après l’installation de WMF, car le processus d’installation arrête la fonctionnalité de Journalisation de l’inventaire logiciel de façon non contrôlée.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem` ne fonctionne pas si -LiteralPath et -Recurse sont utilisés ensemble

Si un nom de répertoire contient un caractère non valide, `Get-ChildItem` ne génère pas les résultats attendus quand -LiteralPath et -Recurse sont utilisés ensemble.

**Résolution :** La solution de contournement actuelle, qui n’est pas idéale, consiste à implémenter la récursivité dans le script plutôt que de se fier à l’applet de commande.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep échoue après l’installation de WMF 5.0

Il existe deux solutions de contournement pour résoudre ce problème, selon la version de Windows Server que vous exécutez.

**Résolution :**

- Pour les systèmes exécutant **Windows Server 2008 R2**
  1. Ouvrez PowerShell en tant qu’administrateur.
  2. Exécutez la commande suivante :

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. Exécutez la commande et ignorez les erreurs, qui sont normales.

     ```powershell
     Publish-SilData
     ```

  4. Supprimez les fichiers du répertoire \Windows\System32\Logfiles\SIL\.

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Installez toutes les mises à jour Windows importantes disponibles et lancez l’opération Sysprep normalement.

- Pour les systèmes exécutant **Windows Server 2012**
  1. Après avoir installé WMF 5.0 sur le serveur sur lequel Sysprep sera exécuté, connectez-vous en tant qu’administrateur.
  2. Copiez Generize.xml du répertoire `\Windows\System32\Sysprep\ActionFiles\` vers un emplacement en dehors du répertoire Windows, par exemple `C:\`.
  3. Ouvrez votre copie de Generalize.xml avec le Bloc-notes.
  4. Recherchez et supprimez les lignes suivantes. Une instance de chaque doit être supprimée (elles se trouvent vers la fin du document).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Enregistrez la copie modifiée de Generalize.xml et fermez le fichier.
  6. Ouvrez une invite de commandes en tant qu’administrateur.
  7. Exécutez la commande suivante pour prendre possession du fichier Generalize.xml dans le dossier system32 :

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Exécutez la commande suivante pour définir l’autorisation appropriée sur le fichier :

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Répondez Oui à l’invite de confirmation.
     - Notez que `<AdministratorUserName>` doit être remplacé par le nom d’utilisateur qui est administrateur sur l’ordinateur. Par exemple, « Administrateur ».

  9. Copiez le fichier que vous avez modifié et enregistré dans le répertoire Sysprep à l’aide de la commande suivante :

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Répondez Oui pour remplacer (vérifiez le chemin entré en l’absence d’invite de remplacement).
     - Cette commande suppose que votre copie modifiée de Generalize.xml a été copiée dans C:\.

  10. Generalize.XML est désormais mis à jour grâce à la solution de contournement. Exécutez Sysprep avec l’option generalize activée.