---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource File DSC
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954676"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="211da-103">Ressource File DSC</span><span class="sxs-lookup"><span data-stu-id="211da-103">DSC File Resource</span></span>

> <span data-ttu-id="211da-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="211da-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="211da-105">La ressource **File** dans DSC Windows PowerShell propose un mécanisme permettant de gérer les fichiers et les dossiers sur le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="211da-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="211da-106">**DestinationPath** et **SourcePath** doivent être accessibles au nœud cible.</span><span class="sxs-lookup"><span data-stu-id="211da-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="211da-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="211da-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="211da-108">Propriétés</span><span class="sxs-lookup"><span data-stu-id="211da-108">Properties</span></span>

|<span data-ttu-id="211da-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="211da-109">Property</span></span> |<span data-ttu-id="211da-110">Description</span><span class="sxs-lookup"><span data-stu-id="211da-110">Description</span></span> |
|---|---|
|<span data-ttu-id="211da-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="211da-111">DestinationPath</span></span> |<span data-ttu-id="211da-112">Emplacement sur le nœud cible où vous voulez vérifier que la propriété **Ensure** a la valeur **Present** ou **Absent**.</span><span class="sxs-lookup"><span data-stu-id="211da-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure**.</span></span> |
|<span data-ttu-id="211da-113">Attributes</span><span class="sxs-lookup"><span data-stu-id="211da-113">Attributes</span></span> |<span data-ttu-id="211da-114">L’état souhaité des attributs du fichier ou du répertoire cible.</span><span class="sxs-lookup"><span data-stu-id="211da-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="211da-115">Les valeurs valides sont _Archive_, _Hidden_, _ReadOnly_ et _System_.</span><span class="sxs-lookup"><span data-stu-id="211da-115">Valid values are _Archive_, _Hidden_, _ReadOnly_, and _System_.</span></span> |
|<span data-ttu-id="211da-116">Checksum</span><span class="sxs-lookup"><span data-stu-id="211da-116">Checksum</span></span> |<span data-ttu-id="211da-117">Le type de somme de contrôle à utiliser pour déterminer si deux fichiers sont identiques.</span><span class="sxs-lookup"><span data-stu-id="211da-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="211da-118">Les valeurs valides sont les suivantes : **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="211da-118">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> |
|<span data-ttu-id="211da-119">Contents</span><span class="sxs-lookup"><span data-stu-id="211da-119">Contents</span></span> |<span data-ttu-id="211da-120">Valide uniquement quand elle est utilisée avec **Type** **File**.</span><span class="sxs-lookup"><span data-stu-id="211da-120">Only valid when used with **Type** **File**.</span></span> <span data-ttu-id="211da-121">Indique le contenu dont la présence ou l’absence doivent être garanties à partir du fichier cible avec **Ensure** et les valeurs **Present** ou **Absent**.</span><span class="sxs-lookup"><span data-stu-id="211da-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="211da-122">Credential</span><span class="sxs-lookup"><span data-stu-id="211da-122">Credential</span></span> |<span data-ttu-id="211da-123">Les informations d’identification nécessaires pour accéder aux ressources, telles que des fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="211da-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="211da-124">Force</span><span class="sxs-lookup"><span data-stu-id="211da-124">Force</span></span> |<span data-ttu-id="211da-125">Remplace les opérations d’accès qui entraîneraient une erreur (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire qui n’est pas vide).</span><span class="sxs-lookup"><span data-stu-id="211da-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="211da-126">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="211da-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="211da-127">Recurse</span><span class="sxs-lookup"><span data-stu-id="211da-127">Recurse</span></span> |<span data-ttu-id="211da-128">Valide uniquement quand elle est utilisée avec **Type** **Directory**.</span><span class="sxs-lookup"><span data-stu-id="211da-128">Only valid when used with **Type** **Directory**.</span></span> <span data-ttu-id="211da-129">Exécute l’opération d’état de manière récursive sur tous les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="211da-129">Performs the state operation recursively to all subdirectories.</span></span> <span data-ttu-id="211da-130">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="211da-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="211da-131">SourcePath</span><span class="sxs-lookup"><span data-stu-id="211da-131">SourcePath</span></span> |<span data-ttu-id="211da-132">Chemin à partir duquel copier la ressource de fichier ou de dossier.</span><span class="sxs-lookup"><span data-stu-id="211da-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="211da-133">Type</span><span class="sxs-lookup"><span data-stu-id="211da-133">Type</span></span> |<span data-ttu-id="211da-134">Le type de ressource en cours de configuration.</span><span class="sxs-lookup"><span data-stu-id="211da-134">The type of resource being configured.</span></span> <span data-ttu-id="211da-135">Les valeurs valides sont **Directory** et **File**.</span><span class="sxs-lookup"><span data-stu-id="211da-135">Valid values are **Directory** and **File**.</span></span> <span data-ttu-id="211da-136">La valeur par défaut est **File**.</span><span class="sxs-lookup"><span data-stu-id="211da-136">Default value is **File**.</span></span> |
|<span data-ttu-id="211da-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="211da-137">MatchSource</span></span> |<span data-ttu-id="211da-138">Détermine si la ressource doit contrôler les nouveaux fichiers ajoutés au répertoire source après la copie initiale.</span><span class="sxs-lookup"><span data-stu-id="211da-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="211da-139">La valeur `$true` indique que, après la copie initiale, les nouveaux fichiers source doivent être copiés dans la destination.</span><span class="sxs-lookup"><span data-stu-id="211da-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="211da-140">Si la valeur est définie sur `$false`, la ressource met en cache le contenu du répertoire source et ignore les fichiers ajoutés après la copie initiale.</span><span class="sxs-lookup"><span data-stu-id="211da-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="211da-141">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="211da-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="211da-142">Si vous ne spécifiez pas de valeur pour **Credential** ou **PSRunAsCredential**, la ressource utilise le compte d’ordinateur du nœud cible pour accéder à **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="211da-142">If you do not specify a value for **Credential** or **PSRunAsCredential**, the resource will use the computer account of the target node to access the **SourcePath**.</span></span> <span data-ttu-id="211da-143">Quand **SourcePath** représente un partage UNC, cela peut provoquer une erreur « Accès refusé ».</span><span class="sxs-lookup"><span data-stu-id="211da-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="211da-144">Vérifiez que vos autorisations sont définies en conséquence, ou utilisez les propriétés **Credential** ou **PSRunAsCredential** pour spécifier le compte qui doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="211da-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="211da-145">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="211da-145">Common properties</span></span>

|<span data-ttu-id="211da-146">Propriété</span><span class="sxs-lookup"><span data-stu-id="211da-146">Property</span></span> |<span data-ttu-id="211da-147">Description</span><span class="sxs-lookup"><span data-stu-id="211da-147">Description</span></span> |
|---|---|
|<span data-ttu-id="211da-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="211da-148">DependsOn</span></span> |<span data-ttu-id="211da-149">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="211da-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="211da-150">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="211da-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="211da-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="211da-151">Ensure</span></span> |<span data-ttu-id="211da-152">Détermine si le fichier et le contenu (**Contents**) à **Destination** doivent exister ou non.</span><span class="sxs-lookup"><span data-stu-id="211da-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="211da-153">Définissez cette propriété sur **Present** pour garantir l’existence du fichier.</span><span class="sxs-lookup"><span data-stu-id="211da-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="211da-154">Définissez la propriété sur **Absent** pour vous assurer que le contenu ne se trouve pas à l’emplacement donné.</span><span class="sxs-lookup"><span data-stu-id="211da-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="211da-155">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="211da-155">The default value is **Present**.</span></span> |
|<span data-ttu-id="211da-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="211da-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="211da-157">Définit les informations d’identification pour l’exécution de l’ensemble de la ressource.</span><span class="sxs-lookup"><span data-stu-id="211da-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="211da-158">La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="211da-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="211da-159">Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="211da-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="211da-160">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="211da-160">Additional information</span></span>

- <span data-ttu-id="211da-161">Quand vous spécifiez uniquement un **DestinationPath**, la ressource vérifie que le chemin existe si la valeur définie est **Present** ou qu’il n’existe pas si la valeur définie est **Absent**.</span><span class="sxs-lookup"><span data-stu-id="211da-161">When you only specify a **DestinationPath**, the resource ensures that the path exists if **Present** or does not exist if **Absent**.</span></span>
- <span data-ttu-id="211da-162">Quand vous spécifiez un **SourcePath** et un **DestinationPath** et que **Type** a la valeur **Directory**, la ressource copie le répertoire source sur le chemin de destination.</span><span class="sxs-lookup"><span data-stu-id="211da-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="211da-163">Les propriétés **Recurse**, **Force** et **MatchSource** modifient le type d’opération de copie effectuée, tandis que **Credential** détermine le compte à utiliser pour accéder au répertoire source.</span><span class="sxs-lookup"><span data-stu-id="211da-163">The properties **Recurse**, **Force**, and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="211da-164">Si vous avez spécifié la valeur **ReadOnly** pour la propriété **Attributes** avec un **DestinationPath**, **Ensure** **Present** crée le chemin spécifié, tandis que **Contents** définit le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="211da-164">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath**, **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="211da-165">Un paramètre **Ensure** **Absent** ignore entièrement la propriété **Attributes** et supprime les fichiers situés sur le chemin spécifié.</span><span class="sxs-lookup"><span data-stu-id="211da-165">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="211da-166">Exemple</span><span class="sxs-lookup"><span data-stu-id="211da-166">Example</span></span>

<span data-ttu-id="211da-167">L’exemple suivant copie un répertoire et ses sous-répertoires d’un serveur Pull vers à un nœud cible à l’aide de la ressource File.</span><span class="sxs-lookup"><span data-stu-id="211da-167">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="211da-168">Si l’opération réussit, la ressource Log consigne un message de confirmation dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="211da-168">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="211da-169">Le répertoire source est un chemin d’accès UNC (`\\PullServer\DemoSource`) partagé à partir du serveur Pull.</span><span class="sxs-lookup"><span data-stu-id="211da-169">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="211da-170">La propriété **Recurse** vérifie que tous les sous-répertoires sont également copiés.</span><span class="sxs-lookup"><span data-stu-id="211da-170">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="211da-171">Le gestionnaire de configuration local (LCM) sur le nœud cible s’exécute dans le contexte du compte système local par défaut.</span><span class="sxs-lookup"><span data-stu-id="211da-171">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="211da-172">Pour autoriser l’accès à **SourcePath**, accordez les autorisations appropriées au compte d’ordinateur du nœud cible.</span><span class="sxs-lookup"><span data-stu-id="211da-172">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="211da-173">**Credential** et **PSDSCRunAsCredential** modifient tous deux le contexte dont se sert le LCM pour accéder au **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="211da-173">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="211da-174">Vous devez quand même accorder l’accès au compte qui sera utilisé pour accéder à **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="211da-174">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="211da-175">Pour plus d’informations sur l’utilisation de **Credentials** dans DSC, consultez [Run As User](../../../configurations/runAsUser.md) (Exécuter en tant qu’utilisateur) ou [Config Data Credentials](../../../configurations/configDataCredentials.md) (Informations d’identification des données de configuration).</span><span class="sxs-lookup"><span data-stu-id="211da-175">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>