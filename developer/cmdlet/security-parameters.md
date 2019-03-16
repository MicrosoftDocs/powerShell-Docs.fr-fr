---
title: Paramètres de sécurité | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057127"
---
# <a name="security-parameters"></a>Paramètres de sécurité

Le tableau suivant répertorie les noms recommandés pour les paramètres utilisés pour fournir des informations de sécurité pour une opération, telles que les paramètres qui spécifient des informations de clé et du privilège de certificat.

|Paramètre|Fonctionnalités|
|---|---|
|**ACL**<br>Type de données : String|Implémentez ce paramètre pour spécifier le niveau de contrôle d’accès de protection pour un catalogue ou pour un identificateur URI (Uniform Resource).|
|**CertFile**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom d’un fichier qui contient l’un des éléments suivants :<br>: Un certificat x.509 encodé en Base64 ou règles DER (Distinguished Encoding)<br>-Un fichier PKCS Public Key Cryptography Standards () #12 contenant au moins un certificat et la clé|
|**CertIssuerName**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom de l’émetteur d’un certificat ou pour que l’utilisateur peut spécifier une sous-chaîne.|
|**CertRequestFile**<br>Type de données : String|Implémentez ce paramètre pour spécifier le nom d’un fichier qui contient une demande de certificat au format Base64 ou encodé DER PKCS #10.|
|**CertSerialNumber**<br>Type de données : String|Implémentez ce paramètre pour spécifier le numéro de série a été émis par l’autorité de certification.|
|**CertStoreLocation**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’emplacement du magasin de certificats. L’emplacement est généralement un chemin d’accès de fichier.|
|**CertSubjectName**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’émetteur d’un certificat ou pour que l’utilisateur peut spécifier une sous-chaîne.|
|**CertUsage**<br>Type de données : String|Implémentez ce paramètre pour spécifier l’utilisation de la clé ou de l’utilisation améliorée de la clé. La clé peut être représentée comme un masque de bits, un peu, un identificateur d’objet (OID), ou une chaîne.|
|**Informations d’identification**<br>Type de données : [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implémentez ce paramètre afin que l’applet de commande vous invite automatiquement l’utilisateur un nom d’utilisateur ou mot de passe. Une invite pour les deux s’affiche si une information d’identification complète n’est pas fournie directement.|
|**CSPName**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom du fournisseur de services de certificat (CSP).|
|**CSPType**<br>Type de données : Entier|Implémentez ce paramètre afin que l’utilisateur peut spécifier le type de fournisseur de services cryptographiques.|
|**Groupe**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une collection d’entités de sécurité pour l’accès. Pour plus d’informations, consultez la description de la **Principal** paramètre.|
|**KeyAlgorithm**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’algorithme de génération de clé à utiliser pour la sécurité.|
|**KeyContainerName**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom du conteneur de clé.|
|**KeyLength**<br>Type de données : Entier|Implémentez ce paramètre afin que l’utilisateur peut spécifier la longueur de la clé en bits.|
|**Opération**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une action qui peut être effectuée sur un objet protégé.|
|**Principal**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une entité unique identifiable pour l’accès.|
|**privilège**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le droit de qu'une applet de commande doit effectuer une opération d’une entité particulière.|
|**Privilèges**<br>Type de données : Tableau des privilèges|Implémentez ce paramètre afin que l’utilisateur peut spécifier les droits qui a besoin d’une applet de commande pour effectuer son opération pour une entrée particulière.|
|**Role**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un ensemble d’opérations qui peuvent être effectuées par une entité.|
|**SaveCred**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les informations d’identification qui ont été précédemment enregistrées par l’utilisateur seront utilisées lorsque le paramètre est spécifié.|
|**Portée**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le groupe d’objets protégés pour l’applet de commande.|
|**SID**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un identificateur unique qui représente une entité de sécurité.|
|**approuvé**<br>Type de données : SwitchParameter|Implémentez ce paramètre afin que les niveaux de confiance sont pris en charge lorsque le paramètre est spécifié.|
|**TrustLevel**<br>Type de données : Mot clé|Implémentez ce paramètre afin que l’utilisateur peut spécifier le niveau de confiance qui est pris en charge. Par exemple, les valeurs possibles incluent fulltrust, internet et intranet.|

## <a name="see-also"></a>Voir aussi

[Paramètres de l’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
