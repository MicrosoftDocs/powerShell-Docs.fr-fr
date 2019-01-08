---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxUser dans DSC pour Linux
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047270"
---
# <a name="dsc-for-linux-nxuser-resource"></a>Ressource nxUser dans DSC pour Linux

La ressource **nxUser** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des utilisateurs locaux sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Indique le nom du compte pour lequel vous souhaitez garantir un état spécifique. |
|---|---|
| UserName| Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état.|
| Ensure| Spécifie si le compte existe. Définissez cette propriété sur « Present » pour vous assurer que le compte existe, ou sur « Absent » pour vous assurer que le compte n’existe pas.|
| FullName| Chaîne contenant le nom complet à utiliser pour le compte d’utilisateur.|
| Description| Description du compte d’utilisateur.|
| Password| Hachage du mot de passe de l’utilisateur dans le format approprié pour l’ordinateur Linux. En règle générale, il s’agit d’un hachage salt SHA-256 ou SHA-512. Pour Debian et Ubuntu Linux, cette valeur peut être générée avec la commande mkpasswd. Pour les autres versions de Linux, vous pouvez générer la valeur de hachage à l’aide de la méthode crypt disponible dans la bibliothèque de cryptage Python.|
| Disabled| Indique si le compte est activé. Définissez cette propriété sur **$true** pour vous assurer que ce compte est désactivé, ou sur **$false** pour vous assurer qu’il est activé.|
| PasswordChangeRequired| Indique si l’utilisateur peut modifier le mot de passe. Définissez cette propriété sur **$true** pour vous assurer que l’utilisateur ne modifie pas le mot de passe, ou sur **$false** pour permettre à l’utilisateur de modifier le mot de passe. La valeur par défaut est **$false**. Cette propriété est évaluée uniquement si le compte d’utilisateur en cours de création n’existe pas encore.|
| HomeDirectory| Indique le répertoire racine de l’utilisateur.|
| GroupID| Indique l’ID de groupe principal de l’utilisateur.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID « ResourceName » et le type « ResourceType », utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemple

L’exemple suivant vérifie que l’utilisateur « monuser » existe et qu’il est membre du groupe « DBusers ».

```
Import-DSCResource -Module nx

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```