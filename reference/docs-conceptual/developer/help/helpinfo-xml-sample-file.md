---
title: Exemple de fichier XML HelpInfo
ms.date: 09/12/2016
ms.openlocfilehash: ccd1f61d8d40232a3e6d2228d382ef4895e13d3d
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893507"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="906ac-102">Exemple de fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="906ac-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="906ac-103">Cette rubrique présente un exemple de fichier d’informations d’aide actualisable bien formé, communément appelé « fichier XML HelpInfo ».</span><span class="sxs-lookup"><span data-stu-id="906ac-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="906ac-104">Dans cet exemple de fichier, les éléments de culture d’interface utilisateur sont organisés par ordre alphabétique par nom de culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="906ac-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="906ac-105">L’ordre alphabétique est une meilleure pratique, mais il n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="906ac-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="906ac-106">Exemple de fichier XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="906ac-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="https://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```
