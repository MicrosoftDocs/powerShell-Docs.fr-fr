---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 5647f9bfa909cba9740e7be17f262b6be0e5c8e9
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342924"
---
# <span data-ttu-id="53e8a-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-103">New-Service</span></span>

## <span data-ttu-id="53e8a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="53e8a-104">SYNOPSIS</span></span>
<span data-ttu-id="53e8a-105">Crée un service Windows.</span><span class="sxs-lookup"><span data-stu-id="53e8a-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="53e8a-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="53e8a-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="53e8a-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="53e8a-107">DESCRIPTION</span></span>

<span data-ttu-id="53e8a-108">L' `New-Service` applet de commande crée une entrée pour un service Windows dans le registre et dans la base de données du service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="53e8a-109">Un nouveau service nécessite un fichier exécutable qui s’exécute pendant le service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="53e8a-110">Les paramètres de cette applet de commande vous permettent de définir le nom d'affichage, la description, le type de démarrage et les dépendances du service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="53e8a-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="53e8a-111">EXAMPLES</span></span>

### <span data-ttu-id="53e8a-112">Exemple 1 : créer un service</span><span class="sxs-lookup"><span data-stu-id="53e8a-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="53e8a-113">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="53e8a-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="53e8a-114">Exemple 2 : créer un service qui comprend une description, un type de démarrage et un nom d’affichage</span><span class="sxs-lookup"><span data-stu-id="53e8a-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

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

<span data-ttu-id="53e8a-115">Cette commande crée un service nommé TestService.</span><span class="sxs-lookup"><span data-stu-id="53e8a-115">This command creates a service named TestService.</span></span> <span data-ttu-id="53e8a-116">Elle utilise les paramètres de `New-Service` pour spécifier une description, un type de démarrage et un nom d’affichage pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="53e8a-117">Exemple 3 : afficher le nouveau service</span><span class="sxs-lookup"><span data-stu-id="53e8a-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="53e8a-118">Cette commande utilise `Get-CimInstance` pour obtenir l’objet **Win32_Service** pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="53e8a-119">Cet objet inclut le mode de démarrage et la description du service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="53e8a-120">Exemple 4 : supprimer un service</span><span class="sxs-lookup"><span data-stu-id="53e8a-120">Example 4: Delete a service</span></span>

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

<span data-ttu-id="53e8a-121">Cet exemple montre deux façons de supprimer le service TestService.</span><span class="sxs-lookup"><span data-stu-id="53e8a-121">This example shows two ways to delete the TestService service.</span></span> <span data-ttu-id="53e8a-122">La première commande utilise l’option DELETE de `Sc.exe` .</span><span class="sxs-lookup"><span data-stu-id="53e8a-122">The first command uses the delete option of `Sc.exe`.</span></span> <span data-ttu-id="53e8a-123">La deuxième commande utilise la méthode **Delete** des objets **Win32_Service** qui `Get-CimInstance` retourne.</span><span class="sxs-lookup"><span data-stu-id="53e8a-123">The second command uses the **Delete** method of the **Win32_Service** objects that `Get-CimInstance` returns.</span></span>

## <span data-ttu-id="53e8a-124">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="53e8a-124">PARAMETERS</span></span>

### <span data-ttu-id="53e8a-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="53e8a-125">-BinaryPathName</span></span>

<span data-ttu-id="53e8a-126">Spécifie le chemin d’accès du fichier exécutable pour le service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="53e8a-127">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="53e8a-127">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53e8a-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="53e8a-128">-Credential</span></span>

<span data-ttu-id="53e8a-129">Spécifie le compte utilisé par le service comme [compte d’ouverture de session du service](/windows/desktop/ad/about-service-logon-accounts).</span><span class="sxs-lookup"><span data-stu-id="53e8a-129">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="53e8a-130">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="53e8a-130">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="53e8a-131">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="53e8a-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="53e8a-132">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="53e8a-132">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="53e8a-133">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="53e8a-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="53e8a-134">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="53e8a-134">-DependsOn</span></span>

<span data-ttu-id="53e8a-135">Spécifie le nom des autres services dont dépend le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-135">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="53e8a-136">Lorsque vous entrez plusieurs noms de services, ajoutez une virgule entre chaque nom.</span><span class="sxs-lookup"><span data-stu-id="53e8a-136">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="53e8a-137">Description</span><span class="sxs-lookup"><span data-stu-id="53e8a-137">-Description</span></span>

<span data-ttu-id="53e8a-138">Spécifie une description du service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-138">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="53e8a-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="53e8a-139">-DisplayName</span></span>

<span data-ttu-id="53e8a-140">Spécifie le nom d'affichage du service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-140">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="53e8a-141">-Name</span><span class="sxs-lookup"><span data-stu-id="53e8a-141">-Name</span></span>

<span data-ttu-id="53e8a-142">Spécifie le nom du service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-142">Specifies the name of the service.</span></span> <span data-ttu-id="53e8a-143">Ce paramètre est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="53e8a-143">This parameter is required.</span></span>

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

### <span data-ttu-id="53e8a-144">-StartupType</span><span class="sxs-lookup"><span data-stu-id="53e8a-144">-StartupType</span></span>

<span data-ttu-id="53e8a-145">Définit le type de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-145">Sets the startup type of the service.</span></span> <span data-ttu-id="53e8a-146">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="53e8a-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="53e8a-147">**Automatique** -le service est démarré ou a été démarré par le système d’exploitation au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="53e8a-147">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="53e8a-148">Si un service démarré automatiquement dépend d'un service démarré manuellement, le service démarré manuellement est également démarré automatiquement au démarrage du système.</span><span class="sxs-lookup"><span data-stu-id="53e8a-148">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="53e8a-149">**Désactivé** : le service est désactivé et ne peut pas être démarré par un utilisateur ou une application.</span><span class="sxs-lookup"><span data-stu-id="53e8a-149">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="53e8a-150">**Manuel** : le service est démarré uniquement manuellement, par un utilisateur, à l’aide du gestionnaire de contrôle des services ou par une application.</span><span class="sxs-lookup"><span data-stu-id="53e8a-150">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="53e8a-151">**Démarrage** -indique que le service est un pilote de périphérique Démarré par le chargeur du système.</span><span class="sxs-lookup"><span data-stu-id="53e8a-151">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="53e8a-152">Cette valeur est valide uniquement pour les pilotes de périphérique.</span><span class="sxs-lookup"><span data-stu-id="53e8a-152">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="53e8a-153">**Système** : indique que le service est un pilote de périphérique Démarré par la fonction « IOInitSystem () ».</span><span class="sxs-lookup"><span data-stu-id="53e8a-153">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="53e8a-154">Cette valeur est valide uniquement pour les pilotes de périphérique.</span><span class="sxs-lookup"><span data-stu-id="53e8a-154">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="53e8a-155">La valeur par défaut est **automatique**.</span><span class="sxs-lookup"><span data-stu-id="53e8a-155">The default value is **Automatic**.</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53e8a-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="53e8a-156">-Confirm</span></span>

<span data-ttu-id="53e8a-157">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="53e8a-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="53e8a-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="53e8a-158">-WhatIf</span></span>

<span data-ttu-id="53e8a-159">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="53e8a-159">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="53e8a-160">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="53e8a-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="53e8a-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53e8a-161">CommonParameters</span></span>

<span data-ttu-id="53e8a-162">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="53e8a-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53e8a-163">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="53e8a-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53e8a-164">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="53e8a-164">INPUTS</span></span>

### <span data-ttu-id="53e8a-165">Aucun</span><span class="sxs-lookup"><span data-stu-id="53e8a-165">None</span></span>

<span data-ttu-id="53e8a-166">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="53e8a-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="53e8a-167">SORTIES</span><span class="sxs-lookup"><span data-stu-id="53e8a-167">OUTPUTS</span></span>

### <span data-ttu-id="53e8a-168">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="53e8a-168">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="53e8a-169">Cette applet de commande retourne un objet qui représente le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-169">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="53e8a-170">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="53e8a-170">NOTES</span></span>

<span data-ttu-id="53e8a-171">Pour exécuter cette applet de commande, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .</span><span class="sxs-lookup"><span data-stu-id="53e8a-171">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="53e8a-172">Pour supprimer un service, utilisez Sc.exe ou utilisez l' `Get-CimInstance` applet de commande pour obtenir l’objet **Win32_Service** qui représente le service, puis utilisez la méthode **Delete** pour supprimer le service.</span><span class="sxs-lookup"><span data-stu-id="53e8a-172">To delete a service, use Sc.exe, or use the `Get-CimInstance` cmdlet to get the **Win32_Service** object that represents the service and then use the **Delete** method to delete the service.</span></span> <span data-ttu-id="53e8a-173">L’objet qui `Get-Service` retourne n’a pas de méthode Delete.</span><span class="sxs-lookup"><span data-stu-id="53e8a-173">The object that `Get-Service` returns does not have a delete method.</span></span>

## <span data-ttu-id="53e8a-174">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="53e8a-174">RELATED LINKS</span></span>

[<span data-ttu-id="53e8a-175">Get-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-175">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="53e8a-176">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-176">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="53e8a-177">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-177">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="53e8a-178">Set-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-178">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="53e8a-179">Start-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-179">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="53e8a-180">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-180">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="53e8a-181">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="53e8a-181">Suspend-Service</span></span>](Suspend-Service.md)
