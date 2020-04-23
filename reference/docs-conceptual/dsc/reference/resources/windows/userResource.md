---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource User dans DSC
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953006"
---
# <a name="dsc-user-resource"></a>Ressource User dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **User** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer des comptes d’utilisateur locaux sur le nœud cible.

## <a name="syntax"></a>Syntaxe

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|UserName |Indique le nom du compte pour lequel vous voulez garantir un état spécifique. |
|Description |Indique la description que vous voulez utiliser pour le compte d’utilisateur. |
|Désactivé |Indique si le compte est activé. Affectez la valeur `$true` à cette propriété pour vous assurer que ce compte est désactivé, ou `$false` pour vous assurer qu’il est activé. |
|FullName |Représente une chaîne avec le nom complet que vous voulez utiliser pour le compte d’utilisateur. |
|Mot de passe |Indique le mot de passe que vous voulez utiliser pour ce compte. |
|PasswordChangeNotAllowed |Indique si l’utilisateur peut modifier le mot de passe. Affectez la valeur `$true` à cette propriété pour vous assurer que l’utilisateur ne modifie pas le mot de passe, ou `$false` pour permettre à l’utilisateur de modifier le mot de passe. La valeur par défaut est `$false`. |
|PasswordChangeRequired |Indique si l’utilisateur doit changer de mot de passe à la prochaine connexion. Affectez la valeur `$true` à cette propriété si l’utilisateur doit changer le mot de passe. La valeur par défaut est `$true`. |
|PasswordNeverExpires |Indique si le mot de passe doit expirer. Pour faire en sorte que le mot de passe de ce compte n’expire jamais, définissez cette propriété sur `$true`. Définissez-la sur `$false` si le mot de passe doit expirer. La valeur par défaut est `$false`. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si le compte existe. Définissez cette propriété sur **Present** pour faire en sorte que le compte existe ; définissez-la sur **Absent** pour faire en sorte qu’il n’existe pas. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

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