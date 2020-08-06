---
title: Comment déclarer des jeux de paramètres | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e6d06a9a78356693fe7a338dc5c9207044b23441
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784161"
---
# <a name="how-to-declare-parameter-sets"></a>Guide pratique pour déclarer des jeux de paramètres

Cet exemple montre comment définir deux jeux de paramètres lorsque vous déclarez les paramètres d’une applet de commande. Chaque jeu de paramètres possède un paramètre unique et un paramètre partagé qui est utilisé par les deux jeux de paramètres. Pour plus d’informations sur les jeux de paramètres, notamment sur la manière de spécifier le jeu de paramètres par défaut, consultez Jeux de paramètres d' [applet](./cmdlet-parameter-sets.md)de commande.

> [!IMPORTANT]
> Dans la mesure du possible, définissez le paramètre unique d’un jeu de paramètres comme paramètre obligatoire. Toutefois, si vous souhaitez que votre applet de commande s’exécute sans spécifier de paramètres, le paramètre unique peut être un paramètre facultatif. Par exemple, le paramètre unique de l' `Get-Command` applet de commande est facultatif.

## <a name="how-to-define-two-parameter-sets"></a>Comment définir deux jeux de paramètres

1. Ajoutez le `ParameterSet` mot clé à l’attribut de paramètre pour le paramètre unique du premier jeu de paramètres.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Ajoutez le `ParameterSet` mot clé à l’attribut de paramètre pour le paramètre unique du deuxième jeu de paramètres.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Pour le paramètre qui appartient aux deux jeux de paramètres, ajoutez un attribut de paramètre pour chaque jeu de paramètres, puis ajoutez le `ParameterSet` mot clé à chaque ensemble. Dans chaque attribut de paramètre, vous pouvez spécifier la façon dont ce paramètre est défini. Un paramètre peut être facultatif dans un jeu et obligatoire dans un autre.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Voir aussi

[Jeux de paramètres des applets de commande](./cmdlet-parameter-sets.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
