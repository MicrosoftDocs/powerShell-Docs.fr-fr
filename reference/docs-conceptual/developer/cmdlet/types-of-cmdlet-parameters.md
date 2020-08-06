---
title: Types de paramètres d’applet de commande | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e704aae6e23568be9935e228752f652929863a98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786371"
---
# <a name="types-of-cmdlet-parameters"></a>Types de paramètres des applets de commande

Cette rubrique décrit les différents types de paramètres que vous pouvez déclarer dans les applets de commande. Les paramètres d’applet de commande peuvent être positionnels, nommés, obligatoires, facultatifs ou commutateurs.

## <a name="positional-and-named-parameters"></a>Paramètres positionnels et nommés

Tous les paramètres d’applet de commande sont des paramètres nommés ou positionnels. Pour un paramètre nommé, vous devez taper le nom du paramètre et l’argument lors de l’appel de l’applet de commande. Un paramètre positionnel requiert uniquement que vous tapez les arguments dans l’ordre relatif. Le système mappe ensuite le premier argument sans nom au premier paramètre positionnel. Le système mappe le deuxième argument sans nom au deuxième paramètre sans nom, et ainsi de suite. Par défaut, tous les paramètres d’applet de commande sont des paramètres nommés.

Pour définir un paramètre nommé, omettez le `Position` mot clé dans la déclaration d’attribut de **paramètre** , comme indiqué dans la déclaration de paramètre suivante.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Pour définir un paramètre positionnel, ajoutez le `Position` mot clé dans la déclaration d’attribut de paramètre, puis spécifiez une position. Dans l’exemple suivant, le `UserName` paramètre est déclaré en tant que paramètre positionnel avec la position 0. Cela signifie que le premier argument de l’appel sera automatiquement lié à ce paramètre.

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
> Une bonne conception d’applets de commande recommande que les paramètres les plus utilisés soient déclarés en tant que paramètres positionnels afin que l’utilisateur n’ait pas à entrer le nom du paramètre lors de l’exécution de l’applet de commande.

Les paramètres positionnels et nommés acceptent des arguments uniques ou plusieurs arguments séparés par des virgules. Plusieurs arguments sont autorisés uniquement si le paramètre accepte une collection telle qu’un tableau de chaînes. Vous pouvez mélanger des paramètres positionnels et nommés dans la même applet de commande. Dans ce cas, le système récupère d’abord les arguments nommés, puis tente de mapper les arguments sans nom restants aux paramètres positionnels.

Les commandes suivantes illustrent les différentes façons dont vous pouvez spécifier des arguments uniques et multiples pour les paramètres de l’applet de commande `Get-Command` . Notez que dans les deux derniers exemples, **-Name** n’a pas besoin d’être spécifié, car le `Name` paramètre est défini en tant que paramètre positionnel.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Paramètres obligatoires et facultatifs

Vous pouvez également définir des paramètres d’applet de commande en tant que paramètres obligatoires ou facultatifs. (Un paramètre obligatoire doit être spécifié avant que le runtime Windows PowerShell appelle l’applet de commande.)  Par défaut, les paramètres sont définis comme facultatifs.

Pour définir un paramètre obligatoire, ajoutez le `Mandatory` mot clé dans la déclaration d’attribut de paramètre et affectez-lui la valeur `true` , comme indiqué dans la déclaration de paramètre suivante.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Pour définir un paramètre facultatif, omettez le `Mandatory` mot clé dans la déclaration d’attribut de **paramètre** , comme indiqué dans la déclaration de paramètre suivante.

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

Windows PowerShell fournit un type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter) qui vous permet de définir un paramètre dont la valeur est automatiquement définie sur `false` si le paramètre n’est pas spécifié lors de l’appel de l’applet de commande. Dans la mesure du possible, utilisez des paramètres de commutateur à la place des paramètres booléens.

Prenons l’exemple suivant. Par défaut, plusieurs applets de commande Windows PowerShell ne transmettent pas un objet de sortie dans le pipeline. Toutefois, ces applets de commande ont un `PassThru` paramètre de commutateur qui remplace le comportement par défaut. Si le `PassThru` paramètre est spécifié lors de l’appel de ces applets de commande, l’applet de commande renvoie un objet de sortie au pipeline.

Si vous avez besoin que le paramètre ait une valeur par défaut `true` lorsque le paramètre n’est pas spécifié dans l’appel, envisagez d’inverser le sens du paramètre. Par exemple, au lieu de définir l’attribut de paramètre sur une valeur booléenne de `true` , déclarez la propriété en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter) , puis affectez à la valeur par défaut du paramètre la valeur `false` .

Pour définir un paramètre de commutateur, déclarez la propriété en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter) , comme indiqué dans l’exemple suivant.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Pour que l’applet de commande agisse sur le paramètre quand elle est spécifiée, utilisez la structure suivante dans l’une des méthodes de traitement d’entrée.

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
