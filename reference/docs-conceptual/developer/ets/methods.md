---
ms.date: 07/09/2020
ms.topic: reference
title: Méthodes de classe de système de type étendu
description: Méthodes de classe de système de type étendu
ms.openlocfilehash: b53604a36e0a0c3587f345262e8f274e3a2c4859
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660385"
---
# <a name="ets-class-methods"></a>Méthodes de la classe ETS

Les méthodes ETS sont des membres qui peuvent prendre des arguments, peuvent retourner des résultats et ne peuvent pas apparaître sur le côté gauche d’une expression. Les méthodes disponibles dans ETS incluent le code, Windows PowerShell et les méthodes de script.

> [!NOTE]
> À partir de scripts, les méthodes sont accessibles à l’aide de la même syntaxe que les autres membres, avec l’ajout de parenthèses à la fin du nom de la méthode.

## <a name="code-methods"></a>Méthodes de code

Une méthode de code est un membre étendu qui est défini dans un langage CLR. Il fournit des fonctionnalités similaires à une méthode définie sur un objet de base. Toutefois, une méthode de code peut être ajoutée dynamiquement à un objet **PSObject** . Pour qu’une méthode de code soit disponible, un développeur doit écrire la propriété dans un langage CLR, compiler et livrer l’assembly résultant. Cet assembly doit être disponible dans l’instance d’exécution où la méthode de code est souhaitée. N’oubliez pas qu’une implémentation de méthode de code doit être thread-safe. L’accès à ces méthodes s’effectue par le biais d’objets [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) qui fournissent les propriétés et méthodes publiques suivantes.

- `PSCodeMethod.Copy` méthode : effectue une copie exacte de l’objet **PSCodeMethod** .
- `PSCodeMethod.Invoke(System.Object[])` méthode : appelle la méthode de code sous-jacente.
- `PSCodeMethod.ToString` méthode : convertit l’objet **PSCodeMethod** en chaîne.
- `PSCodeMethod.CodeReference` Property : obtient la méthode sous-jacente sur laquelle la méthode de code est basée.
- Propriété **PSMemberInfo. isInstance** : obtient une valeur **booléenne** qui indique la source du membre.
- Propriété **PSCodeMethod. MemberType** : obtient une constante d’énumération **PSMemberTypes. CodeMethod** qui identifie cette méthode en tant que méthode de code.
- Propriété **PSMemberInfo.Name** : obtient le nom de la méthode de code sous-jacente.
- Propriété **PSCodeMethod. OverloadDefinitions** : obtient une définition de toutes les surcharges de la méthode de code sous-jacente.
- Propriété **PSCodeMethod. TypeNameOfValue** : obtient le nom complet de la méthode de code.
- **PSMemberInfo. Value,** propriété : obtient l’objet **PSCodeMethod** .

## <a name="windows-powershell-methods"></a>Méthodes Windows PowerShell

Une méthode PowerShell est une méthode CLR définie sur l’objet de base ou rendue accessible via un adaptateur. L’accès à ces méthodes s’effectue par le biais d’objets **PSMethod** qui fournissent les propriétés et méthodes publiques suivantes.

- `PSMethod.Copy` méthode : effectue une copie exacte de l’objet **PSMethod** .
- `PSMethod.Invoke(System.Object[])` méthode : appelle la méthode sous-jacente.
- `PSMethod.ToString` méthode : convertit l’objet **PSMethod** en chaîne.
- Propriété **PSMemberInfo. isInstance** : obtient une valeur **booléenne** qui indique la source du membre.
- Propriété **PSMethod. MemberType** : obtient une constante d’énumération **PSMemberTypes. Method** qui identifie cette méthode en tant que méthode PowerShell.
- Propriété **PSMemberInfo.Name** : obtient le nom de la méthode sous-jacente.
- Propriété **PSMethod. OverloadDefinitions** : obtient les définitions de toutes les surcharges de la méthode sous-jacente.
- Propriété **PSMethod. TypeNameOfValue** : obtient le type ETS de cette méthode.
- **PSMemberInfo. Value,** propriété : obtient l’objet **PSMethod** .

## <a name="script-methods"></a>Méthodes de script

Une méthode de script est un membre étendu qui est défini dans le langage PowerShell. Il fournit des fonctionnalités similaires à une méthode définie sur un objet de base. Toutefois, une méthode de script peut être ajoutée dynamiquement à un objet **PSObject** . L’accès à ces méthodes s’effectue par le biais d’objets [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) qui fournissent les propriétés et méthodes publiques suivantes.

- `PSScriptMethod.Copy` méthode : effectue une copie exacte de l’objet **PSScriptMethod** .
- `PSScriptMethod.Invoke(System.Object[])` méthode : appelle la méthode de script sous-jacente.
- `PSScriptMethod.ToString` méthode : convertit l’objet **PSScriptMethod** en chaîne.
- Propriété **PSMemberInfo. isInstance** : obtient une valeur **booléenne** qui indique la source du membre.
- Propriété **PSScriptMethod. MemberType** : obtient une constante d’énumération **PSMemberTypes. ScriptMethod** qui identifie cette méthode en tant que méthode de script.
- Propriété **PSMemberInfo.Name** : obtient le nom de la méthode de code sous-jacente.
- Propriété **PSScriptMethod. OverloadDefinitions** : obtient les définitions de toutes les surcharges de la méthode de script sous-jacente.
- Propriété **PSScriptMethod. TypeNameOfValue** : obtient le type ETS de cette méthode.
- Propriété **PSScriptMethod. script** : obtient le script utilisé pour appeler la méthode.
- **PSMemberInfo. Value,** propriété : obtient l’objet **PSScriptMethod** .
