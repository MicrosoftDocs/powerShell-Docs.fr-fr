---
title: Informations d’identification de la déclaration d’attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: abdd6e915b768b8ac688b6fc8c3194723961765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863395"
---
# <a name="credential-attribute-declaration"></a>Déclaration de l’attribut Credential

L’attribut d’informations d’identification est un attribut facultatif qui peut être utilisé avec les paramètres d’informations d’identification de type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne peut également être passée en tant qu’argument au paramètre. Lorsque cet attribut est ajouté à une déclaration de paramètre, Windows PowerShell convertit l’entrée de chaîne dans un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objet. Par exemple, le [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) applet de commande utilise cet attribut pour que Windows PowerShell génère le [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objet qui est retourné par l’applet de commande.
L’attribut d’informations d’identification est un attribut facultatif qui peut être utilisé avec les paramètres d’informations d’identification de type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne peut également être passée en tant qu’argument au paramètre. Lorsque cet attribut est ajouté à une déclaration de paramètre, Windows PowerShell convertit l’entrée de chaîne dans un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objet. Par exemple, le [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) applet de commande utilise cet attribut pour que Windows PowerShell génère le [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objet qui est retourné par l’applet de commande.

## <a name="syntax"></a>Syntaxe

```csharp
[Credential]
```

## <a name="remarks"></a>Remarques

- En général, cet attribut est utilisé par les paramètres de type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne peut également être passée en tant qu’argument au paramètre. Quand un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objet est passé au paramètre, Windows PowerShell n’a aucun effet.

- Lorsque vous créez le [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) de l’objet, Windows PowerShell utilise l’hôte actuel pour afficher les messages appropriés à l’utilisateur. Par exemple, la valeur par défaut hôte affiche une invite pour le nom d’utilisateur et mot de passe lorsque cet attribut est utilisé. Toutefois, si un hôte personnalisé est utilisé qui définit une autre invite ensuite cette invite s’affiche.

- Cet attribut est utilisé avec l’attribut de paramètre. Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

- L’attribut d’informations d’identification est définie par le [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.

## <a name="see-also"></a>Voir aussi

[Alias de paramètre](./parameter-aliases.md)

[Déclaration d’attribut de paramètre](./parameter-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
