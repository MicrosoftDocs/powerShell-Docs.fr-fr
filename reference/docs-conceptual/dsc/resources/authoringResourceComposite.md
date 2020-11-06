---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,installation
title: Ressources composites - utilisation d’une configuration DSC comme ressource
description: Cet article décrit comment créer et utiliser une ressource composite.
ms.openlocfilehash: c1f0e3b45c3a393c04700b5a4bc88be365794820
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667298"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="16e58-104">Ressources composites : utilisation d’une configuration DSC comme ressource</span><span class="sxs-lookup"><span data-stu-id="16e58-104">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="16e58-105">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="16e58-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="16e58-106">Les configurations peuvent parfois s’avérer longues et complexes, faire appel à de nombreuses ressources différentes et définir un grand nombre de propriétés.</span><span class="sxs-lookup"><span data-stu-id="16e58-106">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="16e58-107">Pour vous faciliter la vie, vous pouvez utiliser une configuration DSC Windows PowerShell comme ressource pour d’autres configurations.</span><span class="sxs-lookup"><span data-stu-id="16e58-107">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="16e58-108">Nous l’appelons ressource composite.</span><span class="sxs-lookup"><span data-stu-id="16e58-108">This is called a composite resource.</span></span> <span data-ttu-id="16e58-109">Une ressource composite est une configuration DSC qui accepte des paramètres.</span><span class="sxs-lookup"><span data-stu-id="16e58-109">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="16e58-110">Les paramètres de la configuration font office de propriétés de la ressource.</span><span class="sxs-lookup"><span data-stu-id="16e58-110">The parameters of the configuration act as the properties of the resource.</span></span>
<span data-ttu-id="16e58-111">La configuration est enregistrée en tant que fichier avec une extension de `.schema.psm1`.</span><span class="sxs-lookup"><span data-stu-id="16e58-111">The configuration is saved as a file with a `.schema.psm1` extension.</span></span> <span data-ttu-id="16e58-112">Elle remplace à la fois le schéma MOF et le script de ressource dans une ressource DSC classique.</span><span class="sxs-lookup"><span data-stu-id="16e58-112">It takes the place of both the MOF schema, and the resource script in a typical DSC resource.</span></span> <span data-ttu-id="16e58-113">Pour plus d’informations sur les ressources DSC, consultez [Ressources Desired State Configuration Windows PowerShell](resources.md).</span><span class="sxs-lookup"><span data-stu-id="16e58-113">For more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="16e58-114">Création de la ressource composite</span><span class="sxs-lookup"><span data-stu-id="16e58-114">Creating the composite resource</span></span>

<span data-ttu-id="16e58-115">Dans notre exemple, nous créons une configuration qui appelle plusieurs ressources existantes pour configurer des machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="16e58-115">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="16e58-116">Au lieu de spécifier les valeurs à définir dans des blocs de configuration, la configuration choisit plusieurs paramètres qui sont ensuite utilisés dans les blocs de configuration.</span><span class="sxs-lookup"><span data-stu-id="16e58-116">Instead of specifying the values to be set in configuration blocks, the configuration takes in parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="16e58-117">DSC ne prend pas actuellement en charge le placement de ressources composites ou de configurations imbriquées dans une ressource composite.</span><span class="sxs-lookup"><span data-stu-id="16e58-117">DSC doesn't currently support placing composite resources or nested configurations within a composite resource.</span></span>

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="16e58-118">Enregistrement de la configuration comme ressource composite</span><span class="sxs-lookup"><span data-stu-id="16e58-118">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="16e58-119">Pour utiliser la configuration paramétrable comme ressource DSC, enregistrez-la dans une structure de répertoires similaire à celle d’une ressource MOF, puis attribuez-lui un nom et une extension `.schema.psm1`.</span><span class="sxs-lookup"><span data-stu-id="16e58-119">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a `.schema.psm1` extension.</span></span> <span data-ttu-id="16e58-120">Dans cet exemple, nous nommons ce fichier `xVirtualMachine.schema.psm1`.</span><span class="sxs-lookup"><span data-stu-id="16e58-120">For this example, we'll name the file `xVirtualMachine.schema.psm1`.</span></span> <span data-ttu-id="16e58-121">Vous devez également créer un manifeste nommé `xVirtualMachine.psd1` contenant la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="16e58-121">You also need to create a manifest named `xVirtualMachine.psd1` that contains the following line.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> <span data-ttu-id="16e58-122">Cela s’ajoute à `MyDscResources.psd1`, le manifeste de module pour toutes les ressources dans le dossier `MyDscResources`.</span><span class="sxs-lookup"><span data-stu-id="16e58-122">This is in addition to `MyDscResources.psd1`, the module manifest for all resources under the `MyDscResources` folder.</span></span>

<span data-ttu-id="16e58-123">Quand vous avez terminé, la structure de dossiers doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="16e58-123">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="16e58-124">La ressource est désormais détectable à l’aide de la cmdlet `Get-DscResource`. Ses propriétés sont détectables par cette cmdlet ou par l’utilisation de l’autocomplétion <kbd>Ctrl</kbd>+<kbd>Espace</kbd> dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="16e58-124">The resource is now discoverable by using the `Get-DscResource` cmdlet, and its properties are discoverable by either that cmdlet or by using <kbd>Ctrl</kbd>+<kbd>Space</kbd> autocomplete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="16e58-125">Utilisation de la ressource composite</span><span class="sxs-lookup"><span data-stu-id="16e58-125">Using the composite resource</span></span>

<span data-ttu-id="16e58-126">Vous créez ensuite une configuration qui appelle la ressource composite.</span><span class="sxs-lookup"><span data-stu-id="16e58-126">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="16e58-127">Cette configuration appelle la ressource composite xVirtualMachine pour créer une machine virtuelle, puis appelle la ressource **xComputer** pour la renommer.</span><span class="sxs-lookup"><span data-stu-id="16e58-127">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell
configuration RenameVM
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

<span data-ttu-id="16e58-128">Vous pouvez également utiliser cette ressource pour créer plusieurs machines virtuelles en transmettant un tableau de noms de machines virtuelles à la ressource xVirtualMachine.</span><span class="sxs-lookup"><span data-stu-id="16e58-128">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="16e58-129">Prise en charge de PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="16e58-129">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="16e58-130">**PsDscRunAsCredential** est pris en charge dans PowerShell 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="16e58-130">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="16e58-131">La propriété **PsDscRunAsCredential** peut être utilisée dans le bloc de ressources [Configurations DSC](../configurations/configurations.md) pour spécifier que la ressource doit être exécutée sous un jeu d’informations d’identification spécifié.</span><span class="sxs-lookup"><span data-stu-id="16e58-131">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="16e58-132">Pour plus d’informations, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="16e58-132">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="16e58-133">Pour accéder au contexte utilisateur dans une ressource personnalisée, vous pouvez utiliser la variable automatique `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="16e58-133">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="16e58-134">Par exemple, le code suivant écrit le contexte de l’utilisateur sous lequel la ressource s’exécute dans le flux de sortie des messages :</span><span class="sxs-lookup"><span data-stu-id="16e58-134">For example, the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="16e58-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16e58-135">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="16e58-136">Concepts</span><span class="sxs-lookup"><span data-stu-id="16e58-136">Concepts</span></span>

- [<span data-ttu-id="16e58-137">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="16e58-137">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="16e58-138">Prendre en main la fonctionnalité DSC (Desired State Configuration) Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="16e58-138">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
