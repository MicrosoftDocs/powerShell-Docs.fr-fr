---
title: Schéma XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 8142a620f0f71de3d2a6b33fc2e45092b5743a54
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996000"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="5bfaf-102">Schéma XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="5bfaf-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="5bfaf-103">Cette rubrique contient le schéma XML pour les fichiers d’informations d’aide actualisables, communément appelés « fichiers XML HelpInfo ».</span><span class="sxs-lookup"><span data-stu-id="5bfaf-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="5bfaf-104">Schéma XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="5bfaf-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="5bfaf-105">Les fichiers XML HelpInfo sont basés sur le schéma XML suivant.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-105">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="https://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="5bfaf-106">Éléments XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="5bfaf-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="5bfaf-107">Le fichier XML HelpInfo contient les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="5bfaf-108">HelpContentURI contient l’URI de l’emplacement des fichiers CAB de l’aide pour le module.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="5bfaf-109">L’URI doit commencer par « http » ou « HTTPS ».</span><span class="sxs-lookup"><span data-stu-id="5bfaf-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="5bfaf-110">L’URI doit spécifier un emplacement Internet, mais ne doit pas inclure le nom du fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="5bfaf-111">La valeur **HelpContentURI** peut être identique ou différente de la valeur **HelpInfoURI** .</span><span class="sxs-lookup"><span data-stu-id="5bfaf-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="5bfaf-112">SupportedUICultures représente les fichiers d’aide du module dans toutes les cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="5bfaf-113">Contient les éléments **UICulture** , chacun représentant un jeu de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="5bfaf-114">UICulture représente un ensemble de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="5bfaf-115">Ajoutez un élément **UICulture** pour chaque culture d’interface utilisateur dans laquelle les fichiers d’aide sont écrits.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="5bfaf-116">UICultureName contient le code de langue pour la culture d’interface utilisateur dans laquelle les fichiers d’aide sont écrits.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="5bfaf-117">UICultureVersion contient un numéro de version en quatre parties dans « N1 ». N2. N3. N4» qui représente la version du fichier CAB d’aide dans la culture de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="5bfaf-118">Incrémentez ce numéro de version chaque fois que vous téléchargez de nouveaux fichiers CAB d’aide dans la culture d’interface utilisateur spécifiée par **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="5bfaf-119">Pour plus d’informations sur cette valeur, consultez « classe de version (système) » dans MSDN.</span><span class="sxs-lookup"><span data-stu-id="5bfaf-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>