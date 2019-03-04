---
title: Paramètres de ressource | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251198"
---
# <a name="resource-parameters"></a>Paramètres de ressource

Le tableau suivant répertorie les noms recommandés pour les paramètres de ressource. Pour ces paramètres, les ressources peut être l’assembly qui contient la classe de l’applet de commande ou de l’application hôte qui exécute l’applet de commande.

|Paramètre|Fonctionnalités|
|---|---|
|**Application**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une application.|
|**Assembly**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un assembly.|
|**Attribut**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un attribut.|
|**Class**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une classe Microsoft .NET Framework.|
|**Cluster**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un cluster.|
|**Culture**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier la culture dans laquelle exécuter l’applet de commande.|
|**Domaine**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le nom de domaine.|
|**Drive**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un nom de lecteur.|
|**Événement**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un nom d’événement.|
|**Interface**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un nom de l’interface réseau.|
|**IpAddress**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une adresse IP.|
|**Job**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un travail.|
|**LiteralPath**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le chemin d’accès à une ressource lorsque les caractères génériques ne sont pas pris en charge. (Utilisez le **chemin d’accès** paramètre lorsque les caractères génériques sont pris en charge.)|
|**Mac**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une adresse media access controller (MAC).|
|**ParentId**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’identificateur du parent.|
|**Path**<br>Type de données : String, String[]|Implémentez ce paramètre afin que l’utilisateur peut indiquer les chemins d’accès à une ressource lorsque les caractères génériques sont pris en charge. (Utilisez le **LiteralPath** paramètre lorsque les caractères génériques ne sont pas pris en charge.) Nous vous recommandons de développer ce paramètre afin qu’il prend en charge la version complète `provider:path` syntaxe utilisée par les fournisseurs. Nous vous recommandons également de développer pour qu’il fonctionne avec les fournisseurs autant que possible.|
|**Port**<br>Type de données : Entier, chaîne|Implémentez ce paramètre afin que l’utilisateur peut spécifier une valeur entière pour la mise en réseau ou une valeur de chaîne tel que « biztalk » pour les autres types de port.|
|**Imprimante**<br>Type de données : Entier, chaîne|Implémentez ce paramètre afin que l’utilisateur peut spécifier l’imprimante pour l’applet de commande à utiliser.|
|**Taille**<br>Type de données : Ent32|Implémentez ce paramètre afin que l’utilisateur peut spécifier une taille.|
|**TID**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier un identificateur de transaction (TID) pour l’applet de commande.|
|**Type**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier le type de ressource à utiliser.|
|**URL**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier une URL Uniform Resource Locator ().|
|**User**<br>Type de données : String|Implémentez ce paramètre afin que l’utilisateur peut spécifier leur nom ou le nom d’un autre utilisateur.|

## <a name="see-also"></a>Voir aussi

[Paramètres de l’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
