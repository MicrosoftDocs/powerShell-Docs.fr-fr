---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code AccessDbProviderSample02
description: Exemple de code AccessDbProviderSample02
ms.openlocfilehash: f467ee59b36027e80852ae1f7b2f1af5c9aa8569
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659398"
---
# <a name="accessdbprovidersample02-code-sample"></a>Exemple de code AccessDbProviderSample02

Le code suivant illustre l’implémentation du fournisseur Windows PowerShell décrit dans [création d’un fournisseur de lecteurs Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).
Cette implémentation crée un chemin d’accès, établit une connexion à une base de données Access, puis supprime le lecteur.

> [!NOTE]
> Vous pouvez télécharger le fichier source C# (AccessDBSampleProvider02.cs) pour ce fournisseur à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et Microsoft .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire. Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Exemple de code

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
