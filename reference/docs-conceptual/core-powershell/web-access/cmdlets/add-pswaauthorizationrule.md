---
ms.topic: reference
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094226"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="06782-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="06782-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="06782-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="06782-104">SYNOPSIS</span></span>

<span data-ttu-id="06782-105">Ajoute une nouvelle règle d’autorisation à l’ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="06782-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="06782-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06782-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="06782-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="06782-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="06782-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="06782-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="06782-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="06782-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="06782-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="06782-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="06782-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="06782-111">DESCRIPTION</span></span>

<span data-ttu-id="06782-112">L’applet de commande **Add-PswaAuthorizationRule** ajoute une nouvelle règle d’autorisation à l’ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="06782-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="06782-113">Vous devez spécifier les utilisateurs, les ordinateurs et les points de terminaison Windows PowerShell pour cette règle.</span><span class="sxs-lookup"><span data-stu-id="06782-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="06782-114">Vous pouvez spécifier des utilisateurs et des ordinateurs en les désignant par des comptes d’utilisateur et des noms d’ordinateur individuels, ou en spécifiant des groupes.</span><span class="sxs-lookup"><span data-stu-id="06782-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="06782-115">Pour un ordinateur qui est joint à un domaine Active Directory, l’applet de commande utilise l’identificateur de sécurité (SID) de l’ordinateur pour créer la règle.</span><span class="sxs-lookup"><span data-stu-id="06782-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="06782-116">Ceci vous permet d’utiliser un nom court, un nom de domaine complet ou une adresse IP pour le champ **Nom de l’ordinateur** dans la page de connexion.</span><span class="sxs-lookup"><span data-stu-id="06782-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="06782-117">Pour un ordinateur qui n’est pas joint à un domaine Active Directory, l’applet de commande crée la règle en utilisant le nom d’ordinateur fourni par l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="06782-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="06782-118">Pour se connecter à cette machine, l’utilisateur final doit fournir le nom d’ordinateur tel qu’il apparaît dans la règle.</span><span class="sxs-lookup"><span data-stu-id="06782-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="06782-119">S’il existe plusieurs ordinateurs portant le même nom sur le réseau, la résolution du nom court peut aboutir à la désignation de plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="06782-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="06782-120">Cela peut entraîner une ambiguïté lors de l’établissement d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="06782-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="06782-121">Par exemple, si une règle existe pour l’ordinateur de groupe de travail nommé «*Serveur1*» et qu’un nouvel ordinateur nommé *server1.contoso.com* est joint au réseau, la validation effectuée en utilisant les règles d’autorisation réussit et Accès Web Windows PowerShell tente d’établir une connexion à l’ordinateur nommé « *Serveur1* ».</span><span class="sxs-lookup"><span data-stu-id="06782-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="06782-122">Il n’est pas garanti que la connexion soit établie avec l’ordinateur de groupe de travail spécifié : la tentative a pu être faite sur le groupe de travail ou sur l’ordinateur du domaine nommé « *Serveur1* ».</span><span class="sxs-lookup"><span data-stu-id="06782-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="06782-123">Pour éviter l’ambiguïté, il est recommandé d’utiliser le nom de domaine complet pour l’ordinateur de destination chaque fois que c’est possible pour créer une règle d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="06782-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="06782-124">Les règles d’autorisation évaluent les informations d’identification de connexion principales des utilisateurs d’Accès Web Windows PowerShell, et non pas les informations d’identification alternatives (le deuxième ensemble d’informations d’identification qui se trouve dans la section **Paramètres de connexion facultatifs** de la page de connexion).</span><span class="sxs-lookup"><span data-stu-id="06782-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="06782-125">Pour obtenir un exemple, consultez l’exemple 6.</span><span class="sxs-lookup"><span data-stu-id="06782-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="06782-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="06782-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="06782-127">-ComputerGroupName \<Chaîne\></span><span class="sxs-lookup"><span data-stu-id="06782-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="06782-128">Spécifie le nom d’un groupe d’ordinateurs dans les Services de domaine Active Directory (AD DS) ou les groupes locaux auxquels cette règle accorde l’accès.</span><span class="sxs-lookup"><span data-stu-id="06782-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-129">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-129">Aliases</span></span>                              | <span data-ttu-id="06782-130">none</span><span class="sxs-lookup"><span data-stu-id="06782-130">none</span></span>                                 |
| <span data-ttu-id="06782-131">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-131">Required?</span></span>                            | <span data-ttu-id="06782-132">true</span><span class="sxs-lookup"><span data-stu-id="06782-132">true</span></span>                                 |
| <span data-ttu-id="06782-133">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-133">Position?</span></span>                            | <span data-ttu-id="06782-134">nommé</span><span class="sxs-lookup"><span data-stu-id="06782-134">named</span></span>                                |
| <span data-ttu-id="06782-135">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-135">Default Value</span></span>                        | <span data-ttu-id="06782-136">none</span><span class="sxs-lookup"><span data-stu-id="06782-136">none</span></span>                                 |
| <span data-ttu-id="06782-137">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="06782-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="06782-139">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-140">false</span><span class="sxs-lookup"><span data-stu-id="06782-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="06782-141">-ComputerName \<Chaîne\></span><span class="sxs-lookup"><span data-stu-id="06782-141">-ComputerName \<String\></span></span>

<span data-ttu-id="06782-142">Spécifie le nom de l’ordinateur auquel cette règle accorde l’accès.</span><span class="sxs-lookup"><span data-stu-id="06782-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-143">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-143">Aliases</span></span>                              | <span data-ttu-id="06782-144">none</span><span class="sxs-lookup"><span data-stu-id="06782-144">none</span></span>                                 |
| <span data-ttu-id="06782-145">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-145">Required?</span></span>                            | <span data-ttu-id="06782-146">true</span><span class="sxs-lookup"><span data-stu-id="06782-146">true</span></span>                                 |
| <span data-ttu-id="06782-147">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-147">Position?</span></span>                            | <span data-ttu-id="06782-148">nommé</span><span class="sxs-lookup"><span data-stu-id="06782-148">named</span></span>                                |
| <span data-ttu-id="06782-149">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-149">Default Value</span></span>                        | <span data-ttu-id="06782-150">none</span><span class="sxs-lookup"><span data-stu-id="06782-150">none</span></span>                                 |
| <span data-ttu-id="06782-151">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="06782-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="06782-153">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-154">false</span><span class="sxs-lookup"><span data-stu-id="06782-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="06782-155">-ConfigurationName \<Chaîne\></span><span class="sxs-lookup"><span data-stu-id="06782-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="06782-156">Spécifie le nom de la configuration de session Windows PowerShell, également appelée instance d’exécution, à laquelle cette règle accorde l’accès.</span><span class="sxs-lookup"><span data-stu-id="06782-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-157">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-157">Aliases</span></span>                              | <span data-ttu-id="06782-158">none</span><span class="sxs-lookup"><span data-stu-id="06782-158">none</span></span>                                 |
| <span data-ttu-id="06782-159">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-159">Required?</span></span>                            | <span data-ttu-id="06782-160">true</span><span class="sxs-lookup"><span data-stu-id="06782-160">true</span></span>                                 |
| <span data-ttu-id="06782-161">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-161">Position?</span></span>                            | <span data-ttu-id="06782-162">nommé</span><span class="sxs-lookup"><span data-stu-id="06782-162">named</span></span>                                |
| <span data-ttu-id="06782-163">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-163">Default Value</span></span>                        | <span data-ttu-id="06782-164">none</span><span class="sxs-lookup"><span data-stu-id="06782-164">none</span></span>                                 |
| <span data-ttu-id="06782-165">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="06782-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="06782-167">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-168">false</span><span class="sxs-lookup"><span data-stu-id="06782-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="06782-169">-Credential  \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="06782-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="06782-170">Spécifie un objet **PSCredential** pour un compte d’utilisateur que vous voulez utiliser pour changer les règles d’autorisation d’Accès Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06782-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="06782-171">Si vous n’ajoutez pas ce paramètre, l’applet de commande utilise le compte d’utilisateur actuellement connecté.</span><span class="sxs-lookup"><span data-stu-id="06782-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="06782-172">Pour obtenir un objet **PSCredential**, qui est nécessaire pour ajouter des règles d’autorisation à distance, exécutez l’applet de commande [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).</span><span class="sxs-lookup"><span data-stu-id="06782-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-173">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-173">Aliases</span></span>                              | <span data-ttu-id="06782-174">none</span><span class="sxs-lookup"><span data-stu-id="06782-174">none</span></span>                                 |
| <span data-ttu-id="06782-175">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-175">Required?</span></span>                            | <span data-ttu-id="06782-176">false</span><span class="sxs-lookup"><span data-stu-id="06782-176">false</span></span>                                |
| <span data-ttu-id="06782-177">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-177">Position?</span></span>                            | <span data-ttu-id="06782-178">nommé</span><span class="sxs-lookup"><span data-stu-id="06782-178">named</span></span>                                |
| <span data-ttu-id="06782-179">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-179">Default Value</span></span>                        | <span data-ttu-id="06782-180">none</span><span class="sxs-lookup"><span data-stu-id="06782-180">none</span></span>                                 |
| <span data-ttu-id="06782-181">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-182">false</span><span class="sxs-lookup"><span data-stu-id="06782-182">false</span></span>                                |
| <span data-ttu-id="06782-183">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-184">false</span><span class="sxs-lookup"><span data-stu-id="06782-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="06782-185">-Force</span><span class="sxs-lookup"><span data-stu-id="06782-185">-Force</span></span>

<span data-ttu-id="06782-186">Force l’exécution de la commande sans demander la confirmation de l’utilisateur.\\</span><span class="sxs-lookup"><span data-stu-id="06782-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="06782-187">En outre, elle vous demande également confirmation quand vous entrez un nom d’ordinateur court ou simple (par exemple un nom qui n’est pas un nom de domaine ou qui n’est pas complet).</span><span class="sxs-lookup"><span data-stu-id="06782-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="06782-188">La confirmation est demandée pour des raisons de sécurité, pour vous permettre d’utiliser le nom simple pour ajouter un ordinateur seulement si l’ordinateur est dans un groupe de travail.</span><span class="sxs-lookup"><span data-stu-id="06782-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-189">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-189">Aliases</span></span>                              | <span data-ttu-id="06782-190">none</span><span class="sxs-lookup"><span data-stu-id="06782-190">none</span></span>                                 |
| <span data-ttu-id="06782-191">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-191">Required?</span></span>                            | <span data-ttu-id="06782-192">false</span><span class="sxs-lookup"><span data-stu-id="06782-192">false</span></span>                                |
| <span data-ttu-id="06782-193">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-193">Position?</span></span>                            | <span data-ttu-id="06782-194">nommé</span><span class="sxs-lookup"><span data-stu-id="06782-194">named</span></span>                                |
| <span data-ttu-id="06782-195">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-195">Default Value</span></span>                        | <span data-ttu-id="06782-196">none</span><span class="sxs-lookup"><span data-stu-id="06782-196">none</span></span>                                 |
| <span data-ttu-id="06782-197">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-198">false</span><span class="sxs-lookup"><span data-stu-id="06782-198">false</span></span>                                |
| <span data-ttu-id="06782-199">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-200">false</span><span class="sxs-lookup"><span data-stu-id="06782-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="06782-201">-RuleName \<Chaîne\></span><span class="sxs-lookup"><span data-stu-id="06782-201">-RuleName \<String\></span></span>

<span data-ttu-id="06782-202">Spécifie le nom convivial de cette règle.</span><span class="sxs-lookup"><span data-stu-id="06782-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-203">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-203">Aliases</span></span>                              | <span data-ttu-id="06782-204">none</span><span class="sxs-lookup"><span data-stu-id="06782-204">none</span></span>                                 |
| <span data-ttu-id="06782-205">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-205">Required?</span></span>                            | <span data-ttu-id="06782-206">false</span><span class="sxs-lookup"><span data-stu-id="06782-206">false</span></span>                                |
| <span data-ttu-id="06782-207">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-207">Position?</span></span>                            | <span data-ttu-id="06782-208">nommé</span><span class="sxs-lookup"><span data-stu-id="06782-208">named</span></span>                                |
| <span data-ttu-id="06782-209">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-209">Default Value</span></span>                        | <span data-ttu-id="06782-210">none</span><span class="sxs-lookup"><span data-stu-id="06782-210">none</span></span>                                 |
| <span data-ttu-id="06782-211">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="06782-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="06782-213">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-214">false</span><span class="sxs-lookup"><span data-stu-id="06782-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="06782-215">-UserGroupName \<Chaîne\[\]\></span><span class="sxs-lookup"><span data-stu-id="06782-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="06782-216">Spécifie le nom d’un ou plusieurs groupes d’utilisateurs dans les services AD DS ou dans des groupes locaux auxquels cette règle accorde l’accès.</span><span class="sxs-lookup"><span data-stu-id="06782-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-217">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-217">Aliases</span></span>                              | <span data-ttu-id="06782-218">none</span><span class="sxs-lookup"><span data-stu-id="06782-218">none</span></span>                                 |
| <span data-ttu-id="06782-219">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-219">Required?</span></span>                            | <span data-ttu-id="06782-220">true</span><span class="sxs-lookup"><span data-stu-id="06782-220">true</span></span>                                 |
| <span data-ttu-id="06782-221">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-221">Position?</span></span>                            | <span data-ttu-id="06782-222">nommé</span><span class="sxs-lookup"><span data-stu-id="06782-222">named</span></span>                                |
| <span data-ttu-id="06782-223">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-223">Default Value</span></span>                        | <span data-ttu-id="06782-224">none</span><span class="sxs-lookup"><span data-stu-id="06782-224">none</span></span>                                 |
| <span data-ttu-id="06782-225">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="06782-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="06782-227">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-228">false</span><span class="sxs-lookup"><span data-stu-id="06782-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="06782-229">-UserName \<Chaîne\[\]\></span><span class="sxs-lookup"><span data-stu-id="06782-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="06782-230">Spécifie un ou plusieurs ordinateurs auxquels cette règle accorde l’accès.</span><span class="sxs-lookup"><span data-stu-id="06782-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="06782-231">Le nom d’utilisateur peut être un compte d’utilisateur local sur l’ordinateur de passerelle ou un utilisateur dans AD DS.</span><span class="sxs-lookup"><span data-stu-id="06782-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="06782-232">Le format est `domain\user` ou `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="06782-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="06782-233">Alias</span><span class="sxs-lookup"><span data-stu-id="06782-233">Aliases</span></span>                              | <span data-ttu-id="06782-234">none</span><span class="sxs-lookup"><span data-stu-id="06782-234">none</span></span>                                 |
| <span data-ttu-id="06782-235">Obligatoire ?</span><span class="sxs-lookup"><span data-stu-id="06782-235">Required?</span></span>                            | <span data-ttu-id="06782-236">true</span><span class="sxs-lookup"><span data-stu-id="06782-236">true</span></span>                                 |
| <span data-ttu-id="06782-237">Position ?</span><span class="sxs-lookup"><span data-stu-id="06782-237">Position?</span></span>                            | <span data-ttu-id="06782-238">1</span><span class="sxs-lookup"><span data-stu-id="06782-238">1</span></span>                                    |
| <span data-ttu-id="06782-239">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="06782-239">Default Value</span></span>                        | <span data-ttu-id="06782-240">none</span><span class="sxs-lookup"><span data-stu-id="06782-240">none</span></span>                                 |
| <span data-ttu-id="06782-241">Accepter l’entrée de pipeline ?</span><span class="sxs-lookup"><span data-stu-id="06782-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="06782-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="06782-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="06782-243">Accepter les caractères génériques ?</span><span class="sxs-lookup"><span data-stu-id="06782-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="06782-244">false</span><span class="sxs-lookup"><span data-stu-id="06782-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="06782-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="06782-245">\<CommonParameters\></span></span>

<span data-ttu-id="06782-246">Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="06782-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="06782-247">Pour plus d’informations, consultez [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="06782-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="06782-248">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="06782-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="06782-249">String</span><span class="sxs-lookup"><span data-stu-id="06782-249">String</span></span>

<span data-ttu-id="06782-250">Cette applet de commande accepte une chaîne ou un tableau de chaînes en entrée.</span><span class="sxs-lookup"><span data-stu-id="06782-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="06782-251">Chaîne\[\]</span><span class="sxs-lookup"><span data-stu-id="06782-251">String\[\]</span></span>

<span data-ttu-id="06782-252">Cette applet de commande accepte une chaîne ou un tableau de chaînes en entrée.</span><span class="sxs-lookup"><span data-stu-id="06782-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="06782-253">Sorties</span><span class="sxs-lookup"><span data-stu-id="06782-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="06782-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="06782-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="06782-255">Cette applet de commande retourne l’objet de règle d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="06782-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="06782-256">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="06782-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="06782-257">EXEMPLE 1</span><span class="sxs-lookup"><span data-stu-id="06782-257">EXAMPLE 1</span></span>

<span data-ttu-id="06782-258">Cet exemple accorde l’accès à la configuration de session _PSWAEndpoint_, une instance d’exécution restreinte, sur _srv2_ pour les utilisateurs du groupe _SMAdmins_.</span><span class="sxs-lookup"><span data-stu-id="06782-258">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="06782-259">Le nom d’ordinateur doit être un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="06782-259">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="06782-260">Les administrateurs définissent une configuration de session restreinte ou une instance d’exécution, qui est un ensemble limité d’applets de commande et de tâches que les utilisateurs finaux peuvent exécuter.</span><span class="sxs-lookup"><span data-stu-id="06782-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="06782-261">La définition d’une instance d’exécution restreinte peut empêcher les utilisateurs d’accéder à d’autres ordinateurs qui ne sont pas dans l’instance d’exécution Windows PowerShell® autorisée, offrant ainsi une connexion plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="06782-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="06782-262">Pour plus d’informations sur les configurations de session, consultez [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) ou [Installer et utiliser Accès Web Windows PowerShell](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="06782-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="06782-263">EXAMPLE 2</span><span class="sxs-lookup"><span data-stu-id="06782-263">EXAMPLE 2</span></span>

<span data-ttu-id="06782-264">Cet exemple accorde l’accès à la configuration de session Windows PowerShell par défaut, `Microsoft.PowerShell`, sur *srv2* pour les utilisateurs nommés `contoso\user1`, `contoso\user2` et `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="06782-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="06782-265">Cette applet de commande crée trois règles (une par personne).</span><span class="sxs-lookup"><span data-stu-id="06782-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="06782-266">EXEMPLE 3</span><span class="sxs-lookup"><span data-stu-id="06782-266">EXAMPLE 3</span></span>

<span data-ttu-id="06782-267">Cet exemple montre comment entrer les valeurs des noms d’utilisateur via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="06782-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="06782-268">EXEMPLE 4</span><span class="sxs-lookup"><span data-stu-id="06782-268">EXAMPLE 4</span></span>

<span data-ttu-id="06782-269">Cet exemple montre comment tous les paramètres prennent des valeurs du pipeline par nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="06782-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="06782-270">EXEMPLE 5</span><span class="sxs-lookup"><span data-stu-id="06782-270">EXAMPLE 5</span></span>

<span data-ttu-id="06782-271">Cet exemple ajoute une règle pour autoriser l’utilisateur local nommé `PswaServer\ChrisLocal` à accéder au serveur nommé **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="06782-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="06782-272">Cet exemple illustre un scénario dans lequel la passerelle est dans un groupe de travail et où l’ordinateur de destination est dans un domaine.</span><span class="sxs-lookup"><span data-stu-id="06782-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="06782-273">La règle d’autorisation s’applique aux utilisateurs locaux sur la passerelle.</span><span class="sxs-lookup"><span data-stu-id="06782-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="06782-274">Dans la page de connexion d’Accès Web Windows PowerShell, pour réussir à s’authentifier, l’utilisateur doit fournir un deuxième ensemble d’informations d’identification dans la zone **Paramètres de connexion facultatifs**.</span><span class="sxs-lookup"><span data-stu-id="06782-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="06782-275">Le serveur de passerelle utilise l’ensemble supplémentaire d’informations d’identification pour authentifier l’utilisateur sur l’ordinateur de destination, un serveur nommé *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="06782-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="06782-276">EXEMPLE 6</span><span class="sxs-lookup"><span data-stu-id="06782-276">EXAMPLE 6</span></span>

<span data-ttu-id="06782-277">Cet exemple autorise tous les utilisateurs à accéder à tous les points de terminaison sur tous les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="06782-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="06782-278">Ceci désactive en fait les règles d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="06782-278">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="06782-279">L’utilisation du caractère générique `*` n’est pas recommandée pour les déploiements où la sécurité est sensible : son utilisation doit être envisagée seulement pour les environnements de test ou dans les déploiements où la sécurité peut être moins stricte.</span><span class="sxs-lookup"><span data-stu-id="06782-279">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="06782-280">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06782-280">See Also</span></span>

<span data-ttu-id="06782-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="06782-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="06782-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="06782-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="06782-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="06782-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="06782-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="06782-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="06782-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="06782-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="06782-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="06782-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="06782-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="06782-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)