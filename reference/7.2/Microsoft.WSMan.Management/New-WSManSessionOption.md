---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: e7d7f132eb82dc1a709a88cbdef525aa83d867e4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597331"
---
# <span data-ttu-id="bdce0-102">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="bdce0-102">New-WSManSessionOption</span></span>

## <span data-ttu-id="bdce0-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="bdce0-103">SYNOPSIS</span></span>
<span data-ttu-id="bdce0-104">Crée une table de hachage des options de session à utiliser comme paramètres d’entrée pour les applets de commande WS-Management.</span><span class="sxs-lookup"><span data-stu-id="bdce0-104">Creates session option hash table to use as input parameters for WS-Management cmdlets.</span></span>

## <span data-ttu-id="bdce0-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="bdce0-105">SYNTAX</span></span>

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## <span data-ttu-id="bdce0-106">Description</span><span class="sxs-lookup"><span data-stu-id="bdce0-106">DESCRIPTION</span></span>
<span data-ttu-id="bdce0-107">L’applet **de commande New-WSManSessionOption** crée une table de hachage de l’option de session WSMan qui peut être passée aux applets de commande WSMan :</span><span class="sxs-lookup"><span data-stu-id="bdce0-107">The **New-WSManSessionOption** cmdlet creates a WSMan Session option hash table which can be passed to WSMan cmdlets:</span></span>

- <span data-ttu-id="bdce0-108">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bdce0-108">Get-WSManInstance</span></span>
- <span data-ttu-id="bdce0-109">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bdce0-109">Set-WSManInstance</span></span>
- <span data-ttu-id="bdce0-110">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="bdce0-110">Invoke-WSManAction</span></span>
- <span data-ttu-id="bdce0-111">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="bdce0-111">Connect-WSMan</span></span>

## <span data-ttu-id="bdce0-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="bdce0-112">EXAMPLES</span></span>

### <span data-ttu-id="bdce0-113">Exemple 1 : créer une connexion qui utilise des options de connexion</span><span class="sxs-lookup"><span data-stu-id="bdce0-113">Example 1: Create a connection that uses connection options</span></span>

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

<span data-ttu-id="bdce0-114">Cet exemple crée une connexion à l’ordinateur SERVEUR01 distant à l’aide des options de connexion définies par **New-WSManSessionOption**.</span><span class="sxs-lookup"><span data-stu-id="bdce0-114">This example creates a connection to the remote server01 computer by using the connection options that are defined by **New-WSManSessionOption**.</span></span>

<span data-ttu-id="bdce0-115">La première commande utilise **New-WSManSessionOption** pour stocker un ensemble d’options de paramètres de connexion dans la variable $a.</span><span class="sxs-lookup"><span data-stu-id="bdce0-115">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="bdce0-116">Dans cet exemple, les options de session définissent un délai de connexion de 30 secondes (30 000 millisecondes).</span><span class="sxs-lookup"><span data-stu-id="bdce0-116">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="bdce0-117">La deuxième commande utilise le paramètre *SessionOption* pour transmettre les informations d’identification stockées dans la variable $A à **connect-wsman**.</span><span class="sxs-lookup"><span data-stu-id="bdce0-117">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan**.</span></span>
<span data-ttu-id="bdce0-118">Ensuite, **connect-wsman** se connecte à l’ordinateur SERVEUR01 distant à l’aide des options de session spécifiées.</span><span class="sxs-lookup"><span data-stu-id="bdce0-118">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

<span data-ttu-id="bdce0-119">**Connect-wsman** est généralement utilisé dans le contexte du fournisseur WSMan pour se connecter à un ordinateur distant, dans le cas présent l’ordinateur SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="bdce0-119">**Connect-WSMan** is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="bdce0-120">Toutefois, vous pouvez utiliser l'applet de commande pour établir des connexions aux ordinateurs distants avant de choisir le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="bdce0-120">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="bdce0-121">Ces connexions s’affichent dans la liste **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="bdce0-121">Those connections appear in the **ComputerName** list.</span></span>

## <span data-ttu-id="bdce0-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bdce0-122">PARAMETERS</span></span>

### <span data-ttu-id="bdce0-123">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="bdce0-123">-NoEncryption</span></span>
<span data-ttu-id="bdce0-124">Indique que la connexion n’utilise pas le chiffrement pour les opérations distantes sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="bdce0-124">Indicates that the connection does not use encryption for remote operations over HTTP.</span></span>

<span data-ttu-id="bdce0-125">Par défaut, le trafic non chiffré n’est pas activé.</span><span class="sxs-lookup"><span data-stu-id="bdce0-125">By default, unencrypted traffic is not enabled.</span></span>
<span data-ttu-id="bdce0-126">Elle doit être activée dans la configuration locale.</span><span class="sxs-lookup"><span data-stu-id="bdce0-126">It must be enabled in the local configuration.</span></span>

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

### <span data-ttu-id="bdce0-127">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="bdce0-127">-OperationTimeout</span></span>
<span data-ttu-id="bdce0-128">Spécifie le délai d’attente, en millisecondes, pour l’opération de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="bdce0-128">Specifies the time-out, in milliseconds, for the WS-Management operation.</span></span>

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

### <span data-ttu-id="bdce0-129">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="bdce0-129">-ProxyAccessType</span></span>
<span data-ttu-id="bdce0-130">Spécifie le mécanisme par lequel le serveur proxy est trouvé.</span><span class="sxs-lookup"><span data-stu-id="bdce0-130">Specifies the mechanism by which the proxy server is located.</span></span>
<span data-ttu-id="bdce0-131">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="bdce0-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bdce0-132">ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="bdce0-132">ProxyIEConfig.</span></span>
<span data-ttu-id="bdce0-133">Utilisez la configuration du proxy Internet Explorer pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="bdce0-133">Use the Internet Explorer proxy configuration for the current user.</span></span>
- <span data-ttu-id="bdce0-134">ProxyWinHttpConfig.</span><span class="sxs-lookup"><span data-stu-id="bdce0-134">ProxyWinHttpConfig.</span></span>
<span data-ttu-id="bdce0-135">Le client WSMan utilise les paramètres de proxy configurés pour WinHTTP, à l’aide de l’utilitaire ProxyCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="bdce0-135">The WSMan client uses the proxy settings configured for WinHTTP, using the ProxyCfg.exe utility.</span></span>
- <span data-ttu-id="bdce0-136">ProxyAutoDetect.</span><span class="sxs-lookup"><span data-stu-id="bdce0-136">ProxyAutoDetect.</span></span>
<span data-ttu-id="bdce0-137">Force la détection automatique d’un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="bdce0-137">Force auto-detection of a proxy server.</span></span>
- <span data-ttu-id="bdce0-138">ProxyNoProxyServer.</span><span class="sxs-lookup"><span data-stu-id="bdce0-138">ProxyNoProxyServer.</span></span>
<span data-ttu-id="bdce0-139">N’utilisez pas de serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="bdce0-139">Do not use a proxy server.</span></span>
<span data-ttu-id="bdce0-140">Résolvez tous les noms d’hôte localement.</span><span class="sxs-lookup"><span data-stu-id="bdce0-140">Resolve all host names locally.</span></span>

<span data-ttu-id="bdce0-141">La valeur par défaut est ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="bdce0-141">The default value is ProxyIEConfig.</span></span>

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

### <span data-ttu-id="bdce0-142">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="bdce0-142">-ProxyAuthentication</span></span>
<span data-ttu-id="bdce0-143">Spécifie la méthode d'authentification à utiliser au niveau du proxy.</span><span class="sxs-lookup"><span data-stu-id="bdce0-143">Specifies the authentication method to use at the proxy.</span></span>
<span data-ttu-id="bdce0-144">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="bdce0-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bdce0-145">De base.</span><span class="sxs-lookup"><span data-stu-id="bdce0-145">Basic.</span></span>
<span data-ttu-id="bdce0-146">L'authentification de base est un modèle dans lequel le nom d'utilisateur et le mot de passe sont envoyés en texte clair au serveur ou au proxy.</span><span class="sxs-lookup"><span data-stu-id="bdce0-146">Basic is a scheme in which the user name and password are sent in clear-text to the server or proxy.</span></span>
- <span data-ttu-id="bdce0-147">Digest.</span><span class="sxs-lookup"><span data-stu-id="bdce0-147">Digest.</span></span>
<span data-ttu-id="bdce0-148">Digest est un modèle de stimulation-réponse qui utilise une chaîne de données spécifiée par le serveur pour la stimulation.</span><span class="sxs-lookup"><span data-stu-id="bdce0-148">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="bdce0-149">Negotiate.</span><span class="sxs-lookup"><span data-stu-id="bdce0-149">Negotiate.</span></span>
<span data-ttu-id="bdce0-150">L'authentification par négociation est un modèle de stimulation- réponse qui négocie avec le serveur ou le proxy pour déterminer le modèle à utiliser pour l'authentification.</span><span class="sxs-lookup"><span data-stu-id="bdce0-150">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine which scheme to use for authentication.</span></span>
<span data-ttu-id="bdce0-151">Le protocole Kerberos et NTLM en sont des exemples.</span><span class="sxs-lookup"><span data-stu-id="bdce0-151">Examples are the Kerberos protocol and NTLM.</span></span>

<span data-ttu-id="bdce0-152">La valeur par défaut est Negotiate.</span><span class="sxs-lookup"><span data-stu-id="bdce0-152">The default value is Negotiate.</span></span>

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

### <span data-ttu-id="bdce0-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="bdce0-153">-ProxyCredential</span></span>
<span data-ttu-id="bdce0-154">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder via un proxy Web intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="bdce0-154">Specifies a user account that has permission to gain access through an intermediate Web proxy.</span></span>

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

### <span data-ttu-id="bdce0-155">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="bdce0-155">-SkipCACheck</span></span>
<span data-ttu-id="bdce0-156">Spécifie que, lorsqu’il se connecte via HTTPs, le client ne valide pas que le certificat de serveur est signé par une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="bdce0-156">Specifies that, when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>
<span data-ttu-id="bdce0-157">Utilisez cette option uniquement lorsque l’ordinateur distant est approuvé par une autre méthode, par exemple, si l’ordinateur distant fait partie d’un réseau qui est physiquement sécurisé et isolé ou que l’ordinateur distant est listé comme un hôte approuvé dans la configuration de WS-Management.</span><span class="sxs-lookup"><span data-stu-id="bdce0-157">Use this option only when the remote computer is trusted by another method, for example, if the remote computer is part of a network that is physically secure and isolated or the remote computer is listed as a trusted host in the WS-Management configuration.</span></span>

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

### <span data-ttu-id="bdce0-158">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="bdce0-158">-SkipCNCheck</span></span>
<span data-ttu-id="bdce0-159">Spécifie que le nom commun de certificat du serveur ne doit pas nécessairement correspondre au nom d’hôte du serveur.</span><span class="sxs-lookup"><span data-stu-id="bdce0-159">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="bdce0-160">Ce paramètre est utilisé uniquement dans les opérations à distance avec HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bdce0-160">This is used only in remote operations using HTTPS.</span></span>
<span data-ttu-id="bdce0-161">Cette option ne doit être utilisée que pour les ordinateurs approuvés.</span><span class="sxs-lookup"><span data-stu-id="bdce0-161">This option should only be used for trusted computers.</span></span>

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

### <span data-ttu-id="bdce0-162">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="bdce0-162">-SkipRevocationCheck</span></span>
<span data-ttu-id="bdce0-163">Indique que la connexion ne valide pas l’état de révocation sur le certificat de serveur.</span><span class="sxs-lookup"><span data-stu-id="bdce0-163">Indicates that the connection does not validate the revocation status on the server certificate.</span></span>

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

### <span data-ttu-id="bdce0-164">-SPNPort</span><span class="sxs-lookup"><span data-stu-id="bdce0-164">-SPNPort</span></span>
<span data-ttu-id="bdce0-165">Spécifie un numéro de port à ajouter au nom de principal du service (SPN) de connexion du serveur distant.</span><span class="sxs-lookup"><span data-stu-id="bdce0-165">Specifies a port number to append to the connection Service Principal Name (SPN) of the remote server.</span></span>
<span data-ttu-id="bdce0-166">Un nom SPN est utilisé quand le mécanisme d'authentification est Kerberos ou par négociation.</span><span class="sxs-lookup"><span data-stu-id="bdce0-166">An SPN is used when the authentication mechanism is Kerberos or Negotiate.</span></span>

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

### <span data-ttu-id="bdce0-167">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="bdce0-167">-UseUTF16</span></span>
<span data-ttu-id="bdce0-168">Indique que la connexion encode la demande au format UTF16 au lieu du format UTF8.</span><span class="sxs-lookup"><span data-stu-id="bdce0-168">Indicates that the connection encodes the request in UTF16 format instead of UTF8 format.</span></span>
<span data-ttu-id="bdce0-169">La valeur par défaut est l'encodage UTF8.</span><span class="sxs-lookup"><span data-stu-id="bdce0-169">The default is UTF8 encoding.</span></span>

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

### <span data-ttu-id="bdce0-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bdce0-170">CommonParameters</span></span>
<span data-ttu-id="bdce0-171">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bdce0-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bdce0-172">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bdce0-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bdce0-173">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="bdce0-173">INPUTS</span></span>

## <span data-ttu-id="bdce0-174">SORTIES</span><span class="sxs-lookup"><span data-stu-id="bdce0-174">OUTPUTS</span></span>

### <span data-ttu-id="bdce0-175">SessionOption</span><span class="sxs-lookup"><span data-stu-id="bdce0-175">SessionOption</span></span>

## <span data-ttu-id="bdce0-176">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="bdce0-176">NOTES</span></span>

## <span data-ttu-id="bdce0-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="bdce0-177">RELATED LINKS</span></span>

[<span data-ttu-id="bdce0-178">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="bdce0-178">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="bdce0-179">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bdce0-179">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="bdce0-180">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="bdce0-180">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="bdce0-181">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bdce0-181">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="bdce0-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bdce0-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="bdce0-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bdce0-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="bdce0-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="bdce0-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="bdce0-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bdce0-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="bdce0-186">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bdce0-186">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="bdce0-187">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bdce0-187">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="bdce0-188">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="bdce0-188">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="bdce0-189">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="bdce0-189">Test-WSMan</span></span>](Test-WSMan.md)

