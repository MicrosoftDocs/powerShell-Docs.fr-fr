---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: e2e2166bbe65256c67937be8da1a3e82944840e8
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343231"
---
# <span data-ttu-id="829e8-103">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="829e8-103">Set-Acl</span></span>

## <span data-ttu-id="829e8-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="829e8-104">SYNOPSIS</span></span>
<span data-ttu-id="829e8-105">Change le descripteur de sécurité de l'élément spécifié, par exemple un fichier ou une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="829e8-105">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

## <span data-ttu-id="829e8-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="829e8-106">SYNTAX</span></span>

### <span data-ttu-id="829e8-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="829e8-107">ByPath (Default)</span></span>

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [[-CentralAccessPolicy] <String>] [-ClearCentralAccessPolicy]
 [-Passthru] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="829e8-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="829e8-108">ByInputObject</span></span>

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="829e8-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="829e8-109">ByLiteralPath</span></span>

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [[-CentralAccessPolicy] <String>]
 [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="829e8-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="829e8-110">DESCRIPTION</span></span>

<span data-ttu-id="829e8-111">L' `Set-Acl` applet de commande modifie le descripteur de sécurité d’un élément spécifié, tel qu’un fichier ou une clé de Registre, pour qu’il corresponde aux valeurs d’un descripteur de sécurité que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="829e8-111">The `Set-Acl` cmdlet changes the security descriptor of a specified item, such as a file or a registry key, to match the values in a security descriptor that you supply.</span></span>

<span data-ttu-id="829e8-112">Pour utiliser `Set-Acl` , utilisez le paramètre **path** ou **InputObject** pour identifier l’élément dont vous souhaitez modifier le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="829e8-112">To use `Set-Acl`, use the **Path** or **InputObject** parameter to identify the item whose security descriptor you want to change.</span></span> <span data-ttu-id="829e8-113">Utilisez ensuite les paramètres **AclObject** ou **SecurityDescriptor** pour fournir un descripteur de sécurité contenant les valeurs à appliquer.</span><span class="sxs-lookup"><span data-stu-id="829e8-113">Then, use the **AclObject** or **SecurityDescriptor** parameters to supply a security descriptor that has the values you want to apply.</span></span> <span data-ttu-id="829e8-114">`Set-Acl` applique le descripteur de sécurité fourni.</span><span class="sxs-lookup"><span data-stu-id="829e8-114">`Set-Acl` applies the security descriptor that is supplied.</span></span> <span data-ttu-id="829e8-115">Cette applet de commande utilise la valeur du paramètre **AclObject** comme modèle, puis change les valeurs du descripteur de sécurité de l'élément pour qu'elles correspondent aux valeurs du paramètre **AclObject**.</span><span class="sxs-lookup"><span data-stu-id="829e8-115">It uses the value of the **AclObject** parameter as a model and changes the values in the item's security descriptor to match the values in the **AclObject** parameter.</span></span>

## <span data-ttu-id="829e8-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="829e8-116">EXAMPLES</span></span>

### <span data-ttu-id="829e8-117">Exemple 1 : copier un descripteur de sécurité d’un fichier à un autre</span><span class="sxs-lookup"><span data-stu-id="829e8-117">Example 1: Copy a security descriptor from one file to another</span></span>

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

<span data-ttu-id="829e8-118">Ces commandes copient les valeurs du descripteur de sécurité du fichier Dog.txt vers le descripteur de sécurité du fichier Cat.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-118">These commands copy the values from the security descriptor of the Dog.txt file to the security descriptor of the Cat.txt file.</span></span> <span data-ttu-id="829e8-119">À la fin de l'exécution des commandes, les descripteurs de sécurité des fichiers Dog.txt et Cat.txt sont identiques.</span><span class="sxs-lookup"><span data-stu-id="829e8-119">When the commands complete, the security descriptors of the Dog.txt and Cat.txt files are identical.</span></span>

<span data-ttu-id="829e8-120">La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>
<span data-ttu-id="829e8-121">L’opérateur d’assignation ( `=` ) stocke le descripteur de sécurité dans la valeur de la variable $DogACL.</span><span class="sxs-lookup"><span data-stu-id="829e8-121">The assignment operator (`=`) stores the security descriptor in the value of the $DogACL variable.</span></span>

<span data-ttu-id="829e8-122">La deuxième commande utilise `Set-Acl` pour modifier les valeurs de la liste de contrôle d’accès de Cat.txt en valeurs dans `$DogACL` .</span><span class="sxs-lookup"><span data-stu-id="829e8-122">The second command uses `Set-Acl` to change the values in the ACL of Cat.txt to the values in `$DogACL`.</span></span>

<span data-ttu-id="829e8-123">La valeur du paramètre **Path** correspond au chemin d'accès du fichier Cat.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-123">The value of the **Path** parameter is the path to the Cat.txt file.</span></span> <span data-ttu-id="829e8-124">La valeur du paramètre **AclObject** est la liste de contrôle d’accès du modèle, dans ce cas, la liste de contrôle d’accès (ACL) de Dog.txt telle qu’elle est enregistrée dans la `$DogACL` variable.</span><span class="sxs-lookup"><span data-stu-id="829e8-124">The value of the **AclObject** parameter is the model ACL, in this case, the ACL of Dog.txt as saved in the `$DogACL` variable.</span></span>

### <span data-ttu-id="829e8-125">Exemple 2 : utiliser l’opérateur de pipeline pour passer un descripteur</span><span class="sxs-lookup"><span data-stu-id="829e8-125">Example 2: Use the pipeline operator to pass a descriptor</span></span>

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

<span data-ttu-id="829e8-126">Cette commande est presque identique à la commande dans l’exemple précédent, à ceci près qu’elle utilise un opérateur de pipeline ( `|` ) pour envoyer le descripteur de sécurité à partir d’une `Get-Acl` commande vers une `Set-Acl` commande.</span><span class="sxs-lookup"><span data-stu-id="829e8-126">This command is almost the same as the command in the previous example, except that it uses a pipeline operator (`|`) to send the security descriptor from a `Get-Acl` command to a `Set-Acl` command.</span></span>

<span data-ttu-id="829e8-127">La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-127">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span> <span data-ttu-id="829e8-128">L’opérateur de pipeline ( `|` ) passe un objet qui représente le descripteur de sécurité Dog.txt à l’applet de commande `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="829e8-128">The pipeline operator (`|`) passes an object that represents the Dog.txt security descriptor to the `Set-Acl` cmdlet.</span></span>

<span data-ttu-id="829e8-129">La deuxième commande utilise `Set-Acl` pour appliquer le descripteur de sécurité de Dog.txt à Cat.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-129">The second command uses `Set-Acl` to apply the security descriptor of Dog.txt to Cat.txt.</span></span>
<span data-ttu-id="829e8-130">À la fin de l'exécution de la commande, les listes ACL des fichiers Dog.txt et Cat.txt sont identiques.</span><span class="sxs-lookup"><span data-stu-id="829e8-130">When the command completes, the ACLs of the Dog.txt and Cat.txt files are identical.</span></span>

### <span data-ttu-id="829e8-131">Exemple 3 : appliquer un descripteur de sécurité à plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="829e8-131">Example 3: Apply a security descriptor to multiple files</span></span>

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

<span data-ttu-id="829e8-132">Ces commandes appliquent les descripteurs de sécurité dans le fichier File0.txt à tous les fichiers texte du `C:\Temp` répertoire et à tous ses sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="829e8-132">These commands apply the security descriptors in the File0.txt file to all text files in the `C:\Temp` directory and all of its subdirectories.</span></span>

<span data-ttu-id="829e8-133">La première commande obtient le descripteur de sécurité du fichier File0.txt dans le répertoire actif et utilise l’opérateur `=` d’assignation () pour le stocker dans la `$NewACL` variable.</span><span class="sxs-lookup"><span data-stu-id="829e8-133">The first command gets the security descriptor of the File0.txt file in the current directory and uses the assignment operator (`=`) to store it in the `$NewACL` variable.</span></span>

<span data-ttu-id="829e8-134">La première commande du pipeline utilise l’applet de commande Get-ChildItem pour récupérer tous les fichiers texte dans le `C:\Temp` répertoire.</span><span class="sxs-lookup"><span data-stu-id="829e8-134">The first command in the pipeline uses the Get-ChildItem cmdlet to get all of the text files in the `C:\Temp` directory.</span></span> <span data-ttu-id="829e8-135">Le paramètre **recurse** étend la commande à tous les sous-répertoires de `C:\temp` .</span><span class="sxs-lookup"><span data-stu-id="829e8-135">The **Recurse** parameter extends the command to all subdirectories of `C:\temp`.</span></span> <span data-ttu-id="829e8-136">Le paramètre **include** limite les fichiers récupérés à ceux avec l' `.txt` extension de nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="829e8-136">The **Include** parameter limits the files retrieved to those with the `.txt` file name extension.</span></span> <span data-ttu-id="829e8-137">Le paramètre **Force** obtient les fichiers cachés, qui seraient sinon exclus.</span><span class="sxs-lookup"><span data-stu-id="829e8-137">The **Force** parameter gets hidden files, which would otherwise be excluded.</span></span> <span data-ttu-id="829e8-138">(Vous ne pouvez pas utiliser `c:\temp\*.txt` , car le paramètre **recurse** fonctionne sur les répertoires, et non sur les fichiers.)</span><span class="sxs-lookup"><span data-stu-id="829e8-138">(You cannot use `c:\temp\*.txt`, because the **Recurse** parameter works on directories, not on files.)</span></span>

<span data-ttu-id="829e8-139">L’opérateur de pipeline ( `|` ) envoie les objets représentant les fichiers récupérés à l’applet de commande `Set-Acl` , qui applique le descripteur de sécurité dans le paramètre **AclObject** à tous les fichiers dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="829e8-139">The pipeline operator (`|`) sends the objects representing the retrieved files to the `Set-Acl` cmdlet, which applies the security descriptor in the **AclObject** parameter to all of the files in the pipeline.</span></span>

<span data-ttu-id="829e8-140">Dans la pratique, il est préférable d’utiliser le paramètre **WhatIf** avec toutes les `Set-Acl` commandes qui peuvent affecter plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="829e8-140">In practice, it is best to use the **WhatIf** parameter with all `Set-Acl` commands that can affect more than one item.</span></span> <span data-ttu-id="829e8-141">Dans ce cas, la deuxième commande dans le pipeline est `Set-Acl -AclObject $NewAcl -WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="829e8-141">In this case, the second command in the pipeline would be `Set-Acl -AclObject $NewAcl -WhatIf`.</span></span> <span data-ttu-id="829e8-142">Cette commande répertorie les fichiers affectés par la commande.</span><span class="sxs-lookup"><span data-stu-id="829e8-142">This command lists the files that would be affected by the command.</span></span> <span data-ttu-id="829e8-143">Après avoir vérifié le résultat, vous pouvez réexécuter la commande sans le paramètre **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="829e8-143">After reviewing the result, you can run the command again without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="829e8-144">Exemple 4 : désactiver l’héritage et conserver les règles d’accès héritées</span><span class="sxs-lookup"><span data-stu-id="829e8-144">Example 4: Disable inheritance and preserve inherited access rules</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="829e8-145">Ces commandes désactivent l’héritage d’accès à partir des dossiers parents, tout en conservant les règles d’accès hérité existantes.</span><span class="sxs-lookup"><span data-stu-id="829e8-145">These commands is will disable access inheritance from parent folders, while still preserving the existing inherited access rules.</span></span>

<span data-ttu-id="829e8-146">La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-146">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="829e8-147">Ensuite, les variables sont créées pour convertir les règles d’accès héritées en règles d’accès explicites.</span><span class="sxs-lookup"><span data-stu-id="829e8-147">Next, variables are created to convert the inherited access rules to explicit access rules.</span></span> <span data-ttu-id="829e8-148">Pour protéger les règles d’accès associées à cet héritage, affectez la valeur à la `$isProtected` variable `$true` . pour autoriser l’héritage, affectez à la valeur `$isProtected` `$false` .</span><span class="sxs-lookup"><span data-stu-id="829e8-148">To protect the access rules associated with this from inheritance, set the `$isProtected` variable to `$true`.to allow inheritance, set `$isProtected` to `$false`.</span></span> <span data-ttu-id="829e8-149">Pour plus d’informations, consultez [Set Access Rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span><span class="sxs-lookup"><span data-stu-id="829e8-149">For more information, see [set access rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span></span>
<span data-ttu-id="829e8-150">La `$preserveInheritance` variable a la valeur `$true` pour conserver les règles d’accès héritées ; false pour supprimer les règles d’accès héritées.</span><span class="sxs-lookup"><span data-stu-id="829e8-150">The `$preserveInheritance` variable set to `$true` to preserve inherited access rules; false to remove inherited access rules.</span></span> <span data-ttu-id="829e8-151">La protection de la règle d’accès est ensuite mise à jour à l’aide de la méthode **SetAccessRuleProtection ()** .</span><span class="sxs-lookup"><span data-stu-id="829e8-151">Then the access rule protection is updated using the **SetAccessRuleProtection()** method.</span></span>

<span data-ttu-id="829e8-152">La dernière commande utilise `Set-Acl` pour appliquer le descripteur de sécurité de à Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-152">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="829e8-153">Une fois la commande terminée, les listes de contrôle d’accès des Dog.txt qui ont été héritées du dossier animaux sont directement appliquées à Dog.txt, et les nouvelles stratégies d’accès ajoutées aux animaux ne modifient pas l’accès à Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-153">When the command completes, the ACLs of the Dog.txt that were inherited from the Pets folder will be applied directly to Dog.txt, and new access policies added to Pets will not change the access to Dog.txt.</span></span>

### <span data-ttu-id="829e8-154">Exemple 5 : accorder aux administrateurs le contrôle total du fichier</span><span class="sxs-lookup"><span data-stu-id="829e8-154">Example 5: Grant Administrators Full Control of the file</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="829e8-155">Cette commande accorde au groupe **BUILTIN\Administrators** le contrôle total du fichier Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-155">This command will grant the **BUILTIN\Administrators** group Full control of the Dog.txt file.</span></span>

<span data-ttu-id="829e8-156">La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-156">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="829e8-157">Les variables suivantes sont créées pour accorder au groupe **BUILTIN\Administrators** le contrôle total du fichier Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-157">Next variables are created to grant the **BUILTIN\Administrators** group full control of the Dog.txt file.</span></span> <span data-ttu-id="829e8-158">La `$identity` variable définie sur le nom d’un [compte d’utilisateur](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span><span class="sxs-lookup"><span data-stu-id="829e8-158">The `$identity` variable set to the name of a [user account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span></span> <span data-ttu-id="829e8-159">La `$fileSystemRights` variable a la valeur FullControl et peut être l’une des valeurs [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) qui spécifie le type d’opération associé à la règle d’accès.</span><span class="sxs-lookup"><span data-stu-id="829e8-159">The `$fileSystemRights` variable set to FullControl, and can be any one of the [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) values that specifies the type of operation associated with the access rule.</span></span> <span data-ttu-id="829e8-160">La `$type` variable a la valeur « Allow » pour spécifier s’il faut autoriser ou refuser l’opération.</span><span class="sxs-lookup"><span data-stu-id="829e8-160">The `$type` variable set to "Allow" to specifies whether to allow or deny the operation.</span></span> <span data-ttu-id="829e8-161">La `$fileSystemAccessRuleArgumentList` variable est une liste d’arguments qui doit être passée lors de la création du nouvel objet **FileSystemAccessRule** .</span><span class="sxs-lookup"><span data-stu-id="829e8-161">The `$fileSystemAccessRuleArgumentList` variable is an argument list is to be passed when making the new **FileSystemAccessRule** object.</span></span> <span data-ttu-id="829e8-162">Un nouvel objet **FileSystemAccessRule** est créé, et l’objet **FileSystemAccessRule** est passé à la méthode **SetAccessRule ()** , ajoute la nouvelle règle d’accès.</span><span class="sxs-lookup"><span data-stu-id="829e8-162">Then a new **FileSystemAccessRule** object is created, and the **FileSystemAccessRule** object is passed to the **SetAccessRule()** method, adds the new access rule.</span></span>

<span data-ttu-id="829e8-163">La dernière commande utilise `Set-Acl` pour appliquer le descripteur de sécurité de à Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-163">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="829e8-164">Une fois la commande terminée, le groupe **BUILTIN\Administrateurs** disposera du contrôle total de la Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="829e8-164">When the command completes, the **BUILTIN\Administrators** group will have full control of the Dog.txt.</span></span>

## <span data-ttu-id="829e8-165">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="829e8-165">PARAMETERS</span></span>

### <span data-ttu-id="829e8-166">-AclObject</span><span class="sxs-lookup"><span data-stu-id="829e8-166">-AclObject</span></span>

<span data-ttu-id="829e8-167">Spécifie une liste de contrôle d'accès (ACL, Access-Control List) avec les valeurs de propriété souhaitées.</span><span class="sxs-lookup"><span data-stu-id="829e8-167">Specifies an ACL with the desired property values.</span></span> <span data-ttu-id="829e8-168">`Set-Acl` modifie la liste de contrôle d’accès de l’élément spécifié par le paramètre **path** ou **InputObject** afin qu’il corresponde aux valeurs de l’objet de sécurité spécifié.</span><span class="sxs-lookup"><span data-stu-id="829e8-168">`Set-Acl` changes the ACL of item specified by the **Path** or **InputObject** parameter to match the values in the specified security object.</span></span>

<span data-ttu-id="829e8-169">Vous pouvez enregistrer la sortie d’une `Get-Acl` commande dans une variable, puis utiliser le paramètre **AclObject** pour passer la variable ou saisir une `Get-Acl` commande.</span><span class="sxs-lookup"><span data-stu-id="829e8-169">You can save the output of a `Get-Acl` command in a variable and then use the **AclObject** parameter to pass the variable, or type a `Get-Acl` command.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-170">-CentralAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="829e8-170">-CentralAccessPolicy</span></span>

<span data-ttu-id="829e8-171">Établit ou change la stratégie d'accès centralisée de l'élément.</span><span class="sxs-lookup"><span data-stu-id="829e8-171">Establishes or changes the central access policy of the item.</span></span>
<span data-ttu-id="829e8-172">Entrez l'ID ou le nom convivial d'une stratégie d'accès centralisée sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="829e8-172">Enter the CAP ID or friendly name of a central access policy on the computer.</span></span>

<span data-ttu-id="829e8-173">À compter de Windows Server 2012, les administrateurs peuvent utiliser Active Directory et stratégie de groupe pour définir des stratégies d’accès centralisées pour les utilisateurs et les groupes.</span><span class="sxs-lookup"><span data-stu-id="829e8-173">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span>
<span data-ttu-id="829e8-174">Pour plus d’informations, consultez [Access Control dynamique : vue d’ensemble du scénario](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span><span class="sxs-lookup"><span data-stu-id="829e8-174">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="829e8-175">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="829e8-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-176">-ClearCentralAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="829e8-176">-ClearCentralAccessPolicy</span></span>

<span data-ttu-id="829e8-177">Supprime la stratégie d'accès centralisée de l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="829e8-177">Removes the central access policy from the specified item.</span></span>

<span data-ttu-id="829e8-178">À compter de Windows Server 2012, les administrateurs peuvent utiliser Active Directory et stratégie de groupe pour définir des stratégies d’accès centralisées pour les utilisateurs et les groupes.</span><span class="sxs-lookup"><span data-stu-id="829e8-178">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="829e8-179">Pour plus d’informations, consultez [Access Control dynamique : vue d’ensemble du scénario](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span><span class="sxs-lookup"><span data-stu-id="829e8-179">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="829e8-180">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="829e8-180">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-181">-Exclude</span><span class="sxs-lookup"><span data-stu-id="829e8-181">-Exclude</span></span>

<span data-ttu-id="829e8-182">Omet les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="829e8-182">Omits the specified items.</span></span> <span data-ttu-id="829e8-183">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="829e8-183">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="829e8-184">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="829e8-184">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="829e8-185">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="829e8-185">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="829e8-186">-Filter</span><span class="sxs-lookup"><span data-stu-id="829e8-186">-Filter</span></span>

<span data-ttu-id="829e8-187">Spécifie un filtre dans le format ou le langage du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="829e8-187">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="829e8-188">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="829e8-188">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="829e8-189">La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="829e8-189">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="829e8-190">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lors de la récupération des objets, plutôt que de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="829e8-190">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="829e8-191">-Include</span><span class="sxs-lookup"><span data-stu-id="829e8-191">-Include</span></span>

<span data-ttu-id="829e8-192">Modifie uniquement les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="829e8-192">Changes only the specified items.</span></span> <span data-ttu-id="829e8-193">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="829e8-193">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="829e8-194">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="829e8-194">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="829e8-195">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="829e8-195">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="829e8-196">-InputObject</span><span class="sxs-lookup"><span data-stu-id="829e8-196">-InputObject</span></span>

<span data-ttu-id="829e8-197">Change le descripteur de sécurité de l'objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="829e8-197">Changes the security descriptor of the specified object.</span></span> <span data-ttu-id="829e8-198">Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.</span><span class="sxs-lookup"><span data-stu-id="829e8-198">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="829e8-199">Vous ne pouvez pas diriger l’objet à modifier en `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="829e8-199">You cannot pipe the object to be changed to `Set-Acl`.</span></span> <span data-ttu-id="829e8-200">Utilisez plutôt le paramètre **InputObject** explicitement dans la commande.</span><span class="sxs-lookup"><span data-stu-id="829e8-200">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="829e8-201">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="829e8-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-202">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="829e8-202">-LiteralPath</span></span>

<span data-ttu-id="829e8-203">Change le descripteur de sécurité de l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="829e8-203">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="829e8-204">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="829e8-204">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="829e8-205">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="829e8-205">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="829e8-206">Si le chemin d’accès comprend des caractères d’échappement, mettez-le entre des guillemets simples ( `'` ).</span><span class="sxs-lookup"><span data-stu-id="829e8-206">If the path includes escape characters, enclose it in single quotation marks (`'`).</span></span>
<span data-ttu-id="829e8-207">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="829e8-207">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="829e8-208">Ce paramètre a été introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="829e8-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-209">-PassThru</span><span class="sxs-lookup"><span data-stu-id="829e8-209">-Passthru</span></span>

<span data-ttu-id="829e8-210">Retourne un objet qui représente le descripteur de sécurité modifié.</span><span class="sxs-lookup"><span data-stu-id="829e8-210">Returns an object that represents the security descriptor that was changed.</span></span> <span data-ttu-id="829e8-211">Par défaut, cette applet de commande ne génère aucun résultat.</span><span class="sxs-lookup"><span data-stu-id="829e8-211">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-212">-Path</span><span class="sxs-lookup"><span data-stu-id="829e8-212">-Path</span></span>

<span data-ttu-id="829e8-213">Change le descripteur de sécurité de l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="829e8-213">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="829e8-214">Entrez le chemin d'accès d'un élément, par exemple le chemin d'accès d'un fichier ou d'une clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="829e8-214">Enter the path to an item, such as a path to a file or registry key.</span></span> <span data-ttu-id="829e8-215">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="829e8-215">Wildcards are permitted.</span></span>

<span data-ttu-id="829e8-216">Si vous passez un objet de sécurité à `Set-Acl` (en utilisant les paramètres **AclObject** ou **SecurityDescriptor** ou en passant un objet de sécurité de Get-Acl à `Set-Acl` ) et que vous omettez le paramètre **path** (Name et value), `Set-Acl` utilise le chemin d’accès qui est inclus dans l’objet de sécurité.</span><span class="sxs-lookup"><span data-stu-id="829e8-216">If you pass a security object to `Set-Acl` (either by using the **AclObject** or **SecurityDescriptor** parameters or by passing a security object from Get-Acl to `Set-Acl`), and you omit the **Path** parameter (name and value), `Set-Acl` uses the path that is included in the security object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="829e8-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="829e8-217">-Confirm</span></span>

<span data-ttu-id="829e8-218">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="829e8-218">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-219">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="829e8-219">-UseTransaction</span></span>

<span data-ttu-id="829e8-220">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="829e8-220">Includes the command in the active transaction.</span></span>
<span data-ttu-id="829e8-221">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="829e8-221">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="829e8-222">Pour plus d'informations, consultez about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="829e8-222">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="829e8-223">-WhatIf</span></span>

<span data-ttu-id="829e8-224">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="829e8-224">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="829e8-225">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="829e8-225">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="829e8-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="829e8-226">CommonParameters</span></span>

<span data-ttu-id="829e8-227">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="829e8-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="829e8-228">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="829e8-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="829e8-229">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="829e8-229">INPUTS</span></span>

### <span data-ttu-id="829e8-230">System. Security. AccessControl. objet ObjectSecurity, System. Security. AccessControl. CommonSecurityDescriptor</span><span class="sxs-lookup"><span data-stu-id="829e8-230">System.Security.AccessControl.ObjectSecurity, System.Security.AccessControl.CommonSecurityDescriptor</span></span>

<span data-ttu-id="829e8-231">Vous pouvez diriger un objet ACL ou un descripteur de sécurité vers `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="829e8-231">You can pipe an ACL object or a security descriptor to `Set-Acl`.</span></span>

## <span data-ttu-id="829e8-232">SORTIES</span><span class="sxs-lookup"><span data-stu-id="829e8-232">OUTPUTS</span></span>

### <span data-ttu-id="829e8-233">System. Security. AccessControl. FileSecurity</span><span class="sxs-lookup"><span data-stu-id="829e8-233">System.Security.AccessControl.FileSecurity</span></span>

<span data-ttu-id="829e8-234">Par défaut, `Set-Acl` ne génère pas de sortie.</span><span class="sxs-lookup"><span data-stu-id="829e8-234">By default, `Set-Acl` does not generate any output.</span></span> <span data-ttu-id="829e8-235">Toutefois, si vous utilisez le paramètre **Passthru** , elle génère un objet de sécurité.</span><span class="sxs-lookup"><span data-stu-id="829e8-235">However, if you use the **Passthru** parameter, it generates a security object.</span></span> <span data-ttu-id="829e8-236">Le type de l'objet de sécurité dépend du type de l'élément.</span><span class="sxs-lookup"><span data-stu-id="829e8-236">The type of the security object depends on the type of the item.</span></span>

## <span data-ttu-id="829e8-237">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="829e8-237">NOTES</span></span>

<span data-ttu-id="829e8-238">L' `Set-Acl` applet de commande est prise en charge par le système de fichiers PowerShell et les fournisseurs de registre.</span><span class="sxs-lookup"><span data-stu-id="829e8-238">The `Set-Acl` cmdlet is supported by the PowerShell file system and registry providers.</span></span> <span data-ttu-id="829e8-239">Ainsi, vous pouvez l'utiliser pour changer les descripteurs de sécurité des fichiers, des répertoires et des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="829e8-239">As such, you can use it to change the security descriptors of files, directories, and registry keys.</span></span>

## <span data-ttu-id="829e8-240">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="829e8-240">RELATED LINKS</span></span>

[<span data-ttu-id="829e8-241">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="829e8-241">Get-Acl</span></span>](Get-Acl.md)

[<span data-ttu-id="829e8-242">FileSystemAccessRule</span><span class="sxs-lookup"><span data-stu-id="829e8-242">FileSystemAccessRule</span></span>](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[<span data-ttu-id="829e8-243">Objet ObjectSecurity. SetAccessRuleProtection</span><span class="sxs-lookup"><span data-stu-id="829e8-243">ObjectSecurity.SetAccessRuleProtection</span></span>](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[<span data-ttu-id="829e8-244">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="829e8-244">FileSystemRights</span></span>](/dotnet/api/system.security.accesscontrol.filesystemrights)
