---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: 8996c550147ab7e0857d97b0a47baf92fac514d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202549"
---
# <span data-ttu-id="eea04-103">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="eea04-103">New-WSManSessionOption</span></span>

## <span data-ttu-id="eea04-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="eea04-104">SYNOPSIS</span></span>
<span data-ttu-id="eea04-105">Crée une table de hachage des options de session à utiliser comme paramètres d’entrée pour les applets de commande WS-Management.</span><span class="sxs-lookup"><span data-stu-id="eea04-105">Creates session option hash table to use as input parameters for WS-Management cmdlets.</span></span>

## <span data-ttu-id="eea04-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eea04-106">SYNTAX</span></span>

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## <span data-ttu-id="eea04-107">Description</span><span class="sxs-lookup"><span data-stu-id="eea04-107">DESCRIPTION</span></span>
<span data-ttu-id="eea04-108">L’applet **de commande New-WSManSessionOption** crée une table de hachage de l’option de session WSMan qui peut être passée aux applets de commande WSMan :</span><span class="sxs-lookup"><span data-stu-id="eea04-108">The **New-WSManSessionOption** cmdlet creates a WSMan Session option hash table which can be passed to WSMan cmdlets:</span></span>

- <span data-ttu-id="eea04-109">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="eea04-109">Get-WSManInstance</span></span>
- <span data-ttu-id="eea04-110">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="eea04-110">Set-WSManInstance</span></span>
- <span data-ttu-id="eea04-111">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="eea04-111">Invoke-WSManAction</span></span>
- <span data-ttu-id="eea04-112">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="eea04-112">Connect-WSMan</span></span>

## <span data-ttu-id="eea04-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="eea04-113">EXAMPLES</span></span>

### <span data-ttu-id="eea04-114">Exemple 1 : créer une connexion qui utilise des options de connexion</span><span class="sxs-lookup"><span data-stu-id="eea04-114">Example 1: Create a connection that uses connection options</span></span>

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="eea04-115">Cet exemple crée une connexion à l’ordinateur SERVEUR01 distant à l’aide des options de connexion définies par **New-WSManSessionOption** .</span><span class="sxs-lookup"><span data-stu-id="eea04-115">This example creates a connection to the remote server01 computer by using the connection options that are defined by **New-WSManSessionOption** .</span></span>

<span data-ttu-id="eea04-116">La première commande utilise **New-WSManSessionOption** pour stocker un ensemble d’options de paramètres de connexion dans la variable $a.</span><span class="sxs-lookup"><span data-stu-id="eea04-116">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="eea04-117">Dans cet exemple, les options de session définissent un délai de connexion de 30 secondes (30 000 millisecondes).</span><span class="sxs-lookup"><span data-stu-id="eea04-117">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="eea04-118">La deuxième commande utilise le paramètre *SessionOption* pour transmettre les informations d’identification stockées dans la variable $A à **connect-wsman** .</span><span class="sxs-lookup"><span data-stu-id="eea04-118">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan** .</span></span>
<span data-ttu-id="eea04-119">Ensuite, **connect-wsman** se connecte à l’ordinateur SERVEUR01 distant à l’aide des options de session spécifiées.</span><span class="sxs-lookup"><span data-stu-id="eea04-119">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

<span data-ttu-id="eea04-120">**Connect-wsman** est généralement utilisé dans le contexte du fournisseur WSMan pour se connecter à un ordinateur distant, dans le cas présent l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="eea04-120">**Connect-WSMan** is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="eea04-121">Toutefois, vous pouvez utiliser l'applet de commande pour établir des connexions aux ordinateurs distants avant de choisir le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="eea04-121">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="eea04-122">Ces connexions s’affichent dans la liste **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="eea04-122">Those connections appear in the **ComputerName** list.</span></span>

## <span data-ttu-id="eea04-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eea04-123">PARAMETERS</span></span>

### <span data-ttu-id="eea04-124">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="eea04-124">-NoEncryption</span></span>
<span data-ttu-id="eea04-125">Indique que la connexion n’utilise pas le chiffrement pour les opérations distantes sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="eea04-125">Indicates that the connection does not use encryption for remote operations over HTTP.</span></span>

<span data-ttu-id="eea04-126">Par défaut, le trafic non chiffré n’est pas activé.</span><span class="sxs-lookup"><span data-stu-id="eea04-126">By default, unencrypted traffic is not enabled.</span></span>
<span data-ttu-id="eea04-127">Elle doit être activée dans la configuration locale.</span><span class="sxs-lookup"><span data-stu-id="eea04-127">It must be enabled in the local configuration.</span></span>

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

### <span data-ttu-id="eea04-128">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="eea04-128">-OperationTimeout</span></span>
<span data-ttu-id="eea04-129">Spécifie le délai d’attente, en millisecondes, pour l’opération de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="eea04-129">Specifies the time-out, in milliseconds, for the WS-Management operation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eea04-130">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="eea04-130">-ProxyAccessType</span></span>
<span data-ttu-id="eea04-131">Spécifie le mécanisme par lequel le serveur proxy est trouvé.</span><span class="sxs-lookup"><span data-stu-id="eea04-131">Specifies the mechanism by which the proxy server is located.</span></span>
<span data-ttu-id="eea04-132">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="eea04-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="eea04-133">ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="eea04-133">ProxyIEConfig.</span></span>
<span data-ttu-id="eea04-134">Utilisez la configuration du proxy Internet Explorer pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="eea04-134">Use the Internet Explorer proxy configuration for the current user.</span></span>
- <span data-ttu-id="eea04-135">ProxyWinHttpConfig.</span><span class="sxs-lookup"><span data-stu-id="eea04-135">ProxyWinHttpConfig.</span></span>
<span data-ttu-id="eea04-136">Le client WSMan utilise les paramètres de proxy configurés pour WinHTTP, à l’aide de l’utilitaire ProxyCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="eea04-136">The WSMan client uses the proxy settings configured for WinHTTP, using the ProxyCfg.exe utility.</span></span>
- <span data-ttu-id="eea04-137">ProxyAutoDetect.</span><span class="sxs-lookup"><span data-stu-id="eea04-137">ProxyAutoDetect.</span></span>
<span data-ttu-id="eea04-138">Force la détection automatique d’un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="eea04-138">Force auto-detection of a proxy server.</span></span>
- <span data-ttu-id="eea04-139">ProxyNoProxyServer.</span><span class="sxs-lookup"><span data-stu-id="eea04-139">ProxyNoProxyServer.</span></span>
<span data-ttu-id="eea04-140">N’utilisez pas de serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="eea04-140">Do not use a proxy server.</span></span>
<span data-ttu-id="eea04-141">Résolvez tous les noms d’hôte localement.</span><span class="sxs-lookup"><span data-stu-id="eea04-141">Resolve all host names locally.</span></span>

<span data-ttu-id="eea04-142">La valeur par défaut est ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="eea04-142">The default value is ProxyIEConfig.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eea04-143">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="eea04-143">-ProxyAuthentication</span></span>
<span data-ttu-id="eea04-144">Spécifie la méthode d'authentification à utiliser au niveau du proxy.</span><span class="sxs-lookup"><span data-stu-id="eea04-144">Specifies the authentication method to use at the proxy.</span></span>
<span data-ttu-id="eea04-145">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="eea04-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="eea04-146">De base.</span><span class="sxs-lookup"><span data-stu-id="eea04-146">Basic.</span></span>
<span data-ttu-id="eea04-147">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="eea04-147">Basic is a scheme in which the user name and password are sent in clear-text to the server or proxy.</span></span>
- <span data-ttu-id="eea04-148">Digest.</span><span class="sxs-lookup"><span data-stu-id="eea04-148">Digest.</span></span>
<span data-ttu-id="eea04-149">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="eea04-149">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="eea04-150">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="eea04-150">Negotiate.</span></span>
<span data-ttu-id="eea04-151">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="eea04-151">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine which scheme to use for authentication.</span></span>
<span data-ttu-id="eea04-152">Le protocole Kerberos et NTLM en sont des exemples.</span><span class="sxs-lookup"><span data-stu-id="eea04-152">Examples are the Kerberos protocol and NTLM.</span></span>

<span data-ttu-id="eea04-153">La valeur par défaut est Negotiate.</span><span class="sxs-lookup"><span data-stu-id="eea04-153">The default value is Negotiate.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eea04-154">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="eea04-154">-ProxyCredential</span></span>
<span data-ttu-id="eea04-155">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder via un proxy Web intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="eea04-155">Specifies a user account that has permission to gain access through an intermediate Web proxy.</span></span>

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

### <span data-ttu-id="eea04-156">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="eea04-156">-SkipCACheck</span></span>
<span data-ttu-id="eea04-157">Spécifie que, lorsqu’il se connecte via HTTPs, le client ne valide pas que le certificat de serveur est signé par une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="eea04-157">Specifies that, when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>
<span data-ttu-id="eea04-158">Utilisez cette option uniquement lorsque l’ordinateur distant est approuvé par une autre méthode, par exemple, si l’ordinateur distant fait partie d’un réseau qui est physiquement sécurisé et isolé ou que l’ordinateur distant est listé comme un hôte approuvé dans la configuration de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="eea04-158">Use this option only when the remote computer is trusted by another method, for example, if the remote computer is part of a network that is physically secure and isolated or the remote computer is listed as a trusted host in the WS-Management configuration.</span></span>

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

### <span data-ttu-id="eea04-159">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="eea04-159">-SkipCNCheck</span></span>
<span data-ttu-id="eea04-160">Spécifie que le nom commun de certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="eea04-160">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="eea04-161">Ce paramètre est utilisé uniquement dans les opérations à distance avec HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eea04-161">This is used only in remote operations using HTTPS.</span></span>
<span data-ttu-id="eea04-162">Cette option ne doit être utilisée que pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="eea04-162">This option should only be used for trusted computers.</span></span>

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

### <span data-ttu-id="eea04-163">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="eea04-163">-SkipRevocationCheck</span></span>
<span data-ttu-id="eea04-164">Indique que la connexion ne valide pas l’état de révocation sur le certificat de serveur.</span><span class="sxs-lookup"><span data-stu-id="eea04-164">Indicates that the connection does not validate the revocation status on the server certificate.</span></span>

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

### <span data-ttu-id="eea04-165">-SPNPort</span><span class="sxs-lookup"><span data-stu-id="eea04-165">-SPNPort</span></span>
<span data-ttu-id="eea04-166">Spécifie un numéro de port à ajouter au nom de principal du service (SPN) de connexion du serveur distant.</span><span class="sxs-lookup"><span data-stu-id="eea04-166">Specifies a port number to append to the connection Service Principal Name (SPN) of the remote server.</span></span>
<span data-ttu-id="eea04-167">Un nom SPN est utilisé quand le mécanisme d'authentification est Kerberos ou par négociation.</span><span class="sxs-lookup"><span data-stu-id="eea04-167">An SPN is used when the authentication mechanism is Kerberos or Negotiate.</span></span>

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

### <span data-ttu-id="eea04-168">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="eea04-168">-UseUTF16</span></span>
<span data-ttu-id="eea04-169">Indique que la connexion encode la demande au format UTF16 au lieu du format UTF8.</span><span class="sxs-lookup"><span data-stu-id="eea04-169">Indicates that the connection encodes the request in UTF16 format instead of UTF8 format.</span></span>
<span data-ttu-id="eea04-170">La valeur par défaut est l'encodage UTF8.</span><span class="sxs-lookup"><span data-stu-id="eea04-170">The default is UTF8 encoding.</span></span>

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

### <span data-ttu-id="eea04-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eea04-171">CommonParameters</span></span>
<span data-ttu-id="eea04-172">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eea04-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eea04-173">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eea04-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eea04-174">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="eea04-174">INPUTS</span></span>

## <span data-ttu-id="eea04-175">SORTIES</span><span class="sxs-lookup"><span data-stu-id="eea04-175">OUTPUTS</span></span>

### <span data-ttu-id="eea04-176">SessionOption</span><span class="sxs-lookup"><span data-stu-id="eea04-176">SessionOption</span></span>

## <span data-ttu-id="eea04-177">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="eea04-177">NOTES</span></span>

## <span data-ttu-id="eea04-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="eea04-178">RELATED LINKS</span></span>

[<span data-ttu-id="eea04-179">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="eea04-179">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="eea04-180">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="eea04-180">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="eea04-181">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="eea04-181">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="eea04-182">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="eea04-182">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="eea04-183">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="eea04-183">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="eea04-184">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="eea04-184">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="eea04-185">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="eea04-185">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="eea04-186">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="eea04-186">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="eea04-187">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="eea04-187">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="eea04-188">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="eea04-188">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="eea04-189">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="eea04-189">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="eea04-190">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="eea04-190">Test-WSMan</span></span>](Test-WSMan.md)
