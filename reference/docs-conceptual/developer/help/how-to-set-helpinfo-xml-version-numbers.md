---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour définir les numéros de version XML HelpInfo
description: Guide pratique pour définir les numéros de version XML HelpInfo
ms.openlocfilehash: 9ef1940ca05d8aa9b04770013287490b71c8065a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658838"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="2cc33-103">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="2cc33-103">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="2cc33-104">Cette rubrique explique comment définir et augmenter les numéros de version dans un fichier d’informations d’aide pouvant être mis à jour, communément appelé « fichier XML HelpInfo ».</span><span class="sxs-lookup"><span data-stu-id="2cc33-104">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="2cc33-105">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="2cc33-105">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="2cc33-106">Les numéros de version d’un fichier XML HelpInfo sont essentiels au fonctionnement de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="2cc33-106">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="2cc33-107">Les applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) téléchargent de nouveaux fichiers d’aide uniquement lorsque le numéro de version d’une culture d’interface utilisateur dans le fichier XML HelpInfo distant est supérieur au numéro de version de cette culture d’interface utilisateur dans le XML HelpInfo local, ou qu’il n’existe aucun fichier XML HelpInfo local.</span><span class="sxs-lookup"><span data-stu-id="2cc33-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="2cc33-108">Le fichier XML HelpInfo utilise le numéro de version en 4 parties qui est défini dans la classe **System. version** de l’infrastructure Microsoft .net.</span><span class="sxs-lookup"><span data-stu-id="2cc33-108">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="2cc33-109">Le format est `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="2cc33-109">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="2cc33-110">Les auteurs de modules peuvent utiliser n’importe quel modèle de numérotation de version qui est autorisé par la classe **System. version** .</span><span class="sxs-lookup"><span data-stu-id="2cc33-110">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="2cc33-111">L’aide actualisable nécessite uniquement que le numéro de version d’une culture d’interface utilisateur augmente lorsqu’une nouvelle version du fichier CAB pour cette culture d’interface utilisateur est téléchargée vers l’emplacement spécifié par l’élément **HelpContentURI** dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="2cc33-111">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="2cc33-112">L’exemple suivant montre les éléments du fichier XML HelpInfo pour la culture d’interface utilisateur allemande (de-DE) lorsque la version est 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="2cc33-112">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="2cc33-113">Le numéro de version d’une culture d’interface utilisateur reflète la version du fichier CAB pour cette culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2cc33-113">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="2cc33-114">Le numéro de version s’applique à l’ensemble du fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="2cc33-114">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="2cc33-115">Vous ne pouvez pas définir des numéros de version différents pour différents fichiers dans le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="2cc33-115">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="2cc33-116">Le numéro de version de chaque culture d’interface utilisateur est évalué indépendamment et n’a pas besoin d’être lié aux numéros de version des autres cultures d’interface utilisateur prises en charge par le module.</span><span class="sxs-lookup"><span data-stu-id="2cc33-116">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>
