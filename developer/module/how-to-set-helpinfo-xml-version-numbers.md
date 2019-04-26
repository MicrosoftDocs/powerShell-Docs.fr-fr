---
title: Comment définir des numéros de Version XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082275"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Guide pratique pour définir les numéros de version XML HelpInfo

Cette rubrique explique comment définir et augmenter les numéros de version dans un fichier d’informations d’aide actualisable, communément appelé « fichier XML HelpInfo ».

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Guide pratique pour définir les numéros de version XML HelpInfo

Les numéros de version dans un fichier XML HelpInfo sont essentielles au fonctionnement de l’aide actualisable.
Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applets de commande téléchargement de nouveaux fichiers d’aide uniquement lorsque le numéro de version pour une culture d’interface utilisateur dans le fichier XML HelpInfo distant est supérieur au nombre de version pour cette culture d’interface utilisateur dans le local HelpInfo XML, ou il n’existe aucun fichier XML HelpInfo local.

Le fichier XML HelpInfo utilise le numéro de version de 4 parties qui est défini dans le **System.Version** classe du Microsoft .NET Framework. Le format est `N1.N2.N3.N4`. Les auteurs de modules peuvent utiliser n’importe quelle version de numérotation est autorisé par le **System.Version** classe. Aide actualisable exige uniquement que le numéro de version pour une augmentation de culture d’interface utilisateur lors du chargée d’une nouvelle version du fichier CAB pour cette culture d’interface utilisateur à l’emplacement spécifié par le **HelpContentURI** élément dans le fichier XML HelpInfo.

L’exemple suivant montre les éléments du fichier XML HelpInfo pour l’allemand (de-DE) l’interface utilisateur de culture lorsque la version est 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Le numéro de version pour une culture d’interface utilisateur reflète la version du fichier CAB pour cette culture d’interface utilisateur. Le numéro de version s’applique à l’intégralité du fichier CAB. Impossible de définir des numéros de version différents pour différents fichiers dans le fichier CAB. Le numéro de version pour chaque culture d’interface utilisateur est évalué indépendamment et ne doivent pas être associé aux numéros de version pour les autres cultures d’interface utilisateur qui prend en charge par le module.