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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853195"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="a760f-102">Création de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="a760f-102">Creating Custom Controls</span></span>

<span data-ttu-id="a760f-103">Les contrôles personnalisés sont les composants plus souples d’un fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="a760f-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="a760f-104">Contrairement à la table, liste et affichage large qui définissent une structure formelle de données, telle qu’une table de données, des contrôles personnalisés permettent de définir l’affichage d’un élément individuel de données.</span><span class="sxs-lookup"><span data-stu-id="a760f-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="a760f-105">Vous pouvez définir un ensemble commun de contrôles personnalisés qui sont disponibles pour toutes les vues du fichier de mise en forme, vous pouvez définir des contrôles personnalisés qui sont disponibles pour une vue spécifique, ou vous pouvez définir un ensemble de contrôles qui sont disponibles pour un groupe d’objets.</span><span class="sxs-lookup"><span data-stu-id="a760f-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="a760f-106">Exemple de contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="a760f-106">Custom Control Example</span></span>

<span data-ttu-id="a760f-107">L’exemple suivant montre un contrôle personnalisé qui est défini dans le fichier Certificates.Format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="a760f-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="a760f-108">Ce contrôle personnalisé est utilisé pour séparer les [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objets affichés dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="a760f-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a760f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a760f-109">See Also</span></span>

[<span data-ttu-id="a760f-110">Écriture d’un fichier de mise en forme de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a760f-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
