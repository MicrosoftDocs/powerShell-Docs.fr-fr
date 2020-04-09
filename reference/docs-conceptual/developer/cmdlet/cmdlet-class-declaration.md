---
title: Déclaration de classe d’applet de commande | Microsoft Docs
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
ms.openlocfilehash: 0de49d979c31b0e8d111323a2e1899d97868ec3f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978710"
---
# <a name="cmdlet-class-declaration"></a>Déclaration de classe d’applets de commande

Une classe Microsoft .NET Framework est déclarée en tant qu’applet de commande en spécifiant l’attribut d' **applet** de commande en tant que métadonnées pour la classe. (L’attribut d' **applet** de commande est le seul attribut requis pour toutes les applets de commande).
Lorsque vous spécifiez l’attribut d' **applet** de commande, vous devez spécifier la paire verbe-and-substantif qui identifie l’applet de commande auprès de l’utilisateur. Et, vous devez décrire les fonctionnalités de Windows PowerShell prises en charge par l’applet de commande. Pour plus d’informations sur la syntaxe de déclaration utilisée pour spécifier l’attribut d' **applet** de commande, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.

> [!NOTE]
> L’attribut d' **applet** de commande est défini par la classe [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Les propriétés de cette classe correspondent aux paramètres de déclaration utilisés lorsque vous déclarez l’attribut.

## <a name="nouns"></a>Noms

Le nom de l’applet de commande spécifie les ressources sur lesquelles agit l’applet de commande. Le substantif fait la différence entre vos applets de commande et d’autres applets de commande.

Les noms des applets de commande doivent être spécifiques, et dans le cas de noms génériques, tels que *serveur*, il est préférable d’ajouter un préfixe abrégé qui différencie votre ressource des autres ressources similaires. Par exemple, un nom d’applet de commande qui comprend un nom avec un préfixe est `Get-SQLServer`. La combinaison d’un nom spécifique avec un verbe plus général permet à l’utilisateur de localiser rapidement l’applet de commande en fonction de son action, puis d’identifier l’applet de commande par sa ressource tout en évitant les doublons de noms d’applets de commande inutiles.

Pour obtenir la liste des caractères spéciaux qui ne peuvent pas être utilisés dans les noms d’applets de commande, consultez [instructions de développement requises](./required-development-guidelines.md).

## <a name="verbs"></a>Verbes et adverbes

Lorsque vous spécifiez un verbe, les instructions de développement vous obligent à utiliser l’un des verbes prédéfinis fournis par Windows PowerShell. En utilisant l’un de ces verbes prédéfinis, vous assurez la cohérence entre les applets de commande que vous écrivez et les applets de commande écrites par Microsoft et par d’autres. Par exemple, le verbe « obtenir » est utilisé pour les applets de commande qui récupèrent des données.

Pour plus d’informations sur les instructions pour les verbes, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande. Pour obtenir la liste des caractères spéciaux qui ne peuvent pas être utilisés dans les noms d’applets de commande, consultez [instructions de développement requises](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Prise en charge des fonctionnalités de Windows PowerShell

L’attribut **cmdlet** vous permet également de spécifier que votre applet de commande prend en charge certaines des fonctionnalités communes fournies par Windows PowerShell. Cela comprend la prise en charge de fonctionnalités communes telles que la confirmation de commentaires des utilisateurs (appelée prise en charge de la fonctionnalité ShouldProcess) et la prise en charge des transactions. (La prise en charge des transactions a été introduite dans Windows PowerShell 2,0).

Pour plus d’informations sur la syntaxe de déclaration utilisée pour spécifier l’attribut d' **applet** de commande, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.

## <a name="cmdlet-class-definition"></a>Définition de la classe cmdlet

Le code suivant est la définition d’une classe d’applet de commande GetProc. Notez que la casse Pascal est utilisée et que le nom de la classe comprend le verbe et le nom de l’applet de commande.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a>Casse Pascal

Lorsque vous nommez des applets de commande, utilisez la casse Pascal. Par exemple, les applets de commande `Get-Item` et `Get-ItemProperty` montrent la méthode correcte pour utiliser la mise en majuscules lorsque vous nommez des applets de commande.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Déclaration CmdletAttribute](./cmdlet-attribute-declaration.md)

[Noms des verbes d’applet de commande](./approved-verbs-for-windows-powershell-commands.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
