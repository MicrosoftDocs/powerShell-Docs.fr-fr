---
ms.date: 09/13/2016
ms.topic: reference
title: Paramètres de sécurité
description: Paramètres de sécurité
ms.openlocfilehash: 2c73a3372fa719ea436d4a3ae1223d4cbaaf9108
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650244"
---
# <a name="security-parameters"></a>Paramètres de sécurité

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres utilisés pour fournir des informations de sécurité pour une opération, telles que les paramètres qui spécifient la clé de certificat et les informations de privilège.

|Paramètre|Fonctionnalité|
|---|---|
|**ACL**<br>Type de données : Chaîne|Implémentez ce paramètre pour spécifier le niveau de contrôle d’accès de protection d’un catalogue ou d’un Uniform Resource Identifier (URI).|
|**CertFile**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom d’un fichier qui contient l’un des éléments suivants :<br>-Un certificat x. 509 encodé en base64 ou Distinguished Encoding Rules (DER)<br>-Un fichier PKCS (Public Key Cryptography Standards) #12 qui contient au moins un certificat et une clé|
|**CertIssuerName**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom de l’émetteur d’un certificat ou pour que l’utilisateur puisse spécifier une sous-chaîne.|
|**CertRequestFile**<br>Type de données : Chaîne|Implémentez ce paramètre pour spécifier le nom d’un fichier qui contient une demande de certificat de #10 PKCS encodé en base64 ou DER.|
|**CertSerialNumber**<br>Type de données : Chaîne|Implémentez ce paramètre pour spécifier le numéro de série qui a été émis par l’autorité de certification.|
|**CertStoreLocation**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’emplacement du magasin de certificats. L’emplacement correspond généralement à un chemin d’accès de fichier.|
|**CertSubjectName**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’émetteur d’un certificat ou pour que l’utilisateur puisse spécifier une sous-chaîne.|
|**CertUsage**<br>Type de données : Chaîne|Implémentez ce paramètre pour spécifier l’utilisation de la clé ou l’utilisation améliorée de la clé. La clé peut être représentée sous la forme d’un masque de bits, d’un bit, d’un identificateur d’objet (OID) ou d’une chaîne.|
|**Informations d'identification**<br>Type de données : [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implémentez ce paramètre afin que l’applet de commande invite automatiquement l’utilisateur à entrer un nom d’utilisateur ou un mot de passe. Une invite s’affiche si les informations d’identification complètes ne sont pas fournies directement.|
|**CSPName**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom du fournisseur de services de certificats (CSP).|
|**CSPType**<br>Type de données : Entier|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier le type de fournisseur de services de chiffrement.|
|**Groupe**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une collection de principaux pour l’accès. Pour plus d’informations, consultez la description du paramètre **principal** .|
|**KeyAlgorithm**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’algorithme de génération de clé à utiliser pour la sécurité.|
|**KeyContainerName**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom du conteneur de clé.|
|**KeyLength**<br>Type de données : Entier|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la longueur de la clé en bits.|
|**opération**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une action qui peut être effectuée sur un objet protégé.|
|**Principal**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une entité identifiable unique pour l’accès.|
|**Privilège**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le droit qu’une applet de commande doive exécuter pour une entité particulière.|
|**Privilèges**<br>Type de données : tableau de privilèges|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier les droits nécessaires à l’exécution d’une applet de commande pour une entrée particulière.|
|**Rôle**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un ensemble d’opérations qui peuvent être effectuées par une entité.|
|**SaveCred**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les informations d’identification précédemment enregistrées par l’utilisateur soient utilisées lorsque le paramètre est spécifié.|
|**Étendue**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le groupe d’objets protégés pour l’applet de commande.|
|**SID**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un identificateur unique qui représente un principal.|
|**TPM**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les niveaux de confiance soient pris en charge lorsque le paramètre est spécifié.|
|**TrustLevel**<br>Type de données : mot clé|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier le niveau de confiance pris en charge. Par exemple, les valeurs possibles sont Internet, intranet et FullTrust.|

## <a name="see-also"></a>Voir aussi

[Paramètres des applets de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
