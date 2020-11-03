---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: a754b6530ecd8b3153d82327a246cbb387d53dd5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201702"
---
# <span data-ttu-id="36a90-103">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="36a90-103">Disconnect-WSMan</span></span>

## <span data-ttu-id="36a90-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="36a90-104">SYNOPSIS</span></span>
<span data-ttu-id="36a90-105">Déconnecte le client du service WinRM sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="36a90-105">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="36a90-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36a90-106">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="36a90-107">Description</span><span class="sxs-lookup"><span data-stu-id="36a90-107">DESCRIPTION</span></span>
<span data-ttu-id="36a90-108">L’applet de commande Disconnect **-WSMan** déconnecte le client du service WinRM sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="36a90-108">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="36a90-109">Si vous avez enregistré la session de WS-Management dans une variable, l’objet de session reste dans la variable, mais l’état de la session de WS-Management est fermé.</span><span class="sxs-lookup"><span data-stu-id="36a90-109">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="36a90-110">Vous pouvez utiliser cette applet de commande dans le contexte du fournisseur WSMan pour déconnecter le client du service WinRM sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="36a90-110">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="36a90-111">Toutefois, vous pouvez également utiliser cette applet de commande pour vous déconnecter du service WinRM sur les ordinateurs distants avant de choisir le fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="36a90-111">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="36a90-112">Pour plus d'informations sur la façon de se connecter au service WinRM sur un ordinateur distant, consultez Connect-WSMan.</span><span class="sxs-lookup"><span data-stu-id="36a90-112">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="36a90-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="36a90-113">EXAMPLES</span></span>

### <span data-ttu-id="36a90-114">Exemple 1 : supprimer une connexion à un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="36a90-114">Example 1: Delete a connection to a remote computer</span></span>

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

<span data-ttu-id="36a90-115">Cette commande supprime la connexion à l’ordinateur distant nommé SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="36a90-115">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="36a90-116">Cette applet de commande est généralement utilisée dans le contexte du fournisseur WSMan pour se déconnecter d'un ordinateur distant, dans ce cas l'ordinateur server01.</span><span class="sxs-lookup"><span data-stu-id="36a90-116">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="36a90-117">Toutefois, vous pouvez également utiliser **Disconnect-WSMan** pour supprimer les connexions aux ordinateurs distants avant de passer au fournisseur WSMan.</span><span class="sxs-lookup"><span data-stu-id="36a90-117">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="36a90-118">Ces connexions n’apparaissent pas dans la liste ComputerName.</span><span class="sxs-lookup"><span data-stu-id="36a90-118">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="36a90-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36a90-119">PARAMETERS</span></span>

### <span data-ttu-id="36a90-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="36a90-120">-ComputerName</span></span>
<span data-ttu-id="36a90-121">Spécifie l’ordinateur sur lequel exécuter l’opération de gestion.</span><span class="sxs-lookup"><span data-stu-id="36a90-121">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="36a90-122">La valeur peut être un nom de domaine complet, un nom NetBIOS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="36a90-122">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="36a90-123">Utilisez le nom de l'ordinateur local, localhost ou un point (.) pour spécifier l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="36a90-123">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="36a90-124">L'ordinateur local est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="36a90-124">The local computer is the default.</span></span>
<span data-ttu-id="36a90-125">Quand l'ordinateur distant est dans un domaine différent de celui de l'utilisateur, vous devez utiliser un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="36a90-125">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="36a90-126">Vous pouvez acheminer par canal une valeur de ce paramètre vers l'applet de commande.</span><span class="sxs-lookup"><span data-stu-id="36a90-126">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="36a90-127">Vous ne pouvez pas vous déconnecter de l’hôte local.</span><span class="sxs-lookup"><span data-stu-id="36a90-127">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="36a90-128">Autrement dit, vous ne pouvez pas déconnecter la connexion par défaut à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="36a90-128">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="36a90-129">Toutefois, si vous créez une connexion distincte à l’ordinateur local, par exemple, en utilisant le nom de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="36a90-129">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a90-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36a90-130">CommonParameters</span></span>
<span data-ttu-id="36a90-131">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36a90-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36a90-132">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="36a90-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36a90-133">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="36a90-133">INPUTS</span></span>

### <span data-ttu-id="36a90-134">Aucun</span><span class="sxs-lookup"><span data-stu-id="36a90-134">None</span></span>
<span data-ttu-id="36a90-135">Cette applet de commande n’accepte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="36a90-135">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="36a90-136">SORTIES</span><span class="sxs-lookup"><span data-stu-id="36a90-136">OUTPUTS</span></span>

### <span data-ttu-id="36a90-137">Aucun</span><span class="sxs-lookup"><span data-stu-id="36a90-137">None</span></span>
<span data-ttu-id="36a90-138">Cette applet de commande ne génère aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="36a90-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="36a90-139">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="36a90-139">NOTES</span></span>

## <span data-ttu-id="36a90-140">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="36a90-140">RELATED LINKS</span></span>

[<span data-ttu-id="36a90-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="36a90-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="36a90-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="36a90-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="36a90-143">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="36a90-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="36a90-144">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="36a90-144">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="36a90-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="36a90-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="36a90-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="36a90-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="36a90-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="36a90-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="36a90-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="36a90-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="36a90-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="36a90-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="36a90-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="36a90-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="36a90-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="36a90-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="36a90-152">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="36a90-152">Test-WSMan</span></span>](Test-WSMan.md)
