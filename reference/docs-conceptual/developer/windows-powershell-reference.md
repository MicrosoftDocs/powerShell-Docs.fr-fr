---
title: Informations de référence sur Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Windows PowerShell SDK
ms.openlocfilehash: 1c1a3a4de2df2043fe12cad6a69b7bc36ab9d3d7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786677"
---
# <a name="windows-powershell-reference"></a>Informations de référence sur Windows PowerShell

Windows PowerShell est un environnement connecté Microsoft .NET Framework conçu pour l’automatisation administrative. Windows PowerShell offre une nouvelle approche pour créer des commandes, composer des solutions et créer des outils de gestion basés sur une interface graphique utilisateur.

Windows PowerShell permet à un administrateur système d’automatiser l’administration des ressources système par l’exécution de commandes soit directement, soit par le biais de scripts.

## <a name="developer-audience"></a>Public de développeurs

Le kit de développement logiciel (SDK) Windows PowerShell est conçu pour les développeurs de commande qui requièrent des informations de référence sur les API fournies par Windows PowerShell. Les développeurs de commandes utilisent Windows PowerShell pour créer des commandes et des fournisseurs qui étendent les tâches qui peuvent être effectuées par Windows PowerShell.

## <a name="windows-powershell-resources"></a>Ressources Windows PowerShell

En plus du kit de développement logiciel (SDK) Windows PowerShell, les ressources suivantes fournissent plus d’informations.

[Prise en main avec Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Fournit une introduction à Windows PowerShell : langage, applets de commande, fournisseurs et utilisation d’objets.

[Écriture d’un module Windows PowerShell](./module/writing-a-windows-powershell-module.md) Fournit des informations et des exemples pour les administrateurs, les développeurs de scripts et les développeurs d’applets de commande qui doivent empaqueter et distribuer leurs solutions Windows PowerShell à l’aide de modules Windows PowerShell.

[Écriture d’une applet de commande Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) Fournit des informations et des exemples de code pour les responsables de programme qui conçoivent des applets de commande et pour les développeurs qui implémentent du code d’applet de commande.

[Blog de l’équipe Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) La meilleure ressource pour l’apprentissage et la collaboration avec d’autres utilisateurs de Windows PowerShell. Lisez le blog de l’équipe Windows PowerShell, puis joignez le Forum des utilisateurs Windows PowerShell (Microsoft. public. Windows. PowerShell).
Utilisez Windows Live Search pour rechercher d’autres blogs et ressources Windows PowerShell. Ensuite, à mesure que vous développez votre expertise, participez librement à vos idées.

[Explorateur de modules PowerShell](/powershell/module/) Fournit les dernières versions des rubriques d’aide de la ligne de commande.

## <a name="class-libraries"></a>Bibliothèques de classes

[System. Management. Automation](/dotnet/api/System.Management.Automation) cet espace de noms est l’espace de noms racine pour Windows PowerShell. Il contient les classes, les énumérations et les interfaces requises pour implémenter des applets de commande personnalisées. En particulier, la classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) est la classe de base à partir de laquelle toutes les classes d’applet de commande doivent être dérivées. Pour plus d’informations sur les applets de commande, consultez.

[System. Management. Automation. Provider](/dotnet/api/System.Management.Automation.Provider) cet espace de noms contient les classes, les énumérations et les interfaces requises pour implémenter un fournisseur Windows PowerShell. En particulier, la classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) est la classe de base à partir de laquelle toutes les classes du fournisseur Windows PowerShell doivent être dérivées.

[Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) cet espace de noms contient les classes pour les applets de commande et les fournisseurs implémentés par Windows PowerShell. De même, il est recommandé de créer une *votre_nom*. Espace de noms Commands pour les applets de commande que vous implémentez.

[System. Management. Automation. Host](/dotnet/api/System.Management.Automation.Host) cet espace de noms contient les classes, les énumérations et les interfaces que l’applet de commande utilise pour définir l’interaction entre l’utilisateur et Windows PowerShell.

[System. Management. Automation. Internal](/dotnet/api/System.Management.Automation.Internal) cet espace de noms contient les classes de base utilisées par d’autres classes d’espace de noms. Par exemple, la classe [System. Management. Automation. Internal. Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) est la classe de base pour la classe [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .

[System. Management. Automation. instances d’exécution](/dotnet/api/System.Management.Automation.Runspaces) cet espace de noms contient les classes, les énumérations et les interfaces utilisées pour créer une instance d’exécution Windows PowerShell. Dans ce contexte, l’instance d’exécution Windows PowerShell est le contexte dans lequel un ou plusieurs pipelines Windows PowerShell appellent des applets de commande. Autrement dit, les applets de commande fonctionnent dans le contexte d’une instance d’exécution Windows PowerShell. Pour plus d’informations sur aboutWindows PowerShell instances d’exécution, consultez [Windows PowerShell instances d’exécution](hosting/creating-runspaces.md).
