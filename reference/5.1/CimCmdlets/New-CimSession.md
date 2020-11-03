---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 04d0b272995538e88fff2725eb8806c66d217460
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "93206093"
---
# <span data-ttu-id="5a4c7-103">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="5a4c7-103">New-CimSession</span></span>

## <span data-ttu-id="5a4c7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5a4c7-104">SYNOPSIS</span></span>

<span data-ttu-id="5a4c7-105">Crée une session CIM.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-105">Creates a CIM session.</span></span>

## <span data-ttu-id="5a4c7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a4c7-106">SYNTAX</span></span>

### <span data-ttu-id="5a4c7-107">CredentialParameterSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="5a4c7-107">CredentialParameterSet (Default)</span></span>

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### <span data-ttu-id="5a4c7-108">CertificatePrameterSet</span><span class="sxs-lookup"><span data-stu-id="5a4c7-108">CertificatePrameterSet</span></span>

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## <span data-ttu-id="5a4c7-109">Description</span><span class="sxs-lookup"><span data-stu-id="5a4c7-109">DESCRIPTION</span></span>

<span data-ttu-id="5a4c7-110">L' `New-CimSession` applet de commande crée une session CIM.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-110">The `New-CimSession` cmdlet creates a CIM session.</span></span> <span data-ttu-id="5a4c7-111">Une session CIM est un objet côté client qui représente une connexion à un ordinateur local ou à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-111">A CIM session is a client-side object representing a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="5a4c7-112">La session CIM contient des informations sur la connexion, telles que **ComputerName** , le protocole utilisé ou divers identificateurs.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-112">The CIM session contains information about the connection, such as **ComputerName** , the protocol used, or various identifiers.</span></span>

<span data-ttu-id="5a4c7-113">Cette applet de commande retourne un objet de session CIM qui peut être utilisé par toutes les autres applets de commande CIM.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-113">This cmdlet returns a CIM session object that can be used by all other CIM cmdlets.</span></span>

## <span data-ttu-id="5a4c7-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5a4c7-114">EXAMPLES</span></span>

### <span data-ttu-id="5a4c7-115">Exemple 1 : créer une session CIM avec les options par défaut</span><span class="sxs-lookup"><span data-stu-id="5a4c7-115">Example 1: Create a CIM session with default options</span></span>

<span data-ttu-id="5a4c7-116">Cet exemple crée une session CIM locale avec les options par défaut.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-116">This example creates a local CIM session with default options.</span></span> <span data-ttu-id="5a4c7-117">Si **ComputerName** n’est pas spécifié, `New-CimSession` crée une session DCOM sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-117">If **ComputerName** is not specified, `New-CimSession` creates a DCOM session to the local computer.</span></span>

```powershell
New-CimSession
```

### <span data-ttu-id="5a4c7-118">Exemple 2 : créer une session CIM sur un ordinateur spécifique</span><span class="sxs-lookup"><span data-stu-id="5a4c7-118">Example 2: Create a CIM session to a specific computer</span></span>

<span data-ttu-id="5a4c7-119">Cet exemple crée une session CIM sur l’ordinateur spécifié par **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-119">This example creates a CIM session to the computer specified by **ComputerName** .</span></span>
<span data-ttu-id="5a4c7-120">Par défaut, `New-CimSession` crée une session WSMan lorsque **ComputerName** est spécifié.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-120">By default, `New-CimSession` creates a WSMan session when **ComputerName** is specified.</span></span>

```powershell
New-CimSession -ComputerName Server01
```

### <span data-ttu-id="5a4c7-121">Exemple 3 : créer une session CIM sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="5a4c7-121">Example 3: Create a CIM session to multiple computers</span></span>

<span data-ttu-id="5a4c7-122">Cet exemple crée une session CIM sur chacun des ordinateurs spécifiés par **ComputerName** , dans la liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-122">This example creates a CIM session to each of the computers specified by **ComputerName** , in the comma separated list.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### <span data-ttu-id="5a4c7-123">Exemple 4 : créer une session CIM avec un nom convivial</span><span class="sxs-lookup"><span data-stu-id="5a4c7-123">Example 4: Create a CIM session with a friendly name</span></span>

<span data-ttu-id="5a4c7-124">Cet exemple crée une session CIM distante sur chacun des ordinateurs spécifiés par **ComputerName** , dans la liste séparée par des virgules, et affecte un nom convivial aux nouvelles sessions, en spécifiant **Name** .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-124">This example creates a remote CIM session to each of the computers specified by **ComputerName** , in the comma separated list, and assigns a friendly name to the new sessions, by specifying **Name** .</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

<span data-ttu-id="5a4c7-125">Vous pouvez utiliser le nom convivial d’une session CIM pour faire référence à la session dans d’autres applets de commande CIM, par exemple, [CimSession](Get-CimSession.md).</span><span class="sxs-lookup"><span data-stu-id="5a4c7-125">You can use the friendly name of a CIM session to refer to the session in other CIM cmdlets, for example, [Get-CimSession](Get-CimSession.md).</span></span>

### <span data-ttu-id="5a4c7-126">Exemple 5 : créer une session CIM sur un ordinateur à l’aide d’un objet PSCredential</span><span class="sxs-lookup"><span data-stu-id="5a4c7-126">Example 5: Create a CIM session to a computer using a PSCredential object</span></span>

<span data-ttu-id="5a4c7-127">Cet exemple crée une session CIM sur l’ordinateur spécifié par **ComputerName** , à l’aide de l’objet **PSCredential** spécifié par **Credential** et du type d’authentification spécifié par **l’authentification** .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-127">This example creates a CIM session to the computer specified by **ComputerName** , using the **PSCredential** object specified by **Credential** , and the authentication type specified by **Authentication** .</span></span>

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

<span data-ttu-id="5a4c7-128">Vous pouvez créer un objet **PSCredential** à l’aide de l’applet de commande [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-128">You can create a **PSCredential** object using the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

### <span data-ttu-id="5a4c7-129">Exemple 6 : créer une session CIM sur un ordinateur à l’aide d’un port spécifique</span><span class="sxs-lookup"><span data-stu-id="5a4c7-129">Example 6: Create a CIM session to a computer using a specific port</span></span>

<span data-ttu-id="5a4c7-130">Cet exemple crée une session CIM sur l’ordinateur spécifié par **ComputerName** à l’aide du port TCP spécifié par **port** .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-130">This example creates a CIM session to the computer specified by **ComputerName** using the TCP port specified by **Port** .</span></span>

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### <span data-ttu-id="5a4c7-131">Exemple 7 : créer une session CIM à l’aide de DCOM</span><span class="sxs-lookup"><span data-stu-id="5a4c7-131">Example 7: Create a CIM session using DCOM</span></span>

<span data-ttu-id="5a4c7-132">Cet exemple crée une session CIM à l’aide du protocole DCOM (Distributed COM) au lieu de WSMan.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-132">This example creates a CIM session using the Distributed COM (DCOM) protocol instead of WSMan.</span></span>

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## <span data-ttu-id="5a4c7-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a4c7-133">PARAMETERS</span></span>

### <span data-ttu-id="5a4c7-134">-Authentification</span><span class="sxs-lookup"><span data-stu-id="5a4c7-134">-Authentication</span></span>

<span data-ttu-id="5a4c7-135">Spécifie le type d’authentification utilisé pour les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-135">Specifies the authentication type used for the user's credentials.</span></span> <span data-ttu-id="5a4c7-136">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="5a4c7-136">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5a4c7-137">Default</span><span class="sxs-lookup"><span data-stu-id="5a4c7-137">Default</span></span>
- <span data-ttu-id="5a4c7-138">Digest</span><span class="sxs-lookup"><span data-stu-id="5a4c7-138">Digest</span></span>
- <span data-ttu-id="5a4c7-139">Negotiate</span><span class="sxs-lookup"><span data-stu-id="5a4c7-139">Negotiate</span></span>
- <span data-ttu-id="5a4c7-140">Basic</span><span class="sxs-lookup"><span data-stu-id="5a4c7-140">Basic</span></span>
- <span data-ttu-id="5a4c7-141">Kerberos</span><span class="sxs-lookup"><span data-stu-id="5a4c7-141">Kerberos</span></span>
- <span data-ttu-id="5a4c7-142">NtlmDomain</span><span class="sxs-lookup"><span data-stu-id="5a4c7-142">NtlmDomain</span></span>
- <span data-ttu-id="5a4c7-143">CredSsp</span><span class="sxs-lookup"><span data-stu-id="5a4c7-143">CredSsp</span></span>

<span data-ttu-id="5a4c7-144">Vous ne pouvez pas utiliser le type d’authentification **NtlmDomain** pour la connexion à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-144">You cannot use the **NtlmDomain** authentication type for connection to the local computer.</span></span> <span data-ttu-id="5a4c7-145">L’authentification **CredSSP** est disponible uniquement dans Windows Vista, windows Server 2008 et les versions ultérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-145">**CredSSP** authentication is available only in Windows Vista, Windows Server 2008, and later versions of Windows.</span></span>

> [!CAUTION]
> <span data-ttu-id="5a4c7-146">L’authentification CredSSP (Credential Security Service Provider) est conçue pour les commandes qui requièrent une authentification sur plusieurs ressources, telles que l’accès à un partage réseau distant.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-146">Credential Security Service Provider (CredSSP) authentication is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="5a4c7-147">Ce mécanisme augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-147">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="5a4c7-148">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-148">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-149">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="5a4c7-149">-CertificateThumbprint</span></span>

<span data-ttu-id="5a4c7-150">Spécifie le certificat de clé publique numérique (X. 509) d’un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-150">Specifies the digital public key certificate (X.509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="5a4c7-151">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-151">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="5a4c7-152">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-152">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="5a4c7-153">Ils peuvent être mappés uniquement aux comptes d'utilisateur locaux ; ils ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-153">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="5a4c7-154">Pour obtenir une empreinte numérique de certificat, utilisez les [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) applets de commande ou dans le fournisseur de certificats PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-154">To get a certificate thumbprint, use the [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) or [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdlets in the PowerShell Certificate Provider.</span></span>

<span data-ttu-id="5a4c7-155">Pour plus d’informations, consultez [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span><span class="sxs-lookup"><span data-stu-id="5a4c7-155">For more information, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

```yaml
Type: System.String
Parameter Sets: CertificatePrameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-156">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="5a4c7-156">-ComputerName</span></span>

<span data-ttu-id="5a4c7-157">Spécifie le nom de l’ordinateur sur lequel créer la session CIM.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-157">Specifies the name of the computer to which to create the CIM session.</span></span> <span data-ttu-id="5a4c7-158">Spécifiez un nom d’ordinateur unique ou plusieurs noms d’ordinateurs séparés par une virgule.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-158">Specify either a single computer name, or multiple computer names separated by a comma.</span></span>

<span data-ttu-id="5a4c7-159">Si **ComputerName** n’est pas spécifié, une session CIM sur l’ordinateur local est créée.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-159">If **ComputerName** is not specified, a CIM session to the local computer is created.</span></span> <span data-ttu-id="5a4c7-160">Vous pouvez spécifier la valeur du nom de l’ordinateur dans l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="5a4c7-160">You can specify the value for computer name in one of the following formats:</span></span>

- <span data-ttu-id="5a4c7-161">Un ou plusieurs noms NetBIOS</span><span class="sxs-lookup"><span data-stu-id="5a4c7-161">One or more NetBIOS names</span></span>
- <span data-ttu-id="5a4c7-162">Une ou plusieurs adresses IP</span><span class="sxs-lookup"><span data-stu-id="5a4c7-162">One or more IP addresses</span></span>
- <span data-ttu-id="5a4c7-163">Un ou plusieurs noms de domaines complets.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-163">One or more fully qualified domain names.</span></span>

<span data-ttu-id="5a4c7-164">Si l’ordinateur se trouve dans un domaine différent de celui de l’utilisateur, vous devez spécifier le nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-164">If the computer is in a different domain than the user, you must specify the fully qualified domain name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="5a4c7-165">-Credential</span></span>

<span data-ttu-id="5a4c7-166">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="5a4c7-167">Si **Credential** n’est pas spécifié, le compte d’utilisateur actuel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-167">If **Credential** is not specified, the current user account is used.</span></span>

<span data-ttu-id="5a4c7-168">Spécifiez la valeur des **informations d’identification** à l’aide de l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="5a4c7-168">Specify the value for **Credential** using one of the following formats:</span></span>

- <span data-ttu-id="5a4c7-169">Nom d’utilisateur : « User01 »</span><span class="sxs-lookup"><span data-stu-id="5a4c7-169">A user name: "User01"</span></span>
- <span data-ttu-id="5a4c7-170">Un nom de domaine et un nom d’utilisateur : « Domaine01\utilisateur01 »</span><span class="sxs-lookup"><span data-stu-id="5a4c7-170">A domain name and a user name: "Domain01\User01"</span></span>
- <span data-ttu-id="5a4c7-171">Un nom d’utilisateur principal : « User@Domain.com »</span><span class="sxs-lookup"><span data-stu-id="5a4c7-171">A user principal name: "User@Domain.com"</span></span>
- <span data-ttu-id="5a4c7-172">Objet PSCredential, tel que celui retourné par l’applet de commande [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-172">A PSCredential object, such as one returned by the [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.</span></span>

<span data-ttu-id="5a4c7-173">Lorsque vous tapez un nom d’utilisateur, vous êtes invité à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-173">When you type a user name, you are prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-174">-Name</span><span class="sxs-lookup"><span data-stu-id="5a4c7-174">-Name</span></span>

<span data-ttu-id="5a4c7-175">Spécifie un nom convivial pour la session CIM.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-175">Specifies a friendly name for the CIM session.</span></span>

<span data-ttu-id="5a4c7-176">Vous pouvez utiliser le nom pour faire référence à la session CIM lors de l’utilisation d’autres applets de commande, telles que l’applet de commande [`Get-CimSession`](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-176">You can use the name to refer to the CIM session when using other cmdlets, such as the [`Get-CimSession`](Get-CimSession.md) cmdlet.</span></span>
<span data-ttu-id="5a4c7-177">Le nom n'a pas obligatoirement à être unique sur l'ordinateur ou dans la session active.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-177">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-178">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="5a4c7-178">-OperationTimeoutSec</span></span>

<span data-ttu-id="5a4c7-179">Durée pendant laquelle l’applet de commande attend une réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-179">Duration for which the cmdlet waits for a response from the server.</span></span>

<span data-ttu-id="5a4c7-180">Par défaut, la valeur de ce paramètre est 0, ce qui signifie que l’applet de commande utilise la valeur de délai d’attente par défaut pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-180">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="5a4c7-181">Si le paramètre **OperationTimeoutSec** est défini sur une valeur inférieure au délai d’attente de nouvelle tentative de connexion fiable de 3 minutes, les défaillances réseau qui durent plus que la valeur du paramètre **OperationTimeoutSec** ne sont pas récupérables, car l’opération sur le serveur expire avant que le client puisse se reconnecter.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-181">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-182">-Port</span><span class="sxs-lookup"><span data-stu-id="5a4c7-182">-Port</span></span>

<span data-ttu-id="5a4c7-183">Spécifie le port réseau sur l’ordinateur distant utilisé pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-183">Specifies the network port on the remote computer that is used for this connection.</span></span>
<span data-ttu-id="5a4c7-184">Pour établir une connexion à un ordinateur distant, l’ordinateur distant doit être à l’écoute sur le port utilisé par la connexion.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-184">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span>
<span data-ttu-id="5a4c7-185">Les ports par défaut sont 5985 (port WinRM pour HTTP) et 5986 (port WinRM pour HTTPS).</span><span class="sxs-lookup"><span data-stu-id="5a4c7-185">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span>

<span data-ttu-id="5a4c7-186">Avant d'utiliser un autre port, vous devez configurer l'écouteur WinRM sur l'ordinateur distant pour qu'il écoute sur ce port.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-186">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>
<span data-ttu-id="5a4c7-187">Utilisez les commandes suivantes pour configurer l'écouteur :</span><span class="sxs-lookup"><span data-stu-id="5a4c7-187">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

<span data-ttu-id="5a4c7-188">N'utilisez pas le paramètre **Port** à moins que vous n'y soyez obligé.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-188">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="5a4c7-189">Le paramètre de port de la commande s'applique à tous les ordinateurs ou sessions sur lesquels la commande s'exécute.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-189">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="5a4c7-190">Un autre paramètre de port peut empêcher la commande de s'exécuter sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-190">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-191">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="5a4c7-191">-SessionOption</span></span>

<span data-ttu-id="5a4c7-192">Définit des options avancées pour la nouvelle session CIM.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-192">Sets advanced options for the new CIM session.</span></span> <span data-ttu-id="5a4c7-193">Entrez le nom d’un objet **CimSessionOption** créé à l’aide de l’applet de commande [`New-CimSessionOption`](New-CimSessionOption.md) .</span><span class="sxs-lookup"><span data-stu-id="5a4c7-193">Enter the name of a **CimSessionOption** object created using the [`New-CimSessionOption`](New-CimSessionOption.md) cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-194">-SkipTestConnection</span><span class="sxs-lookup"><span data-stu-id="5a4c7-194">-SkipTestConnection</span></span>

<span data-ttu-id="5a4c7-195">Par défaut, l' `New-CimSession` applet de commande établit une connexion avec un point de terminaison de WS-Management distant pour deux raisons : pour vérifier que le serveur distant écoute sur le numéro de port spécifié à l’aide du paramètre de **port** et pour vérifier les informations d’identification de compte spécifiées.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-195">By default, the `New-CimSession` cmdlet establishes a connection with a remote WS-Management endpoint for two reasons: to verify that the remote server is listening on the port number that is specified using the **Port** parameter, and to verify the specified account credentials.</span></span> <span data-ttu-id="5a4c7-196">La vérification s’effectue à l’aide d’une opération de WS-Identity standard.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-196">The verification is accomplished using a standard WS-Identity operation.</span></span> <span data-ttu-id="5a4c7-197">Vous pouvez ajouter le paramètre de commutateur **SkipTestConnection** si le point de terminaison de WS-Management distant ne peut pas utiliser WS-identify ou pour réduire le temps de transmission de données.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-197">You can add the **SkipTestConnection** switch parameter if the remote WS-Management endpoint cannot use WS-Identify, or to reduce some data transmission time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5a4c7-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a4c7-198">CommonParameters</span></span>

<span data-ttu-id="5a4c7-199">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a4c7-200">Pour plus d’informations, consultez [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="5a4c7-200">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5a4c7-201">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5a4c7-201">INPUTS</span></span>

### <span data-ttu-id="5a4c7-202">Aucun</span><span class="sxs-lookup"><span data-stu-id="5a4c7-202">None</span></span>

<span data-ttu-id="5a4c7-203">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="5a4c7-203">This cmdlet accepts no inputs.</span></span>

## <span data-ttu-id="5a4c7-204">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5a4c7-204">OUTPUTS</span></span>

### <span data-ttu-id="5a4c7-205">Microsoft.Management.Infrastructure.CimSession</span><span class="sxs-lookup"><span data-stu-id="5a4c7-205">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="5a4c7-206">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5a4c7-206">NOTES</span></span>

## <span data-ttu-id="5a4c7-207">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5a4c7-207">RELATED LINKS</span></span>

[<span data-ttu-id="5a4c7-208">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5a4c7-208">Get-ChildItem</span></span>](../Microsoft.Powershell.Management/Get-ChildItem.md)

[<span data-ttu-id="5a4c7-209">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="5a4c7-209">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="5a4c7-210">Get-Item</span><span class="sxs-lookup"><span data-stu-id="5a4c7-210">Get-Item</span></span>](../Microsoft.Powershell.Management/Get-Item.md)

[<span data-ttu-id="5a4c7-211">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="5a4c7-211">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="5a4c7-212">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="5a4c7-212">Remove-CimSession</span></span>](Remove-CimSession.md)

[<span data-ttu-id="5a4c7-213">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="5a4c7-213">New-CimSessionOption</span></span>](New-CimSessionOption.md)

[<span data-ttu-id="5a4c7-214">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="5a4c7-214">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)
