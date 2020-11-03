---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 17b28b14a9610dd48a03cc8c654806e75d3d97e3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201765"
---
# <span data-ttu-id="20fe2-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-103">New-Service</span></span>

## <span data-ttu-id="20fe2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="20fe2-104">SYNOPSIS</span></span>
<span data-ttu-id="20fe2-105">Crée un service Windows.</span><span class="sxs-lookup"><span data-stu-id="20fe2-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="20fe2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20fe2-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-SecurityDescriptorSddl <String>] [-StartupType <ServiceStartupType>] [-Credential <PSCredential>]
 [-DependsOn <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="20fe2-107">Description</span><span class="sxs-lookup"><span data-stu-id="20fe2-107">DESCRIPTION</span></span>

<span data-ttu-id="20fe2-108">L' `New-Service` applet de commande crée une entrée pour un service Windows dans le registre et dans la base de données du service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="20fe2-109">Un nouveau service nécessite un fichier exécutable qui s’exécute pendant le service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="20fe2-110">Les paramètres de cette applet de commande vous permettent de définir le nom d'affichage, la description, le type de démarrage et les dépendances du service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="20fe2-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="20fe2-111">EXAMPLES</span></span>

### <span data-ttu-id="20fe2-112">Exemple 1 : créer un service</span><span class="sxs-lookup"><span data-stu-id="20fe2-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="20fe2-113">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="20fe2-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="20fe2-114">Exemple 2 : créer un service qui comprend une description, un type de démarrage et un nom d’affichage</span><span class="sxs-lookup"><span data-stu-id="20fe2-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="20fe2-115">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="20fe2-115">This command creates a service named TestService.</span></span> <span data-ttu-id="20fe2-116">Elle utilise les paramètres de `New-Service` pour spécifier une description, un type de démarrage et un nom d’affichage pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="20fe2-117">Exemple 3 : afficher le nouveau service</span><span class="sxs-lookup"><span data-stu-id="20fe2-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="20fe2-118">Cette commande utilise `Get-CimInstance` pour obtenir l’objet **Win32_Service** pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="20fe2-119">Cet objet inclut le mode de démarrage et la description du service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="20fe2-120">Exemple 4 : définir le SecurityDescriptor d’un service lors de la création.</span><span class="sxs-lookup"><span data-stu-id="20fe2-120">Example 4: Set the SecurityDescriptor of a service when creating.</span></span>

<span data-ttu-id="20fe2-121">Cet exemple ajoute l' **SecurityDescriptor** du service en cours de création.</span><span class="sxs-lookup"><span data-stu-id="20fe2-121">This example adds the **SecurityDescriptor** of the service being created.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
$params = @{
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
  SecurityDescriptorSddl = $SDDL
}
New-Service @params
```

<span data-ttu-id="20fe2-122">Le **SecurityDescriptor** est stocké dans la `$SDDLToSet` variable.</span><span class="sxs-lookup"><span data-stu-id="20fe2-122">The **SecurityDescriptor** is stored in the `$SDDLToSet` variable.</span></span> <span data-ttu-id="20fe2-123">Le paramètre **SecurityDescriptorSddl** utilise `$SDDL` pour définir la valeur **SecurityDescriptor** du nouveau service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-123">The **SecurityDescriptorSddl** parameter uses `$SDDL` to set the **SecurityDescriptor** of the new service.</span></span>

## <span data-ttu-id="20fe2-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20fe2-124">PARAMETERS</span></span>

### <span data-ttu-id="20fe2-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="20fe2-125">-BinaryPathName</span></span>

<span data-ttu-id="20fe2-126">Spécifie le chemin d’accès du fichier exécutable pour le service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="20fe2-127">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="20fe2-127">This parameter is required.</span></span>

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

### <span data-ttu-id="20fe2-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="20fe2-128">-Credential</span></span>

<span data-ttu-id="20fe2-129">Spécifie le compte utilisé par le service comme [compte d’ouverture de session du service](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="20fe2-129">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="20fe2-130">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="20fe2-130">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="20fe2-131">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="20fe2-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="20fe2-132">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="20fe2-132">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="20fe2-133">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="20fe2-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="20fe2-134">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="20fe2-134">-DependsOn</span></span>

<span data-ttu-id="20fe2-135">Spécifie le nom des autres services dont dépend le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-135">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="20fe2-136">Lorsque vous entrez plusieurs noms de services, ajoutez une virgule entre chaque nom.</span><span class="sxs-lookup"><span data-stu-id="20fe2-136">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="20fe2-137">Description</span><span class="sxs-lookup"><span data-stu-id="20fe2-137">-Description</span></span>

<span data-ttu-id="20fe2-138">Spécifie une description du service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-138">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="20fe2-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="20fe2-139">-DisplayName</span></span>

<span data-ttu-id="20fe2-140">Spécifie le nom d'affichage du service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-140">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="20fe2-141">-Name</span><span class="sxs-lookup"><span data-stu-id="20fe2-141">-Name</span></span>

<span data-ttu-id="20fe2-142">Spécifie le nom du service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-142">Specifies the name of the service.</span></span>
<span data-ttu-id="20fe2-143">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="20fe2-143">This parameter is required.</span></span>

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

### <span data-ttu-id="20fe2-144">-StartupType</span><span class="sxs-lookup"><span data-stu-id="20fe2-144">-StartupType</span></span>

<span data-ttu-id="20fe2-145">Définit le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-145">Sets the startup type of the service.</span></span> <span data-ttu-id="20fe2-146">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="20fe2-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="20fe2-147">**Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="20fe2-147">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="20fe2-148">Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="20fe2-148">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="20fe2-149">**AutomaticDelayedStart** -démarre peu après le démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="20fe2-149">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="20fe2-150">**Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.</span><span class="sxs-lookup"><span data-stu-id="20fe2-150">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="20fe2-151">**InvalidValue** : cette valeur n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="20fe2-151">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="20fe2-152">L’utilisation de cette valeur génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="20fe2-152">Using this value results in an error.</span></span>
- <span data-ttu-id="20fe2-153">**Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.</span><span class="sxs-lookup"><span data-stu-id="20fe2-153">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="20fe2-154">La valeur par défaut est **automatique** .</span><span class="sxs-lookup"><span data-stu-id="20fe2-154">The default value is **Automatic** .</span></span>

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

### <span data-ttu-id="20fe2-155">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="20fe2-155">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="20fe2-156">Spécifie le **SecurityDescriptor** du service au format **SDDL** .</span><span class="sxs-lookup"><span data-stu-id="20fe2-156">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="20fe2-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="20fe2-157">-Confirm</span></span>

<span data-ttu-id="20fe2-158">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="20fe2-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="20fe2-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="20fe2-159">-WhatIf</span></span>

<span data-ttu-id="20fe2-160">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="20fe2-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="20fe2-161">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="20fe2-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="20fe2-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20fe2-162">CommonParameters</span></span>

<span data-ttu-id="20fe2-163">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20fe2-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20fe2-164">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="20fe2-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20fe2-165">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="20fe2-165">INPUTS</span></span>

### <span data-ttu-id="20fe2-166">Aucun</span><span class="sxs-lookup"><span data-stu-id="20fe2-166">None</span></span>

<span data-ttu-id="20fe2-167">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="20fe2-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="20fe2-168">SORTIES</span><span class="sxs-lookup"><span data-stu-id="20fe2-168">OUTPUTS</span></span>

### <span data-ttu-id="20fe2-169">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="20fe2-169">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="20fe2-170">Cette applet de commande retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="20fe2-170">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="20fe2-171">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="20fe2-171">NOTES</span></span>

<span data-ttu-id="20fe2-172">Pour exécuter cette applet de commande sur Windows Vista et les versions ultérieures du système d’exploitation Windows, démarrez PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="20fe2-172">To run this cmdlet on Windows Vista and later versions of the Windows operating system, start PowerShell by using the Run as administrator option.</span></span>

## <span data-ttu-id="20fe2-173">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="20fe2-173">RELATED LINKS</span></span>

[<span data-ttu-id="20fe2-174">Get-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-174">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="20fe2-175">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-175">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="20fe2-176">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-176">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="20fe2-177">Set-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-177">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="20fe2-178">Start-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-178">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="20fe2-179">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-179">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="20fe2-180">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-180">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="20fe2-181">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="20fe2-181">Remove-Service</span></span>](Remove-Service.md)
