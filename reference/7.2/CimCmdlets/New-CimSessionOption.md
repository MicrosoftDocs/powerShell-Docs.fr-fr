---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 54a2ca8a28d54bfe1d9676acdaace4592f62620f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598345"
---
# <span data-ttu-id="b7479-102">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="b7479-102">New-CimSessionOption</span></span>

## <span data-ttu-id="b7479-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b7479-103">SYNOPSIS</span></span>
<span data-ttu-id="b7479-104">Spécifie les options avancées pour l’applet de commande New-CimSession.</span><span class="sxs-lookup"><span data-stu-id="b7479-104">Specifies advanced options for the New-CimSession cmdlet.</span></span>

## <span data-ttu-id="b7479-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b7479-105">SYNTAX</span></span>

### <span data-ttu-id="b7479-106">ProtocolTypeSet (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b7479-106">ProtocolTypeSet (Default)</span></span>

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### <span data-ttu-id="b7479-107">WSManParameterSet</span><span class="sxs-lookup"><span data-stu-id="b7479-107">WSManParameterSet</span></span>

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### <span data-ttu-id="b7479-108">DcomParameterSet</span><span class="sxs-lookup"><span data-stu-id="b7479-108">DcomParameterSet</span></span>

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## <span data-ttu-id="b7479-109">Description</span><span class="sxs-lookup"><span data-stu-id="b7479-109">DESCRIPTION</span></span>

<span data-ttu-id="b7479-110">L' `New-CimSessionOption` applet de commande crée une instance d’un objet d’options de session CIM.</span><span class="sxs-lookup"><span data-stu-id="b7479-110">The `New-CimSessionOption` cmdlet creates an instance of a CIM session options object.</span></span> <span data-ttu-id="b7479-111">Vous utilisez un objet d’options de session CIM comme entrée de l' `New-CimSession` applet de commande pour spécifier les options pour une session CIM.</span><span class="sxs-lookup"><span data-stu-id="b7479-111">You use a CIM session options object as input to the `New-CimSession` cmdlet to specify the options for a CIM session.</span></span>

<span data-ttu-id="b7479-112">Cette applet de commande a deux jeux de paramètres : un pour les options WsMan et un pour les options DCOM (Distributed Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="b7479-112">This cmdlet has two parameter sets, one for WsMan options and one for Distributed Component Object Model (DCOM) options.</span></span> <span data-ttu-id="b7479-113">Selon les paramètres que vous utilisez, l’applet de commande retourne une instance d’options de session DCOM ou retourne des options de session WsMan.</span><span class="sxs-lookup"><span data-stu-id="b7479-113">Depending on which parameters you use, the cmdlet returns either an instance of DCOM session options or returns WsMan session options.</span></span>

## <span data-ttu-id="b7479-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b7479-114">EXAMPLES</span></span>

### <span data-ttu-id="b7479-115">Exemple 1 : créer un objet d’options de session CIM pour DCOM</span><span class="sxs-lookup"><span data-stu-id="b7479-115">Example 1: Create a CIM session options object for DCOM</span></span>

<span data-ttu-id="b7479-116">Cet exemple crée un objet d’options de session CIM pour le protocole DCOM et le stocke dans une variable nommée `$so` .</span><span class="sxs-lookup"><span data-stu-id="b7479-116">This example creates a CIM session options object for the DCOM protocol and stores it in a variable named `$so`.</span></span> <span data-ttu-id="b7479-117">Le contenu de la variable est ensuite transmis à l' `New-CimSession` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b7479-117">The contents of the variable are then passed to the `New-CimSession` cmdlet.</span></span>
<span data-ttu-id="b7479-118">`New-CimSession` crée ensuite une nouvelle session CIM avec le serveur distant nommé Serveur01, à l’aide des options définies dans la variable.</span><span class="sxs-lookup"><span data-stu-id="b7479-118">`New-CimSession` then creates a new CIM session with the remote server named Server01, using the options defined in the variable.</span></span>

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### <span data-ttu-id="b7479-119">Exemple 2 : créer un objet d’options de session CIM pour WsMan</span><span class="sxs-lookup"><span data-stu-id="b7479-119">Example 2: Create a CIM session options object for WsMan</span></span>

<span data-ttu-id="b7479-120">Cet exemple crée un objet d’options de session CIM pour le protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="b7479-120">This example creates a CIM session options object for the WsMan protocol.</span></span> <span data-ttu-id="b7479-121">L’objet contient une configuration pour le mode d’authentification **Kerberos** spécifié par le paramètre **ProxyAuthentication** , les informations d’identification spécifiées par le paramètre **ProxyCredential** , et spécifie que la commande doit ignorer la vérification de l’autorité de certification, ignorer la vérification CN et utiliser SSL.</span><span class="sxs-lookup"><span data-stu-id="b7479-121">The object contains configuration for the authentication mode of **Kerberos** specified by the **ProxyAuthentication** parameter, the credentials specified by the **ProxyCredential** parameter, and specifies that the command is to skip the CA check, skip the CN check, and use SSL.</span></span>

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### <span data-ttu-id="b7479-122">Exemple 3 : créer un objet d’options de session CIM avec la culture spécifiée</span><span class="sxs-lookup"><span data-stu-id="b7479-122">Example 3: Create a CIM session options object with the culture specified</span></span>

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

<span data-ttu-id="b7479-123">Cet exemple spécifie la culture utilisée pour la session CIM.</span><span class="sxs-lookup"><span data-stu-id="b7479-123">This example specifies the culture that is used for the CIM session.</span></span> <span data-ttu-id="b7479-124">Par défaut, la culture du client est utilisée lors de l’exécution d’opérations.</span><span class="sxs-lookup"><span data-stu-id="b7479-124">By default, the culture of the client is used when performing operations.</span></span> <span data-ttu-id="b7479-125">Toutefois, la culture par défaut peut être substituée à l’aide du paramètre **culture** .</span><span class="sxs-lookup"><span data-stu-id="b7479-125">However, the default culture can be overridden using the **Culture** parameter.</span></span>

## <span data-ttu-id="b7479-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7479-126">PARAMETERS</span></span>

### <span data-ttu-id="b7479-127">-Culture</span><span class="sxs-lookup"><span data-stu-id="b7479-127">-Culture</span></span>

<span data-ttu-id="b7479-128">Spécifie la culture de l’interface utilisateur à utiliser pour la session CIM.</span><span class="sxs-lookup"><span data-stu-id="b7479-128">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="b7479-129">Spécifiez la valeur de ce paramètre à l’aide de l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="b7479-129">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="b7479-130">Nom de culture dans un `<languagecode2>-<country/regioncode2>` format tel que « en-US ».</span><span class="sxs-lookup"><span data-stu-id="b7479-130">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="b7479-131">Variable qui contient un objet **CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="b7479-131">A variable that contains a **CultureInfo** object.</span></span>
- <span data-ttu-id="b7479-132">Une commande qui obtient un objet **CultureInfo** , tel que la [culture « obtenir-culture »](../Microsoft.PowerShell.Utility/Get-Culture.md) ;</span><span class="sxs-lookup"><span data-stu-id="b7479-132">A command that gets a **CultureInfo** object, such as [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-133">-EncodePortInServicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="b7479-133">-EncodePortInServicePrincipalName</span></span>

<span data-ttu-id="b7479-134">Indique que la connexion Kerberos se connecte à un service dont le nom de principal du service (SPN) comprend le numéro de port du service.</span><span class="sxs-lookup"><span data-stu-id="b7479-134">Indicates that the Kerberos connection is connecting to a service whose service principal name (SPN) includes the service port number.</span></span> <span data-ttu-id="b7479-135">Ce type de connexion n’est pas courant.</span><span class="sxs-lookup"><span data-stu-id="b7479-135">This type of connection is not common.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-136">-Encoding</span><span class="sxs-lookup"><span data-stu-id="b7479-136">-Encoding</span></span>

<span data-ttu-id="b7479-137">Spécifie l’encodage utilisé pour le protocole WsMan.</span><span class="sxs-lookup"><span data-stu-id="b7479-137">Specifies the encoding used for the WsMan protocol.</span></span> <span data-ttu-id="b7479-138">Les valeurs acceptables pour ce paramètre sont les suivantes : **default**, **UTF8** ou **Utf16**.</span><span class="sxs-lookup"><span data-stu-id="b7479-138">The acceptable values for this parameter are: **Default**, **Utf8**, or **Utf16**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-139">-HttpPrefix</span><span class="sxs-lookup"><span data-stu-id="b7479-139">-HttpPrefix</span></span>

<span data-ttu-id="b7479-140">Spécifie la partie de l’URL HTTP Après le nom de l’ordinateur et le numéro de port.</span><span class="sxs-lookup"><span data-stu-id="b7479-140">Specifies the part of the HTTP URL after the computer name and port number.</span></span> <span data-ttu-id="b7479-141">La modification de ce n’est pas courante.</span><span class="sxs-lookup"><span data-stu-id="b7479-141">Changing this is not common.</span></span> <span data-ttu-id="b7479-142">Par défaut, la valeur de ce paramètre est **/WSMan**.</span><span class="sxs-lookup"><span data-stu-id="b7479-142">By default, the value of this parameter is **/wsman**.</span></span>

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-143">-Emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="b7479-143">-Impersonation</span></span>

<span data-ttu-id="b7479-144">Crée une session DCOM pour Windows Management Instrumentation (WMI) à l’aide de l’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="b7479-144">Creates a DCOM session to Windows Management Instrumentation (WMI) using impersonation.</span></span>

<span data-ttu-id="b7479-145">Les valeurs valides pour ce paramètre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7479-145">Valid values for this parameter are:</span></span>

- <span data-ttu-id="b7479-146">Par défaut : DCOM peut choisir le niveau d’emprunt d’identité à l’aide de son algorithme de négociation de sécurité normal.</span><span class="sxs-lookup"><span data-stu-id="b7479-146">Default: DCOM can choose the impersonation level using its normal security negotiation algorithm.</span></span>
- <span data-ttu-id="b7479-147">None : le client est anonyme pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="b7479-147">None: The client is anonymous to the server.</span></span> <span data-ttu-id="b7479-148">Le processus serveur peut emprunter l’identité du client, mais le jeton d’emprunt d’identité ne contient aucune information et ne peut pas être utilisé.</span><span class="sxs-lookup"><span data-stu-id="b7479-148">The server process can impersonate the client, but the impersonation token does not contain any information and cannot be used.</span></span>
- <span data-ttu-id="b7479-149">Identify : permet aux objets d’interroger les informations d’identification de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b7479-149">Identify: Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="b7479-150">Impersonate : permet aux objets d’utiliser les informations d’identification de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b7479-150">Impersonate: Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="b7479-151">Delegate : permet aux objets d’autoriser d’autres objets à utiliser les informations d’identification de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b7479-151">Delegate: Allows objects to permit other objects to use the credentials of the caller.</span></span>

<span data-ttu-id="b7479-152">Si l' **emprunt d’identité** n’est pas spécifié, l' `New-CimSession` applet de commande utilise la valeur de **Impersonate**.</span><span class="sxs-lookup"><span data-stu-id="b7479-152">If **Impersonation** is not specified, the `New-CimSession` cmdlet uses the value of **Impersonate**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-153">-MaxEnvelopeSizeKB</span><span class="sxs-lookup"><span data-stu-id="b7479-153">-MaxEnvelopeSizeKB</span></span>

<span data-ttu-id="b7479-154">Spécifie la taille limite des messages XML WsMan pour l’une ou l’autre direction.</span><span class="sxs-lookup"><span data-stu-id="b7479-154">Specifies the size limit of WsMan XML messages for either direction.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-155">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="b7479-155">-NoEncryption</span></span>

<span data-ttu-id="b7479-156">Spécifie que le chiffrement des données est désactivé.</span><span class="sxs-lookup"><span data-stu-id="b7479-156">Specifies that data encryption is turned off.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-157">-PacketIntegrity</span><span class="sxs-lookup"><span data-stu-id="b7479-157">-PacketIntegrity</span></span>

<span data-ttu-id="b7479-158">Spécifie que la session DCOM créée à l’aide de WMI utilise la fonctionnalité _PACKETINTEGRITY_ com (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="b7479-158">Specifies that the DCOM session created to WMI uses the Component Object Model (COM) _PacketIntegrity_ functionality.</span></span> <span data-ttu-id="b7479-159">Par défaut, toutes les sessions CIM créées à l’aide de DCOM ont le paramètre **PacketIntegrity** défini sur **true**.</span><span class="sxs-lookup"><span data-stu-id="b7479-159">By default, all CIM sessions created using DCOM have the **PacketIntegrity** parameter set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-160">-PacketPrivacy</span><span class="sxs-lookup"><span data-stu-id="b7479-160">-PacketPrivacy</span></span>

<span data-ttu-id="b7479-161">Crée une session DCOM vers WMI à l’aide de l' _PACKETPRIVACY_ com.</span><span class="sxs-lookup"><span data-stu-id="b7479-161">Creates a DCOM session to WMI using the COM _PacketPrivacy_.</span></span> <span data-ttu-id="b7479-162">Par défaut, toutes les sessions CIM créées à l’aide de DCOM ont le paramètre **PacketPrivacy** défini sur **true**.</span><span class="sxs-lookup"><span data-stu-id="b7479-162">By default, all CIM sessions created using DCOM have the **PacketPrivacy** parameter set to **true**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-163">-Protocol</span><span class="sxs-lookup"><span data-stu-id="b7479-163">-Protocol</span></span>

<span data-ttu-id="b7479-164">Spécifie le protocole à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b7479-164">Specifies the protocol to use.</span></span> <span data-ttu-id="b7479-165">Les valeurs acceptables pour ce paramètre sont les suivantes : **DCOM**, **default** ou **WSMan**.</span><span class="sxs-lookup"><span data-stu-id="b7479-165">The acceptable values for this parameter are: **DCOM**, **Default**, or **Wsman**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-166">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="b7479-166">-ProxyAuthentication</span></span>

<span data-ttu-id="b7479-167">Spécifie la méthode d’authentification à utiliser pour la résolution du proxy.</span><span class="sxs-lookup"><span data-stu-id="b7479-167">Specifies the authentication method to use for proxy resolution.</span></span> <span data-ttu-id="b7479-168">Les valeurs acceptables pour ce paramètre sont les suivantes : **default**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain** ou **CredSsp**.</span><span class="sxs-lookup"><span data-stu-id="b7479-168">The acceptable values for this parameter are: **Default**, **Digest**, **Negotiate**, **Basic**, **Kerberos**, **NtlmDomain**, or **CredSsp**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-169">-ProxyCertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="b7479-169">-ProxyCertificateThumbprint</span></span>

<span data-ttu-id="b7479-170">Spécifie le certificat de clé publique numérique (x. 509) d’un compte d’utilisateur pour l’authentification du proxy.</span><span class="sxs-lookup"><span data-stu-id="b7479-170">Specifies the (x.509) digital public key certificate of a user account for proxy authentication.</span></span>
<span data-ttu-id="b7479-171">Entrez l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="b7479-171">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="b7479-172">Les certificats sont utilisés dans l'authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="b7479-172">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="b7479-173">Ils peuvent uniquement être mappés à des comptes d’utilisateurs locaux et ne fonctionnent pas avec les comptes de domaine.</span><span class="sxs-lookup"><span data-stu-id="b7479-173">They can only be mapped to local user accounts and they do not work with domain accounts.</span></span>

<span data-ttu-id="b7479-174">Pour obtenir une empreinte numérique de certificat, utilisez les `Get-Item` `Get-ChildItem` applets de commande ou dans le lecteur de certificat PowerShell :.</span><span class="sxs-lookup"><span data-stu-id="b7479-174">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b7479-175">-ProxyCredential</span></span>

<span data-ttu-id="b7479-176">Spécifie les informations d'identification à utiliser pour l'authentification du proxy.</span><span class="sxs-lookup"><span data-stu-id="b7479-176">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="b7479-177">Entrez l'une des informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7479-177">Enter one of the following:</span></span>

- <span data-ttu-id="b7479-178">Variable qui contient un objet PSCredential.</span><span class="sxs-lookup"><span data-stu-id="b7479-178">A variable that contains a PSCredential object.</span></span>
- <span data-ttu-id="b7479-179">Commande qui obtient un objet PSCredential, tel que `Get-Credential`</span><span class="sxs-lookup"><span data-stu-id="b7479-179">A command that gets a PSCredential object, such as `Get-Credential`</span></span>

<span data-ttu-id="b7479-180">Si cette option n’est pas définie, vous ne pouvez pas spécifier d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b7479-180">If this option is not set, then you cannot specify any credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-181">-ProxyType</span><span class="sxs-lookup"><span data-stu-id="b7479-181">-ProxyType</span></span>

<span data-ttu-id="b7479-182">Spécifie le mécanisme de résolution de nom d’hôte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b7479-182">Specifies the host name resolution mechanism to use.</span></span> <span data-ttu-id="b7479-183">Les valeurs acceptables pour ce paramètre sont : **None**, **WinHTTP**, **auto** ou **InternetExplorer**.</span><span class="sxs-lookup"><span data-stu-id="b7479-183">The acceptable values for this parameter are: **None**, **WinHttp**, **Auto**, or **InternetExplorer**.</span></span>

<span data-ttu-id="b7479-184">La valeur par défaut de ce paramètre est **InternetExplorer**.</span><span class="sxs-lookup"><span data-stu-id="b7479-184">The default value of this parameter is **InternetExplorer**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-185">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="b7479-185">-SkipCACheck</span></span>

<span data-ttu-id="b7479-186">Indique que lors de la connexion via HTTPs, le client ne valide pas que le certificat de serveur est signé par une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="b7479-186">Indicates that when connecting over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="b7479-187">Utilisez ce paramètre uniquement lorsque l’ordinateur distant est approuvé à l’aide d’un autre mécanisme, par exemple quand l’ordinateur distant fait partie d’un réseau qui est physiquement sécurisé et isolé, ou lorsque l’ordinateur distant est listé comme un hôte approuvé dans une configuration WinRM.</span><span class="sxs-lookup"><span data-stu-id="b7479-187">Use this parameter only when the remote computer is trusted using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated, or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-188">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="b7479-188">-SkipCNCheck</span></span>

<span data-ttu-id="b7479-189">Indique que le nom commun du certificat du serveur n’a pas besoin de correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="b7479-189">Indicates that the certificate common name (CN) of the server does not need to match the hostname of the server.</span></span> <span data-ttu-id="b7479-190">Utilisez ce paramètre pour les opérations à distance uniquement avec les ordinateurs approuvés qui utilisent le protocole HTTPs.</span><span class="sxs-lookup"><span data-stu-id="b7479-190">Use this parameter for remote operations only with trusted computers that use the HTTPS protocol.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-191">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="b7479-191">-SkipRevocationCheck</span></span>

<span data-ttu-id="b7479-192">Indique que la vérification de la révocation des certificats de serveur est ignorée.</span><span class="sxs-lookup"><span data-stu-id="b7479-192">Indicates that the revocation check for server certificates is skipped.</span></span> <span data-ttu-id="b7479-193">Utilisez ce paramètre uniquement pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="b7479-193">Use this parameter only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-194">-UICulture</span><span class="sxs-lookup"><span data-stu-id="b7479-194">-UICulture</span></span>

<span data-ttu-id="b7479-195">Spécifie la culture de l’interface utilisateur à utiliser pour la session CIM.</span><span class="sxs-lookup"><span data-stu-id="b7479-195">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="b7479-196">Spécifiez la valeur de ce paramètre à l’aide de l’un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="b7479-196">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="b7479-197">Nom de culture dans un `<languagecode2>-<country/regioncode2>` format tel que « en-US ».</span><span class="sxs-lookup"><span data-stu-id="b7479-197">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="b7479-198">Variable qui contient un objet CultureInfo.</span><span class="sxs-lookup"><span data-stu-id="b7479-198">A variable that contains a CultureInfo object.</span></span>
- <span data-ttu-id="b7479-199">Commande qui obtient un objet CultureInfo, tel que `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="b7479-199">A command that gets a CultureInfo object, such as `Get-Culture`.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-200">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="b7479-200">-UseSsl</span></span>

<span data-ttu-id="b7479-201">Indique que le protocole SSL doit être utilisé pour établir une connexion à l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b7479-201">Indicates that SSL should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="b7479-202">Par défaut, SSL n'est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="b7479-202">By default, SSL is not used.</span></span> <span data-ttu-id="b7479-203">WsMan chiffre tout le contenu transmis sur le réseau, même en cas d’utilisation du protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="b7479-203">WsMan encrypts all content that is transmitted over the network, even when using HTTP.</span></span>

<span data-ttu-id="b7479-204">Ce paramètre vous permet de spécifier la protection supplémentaire du protocole HTTPs au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="b7479-204">This parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="b7479-205">Si SSL n’est pas disponible sur le port utilisé pour la connexion et que vous spécifiez ce paramètre, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="b7479-205">If SSL is not available on the port used for the connection and you specify this parameter, then the command fails.</span></span>

<span data-ttu-id="b7479-206">Il est recommandé d’utiliser ce paramètre uniquement lorsque le paramètre **PacketPrivacy** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="b7479-206">It is recommended that you use this parameter only when the **PacketPrivacy** parameter is not specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7479-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7479-207">CommonParameters</span></span>

<span data-ttu-id="b7479-208">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7479-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7479-209">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b7479-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7479-210">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b7479-210">INPUTS</span></span>

### <span data-ttu-id="b7479-211">None</span><span class="sxs-lookup"><span data-stu-id="b7479-211">None</span></span>

<span data-ttu-id="b7479-212">Cette applet de commande n’accepte aucun objet d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b7479-212">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="b7479-213">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b7479-213">OUTPUTS</span></span>

### <span data-ttu-id="b7479-214">CIMSessionOption</span><span class="sxs-lookup"><span data-stu-id="b7479-214">CIMSessionOption</span></span>

<span data-ttu-id="b7479-215">Cette applet de commande retourne un objet qui contient des informations sur les options de session CIM.</span><span class="sxs-lookup"><span data-stu-id="b7479-215">This cmdlet returns an object that contains CIM session options information.</span></span>

## <span data-ttu-id="b7479-216">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b7479-216">NOTES</span></span>

## <span data-ttu-id="b7479-217">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b7479-217">RELATED LINKS</span></span>

[<span data-ttu-id="b7479-218">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="b7479-218">Get-ChildItem</span></span>](../microsoft.powershell.management/get-childitem.md)

[<span data-ttu-id="b7479-219">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="b7479-219">Get-Credential</span></span>](../microsoft.powershell.security/get-credential.md)

[<span data-ttu-id="b7479-220">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="b7479-220">Get-Culture</span></span>](../microsoft.powershell.utility/get-culture.md)

[<span data-ttu-id="b7479-221">Get-Item</span><span class="sxs-lookup"><span data-stu-id="b7479-221">Get-Item</span></span>](../microsoft.powershell.management/get-item.md)

[<span data-ttu-id="b7479-222">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="b7479-222">New-CimSession</span></span>](New-CimSession.md)

