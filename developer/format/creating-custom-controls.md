---
title: Création de contrôles personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066683"
---
# <a name="creating-custom-controls"></a>Création de contrôles personnalisés

Les contrôles personnalisés sont les composants plus souples d’un fichier de mise en forme. Contrairement à la table, liste et affichage large qui définissent une structure formelle de données, telle qu’une table de données, des contrôles personnalisés permettent de définir l’affichage d’un élément individuel de données. Vous pouvez définir un ensemble commun de contrôles personnalisés qui sont disponibles pour toutes les vues du fichier de mise en forme, vous pouvez définir des contrôles personnalisés qui sont disponibles pour une vue spécifique, ou vous pouvez définir un ensemble de contrôles qui sont disponibles pour un groupe d’objets.

## <a name="custom-control-example"></a>Exemple de contrôle personnalisé

L’exemple suivant montre un contrôle personnalisé qui est défini dans le fichier Certificates.Format.ps1xml. Ce contrôle personnalisé est utilisé pour séparer les [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objets affichés dans un tableau.

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a>Voir aussi

[Écriture d’un fichier de mise en forme de PowerShell](./writing-a-powershell-formatting-file.md)
