---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxSshAuthorizedKeys dans DSC pour Linux
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077691"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>Ressource nxSshAuthorizedKeys dans DSC pour Linux

La ressource **nxAuthorizedKeys** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des clés SSH autorisées pour un utilisateur spécifique.

## <a name="syntax"></a>Syntaxe

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Description |
|---|---|
| KeyComment| Commentaire unique utilisé pour identifier une clé de manière unique.|
| Ensure| Spécifie si la clé est définie. Définissez cette propriété sur « Absent » pour vous assurer que la clé n’existe pas dans le fichier de clés autorisées de l’utilisateur. Définissez cette propriété sur « Present » pour vous assurer que la clé est définie dans le fichier de clés autorisées de l’utilisateur.|
| Username| Nom de l’utilisateur pour lequel gérer les clés SSH autorisées. Si aucun nom n’est défini, l’utilisateur par défaut est l’utilisateur « racine ».|
| Key| Contenu de la clé. Cette propriété doit être spécifiée si **Ensure** est défini sur « Present ».|
| DependsOn | Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemple

L’exemple suivant définit une clé SSH autorisée publique pour l’utilisateur « monuser ».

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```