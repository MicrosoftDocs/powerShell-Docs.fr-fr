---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,installation
title: Utilisation du Concepteur de ressources
description: L’outil Concepteur de ressources est un ensemble d’applets de commande exposées par le module xDscResourceDesigner qui facilite la création de ressources DSC PowerShell.
ms.openlocfilehash: efe36d045ac3fba3823cb1f812bb5761d238fdf1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656485"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="8e984-104">Utilisation du Concepteur de ressources</span><span class="sxs-lookup"><span data-stu-id="8e984-104">Using the Resource Designer tool</span></span>

> <span data-ttu-id="8e984-105">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8e984-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8e984-106">L’outil Concepteur de ressources est un ensemble d’applets de commande exposées par le module **xDscResourceDesigner** qui facilite la création de ressources DSC Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8e984-106">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="8e984-107">Les applets de commande de cette ressource vous aident à créer le schéma MOF, le module de script et la structure de répertoires de votre nouvelle ressource.</span><span class="sxs-lookup"><span data-stu-id="8e984-107">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="8e984-108">Pour plus d’informations sur les ressources DSC, consultez [Création de ressources DSC Windows PowerShell personnalisées](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="8e984-108">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span> <span data-ttu-id="8e984-109">Dans cet article, nous allons créer une ressource DSC qui gère les utilisateurs Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8e984-109">In this article, we will create a DSC resource that manages Active Directory users.</span></span> <span data-ttu-id="8e984-110">Utilisez l’applet de commande [Install-Module](/powershell/module/PowershellGet/Install-Module) pour installer le module **xDscResourceDesigner**.</span><span class="sxs-lookup"><span data-stu-id="8e984-110">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="8e984-111">Création de propriétés de ressource</span><span class="sxs-lookup"><span data-stu-id="8e984-111">Creating resource properties</span></span>

<span data-ttu-id="8e984-112">La première chose à faire est de décider des propriétés que doit exposer la ressource.</span><span class="sxs-lookup"><span data-stu-id="8e984-112">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="8e984-113">Pour cet exemple, nous allons définir un utilisateur Active Directory avec les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="8e984-113">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="8e984-114">Nom du paramètre  Description</span><span class="sxs-lookup"><span data-stu-id="8e984-114">Parameter name  Description</span></span>

- <span data-ttu-id="8e984-115">**UserName**  : propriété de clé qui identifie de façon unique un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e984-115">**UserName** : Key property that uniquely identifies a user.</span></span>
- <span data-ttu-id="8e984-116">**Ensure**  : spécifie si le compte d’utilisateur doit être Present ou Absent.</span><span class="sxs-lookup"><span data-stu-id="8e984-116">**Ensure** : Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="8e984-117">Ce paramètre a seulement deux valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="8e984-117">This parameter will have only two possible values.</span></span>
- <span data-ttu-id="8e984-118">**DomainCredential**  : mot de passe de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e984-118">**DomainCredential** : The domain password for the user.</span></span>
- <span data-ttu-id="8e984-119">**Password**  : mot de passe souhaité pour que l’utilisateur autorise une configuration à modifier le mot de passe si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8e984-119">**Password** : The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="8e984-120">Pour créer les propriétés, nous utilisons l’applet de commande `New-xDscResourceProperty`.</span><span class="sxs-lookup"><span data-stu-id="8e984-120">To create the properties, we use the `New-xDscResourceProperty` cmdlet.</span></span> <span data-ttu-id="8e984-121">Les commandes PowerShell suivantes créent les propriétés décrites ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="8e984-121">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="8e984-122">Créer la ressource</span><span class="sxs-lookup"><span data-stu-id="8e984-122">Create the resource</span></span>

<span data-ttu-id="8e984-123">Maintenant que les propriétés de la ressource ont été créées, nous pouvons appeler l’applet de commande `New-xDscResource` pour créer la ressource.</span><span class="sxs-lookup"><span data-stu-id="8e984-123">Now that the resource properties have been created, we can call the `New-xDscResource` cmdlet to create the resource.</span></span> <span data-ttu-id="8e984-124">L’applet de commande `New-xDscResource` prend la liste des propriétés comme paramètres.</span><span class="sxs-lookup"><span data-stu-id="8e984-124">The `New-xDscResource` cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="8e984-125">Elle prend également le chemin de l’emplacement auquel le module doit être créé, le nom de la nouvelle ressource et le nom du module dans lequel elle est contenue.</span><span class="sxs-lookup"><span data-stu-id="8e984-125">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="8e984-126">La commande PowerShell suivante crée la ressource.</span><span class="sxs-lookup"><span data-stu-id="8e984-126">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="8e984-127">L’applet de commande `New-xDscResource` crée le schéma MOF, un script de ressource squelette, la structure de répertoires nécessaire pour votre nouvelle ressource et un manifeste pour le module qui expose la nouvelle ressource.</span><span class="sxs-lookup"><span data-stu-id="8e984-127">The `New-xDscResource` cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="8e984-128">Le fichier du schéma MOF se trouve dans `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof` et son contenu est le suivant.</span><span class="sxs-lookup"><span data-stu-id="8e984-128">The MOF schema file is at `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof`, and its contents are as follows.</span></span>

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

<span data-ttu-id="8e984-129">Le script de la ressource se trouve dans `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1`.</span><span class="sxs-lookup"><span data-stu-id="8e984-129">The resource script is at `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1`.</span></span>
<span data-ttu-id="8e984-130">Il ne comprend pas la logique permettant d’implémenter la ressource. Vous devrez l’ajouter vous-même.</span><span class="sxs-lookup"><span data-stu-id="8e984-130">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="8e984-131">Voici le contenu du script squelette.</span><span class="sxs-lookup"><span data-stu-id="8e984-131">The contents of the skeleton script are as follows.</span></span>

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}

function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1
}

function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  <#
  $result = [System.Boolean]

  $result
  #>
}

Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a><span data-ttu-id="8e984-132">Mise à jour de la ressource</span><span class="sxs-lookup"><span data-stu-id="8e984-132">Updating the resource</span></span>

<span data-ttu-id="8e984-133">Si vous avez besoin d’ajouter ou de modifier la liste des paramètres de la ressource, vous pouvez appeler l’applet de commande `Update-xDscResource`.</span><span class="sxs-lookup"><span data-stu-id="8e984-133">If you need to add or modify the parameter list of the resource, you can call the `Update-xDscResource` cmdlet.</span></span> <span data-ttu-id="8e984-134">L’applet de commande met à jour la ressource avec une nouvelle liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="8e984-134">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="8e984-135">Si vous avez déjà ajouté une logique au script de votre ressource, celle-ci reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="8e984-135">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="8e984-136">Supposons, par exemple, que vous vouliez inclure le dernier journal en date dans votre ressource pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8e984-136">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="8e984-137">Au lieu de réécrire complètement la ressource, vous pouvez appeler `New-xDscResourceProperty` pour créer la nouvelle propriété, puis appeler `Update-xDscResource` et ajouter votre nouvelle propriété à la liste des propriétés.</span><span class="sxs-lookup"><span data-stu-id="8e984-137">Rather than writing the resource again completely, you can call the `New-xDscResourceProperty` to create the new property, and then call `Update-xDscResource` and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="8e984-138">Test d’un schéma de ressource</span><span class="sxs-lookup"><span data-stu-id="8e984-138">Testing a resource schema</span></span>

<span data-ttu-id="8e984-139">L’outil Concepteur de ressources expose une applet de commande supplémentaire qui peut être utilisée pour tester la validité d’un schéma MOF que vous avez écrit manuellement.</span><span class="sxs-lookup"><span data-stu-id="8e984-139">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="8e984-140">Appelez l’applet de commande `Test-xDscSchema` en passant le chemin d’un schéma de ressource MOF comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="8e984-140">Call the `Test-xDscSchema` cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="8e984-141">C’est dans ce schéma que l’applet de commande affiche les éventuelles erreurs.</span><span class="sxs-lookup"><span data-stu-id="8e984-141">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="8e984-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e984-142">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="8e984-143">Concepts</span><span class="sxs-lookup"><span data-stu-id="8e984-143">Concepts</span></span>

[<span data-ttu-id="8e984-144">Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e984-144">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="8e984-145">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="8e984-145">Other Resources</span></span>

[<span data-ttu-id="8e984-146">Module xDscResourceDesigner</span><span class="sxs-lookup"><span data-stu-id="8e984-146">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
