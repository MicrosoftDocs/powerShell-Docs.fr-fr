---
title: Schéma XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082462"
---
# <a name="helpinfo-xml-schema"></a>Schéma XML HelpInfo

Cette rubrique contient le schéma XML pour les fichiers d’informations d’aide actualisable, communément appelé « Fichiers XML HelpInfo ».

## <a name="helpinfo-xml-schema"></a>Schéma XML HelpInfo

Fichiers HelpInfo XML sont basées sur le schéma XML suivant.

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

Le fichier XML HelpInfo inclut les éléments suivants.

HelpContentURI contient l’URI de l’emplacement de l’aide de fichiers CAB pour le module. L’URI doit commencer par « http » ou « https ». L’URI doit spécifier un emplacement Internet, mais ne doit pas inclure le nom du fichier CAB. Le **HelpContentURI** valeur peut être identique ou différent de la **HelpInfoURI** valeur.

SupportedUICultures représente les fichiers d’aide de module dans toutes les cultures d’interface utilisateur. Contient **UICulture** éléments, chacun d’eux représente un ensemble de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifié.

UICulture représente un ensemble de fichiers d’aide pour le module dans une culture d’interface utilisateur spécifié. Ajouter un **UICulture** élément pour chaque culture d’interface utilisateur dans lequel les fichiers d’aide sont écrites.

UICultureName contient le code de langue pour la culture d’interface utilisateur dans lequel les fichiers d’aide sont écrites.

UICultureVersion contient un numéro de version 4 parties dans « N1. N2. N3. N4 « format qui représente la version du fichier d’aide CAB dans la culture d’interface utilisateur. Incrémenter ce numéro de version, chaque fois que vous chargez nouvelle aide aux fichiers CAB de la culture d’interface utilisateur qui est spécifié par **UICultureName**. Pour plus d’informations sur cette valeur, consultez « Classe Version (système) » dans MSDN.