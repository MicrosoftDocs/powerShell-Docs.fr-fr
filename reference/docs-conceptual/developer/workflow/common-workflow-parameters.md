---
title: Paramètres de flux de travail communs | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366048"
---
# <a name="common-workflow-parameters"></a>Paramètres de workflow courants

Une activité de workflow générée à partir d’une applet de commande Windows PowerShell définit un certain nombre de paramètres qui sont communs à toutes les activités. Un sous-ensemble de ces paramètres peut être spécifié au moment de la création afin que les auteurs de workflow puissent personnaliser les activités. Un autre sous-ensemble de ces paramètres peut être spécifié par l’utilisateur lors de l’appel de l’activité.

Les paramètres de flux de travail communs sont regroupés dans plusieurs catégories comme suit.

## <a name="connectivity-parameters"></a>Paramètres de connectivité

|Name|Type|Description|Peut être spécifié par l’utilisateur final au moment de l’exécution ?|Peut être spécifié par l’auteur du flux de travail au moment de la création ?|Peut être spécifié par l’auteur du flux de travail au moment de l’instanciation ?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Liste des noms d’ordinateurs pour lesquels des travaux doivent être lancés.|Oui|Oui|Oui|
|PSCredential|[System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Informations d’identification d’authentification à utiliser pour se connecter aux ordinateurs spécifiés par le paramètre PSComputerName. Ce paramètre est valide uniquement si PSComputerName est spécifié.|Oui|Oui|Oui|
|PSPort|UInt32|Port à utiliser pour exécuter le flux de travail.|Oui|Oui|Oui|
|PSUseSSL|Booléen|Utilisez le protocole protocole SSL (SSL) pour établir une connexion sécurisée à l’ordinateur distant afin d’exécuter le flux de travail.|Oui|Oui|Oui|
|PSConfigurationName|String|Configuration de session utilisée pour exécuter le flux de travail.|Oui|Oui|Oui|
|PSApplicationName|String|Partie nom de l’application de l’URI de connexion pour l’exécution du flux de travail. Utilisez ce paramètre uniquement lorsque vous n’utilisez pas le paramètre ConnectionURI.|Oui|Oui|Oui|
|PSThrottleLimit|UInt32|Nombre maximal de connexions simultanées qui peuvent être établies pour exécuter le flux de travail.|Oui|TBD|Oui|
|PSConnectionURI|String[]|Tableau d’URI qualifiés complets qui spécifient les points de terminaison pour les sessions interactives utilisées pour exécuter le Workflow.|Oui|Oui|Oui|
|PSAllowRedirection|Booléen|Spécifie s’il faut autoriser la redirection de cette connexion vers un autre URI pour exécuter le Workflow.|Oui|Oui|Oui|
|PSSessionOption|[System. Management. Automation. Remoting. PSSessionOption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Options avancées pour la session utilisée pour exécuter le flux de travail.|Oui|Oui|Oui|
|PSAuthentication|[System. Management. Automation. instances d’exécution. AuthenticationMechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Valeur de l’énumération [System. Management. Automation. instances d’exécution. AuthenticationMechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) qui spécifie le mécanisme d’authentification utilisé pour authentifier les informations d’identification de l’utilisateur.|Oui|Oui|Oui|
|PSCertificateThumbprint|String|Le certificat de clé publique numérique (x509) d’un compte d’utilisateur qui a l’autorisation d’exécuter le flux de travail.|Oui|Oui|Oui|

### <a name="behavior-parameters"></a>Paramètres de comportement