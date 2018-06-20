---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Préparation à l’utilisation de Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950965"
---
# <a name="getting-ready-to-use-windows-powershell"></a>Préparation à l’utilisation de Windows PowerShell
Une fois Windows PowerShell installé et démarré, envisagez les options de configuration suivantes. Vous pouvez effectuer ces tâches à tout moment.

- **Installez les fichiers d’aide.** Les applets de commande incluses dans Windows PowerShell 3.0 ne sont pas fournies avec des fichiers d’aide. En revanche, vous pouvez utiliser l’applet de commande [Update-Help](/powershell/module/microsoft.powershell.core/update-help) pour télécharger et installer les fichiers d’aide les plus récents sur votre ordinateur. Lorsque les fichiers sont installés, vous pouvez utiliser l’applet de commande [Get-Help](/powershell/module/microsoft.powershell.core/get-help) pour les afficher sur la ligne de commande. Pour plus d’informations, voir [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help).

    Si vous décidez de ne pas installer les fichiers d’aide, vous pouvez toujours lire les rubriques d’aide en ligne. Pour trouver la version en ligne de la rubrique d’aide relative à une applet de commande, tapez : `Get-Help <CmdletName> -Online`. Pour parcourir les rubriques d’aide de Windows PowerShell, consultez la [documentation de PowerShell](/powershell/scripting).

- **Exécutez les scripts.** Pour sécuriser Windows PowerShell, la stratégie d’exécution par défaut de Windows PowerShell est **Restricted**. Cette stratégie permet d’exécuter des applets de commande, mais pas des scripts. Pour exécuter des scripts, utilisez l’applet de commande [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) afin de modifier la stratégie d’exécution en la définissant sur **AllSigned** ou **RemoteSigned**. Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent exécuter cette applet de commande. Pour plus d’informations, consultez [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Activez la communication à distance.** Le système est déjà configuré pour exécuter des commandes à distance sur d’autres ordinateurs. Sur Windows Server 2012 R2 et Windows Server 2012, le système est également configuré pour recevoir des commandes à distance, c’est-à-dire pour permettre à d’autres ordinateurs d’exécuter des commandes à distance sur l’ordinateur local. Pour permettre à des ordinateurs exécutant d’autres versions de Windows de recevoir des commandes à distance, exécutez l’applet de commande [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) sur l’ordinateur que vous souhaitez gérer à distance. Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent exécuter cette applet de commande. Pour plus d’informations, voir [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote).

    REMARQUE : Si la communication à distance est activée sur un ordinateur exécutant Windows PowerShell 2.0, la communication à distance reste activée après l’installation de Windows Management Framework 3.0. Toutefois, sur Windows Server 2008 (pas sur Windows Server 2008 R2), vous devez réactiver la communication à distance après l’installation de Windows Management Framework 3.0.

## <a name="see-also"></a>Voir aussi
- [Installation de Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Démarrage de Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)