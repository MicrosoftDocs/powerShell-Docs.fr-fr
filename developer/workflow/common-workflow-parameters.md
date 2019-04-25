---
title: Paramètres communs de flux de travail | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080405"
---
# <a name="common-workflow-parameters"></a>Paramètres de workflow courants

Une activité de flux de travail générée à partir d’une applet de commande Windows PowerShell définit un nombre de paramètres communes à toutes les activités. Un sous-ensemble de ces paramètres peut être spécifié lors de la création afin que les auteurs de workflow peuvent personnaliser des activités. Un autre sous-ensemble de ces paramètres peut être spécifié par l’utilisateur lors de l’appel de l’activité.

Les paramètres communs de flux de travail sont regroupées en plusieurs catégories comme suit.

## <a name="connectivity-parameters"></a>Paramètres de connectivité

|Name|Type|Description|Peut être spécifié par l’utilisateur final au moment de l’exécution ?|Peut être spécifié par l’auteur de workflow lors de la création ?|Peut être spécifié par l’auteur de workflow à l’instanciation ?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Une liste de noms d’ordinateurs pour lequel lancer les travaux.|Oui|Oui|Oui|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Les informations d’identification de l’authentification à utiliser pour vous connecter à des ordinateurs spécifiés par le paramètre PSComputerName. Ce paramètre est valide uniquement si PSComputerName est spécifié.|Oui|Oui|Oui|
|PSPort|UInt32|Le port à utiliser pour exécuter le workflow.|Oui|Oui|Oui|
|PSUseSSL|Booléen|Utiliser le protocole de couche de Sockets sécurisée (SSL) pour établir une connexion sécurisée à l’ordinateur distant pour exécuter le workflow.|Oui|Oui|Oui|
|PSConfigurationName|String|La configuration de session utilisée pour exécuter le flux de travail.|Oui|Oui|Oui|
|PSApplicationName|String|La partie de nom d’application de l’URI de connexion pour l’exécution de flux de travail. Utilisez ce paramètre uniquement lorsque vous n’utilisez pas le paramètre ConnectionURI.|Oui|Oui|Oui|
|PSThrottleLimit|UInt32|Le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter le flux de travail.|Oui|TBD|Oui|
|PSConnectionURI|String[]|Tableau d’URI qualifié complet qui spécifient les points de terminaison pour les sessions interactives permettant d’exécuter le flux de travail.|Oui|Oui|Oui|
|PSAllowRedirection|Booléen|Spécifie s’il faut autoriser la redirection de cette connexion vers un autre URI pour exécuter le workflow.|Oui|Oui|Oui|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Options avancées pour la session utilisée pour exécuter le workflow.|Oui|Oui|Oui|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Une valeur de la [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) énumération qui spécifie le mécanisme d’authentification utilisé pour authentifier les informations d’identification de l’utilisateur.|Oui|Oui|Oui|
|PSCertificateThumbprint|String|Numérique certificat de clé publique (X509) d’un compte d’utilisateur qui a l’autorisation d’exécuter le workflow.|Oui|Oui|Oui|

### <a name="behavior-parameters"></a>Paramètres de comportement