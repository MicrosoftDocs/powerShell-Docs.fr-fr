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
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863315"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="57ece-102">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="57ece-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="57ece-103">Cette rubrique explique comment définir et augmenter les numéros de version dans un fichier d’informations d’aide actualisable, communément appelé « fichier XML HelpInfo ».</span><span class="sxs-lookup"><span data-stu-id="57ece-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="57ece-104">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="57ece-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="57ece-105">Les numéros de version dans un fichier XML HelpInfo sont essentielles au fonctionnement de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="57ece-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="57ece-106">Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applets de commande téléchargement de nouveaux fichiers d’aide uniquement lorsque le numéro de version pour une culture d’interface utilisateur dans le fichier XML HelpInfo distant est supérieur au nombre de version pour cette culture d’interface utilisateur dans le local HelpInfo XML, ou il n’existe aucun fichier XML HelpInfo local.</span><span class="sxs-lookup"><span data-stu-id="57ece-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>
<span data-ttu-id="57ece-107">Les numéros de version dans un fichier XML HelpInfo sont essentielles au fonctionnement de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="57ece-107">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="57ece-108">Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applets de commande téléchargement de nouveaux fichiers d’aide uniquement lorsque le numéro de version pour une culture d’interface utilisateur dans le fichier XML HelpInfo distant est supérieur au nombre de version pour cette culture d’interface utilisateur dans le local HelpInfo XML, ou il n’existe aucun fichier XML HelpInfo local.</span><span class="sxs-lookup"><span data-stu-id="57ece-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="57ece-109">Le fichier XML HelpInfo utilise le numéro de version de 4 parties qui est défini dans le **System.Version** classe du Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="57ece-109">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="57ece-110">Le format est `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="57ece-110">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="57ece-111">Les auteurs de modules peuvent utiliser n’importe quelle version de numérotation est autorisé par le **System.Version** classe.</span><span class="sxs-lookup"><span data-stu-id="57ece-111">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="57ece-112">Aide actualisable exige uniquement que le numéro de version pour une augmentation de culture d’interface utilisateur lors du chargée d’une nouvelle version du fichier CAB pour cette culture d’interface utilisateur à l’emplacement spécifié par le **HelpContentURI** élément dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="57ece-112">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="57ece-113">L’exemple suivant montre les éléments du fichier XML HelpInfo pour l’allemand (de-DE) l’interface utilisateur de culture lorsque la version est 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="57ece-113">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="57ece-114">Le numéro de version pour une culture d’interface utilisateur reflète la version du fichier CAB pour cette culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="57ece-114">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="57ece-115">Le numéro de version s’applique à l’intégralité du fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="57ece-115">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="57ece-116">Impossible de définir des numéros de version différents pour différents fichiers dans le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="57ece-116">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="57ece-117">Le numéro de version pour chaque culture d’interface utilisateur est évalué indépendamment et ne doivent pas être associé aux numéros de version pour les autres cultures d’interface utilisateur qui prend en charge par le module.</span><span class="sxs-lookup"><span data-stu-id="57ece-117">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>