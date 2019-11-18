---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 'Ressources composites : utilisation d’une configuration DSC comme ressource'
ms.openlocfilehash: 7fa6ee56d4706b96fb47123c7aa00c4df6256492
ms.sourcegitcommit: 14b50e5446f69729f72231f5dc6f536cdd1084c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73933825"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="7ae5a-103">Ressources composites : utilisation d’une configuration DSC comme ressource</span><span class="sxs-lookup"><span data-stu-id="7ae5a-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="7ae5a-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7ae5a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7ae5a-105">Les configurations peuvent parfois s’avérer longues et complexes, faire appel à de nombreuses ressources différentes et définir un grand nombre de propriétés.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="7ae5a-106">Pour vous faciliter la vie, vous pouvez utiliser une configuration DSC Windows PowerShell comme ressource pour d’autres configurations.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="7ae5a-107">Nous l’appelons « ressource composite ».</span><span class="sxs-lookup"><span data-stu-id="7ae5a-107">We call this a composite resource.</span></span> <span data-ttu-id="7ae5a-108">Une ressource composite est une configuration DSC qui accepte des paramètres.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="7ae5a-109">Les paramètres de la configuration font office de propriétés de la ressource.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="7ae5a-110">La configuration est enregistrée dans un fichier avec une extension **.schema.psm1**. Elle remplace à la fois le schéma MOF et le script de ressource dans une ressource DSC classique. Pour plus d’informations sur les ressources DSC, consultez [DSC Resources](resources.md).</span><span class="sxs-lookup"><span data-stu-id="7ae5a-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="7ae5a-111">Création de la ressource composite</span><span class="sxs-lookup"><span data-stu-id="7ae5a-111">Creating the composite resource</span></span>

<span data-ttu-id="7ae5a-112">Dans notre exemple, nous créons une configuration qui appelle plusieurs ressources existantes pour configurer des machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="7ae5a-113">Au lieu de spécifier les valeurs à définir dans des blocs de configuration, la configuration choisit plusieurs paramètres qui sont ensuite utilisés dans les blocs de configuration.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="7ae5a-114">Enregistrement de la configuration comme ressource composite</span><span class="sxs-lookup"><span data-stu-id="7ae5a-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="7ae5a-115">Pour utiliser la configuration paramétrable comme ressource DSC, enregistrez-la dans une structure de répertoires similaire à celle d’une ressource MOF, puis attribuez-lui un nom et une extension **.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="7ae5a-116">Pour cet exemple, nous allons nommer le fichier **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-116">For this example, we'll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="7ae5a-117">Vous devez également créer un manifeste nommé **xVirtualMachine.psd1** contenant la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="7ae5a-118">Notez que cela vient s’ajouter à **MyDscResources.psd1**, manifeste de module de toutes les ressources situé dans le dossier **MyDscResources**.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="7ae5a-119">Quand vous avez terminé, la structure de dossiers doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="7ae5a-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="7ae5a-120">La ressource est désormais détectable à l’aide de l’applet de commande Get-DscResource. Ses propriétés sont détectables par cette applet de commande ou par la saisie semi-automatique **Ctrl+Espace** dans Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="7ae5a-121">Utilisation de la ressource composite</span><span class="sxs-lookup"><span data-stu-id="7ae5a-121">Using the composite resource</span></span>

<span data-ttu-id="7ae5a-122">Vous créez ensuite une configuration qui appelle la ressource composite.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="7ae5a-123">Cette configuration appelle la ressource composite xVirtualMachine pour créer une machine virtuelle, puis appelle la ressource **xComputer** pour la renommer.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

<span data-ttu-id="7ae5a-124">Vous pouvez également utiliser cette ressource pour créer plusieurs machines virtuelles en transmettant un tableau de noms de machines virtuelles à la ressource xVirtualMachine.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-124">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="7ae5a-125">Prise en charge de PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7ae5a-125">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="7ae5a-126">**PsDscRunAsCredential** est pris en charge dans PowerShell 5.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-126">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="7ae5a-127">La propriété **PsDscRunAsCredential** peut être utilisée dans le bloc de ressources [Configurations DSC](../configurations/configurations.md) pour spécifier que la ressource doit être exécutée sous un jeu d’informations d’identification spécifié.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-127">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="7ae5a-128">Pour plus d’informations, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="7ae5a-128">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="7ae5a-129">Pour accéder au contexte utilisateur dans une ressource personnalisée, vous pouvez utiliser la variable automatique `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="7ae5a-129">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="7ae5a-130">Par exemple, le code suivant écrit le contexte de l’utilisateur sous lequel la ressource s’exécute dans le flux de sortie des messages :</span><span class="sxs-lookup"><span data-stu-id="7ae5a-130">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="7ae5a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ae5a-131">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="7ae5a-132">Concepts</span><span class="sxs-lookup"><span data-stu-id="7ae5a-132">Concepts</span></span>
* [<span data-ttu-id="7ae5a-133">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="7ae5a-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="7ae5a-134">Get Started with Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="7ae5a-134">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
