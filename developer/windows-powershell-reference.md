---
title: Référence de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: dfda6cb68b089a30a156760345420ee80d1d3ae9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862105"
---
# <a name="windows-powershell-reference"></a>Informations de référence sur Windows PowerShell

Windows PowerShell est un environnement Microsoft connectées à .NET Framework, conçu pour l’automatisation administrative. Windows PowerShell fournit une nouvelle approche pour la création de commandes, de composition de solutions et de création d’outils de gestion basée sur l’interface utilisateur graphique.

Windows PowerShell permet à un administrateur système automatiser l’administration des ressources système par l’exécution des commandes directement ou via des scripts.

## <a name="developer-audience"></a>Développeurs concernés

Le Kit de développement logiciel (SDK) Windows PowerShell est écrit pour les développeurs de commande qui requièrent des informations de référence sur les API fournies par Windows PowerShell. Les développeurs de commande utiliser Windows PowerShell pour créer les commandes et les fournisseurs qui étendent les tâches qui peuvent être effectuées par Windows PowerShell.

## <a name="windows-powershell-resources"></a>Ressources de Windows PowerShell

Outre le Kit de développement Windows PowerShell, les ressources suivantes fournissent plus d’informations.

[Mise en route avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) fournit une introduction à Windows PowerShell : la langue, les applets de commande, les fournisseurs et l’utilisation d’objets.

[Écrire un PowerShell Module de Windows](./module/writing-a-windows-powershell-module.md) fournit des informations et des exemples pour les administrateurs, développeurs de script et les développeurs d’applet de commande qui doivent empaqueter et distribuer leurs solutions de Windows PowerShell à l’aide de modules Windows PowerShell.

[Écriture d’une applet de commande Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) fournit des exemples de code et des informations pour les responsables de programme qui concevez des applets de commande et pour les développeurs qui implémentent le code de l’applet de commande.

[Blog de l’équipe Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) la meilleure ressource pour l’apprentissage et la collaboration avec d’autres utilisateurs de Windows PowerShell. Lire le blog de l’équipe de Windows PowerShell et joignez le Forum des utilisateurs Windows PowerShell (microsoft.public.windows.powershell). Utiliser Windows Live Search pour rechercher d’autres blogs de Windows PowerShell et les ressources. Ensuite, lorsque vous développez votre expertise, librement Valorisez vos idées.

[Explorateur de modules PowerShell](/powershell/module/) fournit les dernières versions des rubriques d’aide en ligne de commande.

## <a name="class-libraries"></a>Bibliothèques de classes

[System.Management.Automation](/dotnet/api/System.Management.Automation) cet espace de noms est l’espace de noms racine pour Windows PowerShell. Il contient les classes, les énumérations et les interfaces requises pour implémenter des applets de commande personnalisées. En particulier, le [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) est la classe de base à partir de l’applet de commande qui toutes les classes doivent être dérivées. Pour plus d’informations sur les applets de commande, consultez.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) cet espace de noms contient les classes, les énumérations et les interfaces requises pour implémenter un fournisseur Windows PowerShell. En particulier, le [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) est la classe de base à partir de quels PowerShell Windows toutes les classes de fournisseur doivent être dérivées.

[Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) cet espace de noms contient les classes pour les applets de commande et les fournisseurs implémentés par Windows PowerShell. De même, il est recommandé de créer un *YourName*. Espace de noms pour ces applets de commande que vous implémentez des commandes.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) cet espace de noms contient les classes, les énumérations et les interfaces que l’applet de commande utilise pour définir l’interaction entre l’utilisateur et Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) cet espace de noms contient les classes de base utilisées par d’autres classes de l’espace de noms. Par exemple, le [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) est la classe de base pour le [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) cet espace de noms contient les classes, les énumérations et les interfaces utilisées pour créer une instance d’exécution Windows PowerShell. Dans ce contexte, l’instance d’exécution Windows PowerShell est le contexte dans lequel un ou plusieurs pipelines de Windows PowerShell appellent les applets de commande. Autrement dit, les applets de commande fonctionnent dans le contexte d’une instance d’exécution Windows PowerShell. Pour plus d’informations aboutWindows une instances d’exécution de PowerShell, consultez [Windows PowerShell Runspaces](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
