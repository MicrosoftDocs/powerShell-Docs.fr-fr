---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource nxSshAuthorizedKeys dans DSC pour Linux
ms.openlocfilehash: 6e008efcbff2e679650d0bc3d5b8b573f6ef83e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953256"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>Ressource nxSshAuthorizedKeys dans DSC pour Linux

La ressource **nxAuthorizedKeys** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des clés SSH autorisées pour un utilisateur spécifique.

## <a name="syntax"></a>Syntaxe

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|KeyComment |Commentaire unique utilisé pour identifier une clé de manière unique. |
|Username |Nom de l’utilisateur pour lequel gérer les clés SSH autorisées. Si aucun nom n’est défini, l’utilisateur par défaut est l’utilisateur **racine**. |
|Clé |Contenu de la clé. Cette propriété doit être spécifiée si **Ensure** est défini sur **Present**.|

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Spécifie si la clé est définie. Définissez cette propriété sur **Absent** pour vous assurer que la clé n’existe pas dans le fichier de clés autorisées de l’utilisateur. Définissez cette propriété sur **Present** pour vous assurer que la clé est définie dans le fichier de clés autorisées de l’utilisateur. |

## <a name="example"></a>Exemple

L’exemple suivant définit une clé SSH autorisée publique pour l’utilisateur « monuser ».

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```