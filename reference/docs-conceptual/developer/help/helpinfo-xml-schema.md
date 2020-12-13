---
ms.date: 09/12/2016
ms.topic: reference
title: Schéma XML HelpInfo
description: Schéma XML HelpInfo
ms.openlocfilehash: 157fd9c0f47c57efbaa9b7888fa174a34ad9567d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662006"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="c5344-103">Schéma XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="c5344-103">HelpInfo XML Schema</span></span>

<span data-ttu-id="c5344-104">Cette rubrique contient le schéma XML pour les fichiers d’informations d’aide actualisables, communément appelés « fichiers XML HelpInfo ».</span><span class="sxs-lookup"><span data-stu-id="c5344-104">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="c5344-105">Schéma XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="c5344-105">HelpInfo XML Schema</span></span>

<span data-ttu-id="c5344-106">Les fichiers XML HelpInfo sont basés sur le schéma XML suivant.</span><span class="sxs-lookup"><span data-stu-id="c5344-106">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="c5344-107">Éléments XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="c5344-107">HelpInfo XML Elements</span></span>

<span data-ttu-id="c5344-108">Le fichier XML HelpInfo contient les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="c5344-108">The HelpInfo XML file includes the following elements.</span></span>

- <span data-ttu-id="c5344-109">**HelpContentURI** : contient l’URI de l’emplacement des fichiers CAB de l’aide pour le module.</span><span class="sxs-lookup"><span data-stu-id="c5344-109">**HelpContentURI** - Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="c5344-110">L’URI doit commencer par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="c5344-110">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="c5344-111">L’URI doit spécifier un emplacement Internet, mais ne doit pas inclure le nom de fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="c5344-111">The URI should specify an internet location, but must not include the CAB filename.</span></span> <span data-ttu-id="c5344-112">La valeur **HelpContentURI** peut être identique ou différente de la valeur **HelpInfoURI** .</span><span class="sxs-lookup"><span data-stu-id="c5344-112">The **HelpContentURI** value can be the same or different from the **HelpInfoURI** value.</span></span>

- <span data-ttu-id="c5344-113">**SupportedUICultures** : représente les fichiers d’aide du module dans toutes les cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c5344-113">**SupportedUICultures** - Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="c5344-114">Contient les éléments **UICulture** , chacun représentant un jeu de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5344-114">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

- <span data-ttu-id="c5344-115">**UICulture** -représente un ensemble de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5344-115">**UICulture** - Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="c5344-116">Ajoutez un élément **UICulture** pour chaque culture d’interface utilisateur dans laquelle les fichiers d’aide sont écrits.</span><span class="sxs-lookup"><span data-stu-id="c5344-116">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

- <span data-ttu-id="c5344-117">**UICultureName** : contient le code de langue pour la culture d’interface utilisateur dans laquelle les fichiers d’aide sont écrits.</span><span class="sxs-lookup"><span data-stu-id="c5344-117">**UICultureName** - Contains the language code for the UI culture in which the help files are written.</span></span>

- <span data-ttu-id="c5344-118">**UICultureVersion** -contient un numéro de version en 4 parties dans « N1 ». N2. N3. N4» qui représente la version du fichier CAB d’aide dans la culture de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c5344-118">**UICultureVersion** - Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="c5344-119">Incrémentez ce numéro de version chaque fois que vous téléchargez de nouveaux fichiers CAB d’aide dans la culture d’interface utilisateur spécifiée par **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="c5344-119">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="c5344-120">Pour plus d’informations sur cette valeur, consultez [version, classe](/dotnet/api/system.version).</span><span class="sxs-lookup"><span data-stu-id="c5344-120">For more information about this value, see [Version Class](/dotnet/api/system.version).</span></span>
