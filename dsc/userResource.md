---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource User dans DSC
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892523"
---
# <a name="dsc-user-resource"></a>Ressource User dans DSC

S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource **User** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des comptes d’utilisateur locaux sur le nœud cible.

## <a name="syntax"></a>Syntaxe

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriétés

|  Propriété  |  Description   |
|---|---|
| UserName| Indique le nom du compte pour lequel vous voulez garantir un état spécifique.|
| Description| Indique la description que vous voulez utiliser pour le compte d’utilisateur.|
| Désactivé| Indique si le compte est activé. Affectez la valeur `$true` à cette propriété pour vous assurer que ce compte est désactivé, ou `$false` pour vous assurer qu’il est activé.|
| Ensure| Indique si le compte existe. Définissez cette propriété sur « Present » pour vous assurer que le compte existe, ou sur « Absent » pour vous assurer que le compte n’existe pas.|
| FullName| Représente une chaîne avec le nom complet que vous voulez utiliser pour le compte d’utilisateur.|
| Password| Indique le mot de passe que vous voulez utiliser pour ce compte. |
| PasswordChangeNotAllowed| Indique si l’utilisateur peut modifier le mot de passe. Affectez la valeur `$true` à cette propriété pour vous assurer que l’utilisateur ne modifie pas le mot de passe, ou `$false` pour permettre à l’utilisateur de modifier le mot de passe. La valeur par défaut est `$false`.|
| PasswordChangeRequired| Indique si l’utilisateur doit changer de mot de passe à la prochaine connexion. Affectez la valeur `$true` à cette propriété si l’utilisateur doit changer le mot de passe. La valeur par défaut est `$true`.|
| PasswordNeverExpires| Indique si le mot de passe doit expirer. Pour vous assurer que le mot de passe pour ce compte n’expire jamais, affectez la valeur `$true` à cette propriété, et affectez-lui la valeur `$false` si le mot de passe doit expirer. La valeur par défaut est `$false`.|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe permettant d’utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemple

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```