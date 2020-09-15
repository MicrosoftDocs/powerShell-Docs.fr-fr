---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation du moteur Windows PowerShell 2.0
ms.openlocfilehash: c5ac92159d63e5669643908016186ed32dfb46db
ms.sourcegitcommit: 3e343f005fe76960c998ef1869a1a093d37ef349
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216020"
---
# <a name="using-the-windows-powershell-20-engine"></a>Utilisation du moteur Windows PowerShell 2.0

Windows PowerShell est conçu pour offrir une compatibilité descendante avec des versions précédentes. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour Windows PowerShell 2.0 s’exécutent sans modification dans les versions plus récentes de Windows PowerShell. Toutefois, Microsoft .NET Framework 4 a changé la stratégie d’activation du runtime.
Les programmes hôtes de Windows PowerShell écrits pour Windows PowerShell 2.0 et compilés avec Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans les nouvelles versions de Windows PowerShell qui sont compilées avec CLR 4.0 (ou version ultérieure).

Le moteur Windows PowerShell 2.0 est destiné à être utilisé uniquement quand un script ou un programme hôte existant ne peut pas s’exécuter car il n’est pas compatible avec Windows PowerShell 5.1. Il peut s’agir, par exemple, de versions antérieures de modules Exchange ou SQL Server. Ces cas sont supposé être rares.

De nombreux programmes qui nécessitent le moteur Windows PowerShell 2.0 le démarrent automatiquement. Ces instructions sont fournies pour les rares cas où vous devez démarrer le moteur manuellement.

## <a name="deprecation-and-security-concerns"></a>Dépréciation et problèmes de sécurité

Windows PowerShell 2.0 a été déprécié en août 2017. Pour plus d’informations, consultez l’[annonce][] sur le blog PowerShell.

Windows PowerShell 2.0 ne dispose pas d’une quantité importante de fonctionnalités de sécurisation de renforcement et de sécurité qui ont été ajoutées dans les versions 3, 4 et 5. Nous recommandons vivement aux utilisateurs de ne pas l’utiliser, s’ils peuvent l’éviter. Pour plus d’informations, consultez [Comparaison de l’interpréteur de commandes et de la sécurité du langage de script][] et [PowerShell ♥ the Blue Team][blueteam].

## <a name="installing-and-enabling-required-programs"></a>Installation et activation des programmes requis

Avant de démarrer le moteur Windows PowerShell 2.0, activez le moteur Windows PowerShell 2.0 et Microsoft .NET Framework 3.5 avec Service Pack 1. Pour obtenir des instructions, voir [Installation de Windows PowerShell][].

Les systèmes sur lesquels Windows Management Framework 3.0 ou les versions ultérieures sont installés disposent de tous les composants nécessaires. Aucune autre configuration n’est nécessaire. Pour plus d’informations sur l’installation de Windows Management Framework, consultez [Installer et configurer WMF][].

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Comment démarrer le moteur Windows PowerShell 2.0

Quand vous démarrez Windows PowerShell, la version la plus récente démarre par défaut. Pour démarrer Windows PowerShell avec le moteur Windows PowerShell 2.0, utilisez le paramètre Version de `PowerShell.exe`. Vous pouvez exécuter la commande à tout invite de commandes, y compris de Windows PowerShell et de Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Comment démarrer une session à distance avec le moteur Windows PowerShell 2.0

Pour exécuter le moteur Windows PowerShell 2.0 dans une session à distance, créez une configuration de session (également appelée _point de terminaison_) sur l’ordinateur distant qui charge le moteur Windows PowerShell 2.0. La configuration de session est enregistrée sur l’ordinateur distant et peut être utilisée par toute personne autorisée à créer des sessions faisant appel au moteur Windows PowerShell 2.0.

Il s’agit d’une tâche avancée généralement effectuée par un administrateur système.

La procédure suivante utilise le paramètre **PSVersion** de l’applet de commande [Register-PSSessionConfiguration][] pour créer une configuration de session qui utilise le moteur Windows PowerShell 2.0. Vous pouvez également utiliser le paramètre **PowerShellVersion** de l’applet de comment [New-PSSessionConfigurationFile][] pour créer un fichier de configuration de session pour une session qui charge le moteur Windows PowerShell 2.0, et pouvez utiliser le paramètre **PSVersion** de l’applet de commande [Set-PSSessionConfiguration][] pour modifier une configuration de session afin d’utiliser le moteur Windows PowerShell 2.0.

Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files][].
Pour obtenir des informations sur les configurations de session, notamment l’installation et la sécurité, consultez [about_Session_Configurations][].

### <a name="to-start-a-remote-windows-powershell-20-session"></a>Pour démarrer une session Windows PowerShell 2.0 à distance

1. Pour créer une configuration de session qui nécessite le moteur Windows PowerShell 2.0, utilisez le paramètre **PSVersion** de l’applet de commande `Register-PSSessionConfiguration` avec la valeur `2.0`.
   Exécutez cette commande sur l’ordinateur « côté serveur » ou en fin de réception de la connexion.

   L’exemple de commande suivant crée la configuration de session PS2 sur l’ordinateur Server01. Pour exécuter cette commande, démarrez Windows PowerShell avec l’option **Exécuter en tant qu’administrateur**.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. Pour créer une session sur l’ordinateur Server01 qui utilise la configuration de session PS2, utilisez le paramètre **ConfigurationName** d’applets de commande qui créent une session à distance, comme l’applet de commande « New-PSSession ».

   Quand une session utilisant la configuration de session démarre, le moteur Windows PowerShell 2.0 est automatiquement chargé dans la session.

   La commande suivante démarre une session sur l’ordinateur Server01 qui utilise la configuration de session PS2. La commande enregistre la session dans la variable `$s`.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Comment démarrer un travail en arrière-plan avec le moteur Windows PowerShell 2.0

Pour démarrer un travail en arrière-plan avec le moteur Windows PowerShell 2.0, utilisez le paramètre **PSVersion** de l’applet de commande [Start-Job][].

La commande suivante démarre un travail en arrière-plan avec le moteur Windows PowerShell 2.0.

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Pour plus d’informations sur les tâches en arrière-plan, consultez [about_Jobs][].

<!-- link references -->
[Annonce]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Comparaison de l’interpréteur de commandes et de la sécurité du langage de script]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Installation de Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installer et configurer WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfigurationFile
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
