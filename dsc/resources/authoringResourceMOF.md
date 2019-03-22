---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Écriture d’une ressource DSC personnalisée avec MOF
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059726"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="3ba4a-103">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="3ba4a-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="3ba4a-104">S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3ba4a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3ba4a-105">Dans cette rubrique, nous allons définir le schéma d’une ressource DSC Windows PowerShell personnalisée dans un fichier MOF et implémenter cette ressource dans un fichier de script Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="3ba4a-106">Cette ressource personnalisée permet de créer et de gérer un site web.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="3ba4a-107">Création du schéma MOF</span><span class="sxs-lookup"><span data-stu-id="3ba4a-107">Creating the MOF schema</span></span>

<span data-ttu-id="3ba4a-108">Le schéma définit les propriétés de votre ressource qui peuvent être configurées par un script de configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="3ba4a-109">Structure de dossiers pour une ressource MOF</span><span class="sxs-lookup"><span data-stu-id="3ba4a-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="3ba4a-110">Pour implémenter une ressource personnalisée DSC avec un schéma MOF, créez la structure de dossiers suivante.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="3ba4a-111">Le schéma MOF est défini dans le fichier Demo_IISWebsite.schema.mof et le script de la ressource est défini dans Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="3ba4a-112">Si vous le voulez, vous pouvez créer un fichier de manifeste de module (psd1).</span><span class="sxs-lookup"><span data-stu-id="3ba4a-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="3ba4a-113">Notez qu’il est nécessaire de créer un dossier nommé DSCResources sous le dossier de niveau supérieur, et que le dossier de chaque ressource doit porter le même nom que la ressource.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="3ba4a-114">Le contenu du fichier MOF</span><span class="sxs-lookup"><span data-stu-id="3ba4a-114">The contents of the MOF file</span></span>

<span data-ttu-id="3ba4a-115">Voici un exemple de fichier MOF qui peut être utilisé pour une ressource de site web personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="3ba4a-116">Pour suivre cet exemple, enregistrez ce schéma dans un fichier et appelez le fichier *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="3ba4a-117">Notez les éléments suivants concernant le code ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="3ba4a-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="3ba4a-118">`FriendlyName` définit le nom que vous pouvez utiliser pour faire référence à cette ressource personnalisée dans les scripts de configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="3ba4a-119">Dans cet exemple, `Website` équivaut au nom convivial `Archive` de la ressource Archive intégrée.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="3ba4a-120">La classe que vous définissez pour la ressource personnalisée doit dériver de `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="3ba4a-121">Le qualificateur de type (`[Key]`) d’une propriété indique que cette propriété identifie de manière unique l’instance de ressource.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="3ba4a-122">Au moins une propriété `[Key]` est requise.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="3ba4a-123">Le qualificateur `[Required]` indique que la propriété est obligatoire (une valeur doit être spécifiée dans un script de configuration qui utilise cette ressource).</span><span class="sxs-lookup"><span data-stu-id="3ba4a-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="3ba4a-124">Le qualificateur `[write]` indique que cette propriété est facultative quand vous utilisez la ressource personnalisée dans un script de configuration.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="3ba4a-125">Le qualificateur `[read]` indique qu’une propriété ne peut pas être définie par une configuration et qu’elle ne peut être utilisée qu’à des fins de création de rapports.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="3ba4a-126">`Values` limite les valeurs pouvant être affectées à la propriété à la liste des valeurs définies dans `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="3ba4a-127">Pour plus d’informations, consultez [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="3ba4a-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="3ba4a-128">Il est recommandé d’utiliser une propriété appelée `Ensure` avec les valeurs `Present` et `Absent` dans votre ressource pour maintenir un style cohérent entre les ressources DSC intégrées.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="3ba4a-129">Nommez le fichier de schéma de la ressource personnalisée comme suit : `classname.schema.mof`, où `classname` est l’identificateur qui suit le mot clé `class` dans votre définition de schéma.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="3ba4a-130">Écriture du script de la ressource</span><span class="sxs-lookup"><span data-stu-id="3ba4a-130">Writing the resource script</span></span>

<span data-ttu-id="3ba4a-131">Le script de la ressource implémente la logique de la ressource.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="3ba4a-132">Dans ce module, vous devez inclure les trois fonctions **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="3ba4a-133">Les trois fonctions doivent accepter un jeu de paramètres identique à l’ensemble de propriétés définies dans le schéma MOF que vous avez créé pour votre ressource.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="3ba4a-134">Dans ce document, nous appelons cet ensemble de propriétés « propriétés de ressource ».</span><span class="sxs-lookup"><span data-stu-id="3ba4a-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="3ba4a-135">Stockez ces trois fonctions dans un fichier appelé <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="3ba4a-136">Dans l’exemple suivant, les fonctions sont stockées dans un fichier appelé Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> [!NOTE]
> <span data-ttu-id="3ba4a-137">Quand vous exécutez le même script de configuration plusieurs fois sur votre ressource, vous ne devez pas obtenir d’erreur et la ressource doit avoir le même état que lorsque le script n’est exécuté qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-137">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="3ba4a-138">Pour cela, assurez-vous que vos fonctions **Get-TargetResource** et **TargetResource-Test** ne modifient pas la ressource, et que le fait d’appeler la fonction **Set-TargetResource** plusieurs fois de suite avec les mêmes valeurs de paramètres équivaut toujours à un appel unique.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="3ba4a-139">Dans l’implémentation de la fonction **Get-TargetResource**, utilisez les valeurs de propriétés de ressource de clé qui sont fournies comme paramètres pour vérifier l’état de l’instance de la ressource spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="3ba4a-140">Cette fonction doit retourner une table de hachage comprenant toutes les propriétés de ressource comme clés, ainsi que les valeurs réelles de ces propriétés comme valeurs correspondantes.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="3ba4a-141">Le code suivant montre un exemple.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

<span data-ttu-id="3ba4a-142">Selon les valeurs qui sont spécifiées pour les propriétés de ressource dans le script de configuration, la fonction **Set-TargetResource** doit effectuer l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ba4a-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="3ba4a-143">Créer un site web</span><span class="sxs-lookup"><span data-stu-id="3ba4a-143">Create a new website</span></span>
* <span data-ttu-id="3ba4a-144">Mettre à jour un site web existant</span><span class="sxs-lookup"><span data-stu-id="3ba4a-144">Update an existing website</span></span>
* <span data-ttu-id="3ba4a-145">Supprimer un site web existant</span><span class="sxs-lookup"><span data-stu-id="3ba4a-145">Delete an existing website</span></span>

<span data-ttu-id="3ba4a-146">L’exemple suivant illustre ces actions.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-146">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="3ba4a-147">Enfin, la fonction **Test-TargetResource** doit prendre le même jeu de paramètres que **Get-TargetResource** et **Set-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="3ba4a-148">Dans votre implémentation de **Test-TargetResource**, vérifiez l’état de l’instance de ressource qui est spécifié dans les paramètres de clé.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="3ba4a-149">Si l’état réel de l’instance de ressource ne correspond pas aux valeurs spécifiées dans le jeu de paramètres, retournez **$false**.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="3ba4a-150">Sinon, retournez **$true**.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="3ba4a-151">Le code suivant implémente la fonction **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-151">The following code implements the **Test-TargetResource** function.</span></span>

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="3ba4a-152">**Remarque** : Pour faciliter le débogage, utilisez la cmdlet **Write-Verbose** dans l’implémentation des trois fonctions précédentes.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="3ba4a-153">Cette applet de commande écrit du texte dans le flux de message détaillé.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="3ba4a-154">Par défaut, le flux de message détaillé n’est pas affiché, mais vous pouvez l’afficher en modifiant la valeur de la variable **$VerbosePreference** ou en utilisant le paramètre **Verbose** dans DSC cmdlets = new.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="3ba4a-155">Création du manifeste de module</span><span class="sxs-lookup"><span data-stu-id="3ba4a-155">Creating the module manifest</span></span>

<span data-ttu-id="3ba4a-156">Enfin, utilisez l’applet de commande **New-ModuleManifest** pour définir un fichier <ResourceName>.psd1 pour votre module de ressource personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="3ba4a-157">Quand vous appelez cette applet de commande, référencez le fichier de module de script (.psm1) décrit dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="3ba4a-158">Ajoutez **Get-TargetResource**, **Set-TargetResource** et **Test-TargetResource** à la liste des fonctions à exporter.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="3ba4a-159">Voici un exemple de fichier de manifeste.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-159">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="3ba4a-160">Prise en charge de PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3ba4a-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="3ba4a-161">**Remarque :** **PsDscRunAsCredential** est pris en charge dans PowerShell 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="3ba4a-162">La propriété **PsDscRunAsCredential** peut être utilisée dans le bloc de ressources [Configurations DSC](../configurations/configurations.md) pour spécifier que la ressource doit être exécutée sous un jeu d’informations d’identification spécifié.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="3ba4a-163">Pour plus d’informations, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="3ba4a-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="3ba4a-164">Pour accéder au contexte utilisateur dans une ressource personnalisée, vous pouvez utiliser la variable automatique `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="3ba4a-165">Par exemple, le code suivant écrit le contexte de l’utilisateur sous lequel la ressource s’exécute dans le flux de sortie des messages :</span><span class="sxs-lookup"><span data-stu-id="3ba4a-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="3ba4a-166">Redémarrage du nœud</span><span class="sxs-lookup"><span data-stu-id="3ba4a-166">Rebooting the Node</span></span>

<span data-ttu-id="3ba4a-167">Si les actions effectuées dans votre fonction `Set-TargetResource` nécessitent un redémarrage, vous pouvez utiliser un indicateur global pour signaler au Gestionnaire de configuration local qu’il faut redémarrer le nœud.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="3ba4a-168">Ce redémarrage se produit juste après l’exécution de la fonction `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="3ba4a-169">À l’intérieur de votre fonction `Set-TargetResource`, ajoutez la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="3ba4a-170">Pour que le Gestionnaire de configuration local redémarre le nœud, il faut que l’indicateur **RebootNodeIfNeeded** ait la valeur `$true`.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="3ba4a-171">Le paramètre **ActionAfterReboot** doit également être défini sur **ContinueConfiguration**, qui est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3ba4a-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="3ba4a-172">Pour plus d’informations sur la configuration du Gestionnaire de configuration local, consultez [Configuration du Gestionnaire de configuration local](../managing-nodes/metaConfig.md) ou [Configuration du Gestionnaire de configuration local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="3ba4a-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
