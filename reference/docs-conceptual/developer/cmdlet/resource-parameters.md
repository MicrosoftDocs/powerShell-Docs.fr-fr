---
title: Paramètres de ressource | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e618951d57ff1cf303b38f0278858144df31afaf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786524"
---
# <a name="resource-parameters"></a>Paramètres de ressource

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres de ressource. Pour ces paramètres, les ressources peuvent être l’assembly qui contient la classe d’applet de commande ou l’application hôte qui exécute l’applet de commande.

|Paramètre|Fonctionnalité|
|---|---|
|**Application**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une application.|
|**Assembly**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un assembly.|
|**Attribut**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un attribut.|
|**Classe**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier une classe Microsoft .NET Framework.|
|**Cluster**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un cluster.|
|**Culture**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la culture dans laquelle l’applet de commande doit être exécutée.|
|**Domaine**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom de domaine.|
|**Lecteur**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un nom de lecteur.|
|**Event**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un nom d’événement.|
|**Interface**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un nom d’interface réseau.|
|**IpAddress**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une adresse IP.|
|**Travail**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un travail.|
|**LiteralPath**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le chemin d’accès à une ressource lorsque les caractères génériques ne sont pas pris en charge. (Utilisez le paramètre **path** lorsque les caractères génériques sont pris en charge.)|
|**Mac**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une adresse MAC (Media Access Controller).|
|**ID**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier l’identificateur parent.|
|**Chemin d’accès**<br>Type de données : String, String []|Implémentez ce paramètre pour permettre à l’utilisateur d’indiquer les chemins d’accès à une ressource lorsque les caractères génériques sont pris en charge. (Utilisez le paramètre **LiteralPath** lorsque les caractères génériques ne sont pas pris en charge.) Nous vous recommandons de développer ce paramètre afin qu’il prenne en charge la `provider:path` syntaxe complète utilisée par les fournisseurs. Nous vous recommandons également de le développer afin qu’il fonctionne avec autant de fournisseurs que possible.|
|**Port**<br>Type de données : entier, chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier une valeur entière pour la mise en réseau ou une valeur de chaîne telle que « BizTalk » pour d’autres types de port.|
|**Imprimante**<br>Type de données : entier, chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’imprimante à utiliser par l’applet de commande.|
|**Taille**<br>Type de données : Int32|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une taille.|
|**TID**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un identificateur de transaction (TID) pour l’applet de commande.|
|**Type**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le type de ressource sur lequel opérer.|
|**URL**<br>Type de données : Chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une Uniform Resource Locator (URL).|
|**Utilisateur**<br>Type de données : Chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier son nom ou le nom d’un autre utilisateur.|

## <a name="see-also"></a>Voir aussi

[Paramètres des applets de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
