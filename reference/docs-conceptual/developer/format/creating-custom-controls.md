---
title: Création de contrôles personnalisés | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c36fa9b778e01501a3c88f735cdefdfbb04411a0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786116"
---
# <a name="creating-custom-controls"></a>Création de contrôles personnalisés

Les contrôles personnalisés sont les composants les plus flexibles d’un fichier de mise en forme. Contrairement aux vues table, liste et larges qui définissent une structure formelle de données, telles qu’une table de données, les contrôles personnalisés vous permettent de définir la manière dont un élément de données individuel est affiché. Vous pouvez définir un ensemble commun de contrôles personnalisés qui sont disponibles pour toutes les vues du fichier de mise en forme, vous pouvez définir des contrôles personnalisés qui sont disponibles pour un affichage spécifique, ou vous pouvez définir un ensemble de contrôles disponibles pour un groupe d’objets.

## <a name="custom-control-example"></a>Exemple de contrôle personnalisé

L’exemple suivant montre un contrôle personnalisé défini dans le fichier XML Certificates.Format.ps1. Ce contrôle personnalisé est utilisé pour séparer les objets [System. Management. Automation. signature](/dotnet/api/System.Management.Automation.Signature) affichés dans une vue table.

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

[Écriture d’un fichier de mise en forme PowerShell](./writing-a-powershell-formatting-file.md)
