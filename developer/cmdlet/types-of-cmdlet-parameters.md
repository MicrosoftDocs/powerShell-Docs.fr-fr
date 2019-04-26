---
title: Types de paramètres de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067193"
---
# <a name="types-of-cmdlet-parameters"></a>Types de paramètres des applets de commande

Cette rubrique décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande. Paramètres de l’applet de commande peuvent être positionnels, nommé, obligatoire, facultatif ou paramètres booléens.

## <a name="positional-and-named-parameters"></a>Paramètres positionnels et nommés

Tous les paramètres de l’applet de commande sont des paramètres nommés ou positionnels. Un paramètre nommé nécessite que vous tapez le nom du paramètre et l’argument lors de l’appel de l’applet de commande. Un paramètre positionnel nécessite uniquement que vous tapez les arguments dans l’ordre relatif. Le système mappe ensuite le premier argument sans nom pour le premier paramètre positionnel. Le système mappe le deuxième argument sans nom au second paramètre sans nom et ainsi de suite. Par défaut, tous les paramètres de l’applet de commande sont des paramètres nommés.

Pour définir un paramètre nommé, omettez la `Position` mot clé dans le **paramètre** attribut de déclaration, comme indiqué dans la déclaration de paramètre suivantes.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Pour définir un paramètre positionnel, ajoutez le `Position` mot clé dans le paramètre de déclaration d’attribut et spécifiez une position. Dans l’exemple suivant, le `UserName` paramètre est déclaré comme un paramètre de positionnement à la position 0. Cela signifie que le premier argument de l’appel sera automatiquement lié à ce paramètre.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Conception de l’applet de commande bonne recommande que les paramètres plus utilisées être déclaré en tant que paramètres positionnels afin que l’utilisateur ne devra pas entrer le nom du paramètre lors de l’exécution de l’applet de commande.

Paramètres nommés et positionnels acceptent des arguments uniques ou plusieurs arguments séparés par des virgules. Plusieurs arguments sont autorisées uniquement si le paramètre accepte une collection, tel qu’un tableau de chaînes. Vous pouvez associer des paramètres positionnels et nommés dans l’applet de commande. Dans ce cas, le système récupère les arguments nommés tout d’abord, puis essaie de mapper le reste d’arguments aux paramètres positionnels sans nom.

Les commandes suivants montrent les différentes façons dans lequel vous pouvez spécifier unique et plusieurs arguments pour les paramètres de la `Get-Command` applet de commande. Notez que dans les deux derniers intervalles **-nom** ne doit pas être spécifiée, car le `Name` paramètre est défini comme un paramètre positionnel.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Paramètres obligatoires et facultatifs

Vous pouvez également définir des paramètres de l’applet de commande en tant que paramètres obligatoires ou facultatifs. (Un paramètre obligatoire doit être spécifié avant que le runtime Windows PowerShell appelle l’applet de commande.)  Par défaut, les paramètres sont définis comme facultatifs.

Pour définir un paramètre obligatoire, ajoutez le `Mandatory` mot clé dans le paramètre de déclaration d’attribut et affectez-lui la valeur `true`, comme indiqué dans la déclaration de paramètre suivantes.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Pour définir un paramètre facultatif, omettez la `Mandatory` mot clé dans le **paramètre** attribut de déclaration, comme indiqué dans la déclaration de paramètre suivantes.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Paramètres de commutateur

Windows PowerShell fournit un [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type qui vous permet de définir un paramètre dont la valeur est automatiquement définie sur `false` si le paramètre n’est pas spécifié lors de l’applet de commande appelée. Si possible, utilisez les paramètres de commutateur à la place des paramètres booléens.

Prenez l’exemple suivant. Par défaut, plusieurs applets de commande Windows PowerShell ne passent pas un objet de sortie dans le pipeline. Toutefois, ces applets de commande ont un `PassThru` changez le paramètre qui remplace le comportement par défaut. Si le `PassThru` est précisé lors de ces applets de commande sont appelées, l’applet de commande retourne un objet de sortie au pipeline.

Si vous devez avoir la valeur par défaut le paramètre `true` lorsque le paramètre n’est pas spécifié dans l’appel, envisagez d’inverser le sens du paramètre. Pour exemple, au lieu de définir l’attribut de paramètre à une valeur booléenne de `true`, déclarez la propriété comme le [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tapez, puis définissez la valeur par défaut du paramètre à `false`.

Pour définir un paramètre de commutateur, déclarez la propriété comme le [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tapez, comme indiqué dans l’exemple suivant.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Pour rendre l’applet de commande d’agir sur le paramètre lorsqu’il est spécifié, utilisez la structure suivante dans une de l’entrée de méthodes de traitement.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
