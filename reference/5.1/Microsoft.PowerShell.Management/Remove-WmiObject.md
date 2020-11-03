---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203558"
---
# <span data-ttu-id="ad4b0-103">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="ad4b0-103">Remove-WmiObject</span></span>

## <span data-ttu-id="ad4b0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ad4b0-104">SYNOPSIS</span></span>
<span data-ttu-id="ad4b0-105">Supprime une instance d'une classe Windows Management Instrumentation (WMI) existante.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-105">Deletes an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="ad4b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ad4b0-106">SYNTAX</span></span>

### <span data-ttu-id="ad4b0-107">classe (par défaut)</span><span class="sxs-lookup"><span data-stu-id="ad4b0-107">class (Default)</span></span>

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad4b0-108">object</span><span class="sxs-lookup"><span data-stu-id="ad4b0-108">object</span></span>

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ad4b0-109">path</span><span class="sxs-lookup"><span data-stu-id="ad4b0-109">path</span></span>

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ad4b0-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="ad4b0-110">WQLQuery</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ad4b0-111">query</span><span class="sxs-lookup"><span data-stu-id="ad4b0-111">query</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ad4b0-112">list</span><span class="sxs-lookup"><span data-stu-id="ad4b0-112">list</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="ad4b0-113">Description</span><span class="sxs-lookup"><span data-stu-id="ad4b0-113">DESCRIPTION</span></span>
<span data-ttu-id="ad4b0-114">L’applet de commande **Remove-WmiObject** supprime une instance d’une classe Windows Management Instrumentation (WMI) existante.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-114">The **Remove-WmiObject** cmdlet deletes an instance of an existing Windows Management Instrumentation (WMI)class.</span></span>

## <span data-ttu-id="ad4b0-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ad4b0-115">EXAMPLES</span></span>

### <span data-ttu-id="ad4b0-116">Exemple 1 : fermer toutes les instances d’un processus Win32</span><span class="sxs-lookup"><span data-stu-id="ad4b0-116">Example 1: Close all instances of a Win32 process</span></span>

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

<span data-ttu-id="ad4b0-117">Cet exemple ferme toutes les instances de Notepad.exe.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-117">This example closes all the instances of Notepad.exe.</span></span>

<span data-ttu-id="ad4b0-118">La première commande démarre une instance de Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-118">The first command starts an instance of Notepad.</span></span>

<span data-ttu-id="ad4b0-119">La deuxième commande utilise l’applet de commande Get-WmiObject pour récupérer les instances du Win32_Process qui correspondent à Notepad.exe, puis les stocke dans la variable $np.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-119">The second command uses the Get-WmiObject cmdlet to retrieve the instances of the Win32_Process that correspond to Notepad.exe, and then stores them in the $np variable.</span></span>

<span data-ttu-id="ad4b0-120">La troisième commande passe l’objet dans la variable $np à **Remove-WmiObject** , qui supprime toutes les instances de Notepad.exe.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-120">The third command passes the object in the $np variable to **Remove-WmiObject** , which deletes all the instances of Notepad.exe.</span></span>

### <span data-ttu-id="ad4b0-121">Exemple 2 : supprimer un dossier</span><span class="sxs-lookup"><span data-stu-id="ad4b0-121">Example 2: Delete a folder</span></span>

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

<span data-ttu-id="ad4b0-122">Cette commande supprime le dossier C:\Test.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-122">This command deletes the C:\Test folder.</span></span>

<span data-ttu-id="ad4b0-123">La première commande utilise l’option **« obtenir-WmiObject »** pour interroger le dossier C:\test, puis stocke l’objet dans la variable $a.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-123">The first command uses **Get-WMIObject** to query for the C:\Test folder, and then stores the object in the $a variable.</span></span>

<span data-ttu-id="ad4b0-124">La deuxième commande dirige la variable $a vers **Remove-WmiObject** , qui supprime le dossier.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-124">The second command pipes the $a variable to **Remove-WMIObject** , which deletes the folder.</span></span>

## <span data-ttu-id="ad4b0-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad4b0-125">PARAMETERS</span></span>

### <span data-ttu-id="ad4b0-126">-AsJob</span><span class="sxs-lookup"><span data-stu-id="ad4b0-126">-AsJob</span></span>
<span data-ttu-id="ad4b0-127">Indique que cette applet de commande s’exécute en tant que tâche en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-127">Indicates that this cmdlet run as a background job.</span></span>
<span data-ttu-id="ad4b0-128">Utilisez ce paramètre pour exécuter des commandes dont l'exécution nécessite beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-128">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="ad4b0-129">De nouvelles applets de commande CIM, introduites dans Windows PowerShell 3.0, effectuent les mêmes tâches que les applets de commande WMI.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-129">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="ad4b0-130">Les applets de commande CIM sont conformes aux normes WS-Management (WSMan) et à la norme Common Information Model (CIM), ce qui permet aux cmdlets d’utiliser les mêmes techniques pour gérer les ordinateurs qui exécutent le système d’exploitation Windows et ceux qui exécutent d’autres systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-130">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those running other operating systems.</span></span>
<span data-ttu-id="ad4b0-131">Au lieu d'utiliser **Remove-WmiObject** , songez à utiliser l'applet de commande Remove-CimInstancehttps://go.microsoft.com/fwlink/?LinkId=227964.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-131">Instead of using **Remove-WmiObject** , consider using the Remove-CimInstancehttps://go.microsoft.com/fwlink/?LinkId=227964 cmdlet.</span></span>

<span data-ttu-id="ad4b0-132">Quand vous utilisez le paramètre *AsJob* , la commande retourne un objet qui représente la tâche en arrière-plan, puis affiche l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-132">When you use the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="ad4b0-133">Vous pouvez continuer à travailler dans la session pendant l'exécution de la tâche.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-133">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="ad4b0-134">Si vous utilisez **Remove-WmiObject** sur un ordinateur distant, la tâche est créée sur l'ordinateur local, et les résultats provenant d'ordinateurs distants sont automatiquement retournés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-134">If **Remove-WmiObject** is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="ad4b0-135">Pour gérer le travail, utilisez les applets de commande qui contiennent le nom du **travail** (les applets de commande **Job** ).</span><span class="sxs-lookup"><span data-stu-id="ad4b0-135">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="ad4b0-136">Pour obtenir les résultats de la tâche, utilisez l'applet de commande Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-136">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="ad4b0-137">Pour utiliser ce paramètre pour les ordinateurs distants, les ordinateurs locaux et distants doivent être configurés pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-137">To use this parameter for remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="ad4b0-138">Démarrez Windows PowerShell à l’aide de l’option Exécuter en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-138">Start Windows PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="ad4b0-139">Pour plus d'informations, consultez about_Remote_Requirements.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-139">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="ad4b0-140">Pour plus d’informations sur les tâches en arrière-plan Windows PowerShell, consultez about_Jobs et about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-140">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="ad4b0-141">-Authentification</span><span class="sxs-lookup"><span data-stu-id="ad4b0-141">-Authentication</span></span>
<span data-ttu-id="ad4b0-142">Spécifie le niveau d’authentification à utiliser pour la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-142">Specifies the authentication level to use for the WMI connection.</span></span>
<span data-ttu-id="ad4b0-143">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="ad4b0-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ad4b0-144">-1 : inchangé.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-144">-1: Unchanged.</span></span>
- <span data-ttu-id="ad4b0-145">0 : Default.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-145">0: Default.</span></span>
- <span data-ttu-id="ad4b0-146">1 : aucune.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-146">1: None.</span></span>
<span data-ttu-id="ad4b0-147">Aucune authentification n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-147">No authentication in performed.</span></span>
- <span data-ttu-id="ad4b0-148">2 : se connecter.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-148">2: Connect.</span></span>
<span data-ttu-id="ad4b0-149">L’authentification est effectuée uniquement lorsque le client établit une relation avec l’application.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-149">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="ad4b0-150">3 : appeler.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-150">3: Call.</span></span>
<span data-ttu-id="ad4b0-151">L’authentification est effectuée uniquement au début de chaque appel lorsque l’application reçoit la demande.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-151">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="ad4b0-152">4 : paquet.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-152">4: Packet.</span></span>
<span data-ttu-id="ad4b0-153">L’authentification est effectuée sur toutes les données reçues du client.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-153">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="ad4b0-154">5 : PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-154">5: PacketIntegrity.</span></span>
<span data-ttu-id="ad4b0-155">Toutes les données transférées entre le client et l’application sont authentifiées et vérifiées.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-155">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="ad4b0-156">6 : PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-156">6: PacketPrivacy.</span></span>
<span data-ttu-id="ad4b0-157">Les propriétés des autres niveaux d’authentification sont utilisées, et toutes les données sont chiffrées.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-157">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-158">-Autorité</span><span class="sxs-lookup"><span data-stu-id="ad4b0-158">-Authority</span></span>
<span data-ttu-id="ad4b0-159">Spécifie l'autorité à utiliser pour authentifier la connexion WMI.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-159">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="ad4b0-160">Vous pouvez spécifier l'authentification Kerberos ou NTLM standard.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-160">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="ad4b0-161">Pour utiliser NTLM, affectez au paramètre d'autorité la valeur ntlmdomain:\<DomainName\>, où \<DomainName\> identifie un nom de domaine NTLM valide.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-161">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="ad4b0-162">Pour utiliser Kerberos, spécifiez Kerberos : \<DomainName\> \\ \<ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="ad4b0-162">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="ad4b0-163">Vous ne pouvez pas inclure le paramètre d'autorité lorsque vous vous connectez à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-163">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-164">-Classe</span><span class="sxs-lookup"><span data-stu-id="ad4b0-164">-Class</span></span>
<span data-ttu-id="ad4b0-165">Spécifie le nom d’une classe WMI que cette applet de commande supprime.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-165">Specifies the name of a WMI class that this cmdlet deletes.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-166">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ad4b0-166">-ComputerName</span></span>
<span data-ttu-id="ad4b0-167">Spécifie le nom de l’ordinateur sur lequel cette applet de commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-167">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="ad4b0-168">La valeur par défaut est l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-168">The default is the local computer.</span></span>

<span data-ttu-id="ad4b0-169">Tapez le nom NetBIOS, une adresse IP ou un nom de domaine complet d'un ou de plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-169">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="ad4b0-170">Pour spécifier l’ordinateur local, tapez le nom de l’ordinateur, un point (.) ou localhost.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-170">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="ad4b0-171">Ce paramètre ne s'appuie pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-171">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="ad4b0-172">Vous pouvez utiliser le paramètre *ComputerName* même si votre ordinateur n'est pas configuré pour exécuter des commandes distantes.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-172">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="ad4b0-173">-Credential</span></span>
<span data-ttu-id="ad4b0-174">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-174">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ad4b0-175">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-175">The default is the current user.</span></span>

<span data-ttu-id="ad4b0-176">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-176">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="ad4b0-177">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-177">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-178">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="ad4b0-178">-EnableAllPrivileges</span></span>
<span data-ttu-id="ad4b0-179">Indique que cette applet de commande active toutes les autorisations de l’utilisateur actuel avant la commande qu’il effectue l’appel WMI.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-179">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-180">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="ad4b0-180">-Impersonation</span></span>
<span data-ttu-id="ad4b0-181">Spécifie le niveau d'emprunt d'identité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-181">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="ad4b0-182">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="ad4b0-182">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ad4b0-183">0 : Default.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-183">0: Default.</span></span>
<span data-ttu-id="ad4b0-184">Lit le registre local pour le niveau d’emprunt d’identité par défaut, qui est généralement défini sur 3 : Impersonate.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-184">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="ad4b0-185">1 : Anonymous.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-185">1: Anonymous.</span></span>
<span data-ttu-id="ad4b0-186">Masque les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-186">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="ad4b0-187">2 : Identify.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-187">2: Identify.</span></span>
<span data-ttu-id="ad4b0-188">Permet aux objets d'interroger les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-188">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="ad4b0-189">3 : Impersonate.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-189">3: Impersonate.</span></span>
<span data-ttu-id="ad4b0-190">Permet aux objets d'utiliser les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-190">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="ad4b0-191">4 : Delegate.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-191">4: Delegate.</span></span>
<span data-ttu-id="ad4b0-192">Permet aux objets d'autoriser d'autres objets à utiliser les informations d'identification de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-192">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-193">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ad4b0-193">-InputObject</span></span>
<span data-ttu-id="ad4b0-194">Spécifie un objet **ManagementObject** à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-194">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="ad4b0-195">Lorsque ce paramètre est utilisé, tous les autres paramètres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-195">When this parameter is used, all other parameters are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-196">Paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="ad4b0-196">-Locale</span></span>
<span data-ttu-id="ad4b0-197">Spécifie les paramètres régionaux par défaut pour les objets WMI.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-197">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="ad4b0-198">Les paramètres *régionaux* sont spécifiés sous la forme d’un tableau au \<LCID\> format MS_ dans l’ordre de préférence.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-198">The *Locale* parameter is specified as an array in the MS_\<LCID\> format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-199">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="ad4b0-199">-Namespace</span></span>
<span data-ttu-id="ad4b0-200">Spécifie l’espace de noms de l’espace de stockage WMI dans lequel se trouve la classe WMI référencée lorsqu’elle est utilisée avec le paramètre de *classe* .</span><span class="sxs-lookup"><span data-stu-id="ad4b0-200">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-201">-Path</span><span class="sxs-lookup"><span data-stu-id="ad4b0-201">-Path</span></span>
<span data-ttu-id="ad4b0-202">Spécifie le chemin d'accès de l'objet WMI d'une classe WMI, ou spécifie le chemin d'accès de l'objet WMI d'une instance d'une classe WMI à supprimer.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-202">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class to delete.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-203">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ad4b0-203">-ThrottleLimit</span></span>
<span data-ttu-id="ad4b0-204">Spécifie le nombre maximal de connexions simultanées qui peuvent être établies pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-204">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="ad4b0-205">Ce paramètre est utilisé conjointement avec le paramètre *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="ad4b0-205">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="ad4b0-206">La limite d'accélération s'applique uniquement à la commande actuelle, et non à la session ou à l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-206">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad4b0-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ad4b0-207">-Confirm</span></span>
<span data-ttu-id="ad4b0-208">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ad4b0-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ad4b0-209">-WhatIf</span></span>
<span data-ttu-id="ad4b0-210">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ad4b0-211">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-211">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ad4b0-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad4b0-212">CommonParameters</span></span>
<span data-ttu-id="ad4b0-213">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ad4b0-214">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ad4b0-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ad4b0-215">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="ad4b0-215">INPUTS</span></span>

### <span data-ttu-id="ad4b0-216">System. Management. ManagementObject</span><span class="sxs-lookup"><span data-stu-id="ad4b0-216">System.Management.ManagementObject</span></span>
<span data-ttu-id="ad4b0-217">Vous pouvez diriger un objet de gestion vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-217">You can pipe a management object to this cmdlet.</span></span>

## <span data-ttu-id="ad4b0-218">SORTIES</span><span class="sxs-lookup"><span data-stu-id="ad4b0-218">OUTPUTS</span></span>

### <span data-ttu-id="ad4b0-219">Aucun, System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="ad4b0-219">None, System.Management.Automation.RemotingJob</span></span>
<span data-ttu-id="ad4b0-220">Cette applet de commande retourne un objet de traitement, si vous spécifiez le paramètre *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="ad4b0-220">This cmdlet returns a job object, if you specify the *AsJob* parameter.</span></span>
<span data-ttu-id="ad4b0-221">Sinon, elle ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="ad4b0-221">Otherwise, it does not generate any output.</span></span>

## <span data-ttu-id="ad4b0-222">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="ad4b0-222">NOTES</span></span>

## <span data-ttu-id="ad4b0-223">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="ad4b0-223">RELATED LINKS</span></span>

[<span data-ttu-id="ad4b0-224">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="ad4b0-224">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="ad4b0-225">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="ad4b0-225">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="ad4b0-226">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="ad4b0-226">Set-WmiInstance</span></span>](Set-WmiInstance.md)
