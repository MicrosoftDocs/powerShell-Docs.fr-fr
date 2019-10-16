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
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="cab7f-102">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="cab7f-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="cab7f-103">Cette rubrique explique comment définir et augmenter les numéros de version dans un fichier d’informations d’aide pouvant être mis à jour, communément appelé « fichier XML HelpInfo ».</span><span class="sxs-lookup"><span data-stu-id="cab7f-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="cab7f-104">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="cab7f-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="cab7f-105">Les numéros de version d’un fichier XML HelpInfo sont essentiels au fonctionnement de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="cab7f-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="cab7f-106">Les applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) téléchargent de nouveaux fichiers d’aide uniquement lorsque le numéro de version d’une culture d’interface utilisateur dans le fichier XML HelpInfo distant est supérieur au numéro de version de cette culture d’interface utilisateur dans le XML HelpInfo local, ou qu’il n’existe aucun HelpInfo local Fichier XML.</span><span class="sxs-lookup"><span data-stu-id="cab7f-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="cab7f-107">Le fichier XML HelpInfo utilise le numéro de version en 4 parties qui est défini dans la classe **System. version** de l’infrastructure Microsoft .net.</span><span class="sxs-lookup"><span data-stu-id="cab7f-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="cab7f-108">Le format est `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="cab7f-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="cab7f-109">Les auteurs de modules peuvent utiliser n’importe quel modèle de numérotation de version qui est autorisé par la classe **System. version** .</span><span class="sxs-lookup"><span data-stu-id="cab7f-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="cab7f-110">L’aide actualisable nécessite uniquement que le numéro de version d’une culture d’interface utilisateur augmente lorsqu’une nouvelle version du fichier CAB pour cette culture d’interface utilisateur est téléchargée vers l’emplacement spécifié par l’élément **HelpContentURI** dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="cab7f-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="cab7f-111">L’exemple suivant montre les éléments du fichier XML HelpInfo pour la culture d’interface utilisateur allemande (de-DE) lorsque la version est 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="cab7f-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="cab7f-112">Le numéro de version d’une culture d’interface utilisateur reflète la version du fichier CAB pour cette culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cab7f-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="cab7f-113">Le numéro de version s’applique à l’ensemble du fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="cab7f-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="cab7f-114">Vous ne pouvez pas définir des numéros de version différents pour différents fichiers dans le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="cab7f-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="cab7f-115">Le numéro de version de chaque culture d’interface utilisateur est évalué indépendamment et n’a pas besoin d’être lié aux numéros de version des autres cultures d’interface utilisateur prises en charge par le module.</span><span class="sxs-lookup"><span data-stu-id="cab7f-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>