---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 7ba9bf66295bcbc2d8f7b7f94007b3fb673882fb
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890972"
---
# <span data-ttu-id="241f7-102">New-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-102">New-Service</span></span>

## <span data-ttu-id="241f7-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="241f7-103">SYNOPSIS</span></span>
<span data-ttu-id="241f7-104">Crée un service Windows.</span><span class="sxs-lookup"><span data-stu-id="241f7-104">Creates a new Windows service.</span></span>

## <span data-ttu-id="241f7-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="241f7-105">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="241f7-106">Description</span><span class="sxs-lookup"><span data-stu-id="241f7-106">DESCRIPTION</span></span>

<span data-ttu-id="241f7-107">L' `New-Service` applet de commande crée une entrée pour un service Windows dans le registre et dans la base de données du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-107">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="241f7-108">Un nouveau service nécessite un fichier exécutable qui s’exécute pendant le service.</span><span class="sxs-lookup"><span data-stu-id="241f7-108">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="241f7-109">Les paramètres de cette applet de commande vous permettent de définir le nom d'affichage, la description, le type de démarrage et les dépendances du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-109">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="241f7-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="241f7-110">EXAMPLES</span></span>

### <span data-ttu-id="241f7-111">Exemple 1 : créer un service</span><span class="sxs-lookup"><span data-stu-id="241f7-111">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="241f7-112">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="241f7-112">This command creates a service named TestService.</span></span>

### <span data-ttu-id="241f7-113">Exemple 2 : créer un service qui comprend une description, un type de démarrage et un nom d’affichage</span><span class="sxs-lookup"><span data-stu-id="241f7-113">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="241f7-114">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="241f7-114">This command creates a service named TestService.</span></span> <span data-ttu-id="241f7-115">Elle utilise les paramètres de `New-Service` pour spécifier une description, un type de démarrage et un nom d’affichage pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="241f7-115">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="241f7-116">Exemple 3 : afficher le nouveau service</span><span class="sxs-lookup"><span data-stu-id="241f7-116">Example 3: View the new service</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

<span data-ttu-id="241f7-117">Cette commande utilise `Get-CimInstance` pour obtenir l’objet **Win32_Service** pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="241f7-117">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="241f7-118">Cet objet inclut le mode de démarrage et la description du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-118">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="241f7-119">Exemple 4 : définir le SecurityDescriptor d’un service lors de la création.</span><span class="sxs-lookup"><span data-stu-id="241f7-119">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="241f7-120">Cet exemple ajoute l' **SecurityDescriptor** du service en cours de création.</span><span class="sxs-lookup"><span data-stu-id="241f7-120">This example adds the **SecurityDescriptor** of the service being created.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

<span data-ttu-id="241f7-121">Le **SecurityDescriptor** est stocké dans la `$SDDLToSet` variable.</span><span class="sxs-lookup"><span data-stu-id="241f7-121">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="241f7-122">Le paramètre **SecurityDescriptorSddl** utilise `$SDDL` pour définir la valeur **SecurityDescriptor** du nouveau service.</span><span class="sxs-lookup"><span data-stu-id="241f7-122">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="241f7-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="241f7-123">PARAMETERS</span></span>

### <span data-ttu-id="241f7-124">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="241f7-124">-BinaryPathName</span></span>

<span data-ttu-id="241f7-125">Spécifie le chemin d’accès du fichier exécutable pour le service.</span><span class="sxs-lookup"><span data-stu-id="241f7-125">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="241f7-126">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="241f7-126">This parameter is required.</span></span>

<span data-ttu-id="241f7-127">Chemin d’accès complet au fichier binaire du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-127">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="241f7-128">Si le chemin d’accès contient un espace, il doit être placé entre guillemets pour qu’il soit correctement interprété.</span><span class="sxs-lookup"><span data-stu-id="241f7-128">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="241f7-129">Par exemple, `d:\my share\myservice.exe` doit être spécifié comme `'"d:\my share\myservice.exe"'` .</span><span class="sxs-lookup"><span data-stu-id="241f7-129">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="241f7-130">Le chemin d’accès peut également inclure des arguments pour un service à démarrage automatique.</span><span class="sxs-lookup"><span data-stu-id="241f7-130">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="241f7-131">Par exemple, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span><span class="sxs-lookup"><span data-stu-id="241f7-131">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="241f7-132">Ces arguments sont passés au point d’entrée du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-132">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="241f7-133">Pour plus d’informations, consultez le paramètre **lpBinaryPathName** de l’API [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) .</span><span class="sxs-lookup"><span data-stu-id="241f7-133">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="241f7-134">-Credential</span></span>

<span data-ttu-id="241f7-135">Spécifie le compte utilisé par le service comme [compte d’ouverture de session du service](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="241f7-135">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="241f7-136">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="241f7-136">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="241f7-137">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="241f7-137">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="241f7-138">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="241f7-138">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="241f7-139">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="241f7-139">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-140">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="241f7-140">-DependsOn</span></span>

<span data-ttu-id="241f7-141">Spécifie le nom des autres services dont dépend le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="241f7-141">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="241f7-142">Lorsque vous entrez plusieurs noms de services, ajoutez une virgule entre chaque nom.</span><span class="sxs-lookup"><span data-stu-id="241f7-142">To enter multiple service names, use a comma to separate the names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-143">Description</span><span class="sxs-lookup"><span data-stu-id="241f7-143">-Description</span></span>

<span data-ttu-id="241f7-144">Spécifie une description du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-144">Specifies a description of the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-145">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="241f7-145">-DisplayName</span></span>

<span data-ttu-id="241f7-146">Spécifie le nom d'affichage du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-146">Specifies a display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-147">-Name</span><span class="sxs-lookup"><span data-stu-id="241f7-147">-Name</span></span>

<span data-ttu-id="241f7-148">Spécifie le nom du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-148">Specifies the name of the service.</span></span> <span data-ttu-id="241f7-149">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="241f7-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-150">-StartupType</span><span class="sxs-lookup"><span data-stu-id="241f7-150">-StartupType</span></span>

<span data-ttu-id="241f7-151">Définit le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="241f7-151">Sets the startup type of the service.</span></span> <span data-ttu-id="241f7-152">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="241f7-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="241f7-153">**Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="241f7-153">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="241f7-154">Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="241f7-154">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="241f7-155">**AutomaticDelayedStart** -démarre peu après le démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="241f7-155">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="241f7-156">**Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.</span><span class="sxs-lookup"><span data-stu-id="241f7-156">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="241f7-157">**InvalidValue** : cette valeur n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="241f7-157">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="241f7-158">L’utilisation de cette valeur génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="241f7-158">Using this value results in an error.</span></span>
- <span data-ttu-id="241f7-159">**Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.</span><span class="sxs-lookup"><span data-stu-id="241f7-159">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="241f7-160">La valeur par défaut est **automatique**.</span><span class="sxs-lookup"><span data-stu-id="241f7-160">The default value is **Automatic**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-161">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="241f7-161">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="241f7-162">Spécifie le **SecurityDescriptor** du service au format **SDDL** .</span><span class="sxs-lookup"><span data-stu-id="241f7-162">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f7-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="241f7-163">-Confirm</span></span>

<span data-ttu-id="241f7-164">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="241f7-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="241f7-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="241f7-165">-WhatIf</span></span>

<span data-ttu-id="241f7-166">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="241f7-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="241f7-167">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="241f7-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="241f7-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="241f7-168">CommonParameters</span></span>

<span data-ttu-id="241f7-169">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="241f7-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="241f7-170">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="241f7-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="241f7-171">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="241f7-171">INPUTS</span></span>

### <span data-ttu-id="241f7-172">None</span><span class="sxs-lookup"><span data-stu-id="241f7-172">None</span></span>

<span data-ttu-id="241f7-173">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="241f7-173">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="241f7-174">SORTIES</span><span class="sxs-lookup"><span data-stu-id="241f7-174">OUTPUTS</span></span>

### <span data-ttu-id="241f7-175">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="241f7-175">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="241f7-176">Cette applet de commande retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="241f7-176">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="241f7-177">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="241f7-177">NOTES</span></span>

<span data-ttu-id="241f7-178">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="241f7-178">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="241f7-179">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="241f7-179">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="241f7-180">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="241f7-180">RELATED LINKS</span></span>

[<span data-ttu-id="241f7-181">Get-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-181">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="241f7-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="241f7-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="241f7-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="241f7-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="241f7-186">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-186">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="241f7-187">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-187">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="241f7-188">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="241f7-188">Remove-Service</span></span>](Remove-Service.md)
