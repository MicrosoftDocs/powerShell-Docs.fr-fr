---
title: Nouveautés de PowerShell 7.1
description: Nouvelles fonctionnalités et modifications de PowerShell 7.1
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577205"
---
# <a name="whats-new-in-powershell-71"></a>Nouveautés de PowerShell 7.1

Le 11 novembre 2020, nous avons [annoncé](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) la disponibilité générale de PowerShell 7.1. En s'appuyant sur les bases établies dans PowerShell 7.0, nos efforts se sont concentrés sur les questions soulevées par la communauté et comprennent un certain nombre d'améliorations et de corrections. Nous nous engageons à faire en sorte que PowerShell reste une plateforme stable et performante.

PowerShell 7.1 comprend les fonctionnalités, les mises à jour et les changements cassants suivants.

- PSReadLine 2.1.0, qui comprend IntelliSense prédictif
- Publication de PowerShell 7.1 sur le Microsoft Store
- Mise à jour des packages d’installation pour les nouvelles versions de système d’exploitation avec prise en charge d’ARM64
- Officialisation de 4 nouvelles fonctionnalités expérimentales et 2 fonctionnalités expérimentales
- Divers changements cassants pour améliorer l’utilisabilité

Pour obtenir la liste complète des changements, consultez [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) dans le dépôt GitHub.

## <a name="psreadline-210"></a>PSReadline 2.1.0

PowerShell 7.1 inclut également PSReadLine 2.1.0. Cette version comprend IntelliSense prédictif. Pour plus d’informations sur la fonctionnalité IntelliSense prédictive, consultez l’[annonce](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) dans le blog PowerShell.

## <a name="microsoft-store-installer-package"></a>Package d’installation Microsoft Store

PowerShell 7.1 a été publié sur le Microsoft Store. Vous trouverez la version PowerShell sur le site Web du [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) ou dans l’application Store de Windows.

Avantages du package Microsoft Store :

- Mises à jour automatiques intégrées à Windows 10
- S’intègre à d’autres mécanismes de distribution de logiciels comme Intune et SCCM

> [!NOTE]
> Les paramètres de configuration au niveau du système, stockés dans `$PSHOME`, ne peuvent pas être modifiés. Cela comprend la configuration WSMAN. Cette stratégie empêche les sessions à distance de se connecter aux installations basées sur le magasin de PowerShell. Les configurations au niveau de l’utilisateur et l’accès à distance SSH sont pris en charge.

## <a name="other-installers"></a>Autres programmes d’installation

Pour plus d’informations à jour sur les systèmes d’exploitation pris en charge et le cycle de vie de support, consultez le [cycle de vie du support PowerShell](/powershell/scripting/powershell-support-lifecycle).

Consultez les instructions d’installation pour votre système d’exploitation par défaut :

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

En outre, PowerShell 7.1 prend en charge les versions ARM32 et ARM64 de Debian, Ubuntu et ARM64 Alpine Linux.

Bien qu’ils ne soit pas officiellement pris en charge, la communauté a également fourni des packages pour [Arch](https://aur.archlinux.org/packages/powershell/) et Kali Linux.

> [!NOTE]
> Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine et Arm ne prennent actuellement pas en charge la communication à distance WinRM. Pour plus d’informations sur la configuration de la communication à distance basée sur SSH, consultez [Communication à distance PowerShell via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="experimental-features"></a>Fonctionnalités expérimentales

Pour plus d’informations sur les fonctionnalités expérimentales, consultez [Utilisation des fonctionnalités expérimentales](../learn/experimental-features.md).

Les fonctionnalités expérimentales suivantes sont maintenant devenues des fonctionnalités standard dans cette version :

- [PSNullConditionalOperators](../learn/experimental-features.md#psnullconditionaloperators)
- [PSUnixFileStat](../learn/experimental-features.md#psunixfilestat)

Les fonctionnalités expérimentales suivantes ont été ajoutées dans cette version :

- [Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - PowerShell 7.1 étend cette fonctionnalité expérimentale pour ajouter le paramètre **Runspace** à toutes les applets de commande `*-PSBreakpoint`. Le paramètre **Runspace** spécifie un objet **Runspace** pour interagir avec des points d’arrêt dans l’instance d’exécution spécifiée.

- [PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - Cette fonctionnalité vous permet de passer des chemins de fournisseur PowerShell à des commandes natives qui ne prennent pas en charge la syntaxe de chemin de PowerShell.

- [PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - Lorsque l’opérande gauche dans une instruction opérateur `-replace` n’est pas une chaîne, cet opérande est converti en chaîne. Lorsque la fonctionnalité est activée, la conversion n’utilise pas les paramètres de culture pour la conversion de chaînes.

- [PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) permet de prendre en charge les futurs plug-ins IntelliSense prédictif.

## <a name="breaking-changes-and-improvements"></a>Dernières modifications et améliorations

- Correction de `$?` pour ne pas être `$false` lorsque la commande native écrit dans `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))

  Il est courant que les commandes natives écrivent dans `stderr` sans avoir à indiquer un échec.
  Avec ce changement, `$?` a la valeur `$false` uniquement lorsque la commande native a également un code de sortie différent de zéro. Ce changement n’est pas lié à la fonctionnalité expérimentale `PSNotApplyErrorActionToStderr`.

- Configuration de `$ErrorActionPreference` pour ne pas affecter la sortie `stderr` des commandes natives ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))

  Il est courant que les commandes natives écrivent dans `stderr` sans avoir à indiquer un échec.
  Avec ce changement, la sortie `stderr` est toujours capturée dans les objets **ErrorRecord**, mais le runtime n’applique plus `$ErrorActionPreference` si le **ErrorRecord** provient d’une commande native.

- Renommage de `-FromUnixTime` en `-UnixTimeSeconds` sur `Get-Date` pour autoriser l’entrée de temps UNIX ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (Merci @aetos382 !)

  Le paramètre `-FromUnixTime` a été ajouté pendant 7.1-preview.2. Le paramètre a été renommé pour mieux correspondre au type de données. Ce paramètre prend une valeur entière qui est représentée en secondes depuis le 1er janvier 1970, 0:00:00.

  Cet exemple convertit une heure UNIX (représentée par le nombre de secondes depuis le 01-01-1970 0:00:00) en DateHeure.

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- Autoriser le paramètre nommé explicitement spécifié à remplacer le même paramètre dans la projection de la table de hachage (#13162)

  Avec ce changement, les paramètres nommés de la projection sont déplacés à la fin de la liste de paramètres afin qu’ils soient liés une fois que tous les paramètres nommés explicitement spécifiés sont liés. La liaison de paramètre pour les fonctions simples ne génère pas d’erreur quand un paramètre nommé spécifié est introuvable. Les paramètres nommés inconnus sont liés au paramètre `$args` de la fonction simple. Le déplacement de la projection à la fin de la liste d’arguments change l’ordre dans lequel les paramètres apparaissent dans `$args`.

  Par exemple :

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  Dans le comportement précédent, **MyPath** n’est pas lié à `-Path` , car il s’agit du troisième argument dans la liste d’arguments. # # Donc, il finit par être placé dans « $args » avec `Blah = "World"`

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  Avec ce changement, les arguments de `@hash` sont déplacés à la fin de la liste d’arguments. **MyPath** devient le premier argument de la liste, donc il est lié à `-Path`.

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- Rendre le paramètre de commutateur `-Qualifier` non positionnel pour `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (Merci @yecril71pl !)

- Correction du répertoire de travail comme chemin littéral pour `Start-Process` lorsqu’il n’est pas spécifié ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (Merci @NoMoreFood !)

- Modification du paramètre `-OutFile` dans les applets de commande web pour qu’il fonctionne comme `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (Merci @iSazonov !)

- Correction de la liaison de paramètre de chaîne pour les littéraux numériques `BigInteger` ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (Merci @vexx32 !)

- Sur Windows, `Start-Process` crée un environnement de processus avec toutes les variables d’environnement à partir de la session active, et `-UseNewEnvironment` crée un nouvel environnement de processus par défaut ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (Merci @iSazonov !)

- Résultat non wrappé dans `PSObject` lors de la conversion de `ScriptBlock` en délégué ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))

  Quand un `ScriptBlock` est converti en type délégué à utiliser dans un contexte C#, le wrapping du résultat dans un `PSObject` pose des problèmes inutiles :

  - Lorsque la valeur est convertie en type de retour délégué, `PSObject` n’est pas wrappé par essence. Donc `PSObject` n’est pas nécessaire.
  - Lorsque le type de retour délégué est `object`, il est wrappé dans un `PSObject`, ce qui rend difficile son utilisation dans le code C#.

  Après ce changement, l’objet retourné est l’objet sous-jacent.
