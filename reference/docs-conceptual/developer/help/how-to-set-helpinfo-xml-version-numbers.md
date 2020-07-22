---
title: Guide pratique pour définir les numéros de version XML HelpInfo
ms.date: 09/12/2016
ms.openlocfilehash: 42164f98414da0b6f1a0021e9d860c57a63a9eec
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892980"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="0ee09-102">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="0ee09-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="0ee09-103">Cette rubrique explique comment définir et augmenter les numéros de version dans un fichier d’informations d’aide pouvant être mis à jour, communément appelé « fichier XML HelpInfo ».</span><span class="sxs-lookup"><span data-stu-id="0ee09-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="0ee09-104">Guide pratique pour définir les numéros de version XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="0ee09-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="0ee09-105">Les numéros de version d’un fichier XML HelpInfo sont essentiels au fonctionnement de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="0ee09-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="0ee09-106">Les applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) téléchargent de nouveaux fichiers d’aide uniquement lorsque le numéro de version d’une culture d’interface utilisateur dans le fichier XML HelpInfo distant est supérieur au numéro de version de cette culture d’interface utilisateur dans le XML HelpInfo local, ou qu’il n’existe aucun fichier XML HelpInfo local.</span><span class="sxs-lookup"><span data-stu-id="0ee09-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="0ee09-107">Le fichier XML HelpInfo utilise le numéro de version en 4 parties qui est défini dans la classe **System. version** de l’infrastructure Microsoft .net.</span><span class="sxs-lookup"><span data-stu-id="0ee09-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="0ee09-108">Le format est `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="0ee09-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="0ee09-109">Les auteurs de modules peuvent utiliser n’importe quel modèle de numérotation de version qui est autorisé par la classe **System. version** .</span><span class="sxs-lookup"><span data-stu-id="0ee09-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="0ee09-110">L’aide actualisable nécessite uniquement que le numéro de version d’une culture d’interface utilisateur augmente lorsqu’une nouvelle version du fichier CAB pour cette culture d’interface utilisateur est téléchargée vers l’emplacement spécifié par l’élément **HelpContentURI** dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="0ee09-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="0ee09-111">L’exemple suivant montre les éléments du fichier XML HelpInfo pour la culture d’interface utilisateur allemande (de-DE) lorsque la version est 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="0ee09-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="0ee09-112">Le numéro de version d’une culture d’interface utilisateur reflète la version du fichier CAB pour cette culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ee09-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="0ee09-113">Le numéro de version s’applique à l’ensemble du fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="0ee09-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="0ee09-114">Vous ne pouvez pas définir des numéros de version différents pour différents fichiers dans le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="0ee09-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="0ee09-115">Le numéro de version de chaque culture d’interface utilisateur est évalué indépendamment et n’a pas besoin d’être lié aux numéros de version des autres cultures d’interface utilisateur prises en charge par le module.</span><span class="sxs-lookup"><span data-stu-id="0ee09-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>
