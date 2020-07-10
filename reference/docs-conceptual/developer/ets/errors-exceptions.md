---
title: Erreurs et exceptions dans le système de type étendu
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 0e0b158e51d15db266415fb1ea6bb16fba319e62
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217960"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a>Erreurs et exceptions dans le système de type étendu

Des erreurs peuvent se produire dans ETS pendant l’initialisation des données de type et lors de l’accès à un membre d’un objet **PSObject** ou à l’aide de l’une des classes utilitaires telles que **LanguagePrimitives**.

## <a name="runtime-errors"></a>Erreurs d’exécution

À une exception près, lors de la conversion, toutes les exceptions levées par ETS pendant l’exécution sont soit une exception **ExtendedTypeSystemException** , soit une exception dérivée de la classe **ExtendedTypeSystemException** . Cela permet aux développeurs de script d’intercepter ces exceptions à l’aide `Trap` de l’instruction dans leur script.

## <a name="errors-getting-member-values"></a>Erreurs lors de l’obtention des valeurs de membre

Toutes les erreurs qui se produisent lors de l’obtention de la valeur d’un membre ETS (propriété, méthode ou propriété paramétrable) entraînent la levée d’une exception **GetValueException** ou **GetValueInvocationException** .
Lorsque ETS reconnaît qu’une erreur s’est produite, une exception **GetValueException** est levée. Lorsque l’accesseur Get sous-jacent d’un membre référencé reconnaît qu’une erreur s’est produite, une exception **GetValueInvocationException** est levée, qui peut inclure ou non l’exception interne qui a provoqué l’erreur obtenir l’invocation.

## <a name="errors-setting-member-values"></a>Erreurs de définition des valeurs de membre

Toutes les erreurs qui se produisent lors de la définition de la valeur d’une propriété ETS entraînent la levée d’une exception **SetValueException** ou **SetValueInvocationException** . Lorsque ETS reconnaît qu’une erreur s’est produite, une exception **SetValueException** est levée. Lorsque l’accesseur Set sous-jacent d’une propriété référencée reconnaît qu’une erreur s’est produite, une exception **SetValueInvocationException** est levée, qui peut inclure ou non l’exception interne qui a provoqué l’erreur d’appel du jeu.

## <a name="errors-invoking-a-method"></a>Erreurs lors de l’appel d’une méthode

Toutes les erreurs qui se produisent lors de l’appel d’une méthode ETS entraînent la levée d’une exception **MethodException** ou **MethodInvocationException** . Lorsque ETS reconnaît qu’une erreur s’est produite, une exception **MethodException** est levée. Quand la méthode référencée reconnaît qu’une erreur s’est produite, une exception **MethodInvocationException** est levée et peut inclure l’exception interne qui a provoqué l’erreur d’appel.

## <a name="casting-errors"></a>Erreurs de conversion

Lors d’une tentative de cast non valide, une **PSInvalidCastException** est levée. Comme cette exception dérive de **System. InvalidCastException**, elle ne peut pas être interceptée directement à partir du script. N’oubliez pas que l’entité qui tente le cast doit encapsuler **PSInvalidCastException** dans un **PSRuntimeException** pour que cela soit récupérable par les scripts. En cas de tentative de définition de la valeur d’un **PSPropertySet**, **PSMemberSet**, **PSMethodInfo**ou d’un membre de **ReadOnlyPSMemberInfoCollection' 1**, une **exception NotSupportedException** est levée.

## <a name="common-runtime-errors"></a>Erreurs d’exécution courantes

Toutes les autres erreurs d’exécution courantes qui se produisent sont de type **ExtendedTypeSystemException** avec des types d’exception spécifiques supplémentaires.

## <a name="initialization-errors"></a>Erreurs d’initialisation

Des erreurs peuvent se produire lors de l’initialisation `types.ps1xml` . En règle générale, ces erreurs s’affichent au démarrage du runtime PowerShell. Toutefois, elles peuvent également être affichées lorsqu’un module est chargé.
