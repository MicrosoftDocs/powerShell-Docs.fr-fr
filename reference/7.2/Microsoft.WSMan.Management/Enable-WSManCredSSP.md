---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: bacafee683fa47d7be331b4e44d2ab75be5bdb23
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597349"
---
# <span data-ttu-id="fee91-102">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="fee91-102">Enable-WSManCredSSP</span></span>

## <span data-ttu-id="fee91-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="fee91-103">SYNOPSIS</span></span>
<span data-ttu-id="fee91-104">Active l’authentification CredSSP (Credential Security Support Provider) sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fee91-104">Enables Credential Security Support Provider (CredSSP) authentication on a computer.</span></span>

## <span data-ttu-id="fee91-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="fee91-105">SYNTAX</span></span>

### <span data-ttu-id="fee91-106">Tous</span><span class="sxs-lookup"><span data-stu-id="fee91-106">All</span></span>

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="fee91-107">Description</span><span class="sxs-lookup"><span data-stu-id="fee91-107">DESCRIPTION</span></span>

<span data-ttu-id="fee91-108">L' `Enable-WSManCredSSP` applet de commande active l’authentification CredSSP sur un client ou sur un ordinateur serveur.</span><span class="sxs-lookup"><span data-stu-id="fee91-108">The `Enable-WSManCredSSP` cmdlet enables CredSSP authentication on a client or on a server computer.</span></span>
<span data-ttu-id="fee91-109">Lorsque l’authentification CredSSP est utilisée, les informations d’identification de l’utilisateur sont transmises à un ordinateur distant pour être authentifiées.</span><span class="sxs-lookup"><span data-stu-id="fee91-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span> <span data-ttu-id="fee91-110">Ce type d’authentification est conçu pour les commandes qui créent une session à distance à partir d’une autre session à distance.</span><span class="sxs-lookup"><span data-stu-id="fee91-110">This type of authentication is designed for commands that create a remote session from another remote session.</span></span> <span data-ttu-id="fee91-111">Par exemple, si vous souhaitez exécuter une tâche en arrière-plan sur un ordinateur distant, utilisez ce type d’authentification.</span><span class="sxs-lookup"><span data-stu-id="fee91-111">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="fee91-112">`Enable-WSManCredSSP` peut activer CredSSP sur un **client** ou un **serveur**.</span><span class="sxs-lookup"><span data-stu-id="fee91-112">`Enable-WSManCredSSP` can enable CredSSP on a **Client** or a **Server**.</span></span> <span data-ttu-id="fee91-113">Pour activer CredSSP sur un client, spécifiez **client** dans le paramètre **role** .</span><span class="sxs-lookup"><span data-stu-id="fee91-113">To enable CredSSP on a client, specify **Client** in the **Role** parameter.</span></span> <span data-ttu-id="fee91-114">Les clients délèguent des informations d’identification explicites à un serveur lorsque l’authentification du serveur est effectuée.</span><span class="sxs-lookup"><span data-stu-id="fee91-114">Clients delegate explicit credentials to a server when server authentication is achieved.</span></span> <span data-ttu-id="fee91-115">Pour activer CredSSP sur un serveur, spécifiez **Server** dans le paramètre **role** .</span><span class="sxs-lookup"><span data-stu-id="fee91-115">To enable CredSSP on a server, specify **Server** in the **Role** parameter.</span></span> <span data-ttu-id="fee91-116">Un serveur agit comme un délégué pour les clients.</span><span class="sxs-lookup"><span data-stu-id="fee91-116">A server acts as a delegate for clients.</span></span> <span data-ttu-id="fee91-117">Pour plus d’informations, consultez **role** dans la section Parameters.</span><span class="sxs-lookup"><span data-stu-id="fee91-117">For more details, see **Role** in the Parameters section.</span></span>

> [!CAUTION]
> <span data-ttu-id="fee91-118">L’authentification CredSSP délègue les informations d’identification de l’utilisateur de l’ordinateur local à un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="fee91-118">CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="fee91-119">Cette pratique augmente le risque de sécurité lié à l'opération distante.</span><span class="sxs-lookup"><span data-stu-id="fee91-119">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="fee91-120">Si l'ordinateur distant n'est pas fiable, les informations d'identification qui lui sont passées peuvent être utilisées pour contrôler la session réseau.</span><span class="sxs-lookup"><span data-stu-id="fee91-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="fee91-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="fee91-121">EXAMPLES</span></span>

### <span data-ttu-id="fee91-122">Exemple 1 : déléguer les informations d’identification du client</span><span class="sxs-lookup"><span data-stu-id="fee91-122">Example 1: Delegate client credentials</span></span>

<span data-ttu-id="fee91-123">Cet exemple permet de déléguer les informations d’identification du client à un ordinateur à l’aide du nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="fee91-123">This example allows the client credentials to be delegated to a computer by using the fully qualified domain name.</span></span>

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

### <span data-ttu-id="fee91-124">Exemple 2 : déléguer les informations d’identification du client à tous les ordinateurs d’un domaine</span><span class="sxs-lookup"><span data-stu-id="fee91-124">Example 2: Delegate client credentials to all computers in a domain</span></span>

<span data-ttu-id="fee91-125">Cet exemple permet de déléguer les informations d’identification du client à tous les ordinateurs du domaine **fabrikam.com** .</span><span class="sxs-lookup"><span data-stu-id="fee91-125">This example allows the client credentials to be delegated to all the computers in the **fabrikam.com** domain.</span></span> <span data-ttu-id="fee91-126">Le `*` caractère générique astérisque () spécifie tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="fee91-126">The asterisk (`*`) wildcard specifies all computers.</span></span>

> [!NOTE]
> <span data-ttu-id="fee91-127">L’utilisation de caractères génériques avec le paramètre **delegatecomputer** peut activer CredSSP sur plus d’ordinateurs que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fee91-127">Using wildcards with the **DelegateComputer** parameter can enable CredSSP on more computers than necessary.</span></span>

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

### <span data-ttu-id="fee91-128">Exemple 3 : déléguer les informations d’identification du client à plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="fee91-128">Example 3: Delegate client credentials to multiple computers</span></span>

<span data-ttu-id="fee91-129">Cet exemple permet de déléguer les informations d’identification du client à plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="fee91-129">This example allows the client credentials to be delegated to multiple computers.</span></span>

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

<span data-ttu-id="fee91-130">La `$servers` variable contient une liste de noms de serveurs.</span><span class="sxs-lookup"><span data-stu-id="fee91-130">The `$servers` variable contains a list of server names.</span></span> <span data-ttu-id="fee91-131">`Enable-WSManCredSSP` utilise le paramètre **role** pour spécifier le rôle **client** .</span><span class="sxs-lookup"><span data-stu-id="fee91-131">`Enable-WSManCredSSP` uses the **Role** parameter to specify the **Client** role.</span></span> <span data-ttu-id="fee91-132">**Delegatecomputer** obtient les noms d’ordinateur à partir de la `$servers` variable.</span><span class="sxs-lookup"><span data-stu-id="fee91-132">The **DelegateComputer** gets the computer names from the `$servers` variable.</span></span>

### <span data-ttu-id="fee91-133">Exemple 4 : autoriser un ordinateur à agir en tant que délégué</span><span class="sxs-lookup"><span data-stu-id="fee91-133">Example 4: Allow a computer to act as a delegate</span></span>

<span data-ttu-id="fee91-134">Cet exemple permet à un ordinateur d’agir en tant que délégué pour un autre.</span><span class="sxs-lookup"><span data-stu-id="fee91-134">This example allows a computer to act as a delegate for another.</span></span> <span data-ttu-id="fee91-135">L' `Enable-WSManCredSSP` applet de commande, illustrée dans les exemples précédents, active uniquement l’authentification CredSSP sur le client et spécifie les ordinateurs distants qui peuvent agir en son nom.</span><span class="sxs-lookup"><span data-stu-id="fee91-135">The `Enable-WSManCredSSP` cmdlet, shown in the earlier examples, only enables CredSSP authentication on the client, and specifies the remote computers that can act on its behalf.</span></span> <span data-ttu-id="fee91-136">Pour que l’ordinateur distant agisse en tant que délégué pour le client, l’élément CredSSP dans le nœud **service** de wsman doit avoir la valeur true.</span><span class="sxs-lookup"><span data-stu-id="fee91-136">In order for the remote computer to act as a delegate for the client, the CredSSP item in the **Service** node of WSMan must be set to true.</span></span> <span data-ttu-id="fee91-137">Cet exemple affecte la valeur true à l’élément CredSSP dans le nœud **service** de wsman.</span><span class="sxs-lookup"><span data-stu-id="fee91-137">This example sets the CredSSP item in the **Service** node of WSMan to true.</span></span>

```powershell
Enable-WSManCredSSP -Role "Server"
```

### <span data-ttu-id="fee91-138">Exemple 5 : autoriser un ordinateur à agir en tant que délégué à l’aide d' Set-Item</span><span class="sxs-lookup"><span data-stu-id="fee91-138">Example 5: Allow a computer to act as a delegate by using Set-Item</span></span>

<span data-ttu-id="fee91-139">Cet exemple permet à un ordinateur d’agir en tant que délégué pour un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fee91-139">This example allows a computer to act as a delegate for another computer.</span></span> <span data-ttu-id="fee91-140">Les `Enable-WSManCredSSP` commandes, présentées dans les exemples précédents, activent l’authentification CredSSP uniquement sur l’ordinateur client et spécifient les ordinateurs distants qui peuvent agir au nom de l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="fee91-140">The `Enable-WSManCredSSP` commands, shown in the earlier examples, enable CredSSP authentication only on the client computer, and they specify the remote computers that can act on behalf of the client computer.</span></span> <span data-ttu-id="fee91-141">Pour que l'ordinateur distant agisse en tant que délégué pour l'ordinateur client, l'élément CredSSP dans le répertoire Service du fournisseur WSMan doit avoir la valeur true.</span><span class="sxs-lookup"><span data-stu-id="fee91-141">For the remote computer to act as a delegate for the client computer, the CredSSP item in the Service directory of the WSMan provider must be set to true.</span></span>

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

<span data-ttu-id="fee91-142">`Connect-WSMan` crée une connexion à l’ordinateur distant, Server02.</span><span class="sxs-lookup"><span data-stu-id="fee91-142">`Connect-WSMan` creates a connection to the remote computer, server02.</span></span> <span data-ttu-id="fee91-143">`Set-Item` utilise le paramètre **path** pour spécifier l’emplacement du fournisseur **WSMan** .</span><span class="sxs-lookup"><span data-stu-id="fee91-143">`Set-Item` uses the **Path** parameter to specify the **WSMan** provider's location.</span></span> <span data-ttu-id="fee91-144">Le paramètre **value** définit le paramètre de **service** sur true.</span><span class="sxs-lookup"><span data-stu-id="fee91-144">The **Value** parameter sets the **Service** setting to true.</span></span>

## <span data-ttu-id="fee91-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fee91-145">PARAMETERS</span></span>

### <span data-ttu-id="fee91-146">-DelegateComputer</span><span class="sxs-lookup"><span data-stu-id="fee91-146">-DelegateComputer</span></span>

<span data-ttu-id="fee91-147">Spécifie les serveurs auxquels les informations d’identification du client sont déléguées.</span><span class="sxs-lookup"><span data-stu-id="fee91-147">Specifies servers to which client credentials are delegated.</span></span> <span data-ttu-id="fee91-148">La meilleure pratique consiste à utiliser des noms de domaine complets.</span><span class="sxs-lookup"><span data-stu-id="fee91-148">The best practice is to use fully qualified domain names.</span></span>

<span data-ttu-id="fee91-149">Les caractères génériques sont acceptés, mais peuvent activer CredSSP sur plus d’ordinateurs que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fee91-149">Wildcards are accepted, but can enable CredSSP on more computers than necessary.</span></span>

<span data-ttu-id="fee91-150">Si le paramètre **role** est **client**, vous devez spécifier ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="fee91-150">If the **Role** parameter is **Client**, you must specify this parameter.</span></span> <span data-ttu-id="fee91-151">Si le **rôle** est **serveur**, ne spécifiez pas ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="fee91-151">If **Role** is **Server**, don't specify this parameter.</span></span>

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

### <span data-ttu-id="fee91-152">-Force</span><span class="sxs-lookup"><span data-stu-id="fee91-152">-Force</span></span>

<span data-ttu-id="fee91-153">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fee91-153">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="fee91-154">-Rôle</span><span class="sxs-lookup"><span data-stu-id="fee91-154">-Role</span></span>

<span data-ttu-id="fee91-155">Spécifie s’il faut activer CredSSP en tant que client ou serveur.</span><span class="sxs-lookup"><span data-stu-id="fee91-155">Specifies whether to enable CredSSP as a client or as a server.</span></span> <span data-ttu-id="fee91-156">Les valeurs acceptables pour ce paramètre sont : **client** et **serveur**.</span><span class="sxs-lookup"><span data-stu-id="fee91-156">The acceptable values for this parameter are: **Client** and **Server**.</span></span>

<span data-ttu-id="fee91-157">Si vous spécifiez **client**, les actions suivantes sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="fee91-157">If you specify **Client**, the following actions are performed.</span></span> <span data-ttu-id="fee91-158">Ces paramètres permettent au client de déléguer les informations d'identification explicites à un serveur quand l'authentification du serveur est effectuée.</span><span class="sxs-lookup"><span data-stu-id="fee91-158">These settings allow the client to delegate explicit credentials to a server when server authentication is achieved.</span></span>

- <span data-ttu-id="fee91-159">Active CredSSP sur le client.</span><span class="sxs-lookup"><span data-stu-id="fee91-159">Enables CredSSP on the client.</span></span>
- <span data-ttu-id="fee91-160">Affecte la valeur true au paramètre WS-Management `\<localhost|computername\>\Client\Auth\CredSSP` .</span><span class="sxs-lookup"><span data-stu-id="fee91-160">Sets the WS-Management setting `\<localhost|computername\>\Client\Auth\CredSSP` to true.</span></span>
- <span data-ttu-id="fee91-161">Définit la stratégie Windows CredSSP **AllowFreshCredentials** sur **WSMan/Delegate** sur le client.</span><span class="sxs-lookup"><span data-stu-id="fee91-161">Sets the Windows CredSSP policy **AllowFreshCredentials** to **WSMan/Delegate** on the client.</span></span>

<span data-ttu-id="fee91-162">Si vous spécifiez **Server**, les actions suivantes sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="fee91-162">If you specify **Server**, the following actions are performed.</span></span> <span data-ttu-id="fee91-163">Ce paramètre de stratégie permet au serveur d'agir en tant que délégué pour les clients.</span><span class="sxs-lookup"><span data-stu-id="fee91-163">This policy setting allows the server to act as a delegate for clients.</span></span>

- <span data-ttu-id="fee91-164">Active CredSSP sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fee91-164">Enables CredSSP on the server.</span></span>
- <span data-ttu-id="fee91-165">Affecte la valeur true au paramètre WS-Management `\<localhost|computername\>\Service\Auth\CredSSP` .</span><span class="sxs-lookup"><span data-stu-id="fee91-165">Sets the WS-Management setting `\<localhost|computername\>\Service\Auth\CredSSP` to true.</span></span>

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

### <span data-ttu-id="fee91-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fee91-166">CommonParameters</span></span>

<span data-ttu-id="fee91-167">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fee91-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fee91-168">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fee91-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fee91-169">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="fee91-169">INPUTS</span></span>

### <span data-ttu-id="fee91-170">None</span><span class="sxs-lookup"><span data-stu-id="fee91-170">None</span></span>

<span data-ttu-id="fee91-171">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="fee91-171">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="fee91-172">SORTIES</span><span class="sxs-lookup"><span data-stu-id="fee91-172">OUTPUTS</span></span>

### <span data-ttu-id="fee91-173">Élément System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="fee91-173">System.Xml.XmlElement</span></span>

<span data-ttu-id="fee91-174">Si l’authentification CredSSP est correctement activée, cette applet de commande génère un objet **XmlElement** .</span><span class="sxs-lookup"><span data-stu-id="fee91-174">If CredSSP authentication is successfully enabled, this cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="fee91-175">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="fee91-175">NOTES</span></span>

<span data-ttu-id="fee91-176">Pour désactiver l’authentification CredSSP, utilisez l’applet de commande `Disable-WSManCredSSP` .</span><span class="sxs-lookup"><span data-stu-id="fee91-176">To disable CredSSP authentication, use the `Disable-WSManCredSSP` cmdlet.</span></span>

## <span data-ttu-id="fee91-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="fee91-177">RELATED LINKS</span></span>

[<span data-ttu-id="fee91-178">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="fee91-178">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="fee91-179">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="fee91-179">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="fee91-180">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="fee91-180">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="fee91-181">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="fee91-181">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="fee91-182">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fee91-182">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="fee91-183">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="fee91-183">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="fee91-184">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fee91-184">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="fee91-185">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="fee91-185">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="fee91-186">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fee91-186">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="fee91-187">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="fee91-187">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="fee91-188">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="fee91-188">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="fee91-189">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="fee91-189">Test-WSMan</span></span>](Test-WSMan.md)

