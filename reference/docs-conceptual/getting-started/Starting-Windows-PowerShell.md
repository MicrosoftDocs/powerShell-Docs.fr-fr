---
ms.date: 12/05/2019
keywords: powershell,applet de commande
title: Démarrage de Windows PowerShell
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953821"
---
# <a name="starting-windows-powershell"></a>Démarrage de Windows PowerShell

Windows PowerShell est une entité `.DLL` de moteur de script qui est incorporée dans plusieurs hôtes. Les hôtes les plus courants que vous démarrerez sont l’outil interactif **powershell.exe** de ligne de commande et l’environnement d’écriture de scripts interactif **powershell_ise.exe**.

Pour démarrer Windows PowerShell® sur Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 et Windows 8, consultez [Tâches de gestion courantes et navigation dans Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).

## <a name="powershell-core-has-renamed-binary"></a>PowerShell Core a un fichier binaire renommé

PowerShell Core (version 6 ou ultérieure), connu en tant que PowerShell, est open source et utilise .NET Core. Les versions prises en charge sont disponibles sur Windows, macOS et Linux.

Depuis PowerShell 6, le fichier binaire PowerShell a été renommé **pwsh.exe** pour Windows et **pwsh** pour macOS et Linux. Vous pouvez démarrer les préversions de PowerShell à l’aide de **pwsh-preview**. Pour plus d’informations, consultez [Nouveautés de PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) et [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).

Pour trouver la référence des applets de commande et la documentation d’installation de PowerShell 7, utilisez les liens suivants :

| Document | Lien |
| ----- | ----- |
| Référence des applets de commande | [Navigateur du module PowerShell](/powershell/module/?view=powershell-7) |
| Installation sur Windows | [Installation de PowerShell Core sur Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| Installation sur macOS | [Installation de PowerShell Core sur macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| Installation sur Linux | [Installation de PowerShell Core sur Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

Pour afficher du contenu pour d’autres versions de PowerShell, consultez [Guide pratique pour utiliser la documentation PowerShell](../how-to-use-docs.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Comment démarrer Windows PowerShell sur des versions antérieures de Windows

Cette section explique comment démarrer Windows PowerShell et l’environnement d’écriture de scripts intégré (ISE) de Windows PowerShell sur Windows® 7, Windows Server® 2008 R2 et Windows Server 2008. Elle explique également comment activer la fonctionnalité facultative pour Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server® 2008 R2 et Windows Server® 2008.

Pour démarrer la version installée de Windows PowerShell 3.0 ou Windows PowerShell 4.0, le cas échéant, utilisez une des méthodes suivantes.

#### <a name="from-the-start-menu"></a>À partir du menu Démarrer

- Cliquez sur **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell**.
- À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>À l’invite de commandes

Dans **cmd.exe**, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :

```
PowerShell
```

Vous pouvez également utiliser les paramètres du programme **powershell.exe** pour personnaliser la session. Pour plus d’informations, voir [Aide sur la ligne de commande PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Avec des privilèges d’administration (Exécuter en tant qu’administrateur)

Cliquez sur **Démarrer**, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell**, puis cliquez sur **Exécuter en tant qu’administrateur**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Comment démarrer Windows PowerShell ISE sur des versions antérieures de Windows

Utilisez une des méthodes suivantes pour démarrer Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>À partir du menu Démarrer

- Cliquez sur **Démarrer**, tapez **ISE**, puis cliquez sur **Windows PowerShell ISE**.
- À partir du menu **Démarrer**, cliquez sur **Démarrer**, **Tous les programmes**, **Accessoires**, cliquez sur le dossier **Windows PowerShell**, puis sur **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>À l’invite de commandes

Dans **cmd.exe**, Windows PowerShell ou Windows PowerShell ISE, pour démarrer Windows PowerShell, tapez :

```
PowerShell_ISE
```

ou

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Avec des privilèges d’administration (Exécuter en tant qu’administrateur)

Cliquez sur **Démarrer**, tapez **ISE**, cliquez avec le bouton droit sur **Windows PowerShell ISE**, puis cliquez sur **Exécuter en tant qu’administrateur**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Comment activer Windows PowerShell ISE sur des versions antérieures de Windows

Dans Windows PowerShell 4.0 et Windows PowerShell 3.0, Windows PowerShell ISE est activé par défaut sur toutes les versions de Windows. S’il n’est pas déjà activé, Windows Management Framework 4.0 ou Windows Management Framework 3.0 l’active.

Dans Windows PowerShell 2.0, Windows PowerShell ISE est activé par défaut sur Windows 7. Toutefois, sur Windows Server 2008 R2 et Windows Server 2008, il s’agit d’une fonctionnalité facultative.

Pour activer Windows PowerShell ISE dans Windows PowerShell 2.0 sur Windows Server 2008 R2 ou Windows Server 2008, utilisez la procédure suivante.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Pour activer Windows PowerShell Integrated Scripting Environment (ISE)

1. Démarrez le Gestionnaire de serveur.
2. Cliquez sur **Fonctionnalités**, puis sur **Ajouter des fonctionnalités**.
3. Dans Sélectionner des fonctionnalités, cliquez sur Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Démarrage de la Version 32 bits de Windows PowerShell

Quand vous installez Windows PowerShell sur un ordinateur 64 bits, **Windows PowerShell (x86)** , version 32 bits de Windows PowerShell, est installé en plus de la version 64 bits. Quand vous exécutez Windows PowerShell, la version 64 bits s’exécute par défaut.

Toutefois, il se peut que vous deviez occasionnellement exécuter **Windows PowerShell (x86)** , par exemple, lorsque vous utilisez un module nécessitant la version 32 bits ou lorsque vous vous connectez à distance à un ordinateur 32 bits.

Pour démarrer une version 32 bits de Windows PowerShell, procédez de l’une des manières suivantes.

#### <a name="in-windows-server-2012-r2"></a>Dans Windows Server® 2012 R2

- Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)** . Cliquez sur la vignette **Windows PowerShell x86**.
- Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)** .
- Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)** .
- Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>Dans Windows Server® 2012

- Dans l’écran **Démarrer**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)** .
- Dans **Server Manager**, dans le menu **Outils**, sélectionnez **Windows PowerShell (x86)** .
- Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **recherche**, tapez **PowerShell**, puis cliquez sur **Windows PowerShell (x86)** .
- Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>Dans Windows® 8.1

- Dans l’écran **Démarrer**, tapez **Windows PowerShell (x86)** . Cliquez sur la vignette **Windows PowerShell x86**.
- Si vous exécutez les [Outils d’administration de serveur distant](https://go.microsoft.com/fwlink/?LinkID=304145) pour Windows 8.1, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**. Sélectionnez **Windows PowerShell (x86)** .
- Sur le Bureau, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Recherche**, tapez **PowerShell x86**, puis cliquez sur **Windows PowerShell (x86)** .
- Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>Dans Windows® 8

- Dans l’écran **Démarrer**, déplacez le curseur vers l’angle supérieur droit, cliquez sur **Paramètres**, **Vignettes**, puis positionnez le curseur **Afficher les outils d’administration** sur **Oui**. Ensuite, tapez **PowerShell** puis cliquez sur **Windows PowerShell (x86)** .
- Si vous exécutez les [Outils d’administration de serveur distant](https://www.microsoft.com/download/details.aspx?id=28972) pour Windows 8, vous pouvez également ouvrir Windows PowerShell x86 à partir du menu **Outils du Gestionnaire de serveur**. Sélectionnez **Windows PowerShell (x86)** .
- Dans l’écran **Démarrer** ou sur le Bureau, tapez **PowerShell (x86)** , puis cliquez sur **Windows PowerShell (x86)** .
- Via la ligne de commande, entrez : `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
