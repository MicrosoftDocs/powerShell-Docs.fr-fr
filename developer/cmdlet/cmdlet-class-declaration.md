---
title: Déclaration de classe de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854445"
---
# <a name="cmdlet-class-declaration"></a>Déclaration de classe d’applets de commande

Une classe Microsoft .NET Framework est déclarée comme une applet de commande en spécifiant le **applet de commande** attribut en tant que métadonnées pour la classe. (Le **applet de commande** attribut est le seul attribut requis pour toutes les applets de commande). Lorsque vous spécifiez le **applet de commande** attribut, vous devez spécifier la paire verbe-substantif qui identifie l’applet de commande à l’utilisateur. Et bien, vous devez décrire les fonctionnalités de Windows PowerShell qui prend en charge de l’applet de commande. Pour plus d’informations sur la syntaxe de déclaration est utilisée pour spécifier le **applet de commande** d’attribut, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Le **applet de commande** attribut est défini par le [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe. Les propriétés de cette classe correspondent aux paramètres de déclaration qui sont utilisés lorsque vous déclarez l’attribut.

## <a name="nouns"></a>Noms

Le nom de l’applet de commande spécifie les ressources sur lesquelles l’applet de commande agit. Le substantif différencie vos applets de commande à partir d’autres applets de commande.

Les noms dans les noms d’applet de commande doivent être spécifique et dans le cas des substantifs génériques, tel que *server*, il est préférable d’ajouter un préfixe court qui différencie votre ressource à partir d’autres ressources similaires. Par exemple, un nom de l’applet de commande qui inclut un nom avec un préfixe est `Get-SQLServer`. La combinaison d’un nom spécifique avec un verbe plus général permet à l’utilisateur localiser rapidement l’applet de commande par son action et d’identifier puis de l’applet de commande par ses ressources tout en évitant de duplication de nom d’applet de commande inutiles.

Pour obtenir la liste des caractères spéciaux ne peuvent pas être utilisés dans les noms d’applet de commande, consultez [directives de développement requis](./required-development-guidelines.md).

## <a name="verbs"></a>Verbes

Lorsque vous spécifiez un verbe, les instructions de développement vous obligent à utiliser un des verbes prédéfinis fournis par Windows PowerShell. En utilisant l’une de ces verbes prédéfinis, vous allez vérifier la cohérence entre les applets de commande que vous écrivez et les applets de commande qui sont écrits par Microsoft et par d’autres utilisateurs. Par exemple, le verbe « Get » est utilisé pour les applets de commande qui extraient des données.

Pour plus d’informations sur les instructions de verbes, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md). Pour obtenir la liste des caractères spéciaux ne peuvent pas être utilisés dans les noms d’applet de commande, consultez [directives de développement requis](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Prise en charge des fonctionnalités de Windows PowerShell

Le **applet de commande** attribut vous permet également de spécifier que votre applet de commande prend en charge certaines des fonctionnalités courantes qui sont fournie par Windows PowerShell. Cela inclut la prise en charge des fonctionnalités communes telles que confirmation de commentaires utilisateur (appelée prise en charge de la fonctionnalité de ShouldProcess) et la prise en charge des transactions. (Prise en charge des transactions a été introduite dans Windows PowerShell 2.0).

Pour plus d’informations sur la syntaxe de déclaration est utilisée pour spécifier le **applet de commande** d’attribut, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Définition de classe de l’applet de commande

Le code suivant est la définition d’une classe d’applet de commande GetProc. Notez que Pascal de la casse appropriée et que le nom de la classe inclut le verbe et un nom de l’applet de commande.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Casse Pascal

Lorsque vous nommez des applets de commande, utilisez Pascal casse. Par exemple, le `Get-Item` et `Get-ItemProperty` applets de commande indiquent la façon correcte d’utiliser des majuscules lorsque vous nommez des applets de commande.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Déclaration CmdletAttribute](./cmdlet-attribute-declaration.md)

[Noms de verbe de l’applet de commande](./approved-verbs-for-windows-powershell-commands.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
