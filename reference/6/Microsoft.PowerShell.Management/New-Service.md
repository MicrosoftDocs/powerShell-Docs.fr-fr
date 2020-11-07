---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: aadb0d53ad180ba1e88d31e5d008c6090ae0c9b3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345219"
---
# <span data-ttu-id="d564f-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-103">New-Service</span></span>

## <span data-ttu-id="d564f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="d564f-104">SYNOPSIS</span></span>
<span data-ttu-id="d564f-105">Crée un service Windows.</span><span class="sxs-lookup"><span data-stu-id="d564f-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="d564f-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="d564f-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartupType>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d564f-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d564f-107">DESCRIPTION</span></span>

<span data-ttu-id="d564f-108">L' `New-Service` applet de commande crée une entrée pour un service Windows dans le registre et dans la base de données du service.</span><span class="sxs-lookup"><span data-stu-id="d564f-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="d564f-109">Un nouveau service nécessite un fichier exécutable qui s’exécute pendant le service.</span><span class="sxs-lookup"><span data-stu-id="d564f-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="d564f-110">Les paramètres de cette applet de commande vous permettent de définir le nom d'affichage, la description, le type de démarrage et les dépendances du service.</span><span class="sxs-lookup"><span data-stu-id="d564f-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="d564f-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="d564f-111">EXAMPLES</span></span>

### <span data-ttu-id="d564f-112">Exemple 1 : créer un service</span><span class="sxs-lookup"><span data-stu-id="d564f-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="d564f-113">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="d564f-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="d564f-114">Exemple 2 : créer un service qui comprend une description, un type de démarrage et un nom d’affichage</span><span class="sxs-lookup"><span data-stu-id="d564f-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

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

<span data-ttu-id="d564f-115">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="d564f-115">This command creates a service named TestService.</span></span> <span data-ttu-id="d564f-116">Elle utilise les paramètres de `New-Service` pour spécifier une description, un type de démarrage et un nom d’affichage pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="d564f-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="d564f-117">Exemple 3 : afficher le nouveau service</span><span class="sxs-lookup"><span data-stu-id="d564f-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="d564f-118">Cette commande utilise `Get-CimInstance` pour obtenir l’objet **Win32_Service** pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="d564f-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="d564f-119">Cet objet inclut le mode de démarrage et la description du service.</span><span class="sxs-lookup"><span data-stu-id="d564f-119">This object includes the start mode and the service description.</span></span>

## <span data-ttu-id="d564f-120">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="d564f-120">PARAMETERS</span></span>

### <span data-ttu-id="d564f-121">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="d564f-121">-BinaryPathName</span></span>

<span data-ttu-id="d564f-122">Spécifie le chemin d’accès du fichier exécutable pour le service.</span><span class="sxs-lookup"><span data-stu-id="d564f-122">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="d564f-123">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d564f-123">This parameter is required.</span></span>

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

### <span data-ttu-id="d564f-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="d564f-124">-Credential</span></span>

<span data-ttu-id="d564f-125">Spécifie le compte utilisé par le service comme [compte d’ouverture de session du service](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="d564f-125">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="d564f-126">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="d564f-126">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="d564f-127">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="d564f-127">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="d564f-128">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="d564f-128">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="d564f-129">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="d564f-129">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="d564f-130">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="d564f-130">-DependsOn</span></span>

<span data-ttu-id="d564f-131">Spécifie le nom des autres services dont dépend le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="d564f-131">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="d564f-132">Lorsque vous entrez plusieurs noms de services, ajoutez une virgule entre chaque nom.</span><span class="sxs-lookup"><span data-stu-id="d564f-132">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="d564f-133">Description</span><span class="sxs-lookup"><span data-stu-id="d564f-133">-Description</span></span>

<span data-ttu-id="d564f-134">Spécifie une description du service.</span><span class="sxs-lookup"><span data-stu-id="d564f-134">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="d564f-135">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="d564f-135">-DisplayName</span></span>

<span data-ttu-id="d564f-136">Spécifie le nom d'affichage du service.</span><span class="sxs-lookup"><span data-stu-id="d564f-136">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="d564f-137">-Name</span><span class="sxs-lookup"><span data-stu-id="d564f-137">-Name</span></span>

<span data-ttu-id="d564f-138">Spécifie le nom du service.</span><span class="sxs-lookup"><span data-stu-id="d564f-138">Specifies the name of the service.</span></span> <span data-ttu-id="d564f-139">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d564f-139">This parameter is required.</span></span>

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

### <span data-ttu-id="d564f-140">-StartupType</span><span class="sxs-lookup"><span data-stu-id="d564f-140">-StartupType</span></span>

<span data-ttu-id="d564f-141">Définit le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="d564f-141">Sets the startup type of the service.</span></span> <span data-ttu-id="d564f-142">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="d564f-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d564f-143">**Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="d564f-143">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="d564f-144">Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="d564f-144">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="d564f-145">**AutomaticDelayedStart** -démarre peu après le démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="d564f-145">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="d564f-146">**Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.</span><span class="sxs-lookup"><span data-stu-id="d564f-146">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="d564f-147">**InvalidValue** : cette valeur n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="d564f-147">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="d564f-148">L’utilisation de cette valeur génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="d564f-148">Using this value results in an error.</span></span>
- <span data-ttu-id="d564f-149">**Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.</span><span class="sxs-lookup"><span data-stu-id="d564f-149">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="d564f-150">La valeur par défaut est **automatique**.</span><span class="sxs-lookup"><span data-stu-id="d564f-150">The default value is **Automatic**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d564f-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d564f-151">-Confirm</span></span>

<span data-ttu-id="d564f-152">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d564f-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d564f-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d564f-153">-WhatIf</span></span>

<span data-ttu-id="d564f-154">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d564f-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d564f-155">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="d564f-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d564f-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d564f-156">CommonParameters</span></span>

<span data-ttu-id="d564f-157">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d564f-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d564f-158">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d564f-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d564f-159">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="d564f-159">INPUTS</span></span>

### <span data-ttu-id="d564f-160">Aucun</span><span class="sxs-lookup"><span data-stu-id="d564f-160">None</span></span>

<span data-ttu-id="d564f-161">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="d564f-161">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d564f-162">SORTIES</span><span class="sxs-lookup"><span data-stu-id="d564f-162">OUTPUTS</span></span>

### <span data-ttu-id="d564f-163">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="d564f-163">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="d564f-164">Cette applet de commande retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="d564f-164">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="d564f-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="d564f-165">NOTES</span></span>

<span data-ttu-id="d564f-166">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="d564f-166">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="d564f-167">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="d564f-167">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="d564f-168">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="d564f-168">RELATED LINKS</span></span>

[<span data-ttu-id="d564f-169">Get-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-169">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="d564f-170">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-170">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="d564f-171">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-171">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="d564f-172">Set-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-172">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="d564f-173">Start-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-173">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="d564f-174">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-174">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="d564f-175">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-175">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="d564f-176">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="d564f-176">Remove-Service</span></span>](Remove-Service.md)
