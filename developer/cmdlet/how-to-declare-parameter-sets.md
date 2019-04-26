---
title: Comment déclarer des jeux de paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067890"
---
# <a name="how-to-declare-parameter-sets"></a>Guide pratique pour déclarer des jeux de paramètres

Cet exemple montre comment définir deux jeux de paramètres lorsque vous déclarez les paramètres pour une applet de commande. Chaque jeu de paramètres a un paramètre unique et un paramètre partagé qui est utilisé par les deux jeux de paramètres. Pour plus d’informations sur les jeux de paramètres, y compris comment spécifier le jeu de paramètres par défaut, consultez [définit des paramètres d’applet de commande](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Si possible, définissez le paramètre unique d’un paramètre défini comme un paramètre obligatoire. Toutefois, si vous souhaitez que votre applet de commande à s’exécuter sans spécifier de paramètres, le paramètre unique peut être un paramètre facultatif. Par exemple, le paramètre unique de la `Get-Command` applet de commande est facultative.

## <a name="how-to-define-two-parameter-sets"></a>Comment définir les deux jeux de paramètres

1. Ajouter le `ParameterSet` mot clé à l’attribut de paramètre pour le paramètre unique du premier jeu de paramètre.

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

2. Ajouter le `ParameterSet` mot clé à l’attribut de paramètre pour le paramètre unique de la deuxième jeu de paramètres.

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

3. Pour le paramètre qui appartient aux deux ensembles de paramètre, ajoutez un attribut de paramètre pour chaque jeu de paramètres, puis ajoutez le `ParameterSet` mot clé à chaque ensemble. Dans chaque attribut de paramètre, vous pouvez spécifier la façon dont ce paramètre est défini. Un paramètre peut être facultatif dans un jeu et obligatoire dans un autre.

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

[Jeux de paramètres d’applet de commande](./cmdlet-parameter-sets.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
