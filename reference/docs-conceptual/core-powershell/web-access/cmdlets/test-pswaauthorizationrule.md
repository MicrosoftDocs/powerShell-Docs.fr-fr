---
ms.topic: reference
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="c9e7e-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c9e7e-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="c9e7e-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="c9e7e-104">SYNOPSIS</span></span>

<span data-ttu-id="c9e7e-105">Vérifie si une règle existe pour un utilisateur, un ordinateur ou un point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9e7e-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="c9e7e-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="c9e7e-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c9e7e-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="c9e7e-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="c9e7e-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="c9e7e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c9e7e-109">DESCRIPTION</span></span>

<span data-ttu-id="c9e7e-110">L’applet de commande **Test-PswaAuthorizationRule** vérifie si une règle existe pour un utilisateur, un ordinateur ou un point de terminaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="c9e7e-111">Cette applet de commande peut également être utilisé pour tester les règles d’autorisation, ou pour vérifier qu’une demande d’accès d’un utilisateur, d’un ordinateur ou d’un point de terminaison particulier est autorisée.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="c9e7e-112">Par défaut, cette applet de commande évalue toutes les règles du fichier d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="c9e7e-113">Vous pouvez cependant spécifier un sous-ensemble de règles à tester.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="c9e7e-114">Vous pouvez utiliser cette applet de commande pour résoudre les problèmes liés aux échecs d’authentification.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="c9e7e-115">Les paramètres de cette applet de commande correspondent aux champs de la page de connexion d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="c9e7e-116">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="c9e7e-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="c9e7e-117">-ComputerName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="c9e7e-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="c9e7e-118">Spécifie le nom de l’ordinateur à tester.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="c9e7e-119">Alias</span><span class="sxs-lookup"><span data-stu-id="c9e7e-119">Aliases</span></span>                              | <span data-ttu-id="c9e7e-120">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-120">none</span></span>                                 |
| <span data-ttu-id="c9e7e-121">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-121">Required?</span></span>                            | <span data-ttu-id="c9e7e-122">true</span><span class="sxs-lookup"><span data-stu-id="c9e7e-122">true</span></span>                                 |
| <span data-ttu-id="c9e7e-123">Position ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-123">Position?</span></span>                            | <span data-ttu-id="c9e7e-124">2</span><span class="sxs-lookup"><span data-stu-id="c9e7e-124">2</span></span>                                    |
| <span data-ttu-id="c9e7e-125">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c9e7e-125">Default Value</span></span>                        | <span data-ttu-id="c9e7e-126">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-126">none</span></span>                                 |
| <span data-ttu-id="c9e7e-127">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c9e7e-128">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-128">false</span></span>                                |
| <span data-ttu-id="c9e7e-129">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c9e7e-130">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="c9e7e-131">-ConfigurationName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="c9e7e-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="c9e7e-132">Spécifie le nom de la configuration de session Windows PowerShell, également appelée point de terminaison ou instance d’exécution, à tester.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="c9e7e-133">Alias</span><span class="sxs-lookup"><span data-stu-id="c9e7e-133">Aliases</span></span>                              | <span data-ttu-id="c9e7e-134">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-134">none</span></span>                                 |
| <span data-ttu-id="c9e7e-135">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-135">Required?</span></span>                            | <span data-ttu-id="c9e7e-136">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-136">false</span></span>                                |
| <span data-ttu-id="c9e7e-137">Position ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-137">Position?</span></span>                            | <span data-ttu-id="c9e7e-138">3</span><span class="sxs-lookup"><span data-stu-id="c9e7e-138">3</span></span>                                    |
| <span data-ttu-id="c9e7e-139">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c9e7e-139">Default Value</span></span>                        | <span data-ttu-id="c9e7e-140">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-140">none</span></span>                                 |
| <span data-ttu-id="c9e7e-141">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c9e7e-142">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-142">false</span></span>                                |
| <span data-ttu-id="c9e7e-143">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c9e7e-144">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="c9e7e-145">-ConnectionUri &lt;URI&gt;</span><span class="sxs-lookup"><span data-stu-id="c9e7e-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="c9e7e-146">Spécifie l’URI de la connexion à tester.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="c9e7e-147">Alias</span><span class="sxs-lookup"><span data-stu-id="c9e7e-147">Aliases</span></span>                              | <span data-ttu-id="c9e7e-148">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-148">none</span></span>                                 |
| <span data-ttu-id="c9e7e-149">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-149">Required?</span></span>                            | <span data-ttu-id="c9e7e-150">true</span><span class="sxs-lookup"><span data-stu-id="c9e7e-150">true</span></span>                                 |
| <span data-ttu-id="c9e7e-151">Position ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-151">Position?</span></span>                            | <span data-ttu-id="c9e7e-152">2</span><span class="sxs-lookup"><span data-stu-id="c9e7e-152">2</span></span>                                    |
| <span data-ttu-id="c9e7e-153">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c9e7e-153">Default Value</span></span>                        | <span data-ttu-id="c9e7e-154">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-154">none</span></span>                                 |
| <span data-ttu-id="c9e7e-155">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c9e7e-156">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-156">false</span></span>                                |
| <span data-ttu-id="c9e7e-157">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c9e7e-158">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="c9e7e-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="c9e7e-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="c9e7e-160">Spécifie un objet **PSCredential** pour un compte d’utilisateur que vous voulez utiliser pour tester les règles d’autorisation d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="c9e7e-161">Si vous n’ajoutez pas ce paramètre, l’applet de commande utilise le compte d’utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="c9e7e-162">Pour obtenir un objet **PSCredential**, qui est nécessaire pour tester des règles d’autorisation à distance, exécutez l’applet de commande [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="c9e7e-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="c9e7e-163">Alias</span><span class="sxs-lookup"><span data-stu-id="c9e7e-163">Aliases</span></span>                              | <span data-ttu-id="c9e7e-164">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-164">none</span></span>                                 |
| <span data-ttu-id="c9e7e-165">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-165">Required?</span></span>                            | <span data-ttu-id="c9e7e-166">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-166">false</span></span>                                |
| <span data-ttu-id="c9e7e-167">Position ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-167">Position?</span></span>                            | <span data-ttu-id="c9e7e-168">nommé</span><span class="sxs-lookup"><span data-stu-id="c9e7e-168">named</span></span>                                |
| <span data-ttu-id="c9e7e-169">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c9e7e-169">Default Value</span></span>                        | <span data-ttu-id="c9e7e-170">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-170">none</span></span>                                 |
| <span data-ttu-id="c9e7e-171">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c9e7e-172">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-172">false</span></span>                                |
| <span data-ttu-id="c9e7e-173">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c9e7e-174">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="c9e7e-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="c9e7e-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="c9e7e-176">Spécifie un sous-ensemble de règles à tester.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="c9e7e-177">Si ce paramètre n’est pas spécifié, cette applet de commande teste en prenant en compte toutes les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="c9e7e-178">Alias</span><span class="sxs-lookup"><span data-stu-id="c9e7e-178">Aliases</span></span>                              | <span data-ttu-id="c9e7e-179">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-179">none</span></span>                                 |
| <span data-ttu-id="c9e7e-180">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-180">Required?</span></span>                            | <span data-ttu-id="c9e7e-181">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-181">false</span></span>                                |
| <span data-ttu-id="c9e7e-182">Position ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-182">Position?</span></span>                            | <span data-ttu-id="c9e7e-183">nommé</span><span class="sxs-lookup"><span data-stu-id="c9e7e-183">named</span></span>                                |
| <span data-ttu-id="c9e7e-184">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c9e7e-184">Default Value</span></span>                        | <span data-ttu-id="c9e7e-185">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-185">none</span></span>                                 |
| <span data-ttu-id="c9e7e-186">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c9e7e-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="c9e7e-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="c9e7e-188">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c9e7e-189">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="c9e7e-190">-UserName &lt;Chaîne&gt;</span><span class="sxs-lookup"><span data-stu-id="c9e7e-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="c9e7e-191">Spécifie le nom de l’utilisateur à tester.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="c9e7e-192">Alias</span><span class="sxs-lookup"><span data-stu-id="c9e7e-192">Aliases</span></span>                              | <span data-ttu-id="c9e7e-193">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-193">none</span></span>                                 |
| <span data-ttu-id="c9e7e-194">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-194">Required?</span></span>                            | <span data-ttu-id="c9e7e-195">true</span><span class="sxs-lookup"><span data-stu-id="c9e7e-195">true</span></span>                                 |
| <span data-ttu-id="c9e7e-196">Position ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-196">Position?</span></span>                            | <span data-ttu-id="c9e7e-197">1</span><span class="sxs-lookup"><span data-stu-id="c9e7e-197">1</span></span>                                    |
| <span data-ttu-id="c9e7e-198">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c9e7e-198">Default Value</span></span>                        | <span data-ttu-id="c9e7e-199">none</span><span class="sxs-lookup"><span data-stu-id="c9e7e-199">none</span></span>                                 |
| <span data-ttu-id="c9e7e-200">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c9e7e-201">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-201">false</span></span>                                |
| <span data-ttu-id="c9e7e-202">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="c9e7e-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c9e7e-203">false</span><span class="sxs-lookup"><span data-stu-id="c9e7e-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="c9e7e-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="c9e7e-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="c9e7e-205">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="c9e7e-206">Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c9e7e-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="c9e7e-207">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="c9e7e-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="c9e7e-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="c9e7e-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="c9e7e-209">Cette applet de commande accepte un tableau d’objets PswaAuthorizationRule en entrée.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="c9e7e-210">SORTIES</span><span class="sxs-lookup"><span data-stu-id="c9e7e-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="c9e7e-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="c9e7e-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="c9e7e-212">Cette applet de commande produit un tableau d’objets PswaAuthorizationRule en sortie.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="c9e7e-213">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="c9e7e-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="c9e7e-214">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="c9e7e-214">EXAMPLE 1</span></span>

<span data-ttu-id="c9e7e-215">Cet exemple teste toutes les règles d’autorisation pour afficher toutes les règles qui permettent à l’utilisateur *contoso\\mhanson* de se connecter à l’ordinateur *srv2* et d’utiliser une configuration de session Windows PowerShell nommée *test*.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="c9e7e-216">EXAMPLE 2</span><span class="sxs-lookup"><span data-stu-id="c9e7e-216">EXAMPLE 2</span></span>

<span data-ttu-id="c9e7e-217">Cet exemple teste toutes les règles d’autorisation pour déterminer quelles règles s’appliquent à l’utilisateur *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="c9e7e-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="c9e7e-218">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c9e7e-218">Related topics</span></span>

- [<span data-ttu-id="c9e7e-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c9e7e-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="c9e7e-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c9e7e-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="c9e7e-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="c9e7e-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="c9e7e-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c9e7e-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)