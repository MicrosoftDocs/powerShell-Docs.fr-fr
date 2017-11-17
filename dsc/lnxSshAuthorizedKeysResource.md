---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxSshAuthorizedKeys dans DSC pour Linux
ms.openlocfilehash: 3c145eeb86d971dc00e1c7cea60fb50c83d7b9a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="f15d7-103">Ressource nxSshAuthorizedKeys dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="f15d7-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="f15d7-104">La ressource **nxAuthorizedKeys** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des clés SSH autorisées pour un utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="f15d7-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="f15d7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f15d7-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f15d7-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f15d7-106">Properties</span></span>

|  <span data-ttu-id="f15d7-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="f15d7-107">Property</span></span> |  <span data-ttu-id="f15d7-108">Description</span><span class="sxs-lookup"><span data-stu-id="f15d7-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="f15d7-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="f15d7-109">KeyComment</span></span>| <span data-ttu-id="f15d7-110">Commentaire unique</span><span class="sxs-lookup"><span data-stu-id="f15d7-110">A unique comment for the key.</span></span> <span data-ttu-id="f15d7-111">utilisé pour identifier une clé de manière unique.</span><span class="sxs-lookup"><span data-stu-id="f15d7-111">This is used to uniquely identify keys.</span></span>| 
| <span data-ttu-id="f15d7-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="f15d7-112">Ensure</span></span>| <span data-ttu-id="f15d7-113">Spécifie si la clé est définie.</span><span class="sxs-lookup"><span data-stu-id="f15d7-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="f15d7-114">Définissez cette propriété sur « Absent » pour vous assurer que la clé n’existe pas dans le fichier de clés autorisées de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f15d7-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="f15d7-115">Définissez cette propriété sur « Present » pour vous assurer que la clé est définie dans le fichier de clés autorisées de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f15d7-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>| 
| <span data-ttu-id="f15d7-116">Username</span><span class="sxs-lookup"><span data-stu-id="f15d7-116">Username</span></span>| <span data-ttu-id="f15d7-117">Nom de l’utilisateur pour lequel gérer les clés SSH autorisées.</span><span class="sxs-lookup"><span data-stu-id="f15d7-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="f15d7-118">Si aucun nom n’est défini, l’utilisateur par défaut est l’utilisateur « racine ».</span><span class="sxs-lookup"><span data-stu-id="f15d7-118">If not defined, the default user is "root".</span></span>| 
| <span data-ttu-id="f15d7-119">Key</span><span class="sxs-lookup"><span data-stu-id="f15d7-119">Key</span></span>| <span data-ttu-id="f15d7-120">Contenu de la clé.</span><span class="sxs-lookup"><span data-stu-id="f15d7-120">The contents of the key.</span></span> <span data-ttu-id="f15d7-121">Cette propriété doit être spécifiée si **Ensure** est défini sur « Present ».</span><span class="sxs-lookup"><span data-stu-id="f15d7-121">This is required if **Ensure** is set to "Present".</span></span>| 
| <span data-ttu-id="f15d7-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f15d7-122">DependsOn</span></span> | <span data-ttu-id="f15d7-123">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="f15d7-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f15d7-124">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f15d7-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="f15d7-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="f15d7-125">Example</span></span>

<span data-ttu-id="f15d7-126">L’exemple suivant définit une clé SSH autorisée publique pour l’utilisateur « monuser ».</span><span class="sxs-lookup"><span data-stu-id="f15d7-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

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

