---
ms.date: 09/13/2016
ms.topic: reference
title: Création de contrôles personnalisés
description: Création de contrôles personnalisés
ms.openlocfilehash: 78d8cc2970b2b3e493bef25d78404ba1be195bb1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668046"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="17cc7-103">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="17cc7-103">Creating Custom Controls</span></span>

<span data-ttu-id="17cc7-104">Les contrôles personnalisés sont les composants les plus flexibles d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="17cc7-104">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="17cc7-105">Contrairement aux vues table, liste et larges qui définissent une structure formelle de données, telles qu’une table de données, les contrôles personnalisés vous permettent de définir la manière dont un élément de données individuel est affiché.</span><span class="sxs-lookup"><span data-stu-id="17cc7-105">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="17cc7-106">Vous pouvez définir un ensemble commun de contrôles personnalisés qui sont disponibles pour toutes les vues du fichier de mise en forme, vous pouvez définir des contrôles personnalisés qui sont disponibles pour un affichage spécifique, ou vous pouvez définir un ensemble de contrôles disponibles pour un groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="17cc7-106">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="17cc7-107">Exemple de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="17cc7-107">Custom Control Example</span></span>

<span data-ttu-id="17cc7-108">L’exemple suivant montre un contrôle personnalisé défini dans le fichier XML Certificates.Format.ps1.</span><span class="sxs-lookup"><span data-stu-id="17cc7-108">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="17cc7-109">Ce contrôle personnalisé est utilisé pour séparer les objets [System. Management. Automation. signature](/dotnet/api/System.Management.Automation.Signature) affichés dans une vue table.</span><span class="sxs-lookup"><span data-stu-id="17cc7-109">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="17cc7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17cc7-110">See Also</span></span>

[<span data-ttu-id="17cc7-111">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="17cc7-111">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
