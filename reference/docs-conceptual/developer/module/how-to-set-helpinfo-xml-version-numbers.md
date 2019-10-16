---
title: Définition des numéros de version XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360678"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Guide pratique pour définir les numéros de version XML HelpInfo

Cette rubrique explique comment définir et augmenter les numéros de version dans un fichier d’informations d’aide pouvant être mis à jour, communément appelé « fichier XML HelpInfo ».

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Guide pratique pour définir les numéros de version XML HelpInfo

Les numéros de version d’un fichier XML HelpInfo sont essentiels au fonctionnement de l’aide actualisable.
Les applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) téléchargent de nouveaux fichiers d’aide uniquement lorsque le numéro de version d’une culture d’interface utilisateur dans le fichier XML HelpInfo distant est supérieur au numéro de version de cette culture d’interface utilisateur dans le XML HelpInfo local, ou qu’il n’existe aucun HelpInfo local Fichier XML.

Le fichier XML HelpInfo utilise le numéro de version en 4 parties qui est défini dans la classe **System. version** de l’infrastructure Microsoft .net. Le format est `N1.N2.N3.N4`. Les auteurs de modules peuvent utiliser n’importe quel modèle de numérotation de version qui est autorisé par la classe **System. version** . L’aide actualisable nécessite uniquement que le numéro de version d’une culture d’interface utilisateur augmente lorsqu’une nouvelle version du fichier CAB pour cette culture d’interface utilisateur est téléchargée vers l’emplacement spécifié par l’élément **HelpContentURI** dans le fichier XML HelpInfo.

L’exemple suivant montre les éléments du fichier XML HelpInfo pour la culture d’interface utilisateur allemande (de-DE) lorsque la version est 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Le numéro de version d’une culture d’interface utilisateur reflète la version du fichier CAB pour cette culture d’interface utilisateur. Le numéro de version s’applique à l’ensemble du fichier CAB. Vous ne pouvez pas définir des numéros de version différents pour différents fichiers dans le fichier CAB. Le numéro de version de chaque culture d’interface utilisateur est évalué indépendamment et n’a pas besoin d’être lié aux numéros de version des autres cultures d’interface utilisateur prises en charge par le module.