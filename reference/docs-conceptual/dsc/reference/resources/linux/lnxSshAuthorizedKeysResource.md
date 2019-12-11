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
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="bb7ff-103">Ressource nxSshAuthorizedKeys dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="bb7ff-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="bb7ff-104">La ressource **nxAuthorizedKeys** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des clés SSH autorisées pour un utilisateur spécifique.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb7ff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb7ff-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="bb7ff-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bb7ff-106">Properties</span></span>

|<span data-ttu-id="bb7ff-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="bb7ff-107">Property</span></span> |<span data-ttu-id="bb7ff-108">Description</span><span class="sxs-lookup"><span data-stu-id="bb7ff-108">Description</span></span> |
|---|---|
|<span data-ttu-id="bb7ff-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="bb7ff-109">KeyComment</span></span> |<span data-ttu-id="bb7ff-110">Commentaire unique</span><span class="sxs-lookup"><span data-stu-id="bb7ff-110">A unique comment for the key.</span></span> <span data-ttu-id="bb7ff-111">utilisé pour identifier une clé de manière unique.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-111">This is used to uniquely identify keys.</span></span> |
|<span data-ttu-id="bb7ff-112">Username</span><span class="sxs-lookup"><span data-stu-id="bb7ff-112">Username</span></span> |<span data-ttu-id="bb7ff-113">Nom de l’utilisateur pour lequel gérer les clés SSH autorisées.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-113">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="bb7ff-114">Si aucun nom n’est défini, l’utilisateur par défaut est l’utilisateur **racine**.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-114">If not defined, the default user is **root**.</span></span> |
|<span data-ttu-id="bb7ff-115">Clé</span><span class="sxs-lookup"><span data-stu-id="bb7ff-115">Key</span></span> |<span data-ttu-id="bb7ff-116">Contenu de la clé.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-116">The contents of the key.</span></span> <span data-ttu-id="bb7ff-117">Cette propriété doit être spécifiée si **Ensure** est défini sur **Present**.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-117">This is required if **Ensure** is set to **Present**.</span></span>|

## <a name="common-properties"></a><span data-ttu-id="bb7ff-118">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="bb7ff-118">Common properties</span></span>

|<span data-ttu-id="bb7ff-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="bb7ff-119">Property</span></span> |<span data-ttu-id="bb7ff-120">Description</span><span class="sxs-lookup"><span data-stu-id="bb7ff-120">Description</span></span> |
|---|---|
|<span data-ttu-id="bb7ff-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bb7ff-121">DependsOn</span></span> |<span data-ttu-id="bb7ff-122">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bb7ff-123">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="bb7ff-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="bb7ff-124">Ensure</span></span> |<span data-ttu-id="bb7ff-125">Spécifie si la clé est définie.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-125">Specifies whether the key is defined.</span></span> <span data-ttu-id="bb7ff-126">Définissez cette propriété sur **Absent** pour vous assurer que la clé n’existe pas dans le fichier de clés autorisées de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-126">Set this property to **Absent** to ensure the key does not exist in the user's authorized keys file.</span></span> <span data-ttu-id="bb7ff-127">Définissez cette propriété sur **Present** pour vous assurer que la clé est définie dans le fichier de clés autorisées de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bb7ff-127">Set it to **Present** to ensure the key is defined in the user's authorized key file.</span></span> |

## <a name="example"></a><span data-ttu-id="bb7ff-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb7ff-128">Example</span></span>

<span data-ttu-id="bb7ff-129">L’exemple suivant définit une clé SSH autorisée publique pour l’utilisateur « monuser ».</span><span class="sxs-lookup"><span data-stu-id="bb7ff-129">The following example defines a public ssh authorized key for the user "monuser".</span></span>

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