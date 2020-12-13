---
ms.date: 09/12/2016
ms.topic: reference
title: Exemple de fichier XML HelpInfo
description: Exemple de fichier XML HelpInfo
ms.openlocfilehash: 321793d61ab5df3cccc7c353b6c93f5a7275b533
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647775"
---
# <a name="helpinfo-xml-sample-file"></a>Exemple de fichier XML HelpInfo

Cette rubrique présente un exemple de fichier d’informations d’aide actualisable bien formé, communément appelé « fichier XML HelpInfo ». Dans cet exemple de fichier, les éléments de culture d’interface utilisateur sont organisés par ordre alphabétique par nom de culture d’interface utilisateur. L’ordre alphabétique est une meilleure pratique, mais il n’est pas obligatoire.

## <a name="helpinfo-xml-sample-file"></a>Exemple de fichier XML HelpInfo

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
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
