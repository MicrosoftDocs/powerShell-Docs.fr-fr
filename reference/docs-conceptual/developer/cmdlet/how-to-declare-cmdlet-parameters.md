---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour déclarer des paramètres d’applet de commande
description: Guide pratique pour déclarer des paramètres d’applet de commande
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667094"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Guide pratique pour déclarer des paramètres d’applet de commande

Ces exemples montrent comment déclarer des paramètres nommés, positionnels, obligatoires, facultatifs et de commutateur. Ces exemples montrent également comment définir un alias de paramètre.

## <a name="how-to-declare-a-named-parameter"></a>Comment déclarer un paramètre nommé

- Définissez une propriété publique comme indiqué dans le code suivant. Lorsque vous ajoutez l’attribut de paramètre, omettez le `Position` mot clé de l’attribut.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Comment déclarer un paramètre positionnel

- Définissez une propriété publique comme indiqué dans le code suivant. Lorsque vous ajoutez l’attribut de paramètre, définissez le `Position` mot clé sur la position de l’argument. La valeur 0 indique la première position.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Comment déclarer un paramètre obligatoire

- Définissez une propriété publique comme indiqué dans le code suivant. Lorsque vous ajoutez l’attribut de paramètre, affectez au `Mandatory` mot clé la valeur `true` .

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Comment déclarer un paramètre facultatif

- Définissez une propriété publique comme indiqué dans le code suivant. Lorsque vous ajoutez l’attribut de paramètre, omettez le `Mandatory` mot clé.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Comment déclarer un paramètre de commutateur

- Définissez une propriété publique en tant que type [System. Management. Automation. Paramètre_Booléen](/dotnet/api/System.Management.Automation.SwitchParameter), puis déclarez l’attribut du paramètre.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Pour plus d’informations sur l’attribut de paramètre, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Comment déclarer un paramètre avec des alias

- Définissez une propriété publique comme indiqué dans le code suivant. Ajoutez un attribut alias qui répertorie les alias pour le paramètre. Dans cet exemple, trois alias sont définis pour le même paramètre. Le premier alias fournit un raccourci. Le deuxième et le troisième alias fournissent des noms que vous pouvez utiliser pour différents scénarios.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Pour plus d’informations sur l’attribut alias, consultez [déclaration d’attribut d’alias](./alias-attribute-declaration.md).

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Déclaration de l’attribut Parameter](./parameter-attribute-declaration.md)

[Déclaration de l’attribut Alias](./alias-attribute-declaration.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
