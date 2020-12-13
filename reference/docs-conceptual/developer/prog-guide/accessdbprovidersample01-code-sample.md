---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code AccessDbProviderSample01
description: Exemple de code AccessDbProviderSample01
ms.openlocfilehash: 5be593b9e86347b2f55de156fe4d9b44cfab5b78
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659419"
---
# <a name="accessdbprovidersample01-code-sample"></a>Exemple de code AccessDbProviderSample01

Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md).
Cette implémentation fournit des méthodes pour démarrer et arrêter le fournisseur et, bien qu’elle ne fournisse pas de moyen d’accéder à un magasin de données ou d’obtenir ou de définir les données dans le magasin de données, elle fournit les fonctionnalités de base requises par tous les fournisseurs.

> [!NOTE]
> Vous pouvez télécharger le fichier source C# (AccessDBSampleProvider01.cs) pour ce fournisseur à l’aide du kit de développement logiciel Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire. Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
