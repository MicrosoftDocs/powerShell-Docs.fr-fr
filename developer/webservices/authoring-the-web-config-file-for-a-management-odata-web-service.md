---
title: Le fichier Web.config pour un service web de gestion OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080711"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Création du fichier Web.config pour un service web Management OData

Avant de pouvoir déployer votre service web de gestion OData, vous devez configurer le fichier web.config pour pointer vers les fichiers de schéma XML et les DLL qui implémentent le [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) et [ System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.

## <a name="sample-config-file"></a>Exemple de fichier de configuration

Voici un exemple de quoi ressemble le fichier web.config pour votre service web.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>Voir aussi

[Implémentation d’une autorisation personnalisée pour un service web de gestion OData](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Mise en œuvre Configurationsession pour un service web de gestion OData](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Le fichier de schéma MOF pour un service web de gestion OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Le fichier de schéma XML pour un service web de gestion OData](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Création d’un Service Web OData de gestion](./creating-a-management-odata-web-service.md)