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
# <a name="helpinfo-xml-schema"></a>Schéma XML HelpInfo

Cette rubrique contient le schéma XML pour les fichiers d’informations d’aide actualisables, communément appelés « fichiers XML HelpInfo ».

## <a name="helpinfo-xml-schema"></a>Schéma XML HelpInfo

Les fichiers XML HelpInfo sont basés sur le schéma XML suivant.

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

## <a name="helpinfo-xml-elements"></a>Éléments XML HelpInfo

Le fichier XML HelpInfo contient les éléments suivants.

- **HelpContentURI** : contient l’URI de l’emplacement des fichiers CAB de l’aide pour le module. L’URI doit commencer par « http » ou « HTTPS ». L’URI doit spécifier un emplacement Internet, mais ne doit pas inclure le nom de fichier CAB. La valeur **HelpContentURI** peut être identique ou différente de la valeur **HelpInfoURI** .

- **SupportedUICultures** : représente les fichiers d’aide du module dans toutes les cultures d’interface utilisateur. Contient les éléments **UICulture** , chacun représentant un jeu de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifiée.

- **UICulture** -représente un ensemble de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifiée. Ajoutez un élément **UICulture** pour chaque culture d’interface utilisateur dans laquelle les fichiers d’aide sont écrits.

- **UICultureName** : contient le code de langue pour la culture d’interface utilisateur dans laquelle les fichiers d’aide sont écrits.

- **UICultureVersion** -contient un numéro de version en 4 parties dans « N1 ». N2. N3. N4» qui représente la version du fichier CAB d’aide dans la culture de l’interface utilisateur. Incrémentez ce numéro de version chaque fois que vous téléchargez de nouveaux fichiers CAB d’aide dans la culture d’interface utilisateur spécifiée par **UICultureName**. Pour plus d’informations sur cette valeur, consultez [version, classe](/dotnet/api/system.version).
