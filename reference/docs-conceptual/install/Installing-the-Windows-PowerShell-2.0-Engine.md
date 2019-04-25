---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Installation du moteur Windows PowerShell 2.0
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: b625b61b4e191402074f57ea2e942f800dbbcd53
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058313"
---
# <a name="installing-the-windows-powershell-20-engine"></a>Installation du moteur Windows PowerShell 2.0
Cette rubrique explique comment installer le moteur Windows PowerShell 2.0.

Windows PowerShell 3.0 est conçu pour offrir une compatibilité descendante avec Windows PowerShell 2.0. Les applets de commande, fournisseurs, composants logiciels enfichables, modules et scripts écrits pour Windows PowerShell 2.0 s’exécutent sans modification dans Windows PowerShell 3.0 et Windows PowerShell 4.0. Toutefois, en raison d’une modification de la stratégie d’activation du runtime de Microsoft .NET Framework 4, les programmes hôtes de Windows PowerShell écrits pour Windows PowerShell 2.0 et compilés avec Common Language Runtime (CLR) 2.0 ne peuvent pas s’exécuter sans modification dans les versions ultérieures de Windows PowerShell, qui sont compilées avec CLR 4.0.

Pour assurer la compatibilité descendante avec les commandes et programmes hôtes qui sont affectés par ces modifications, les moteurs Windows PowerShell 2.0, Windows PowerShell 3.0 et Windows PowerShell 4.0 sont conçus pour s’exécuter côte à côte. En outre, le moteur Windows PowerShell 2.0 est inclus dans Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 et Windows Management Framework 3.0. Le moteur Windows PowerShell 2.0 est destiné à être utilisé uniquement quand un script ou un programme hôte existant ne peut pas s’exécuter parce qu’il n’est pas compatible avec Windows PowerShell 3.0, Windows PowerShell 4.0 ou Microsoft .NET Framework 4. Ces cas sont supposé être rares.

Le moteur Windows PowerShell 2.0 est une fonctionnalité facultative de Windows Server 2012 R2, Windows 8.1, Windows® 8 et Windows Server® 2012. Dans les versions antérieures de Windows, quand vous installez Windows Management Framework 3.0, l’installation de Windows PowerShell 3.0 remplace complètement l’installation de Windows PowerShell 2.0 dans le répertoire d’installation de Windows PowerShell. Toutefois, le moteur Windows PowerShell 2.0 est conservé.

Pour plus d’informations sur le démarrage du moteur Windows PowerShell 2.0, consultez [Démarrage du moteur Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>Sur Windows 8.1 et Windows 8
Sur Windows 8.1 et Windows 8, la fonctionnalité Moteur Windows PowerShell 2.0 est activée par défaut. Toutefois, pour l’utiliser, vous devez activer l’option pour Microsoft .NET Framework 3.5 dont il a besoin. Cette section explique également comment activer et désactiver la fonctionnalité Moteur Windows PowerShell 2.0.

#### <a name="to-turn-on-net-framework-35"></a>Pour activer .NET Framework 3.5

1. Dans l’écran **Démarrer**, tapez **Fonctionnalités Windows**.

2. Dans la barre **Applications**, cliquez sur **Paramètres**, puis sur **Activer ou désactiver des fonctionnalités Windows**.

3. Dans la zone **Fonctionnalités Windows**, cliquez sur **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)** pour sélectionner cette fonctionnalité.

    Lorsque vous sélectionnez **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, la zone indique que seule une partie de la fonctionnalité est activée. Toutefois, cela est suffisant pour le moteur Windows PowerShell 2.0.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Pour activer et désactiver le moteur Windows PowerShell 2.0

1. Dans l’écran **Démarrer**, tapez **Fonctionnalités Windows**.

2. Dans la barre **Applications**, cliquez sur **Paramètres**, puis sur **Activer ou désactiver des fonctionnalités Windows**.

3. Dans la boîte de dialogue **Fonctionnalités Windows**, développez le nœud **Windows PowerShell 2.0**, puis cliquez sur la case **Moteur Windows PowerShell 2.0** pour la cocher ou la décocher.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>Sur Windows Server 2012 R2 et Windows Server 2012
Procédez comme suit pour ajouter le moteur Windows PowerShell 2.0 et les fonctionnalités Microsoft .NET Framework 3.5. Le moteur Windows PowerShell 2.0 nécessite au minimum Microsoft .NET Framework 2.0.50727. Cette condition est remplie par Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Pour ajouter la fonctionnalité .NET Framework 3.5

1. Dans le **Gestionnaire de serveur**, dans le menu **Gérer**, cliquez sur **Ajouter des rôles et fonctionnalités**.

    Ou bien, dans le **Gestionnaire de serveur**, cliquez sur **Tous les serveurs**, cliquez avec le bouton droit sur un nom de serveur, puis sélectionnez **Ajouter des rôles et fonctionnalités**.

2. Dans la page **Type d’installation**, sélectionnez **Installation basée sur un rôle ou une fonctionnalité**.

3. Dans la page **Fonctionnalités**, développez le nœud **Fonctionnalités .NET Framework 3.5**, puis sélectionnez **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**.

    Les autres options sous ce nœud ne sont pas requises pour le moteur Windows PowerShell 2.0.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Pour ajouter la fonctionnalité Moteur Windows PowerShell 2.0

- Dans le **Gestionnaire de serveur**, dans le menu **Gérer**, cliquez sur **Ajouter des rôles et fonctionnalités**.

    Ou bien, dans **Gestionnaire de serveur**, cliquez sur **Tous les serveurs**, cliquez avec le bouton droit sur un nom de serveur, puis sélectionnez **Ajouter des rôles et fonctionnalités**.

- Dans la page **Type d’installation**, sélectionnez **Installation basée sur un rôle ou une fonctionnalité**.

- Dans la page **Fonctionnalités**, développez le nœud **Windows PowerShell (installé)** et sélectionnez **Moteur Windows PowerShell 2.0**.

Pour plus d’informations sur le démarrage du moteur Windows PowerShell 2.0, consultez [Démarrage du moteur Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Sur les systèmes antérieurs
Le package [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) qui installe Windows PowerShell 4.0 sur Windows 7, Windows Server 2008 R2 et Windows Server 2012 inclut le moteur Windows PowerShell 2.0. Le moteur Windows PowerShell 2.0 est activé et prêt à l’usage, si nécessaire, sans autre installation, paramétrage ou configuration.

Le package Windows Management Framework 3.0 qui installe Windows PowerShell 3.0 sur Windows 7, Windows Server 2008 R2 et Windows Server 2008 inclut le moteur Windows PowerShell 2.0. Le moteur Windows PowerShell 2.0 est activé et prêt à l’usage, si nécessaire, sans autre installation, paramétrage ou configuration.

## <a name="see-also"></a>Voir aussi
- [Configuration nécessaire pour Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Installation de Windows PowerShell](Installing-Windows-PowerShell.md)
- [Démarrage de Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Démarrage du moteur Windows PowerShell 2.0](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)