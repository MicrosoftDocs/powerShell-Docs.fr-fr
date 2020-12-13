---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut Credential
description: Déclaration de l’attribut Credential
ms.openlocfilehash: fb826d9a46cadc021fe0c667091bbc7a9251aaa8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648608"
---
# <a name="credential-attribute-declaration"></a>Déclaration de l’attribut Credential

L’attribut Credential est un attribut facultatif qui peut être utilisé avec les paramètres d’informations d’identification de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre. Lorsque cet attribut est ajouté à une déclaration de paramètre, Windows PowerShell convertit l’entrée de chaîne en objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) . Par exemple, l’applet de commande [« obtenir des informations d’identification »](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) utilise cet attribut pour que Windows PowerShell génère l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) qui est retourné par l’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[Credential]
```

## <a name="remarks"></a>Notes

- En général, cet attribut est utilisé par les paramètres de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre. Quand un objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) est passé au paramètre, Windows PowerShell ne fait rien.

- Lors de la création de l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell utilise l’hôte actuel pour afficher les invites appropriées à l’utilisateur. Par exemple, l’hôte par défaut affiche une invite pour un nom d’utilisateur et un mot de passe lorsque cet attribut est utilisé. Toutefois, si un hôte personnalisé est utilisé et définit une invite différente, l’invite s’affiche.

- Cet attribut est utilisé avec l’attribut Parameter. Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

- L’attribut Credential est défini par la classe [System. Management. Automation. CredentialAttribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .

## <a name="see-also"></a>Voir aussi

[Alias de paramètres](./parameter-aliases.md)

[Déclaration de l’attribut Parameter](./parameter-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
