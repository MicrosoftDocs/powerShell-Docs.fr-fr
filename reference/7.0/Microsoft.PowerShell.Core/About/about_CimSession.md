---
description: Décrit un objet **CimSession** et la différence entre les sessions CIM et les sessions PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 21015e1457dfcc037dd65cbf3b2f7f85c9076106
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206662"
---
# <a name="about-cimsession"></a>À propos de CimSession

## <a name="short-description"></a>Description courte
Décrit un objet **CimSession** et la différence entre les sessions CIM et les sessions PowerShell.

## <a name="long-description"></a>Description longue

Une session Common Information Model (CIM) est un objet côté client qui représente une connexion à un ordinateur local ou à un ordinateur distant. Vous pouvez utiliser des sessions CIM comme alternative aux sessions PowerShell (sessions PSSession). Les deux approches ont des avantages.

Vous pouvez utiliser l' `New-CimSession` applet de commande pour créer une session CIM qui contient des informations sur une connexion, telles que le nom de l’ordinateur, le protocole utilisé pour la connexion, l’ID de session et l’ID d’instance.

Une fois que vous avez créé un objet **CimSession** qui spécifie les informations requises pour établir une connexion, PowerShell n’établit pas la connexion immédiatement. Quand une applet de commande utilise la session CIM, PowerShell se connecte à l’ordinateur spécifié, puis, une fois l’applet de commande terminée, PowerShell met fin à la connexion.

Si vous créez une session **PSSession** au lieu d’utiliser une session CIM, PowerShell valide les paramètres de connexion, puis établit et maintient la connexion. Si vous utilisez des sessions CIM, PowerShell n’ouvre pas de connexion réseau tant que nécessaire. Pour plus d’informations sur les sessions PowerShell, consultez [about_PSSessions](about_PSSessions.md).

## <a name="when-to-use-a-cim-session"></a>Quand utiliser une session CIM

Seules les applets de commande qui fonctionnent avec un fournisseur Windows Management Instrumentation (WMI) ou CIM sur WS-Man acceptent les sessions CIM. Pour les autres applets de commande, utilisez **sessions PSSession** .

Lorsque vous utilisez une session CIM, PowerShell exécute l’applet de commande sur le client local. Il se connecte au fournisseur WMI à l’aide de la session CIM. L’ordinateur cible ne nécessite pas PowerShell, ni même aucune version du système d’exploitation Windows.

En revanche, une applet de commande s’exécute à l’aide d’une **session PSSession** s’exécute sur l’ordinateur cible.
Il nécessite PowerShell sur le système cible. En outre, l’applet de commande renvoie des données à l’ordinateur local. PowerShell gère les données envoyées sur la connexion et conserve la taille dans les limites définies par Windows Remote Management (WinRM). Les sessions CIM n’imposent pas les limites WinRM.

## <a name="using-cdxml-cmdlets"></a>Utilisation des applets de commande CDXML

Vous pouvez écrire des applets de commande de définition d’applets de commande (CDXML) basées sur CIM pour utiliser n’importe quel fournisseur WMI. Tous les fournisseurs WMI utilisent des objets **CimSession** . Pour plus d’informations sur CDXML, consultez [définition et termes du cdxml](/previous-versions/windows/desktop/wmi_v2/cdxml-overview).

Les applets de commande CDXML ont un paramètre **CimSession** automatique qui peut prendre un tableau d’objets **CimSession** . Par défaut, PowerShell limite le nombre de connexions simultanées CIM à 15. Cette limite peut être remplacée par les applets de commande CDXML qui implémentent **ThrottleLimit** . Consultez la documentation de l’applet de commande pour comprendre le **ThrottleLimit** .

## <a name="see-also"></a>VOIR AUSSI

[New-CimSession](xref:CimCmdlets.New-CimSession)

[about_PSSessions](about_PSSessions.md)
