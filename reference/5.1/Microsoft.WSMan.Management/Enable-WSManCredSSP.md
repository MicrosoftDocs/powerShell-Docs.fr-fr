---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 3dd2aa9c1f35de80d86dde508aaa9a3c964dff05
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208689"
---
# <span data-ttu-id="a0ea2-103">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a0ea2-103">Enable-WSManCredSSP</span></span>

## <span data-ttu-id="a0ea2-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a0ea2-104">SYNOPSIS</span></span>
<span data-ttu-id="a0ea2-105">Active l’authentification CredSSP (Credential Security Support Provider) sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-105">Enables Credential Security Support Provider (CredSSP) authentication on a computer.</span></span>

## <span data-ttu-id="a0ea2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0ea2-106">SYNTAX</span></span>

### <span data-ttu-id="a0ea2-107">Tous</span><span class="sxs-lookup"><span data-stu-id="a0ea2-107">All</span></span>

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="a0ea2-108">Description</span><span class="sxs-lookup"><span data-stu-id="a0ea2-108">DESCRIPTION</span></span>

<span data-ttu-id="a0ea2-109">L' `Enable-WSManCredSSP` applet de commande active l’authentification CredSSP sur un client ou sur un ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-109">The `Enable-WSManCredSSP` cmdlet enables CredSSP authentication on a client or on a server computer.</span></span>
<span data-ttu-id="a0ea2-110">Lorsque l’authentification CredSSP est utilisée, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-110">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span> <span data-ttu-id="a0ea2-111">Ce type d’authentification est conçu pour les commandes qui créent une session à distance à partir d’une autre session à distance.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span> <span data-ttu-id="a0ea2-112">Par exemple, si vous souhaitez exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez ce type d’authentification.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="a0ea2-113">`Enable-WSManCredSSP` peut activer CredSSP sur un **client** ou un **serveur** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-113">`Enable-WSManCredSSP` can enable CredSSP on a **Client** or a **Server** .</span></span> <span data-ttu-id="a0ea2-114">Pour activer CredSSP sur un client, spécifiez **client** dans le paramètre **role** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-114">To enable CredSSP on a client, specify **Client** in the **Role** parameter.</span></span> <span data-ttu-id="a0ea2-115">Les clients délèguent des informations d’identification explicites à un serveur lorsque l’authentification du serveur est effectuée.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-115">Clients delegate explicit credentials to a server when server authentication is achieved.</span></span> <span data-ttu-id="a0ea2-116">Pour activer CredSSP sur un serveur, spécifiez **Server** dans le paramètre **role** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-116">To enable CredSSP on a server, specify **Server** in the **Role** parameter.</span></span> <span data-ttu-id="a0ea2-117">Un serveur agit comme un délégué pour les clients.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-117">A server acts as a delegate for clients.</span></span> <span data-ttu-id="a0ea2-118">Pour plus d’informations, consultez **role** dans la section Parameters.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-118">For more details, see **Role** in the Parameters section.</span></span>

> [!CAUTION]
> <span data-ttu-id="a0ea2-119">L’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-119">CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="a0ea2-120">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-120">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="a0ea2-121">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="a0ea2-122">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a0ea2-122">EXAMPLES</span></span>

### <span data-ttu-id="a0ea2-123">Exemple 1 : déléguer les informations d’identification du client</span><span class="sxs-lookup"><span data-stu-id="a0ea2-123">Example 1: Delegate client credentials</span></span>

<span data-ttu-id="a0ea2-124">Cet exemple permet de déléguer les informations d’identification du client à un ordinateur à l’aide du nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-124">This example allows the client credentials to be delegated to a computer by using the fully qualified domain name.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="a0ea2-125">Exemple 2 : déléguer les informations d’identification du client à tous les ordinateurs d’un domaine</span><span class="sxs-lookup"><span data-stu-id="a0ea2-125">Example 2: Delegate client credentials to all computers in a domain</span></span>

<span data-ttu-id="a0ea2-126">Cet exemple permet de déléguer les informations d’identification du client à tous les ordinateurs du domaine **fabrikam.com** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-126">This example allows the client credentials to be delegated to all the computers in the **fabrikam.com** domain.</span></span> <span data-ttu-id="a0ea2-127">Le `*` caractère générique astérisque () spécifie tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-127">The asterisk (`*`) wildcard specifies all computers.</span></span>

> [!NOTE]
> <span data-ttu-id="a0ea2-128">L’utilisation de caractères génériques avec le paramètre **delegatecomputer** peut activer CredSSP sur plus d’ordinateurs que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-128">Using wildcards with the **DelegateComputer** parameter can enable CredSSP on more computers than necessary.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="a0ea2-129">Exemple 3 : déléguer les informations d’identification du client à plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="a0ea2-129">Example 3: Delegate client credentials to multiple computers</span></span>

<span data-ttu-id="a0ea2-130">Cet exemple permet de déléguer les informations d’identification du client à plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-130">This example allows the client credentials to be delegated to multiple computers.</span></span>

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

<span data-ttu-id="a0ea2-131">La `$servers` variable contient une liste de noms de serveurs.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-131">The `$servers` variable contains a list of server names.</span></span> <span data-ttu-id="a0ea2-132">`Enable-WSManCredSSP` utilise le paramètre **role** pour spécifier le rôle **client** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-132">`Enable-WSManCredSSP` uses the **Role** parameter to specify the **Client** role.</span></span> <span data-ttu-id="a0ea2-133">**Delegatecomputer** obtient les noms d’ordinateur à partir de la `$servers` variable.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-133">The **DelegateComputer** gets the computer names from the `$servers` variable.</span></span>

### <span data-ttu-id="a0ea2-134">Exemple 4 : autoriser un ordinateur à agir en tant que délégué</span><span class="sxs-lookup"><span data-stu-id="a0ea2-134">Example 4: Allow a computer to act as a delegate</span></span>

<span data-ttu-id="a0ea2-135">Cet exemple permet à un ordinateur d’agir en tant que délégué pour un autre.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-135">This example allows a computer to act as a delegate for another.</span></span> <span data-ttu-id="a0ea2-136">L' `Enable-WSManCredSSP` applet de commande, illustrée dans les exemples précédents, active uniquement l’authentification CredSSP sur le client et spécifie les ordinateurs distants qui peuvent agir en son nom.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-136">The `Enable-WSManCredSSP` cmdlet, shown in the earlier examples, only enables CredSSP authentication on the client, and specifies the remote computers that can act on its behalf.</span></span> <span data-ttu-id="a0ea2-137">Pour que l’ordinateur distant agisse en tant que délégué pour le client, l’élément CredSSP dans le nœud **service** de wsman doit avoir la valeur true.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-137">In order for the remote computer to act as a delegate for the client, the CredSSP item in the **Service** node of WSMan must be set to true.</span></span> <span data-ttu-id="a0ea2-138">Cet exemple affecte la valeur true à l’élément CredSSP dans le nœud **service** de wsman.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-138">This example sets the CredSSP item in the **Service** node of WSMan to true.</span></span>

```powershell
Enable-WSManCredSSP -Role "Server"
```

### <span data-ttu-id="a0ea2-139">Exemple 5 : autoriser un ordinateur à agir en tant que délégué à l’aide d' Set-Item</span><span class="sxs-lookup"><span data-stu-id="a0ea2-139">Example 5: Allow a computer to act as a delegate by using Set-Item</span></span>

<span data-ttu-id="a0ea2-140">Cet exemple permet à un ordinateur d’agir en tant que délégué pour un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-140">This example allows a computer to act as a delegate for another computer.</span></span> <span data-ttu-id="a0ea2-141">Les `Enable-WSManCredSSP` commandes, présentées dans les exemples précédents, activent l’authentification CredSSP uniquement sur l’ordinateur client et spécifient les ordinateurs distants qui peuvent agir au nom de l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-141">The `Enable-WSManCredSSP` commands, shown in the earlier examples, enable CredSSP authentication only on the client computer, and they specify the remote computers that can act on behalf of the client computer.</span></span> <span data-ttu-id="a0ea2-142">Pour que l'ordinateur distant agisse en tant que délégué pour l'ordinateur client, l'élément CredSSP dans le répertoire Service du fournisseur WSMan doit avoir la valeur true.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-142">For the remote computer to act as a delegate for the client computer, the CredSSP item in the Service directory of the WSMan provider must be set to true.</span></span>

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

<span data-ttu-id="a0ea2-143">`Connect-WSMan` crée une connexion à l’ordinateur distant, Server02.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-143">`Connect-WSMan` creates a connection to the remote computer, server02.</span></span> <span data-ttu-id="a0ea2-144">`Set-Item` utilise le paramètre **path** pour spécifier l’emplacement du fournisseur **WSMan** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-144">`Set-Item` uses the **Path** parameter to specify the **WSMan** provider's location.</span></span> <span data-ttu-id="a0ea2-145">Le paramètre **value** définit le paramètre de **service** sur true.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-145">The **Value** parameter sets the **Service** setting to true.</span></span>

## <span data-ttu-id="a0ea2-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0ea2-146">PARAMETERS</span></span>

### <span data-ttu-id="a0ea2-147">-DelegateComputer</span><span class="sxs-lookup"><span data-stu-id="a0ea2-147">-DelegateComputer</span></span>

<span data-ttu-id="a0ea2-148">Spécifie les serveurs auxquels les informations d’identification du client sont déléguées.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-148">Specifies servers to which client credentials are delegated.</span></span> <span data-ttu-id="a0ea2-149">La meilleure pratique consiste à utiliser des noms de domaine complets.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-149">The best practice is to use fully qualified domain names.</span></span>

<span data-ttu-id="a0ea2-150">Les caractères génériques sont acceptés, mais peuvent activer CredSSP sur plus d’ordinateurs que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-150">Wildcards are accepted, but can enable CredSSP on more computers than necessary.</span></span>

<span data-ttu-id="a0ea2-151">Si le paramètre **role** est **client** , vous devez spécifier ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-151">If the **Role** parameter is **Client** , you must specify this parameter.</span></span> <span data-ttu-id="a0ea2-152">Si le **rôle** est **serveur** , ne spécifiez pas ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-152">If **Role** is **Server** , don't specify this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a0ea2-153">-Force</span><span class="sxs-lookup"><span data-stu-id="a0ea2-153">-Force</span></span>

<span data-ttu-id="a0ea2-154">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-154">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0ea2-155">-Rôle</span><span class="sxs-lookup"><span data-stu-id="a0ea2-155">-Role</span></span>

<span data-ttu-id="a0ea2-156">Spécifie s’il faut activer CredSSP en tant que client ou serveur.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-156">Specifies whether to enable CredSSP as a client or as a server.</span></span> <span data-ttu-id="a0ea2-157">Les valeurs acceptables pour ce paramètre sont : **client** et **serveur** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-157">The acceptable values for this parameter are: **Client** and **Server** .</span></span>

<span data-ttu-id="a0ea2-158">Si vous spécifiez **client** , les actions suivantes sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-158">If you specify **Client** , the following actions are performed.</span></span> <span data-ttu-id="a0ea2-159">Ces paramètres permettent au client de déléguer les informations d'identification explicites à un serveur quand l'authentification du serveur est effectuée.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-159">These settings allow the client to delegate explicit credentials to a server when server authentication is achieved.</span></span>

- <span data-ttu-id="a0ea2-160">Active CredSSP sur le client.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-160">Enables CredSSP on the client.</span></span>
- <span data-ttu-id="a0ea2-161">Affecte la valeur true au paramètre WS-Management `\<localhost|computername\>\Client\Auth\CredSSP` .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-161">Sets the WS-Management setting `\<localhost|computername\>\Client\Auth\CredSSP` to true.</span></span>
- <span data-ttu-id="a0ea2-162">Définit la stratégie Windows CredSSP **AllowFreshCredentials** sur **WSMan/Delegate** sur le client.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-162">Sets the Windows CredSSP policy **AllowFreshCredentials** to **WSMan/Delegate** on the client.</span></span>

<span data-ttu-id="a0ea2-163">Si vous spécifiez **Server** , les actions suivantes sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-163">If you specify **Server** , the following actions are performed.</span></span> <span data-ttu-id="a0ea2-164">Ce paramètre de stratégie permet au serveur d'agir en tant que délégué pour les clients.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-164">This policy setting allows the server to act as a delegate for clients.</span></span>

- <span data-ttu-id="a0ea2-165">Active CredSSP sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-165">Enables CredSSP on the server.</span></span>
- <span data-ttu-id="a0ea2-166">Affecte la valeur true au paramètre WS-Management `\<localhost|computername\>\Service\Auth\CredSSP` .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-166">Sets the WS-Management setting `\<localhost|computername\>\Service\Auth\CredSSP` to true.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0ea2-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0ea2-167">CommonParameters</span></span>

<span data-ttu-id="a0ea2-168">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0ea2-169">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a0ea2-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0ea2-170">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a0ea2-170">INPUTS</span></span>

### <span data-ttu-id="a0ea2-171">Aucun</span><span class="sxs-lookup"><span data-stu-id="a0ea2-171">None</span></span>

<span data-ttu-id="a0ea2-172">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-172">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="a0ea2-173">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a0ea2-173">OUTPUTS</span></span>

### <span data-ttu-id="a0ea2-174">Élément System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="a0ea2-174">System.Xml.XmlElement</span></span>

<span data-ttu-id="a0ea2-175">Si l’authentification CredSSP est correctement activée, cette applet de commande génère un objet **XmlElement** .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-175">If CredSSP authentication is successfully enabled, this cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="a0ea2-176">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a0ea2-176">NOTES</span></span>

<span data-ttu-id="a0ea2-177">Pour désactiver l’authentification CredSSP, utilisez l’applet de commande `Disable-WSManCredSSP` .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-177">To disable CredSSP authentication, use the `Disable-WSManCredSSP` cmdlet.</span></span>

## <span data-ttu-id="a0ea2-178">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a0ea2-178">RELATED LINKS</span></span>

[<span data-ttu-id="a0ea2-179">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a0ea2-179">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="a0ea2-180">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a0ea2-180">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="a0ea2-181">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="a0ea2-181">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="a0ea2-182">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="a0ea2-182">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="a0ea2-183">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0ea2-183">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="a0ea2-184">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="a0ea2-184">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="a0ea2-185">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0ea2-185">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="a0ea2-186">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="a0ea2-186">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="a0ea2-187">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0ea2-187">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="a0ea2-188">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="a0ea2-188">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="a0ea2-189">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="a0ea2-189">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="a0ea2-190">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="a0ea2-190">Test-WSMan</span></span>](Test-WSMan.md)
