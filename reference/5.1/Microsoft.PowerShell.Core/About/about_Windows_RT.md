---
description: Explique les limitations de Windows PowerShell 4,0 sur Windows RT 8,1.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207505"
---
# <a name="about-windows-rt"></a>À propos de Windows RT

## <a name="short-description"></a>DESCRIPTION COURTE

Explique les limitations de Windows PowerShell 4,0 sur Windows RT 8,1.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le système d’exploitation Windows RT 8,1 est installé sur les ordinateurs et les périphériques (tels que Microsoft Surface 2, sur lequel il s’agit du système d’exploitation fourni avec l’ordinateur) qui utilisent des processeurs ARM (Advanced RISC machine).

Windows PowerShell 4,0 est inclus dans Windows RT 8,1. Toutes les applets de commande, tous les fournisseurs et tous les modules, ainsi que la plupart des scripts conçus pour Windows PowerShell 2,0 et versions ultérieures, s’exécutent sur Windows RT 8,1 sans aucune modification.

Étant donné que Windows RT 8,1 n’inclut pas toutes les fonctionnalités de Windows, certaines fonctionnalités de Windows PowerShell fonctionnent différemment ou ne fonctionnent pas sur les périphériques basés sur Windows RT. La liste suivante explique les différences.

- Windows PowerShell ISE n’est pas inclus dans et ne peut pas s’exécuter sur Windows RT 8,1.
  Windows PowerShell ISE nécessite Windows Presentation Foundation, qui n’est pas inclus dans Windows RT 8,1.

- La communication à distance Windows PowerShell et le service WinRM sont désactivés par défaut.
  Pour activer la communication à distance, exécutez l’applet de commande Enable-PSRemoting. Exécutez également l’applet de commande Set-Service pour définir le type de démarrage du service WinRM sur automatique ou automatique (début différé).

  Alors que la communication à distance est désactivée, vous pouvez utiliser la communication à distance Windows PowerShell pour exécuter des commandes sur d’autres ordinateurs, mais les autres ordinateurs ne peuvent pas exécuter de commandes sur l’appareil Windows RT. En outre, la communication à distance implicite, c’est-à-dire la communication à distance qui est intégrée à une applet de commande ou à un script, et qui n’est pas explicitement demandée avec des paramètres ajoutés
  - ne fonctionne pas dans Windows PowerShell s’exécutant sur Windows RT 8,1.

- L’informatique jointe à un domaine et l’authentification Kerberos ne sont pas prises en charge sur Windows RT 8,1. Vous ne pouvez pas utiliser Windows PowerShell pour ajouter ou gérer ces fonctionnalités.

- Les classes Microsoft .NET Framework qui ne sont pas prises en charge sur Windows RT 8,1 ne sont pas non plus prises en charge par Windows PowerShell sur Windows RT 8,1.

- Les transactions ne sont pas activées sur Windows RT 8,1. Les applets de commande de transaction, telles que start-transaction et les paramètres de transaction, tels que UseTransaction, ne fonctionnent pas correctement.

- Toutes les sessions Windows PowerShell sur les périphériques Windows RT 8,1 utilisent le mode de langage ConstrainedLanguage. Le mode ConstrainedLanguage Language est un complément de l’intégrité du code du mode utilisateur (UMCI). Il autorise toutes les applets de commande Windows et les éléments de langage Windows PowerShell, mais limite les types pour s’assurer que les utilisateurs ne peuvent pas utiliser Windows PowerShell pour contourner ou violer les protections UMCI.

Pour plus d’informations sur le mode de langage ConstrainedLanguage, consultez [about_Language_Modes](about_Language_Modes.md).

## <a name="see-also"></a>VOIR AUSSI

[about_Language_Modes](about_Language_Modes.md)

[about_Remote](about_Remote.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)
