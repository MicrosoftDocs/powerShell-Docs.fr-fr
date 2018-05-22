---
ms.topic: reference
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: b8020f8b034ab24d79a96da3908e9b63bf017cd9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Ajoute une nouvelle règle d’autorisation à l’ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.

## <a name="syntax"></a>Syntaxe

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPTION

L’applet de commande **Add-PswaAuthorizationRule** ajoute une nouvelle règle d’autorisation à l’ensemble de règles d’autorisation d’Accès Web Windows PowerShell®.

Vous devez spécifier les utilisateurs, les ordinateurs et les points de terminaison Windows PowerShell pour cette règle. Vous pouvez spécifier des utilisateurs et des ordinateurs en les désignant par des comptes d’utilisateur et des noms d’ordinateur individuels, ou en spécifiant des groupes.

Pour un ordinateur qui est joint à un domaine Active Directory, l’applet de commande utilise l’identificateur de sécurité (SID) de l’ordinateur pour créer la règle.
Ceci vous permet d’utiliser un nom court, un nom de domaine complet ou une adresse IP pour le champ **Nom de l’ordinateur** dans la page de connexion.

Pour un ordinateur qui n’est pas joint à un domaine Active Directory, l’applet de commande crée la règle en utilisant le nom d’ordinateur fourni par l’administrateur. Pour se connecter à cette machine, l’utilisateur final doit fournir le nom d’ordinateur tel qu’il apparaît dans la règle.

S’il existe plusieurs ordinateurs portant le même nom sur le réseau, la résolution du nom court peut aboutir à la désignation de plusieurs ordinateurs. Cela peut entraîner une ambiguïté lors de l’établissement d’une connexion. Par exemple, si une règle existe pour l’ordinateur de groupe de travail nommé «*Serveur1*» et qu’un nouvel ordinateur nommé *server1.contoso.com* est joint au réseau, la validation effectuée en utilisant les règles d’autorisation réussit et Accès Web Windows PowerShell tente d’établir une connexion à l’ordinateur nommé « *Serveur1* ». Il n’est pas garanti que la connexion soit établie avec l’ordinateur de groupe de travail spécifié : la tentative a pu être faite sur le groupe de travail ou sur l’ordinateur du domaine nommé « *Serveur1* ». Pour éviter l’ambiguïté, il est recommandé d’utiliser le nom de domaine complet pour l’ordinateur de destination chaque fois que c’est possible pour créer une règle d’autorisation.

Les règles d’autorisation évaluent les informations d’identification de connexion principales des utilisateurs d’Accès Web Windows PowerShell, et non pas les informations d’identification alternatives (le deuxième ensemble d’informations d’identification qui se trouve dans la section **Paramètres de connexion facultatifs** de la page de connexion). Pour obtenir un exemple, consultez l’exemple 6.

## <a name="parameters"></a>Paramètres

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;Chaîne&gt;

Spécifie le nom d’un groupe d’ordinateurs dans les Services de domaine Active Directory (AD DS) ou les groupes locaux auxquels cette règle accorde l’accès.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByPropertyName)                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;Chaîne&gt;

Spécifie le nom de l’ordinateur auquel cette règle accorde l’accès.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByPropertyName)                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;Chaîne&gt;

Spécifie le nom de la configuration de session Windows PowerShell, également appelée instance d’exécution, à laquelle cette règle accorde l’accès.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByPropertyName)                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Spécifie un objet **PSCredential** pour un compte d’utilisateur que vous voulez utiliser pour changer les règles d’autorisation d’Accès Web Windows PowerShell. Si vous n’ajoutez pas ce paramètre, l’applet de commande utilise le compte d’utilisateur actuellement connecté. Pour obtenir un objet **PSCredential**, qui est nécessaire pour ajouter des règles d’autorisation à distance, exécutez l’applet de commande [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-force"></a>-Force

Force l’exécution de la commande sans demander la confirmation de l’utilisateur.\
En outre, elle vous demande également confirmation quand vous entrez un nom d’ordinateur court ou simple (par exemple un nom qui n’est pas un nom de domaine ou qui n’est pas complet). La confirmation est demandée pour des raisons de sécurité, pour vous permettre d’utiliser le nom simple pour ajouter un ordinateur seulement si l’ordinateur est dans un groupe de travail.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;Chaîne&gt;

Spécifie le nom convivial de cette règle.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByPropertyName)                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;Chaîne\[\]&gt;

Spécifie le nom d’un ou plusieurs groupes d’utilisateurs dans les services AD DS ou dans des groupes locaux auxquels cette règle accorde l’accès.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByPropertyName)                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;Chaîne\[\]&gt;

Spécifie un ou plusieurs ordinateurs auxquels cette règle accorde l’accès. Le nom d’utilisateur peut être un compte d’utilisateur local sur l’ordinateur de passerelle ou un utilisateur dans AD DS.
Le format est `domain\user` ou `computer\user`.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | 1                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByValue, ByPropertyName)       |
| Accepter les caractères génériques ?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.
Pour plus d’informations, consultez [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>ENTRÉES

### <a name="string"></a>String

Cette applet de commande accepte une chaîne ou un tableau de chaînes en entrée.

### <a name="string"></a>Chaîne\[\]

Cette applet de commande accepte une chaîne ou un tableau de chaînes en entrée.

## <a name="outputs"></a>Sorties

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Cette applet de commande retourne l’objet de règle d’autorisation.

## <a name="examples"></a>EXEMPLES

### <a name="example-1"></a>EXEMPLE 1

Cet exemple accorde l’accès à la configuration de session *PSWAEndpoint*, une instance d’exécution restreinte, sur *srv2* pour les utilisateurs du groupe *SMAdmins*.\
**Remarque** : Le nom d’ordinateur doit être un nom de domaine complet. Les administrateurs définissent une configuration de session restreinte ou une instance d’exécution, qui est un ensemble limité d’applets de commande et de tâches que les utilisateurs finaux peuvent exécuter. La définition d’une instance d’exécution restreinte peut empêcher les utilisateurs d’accéder à d’autres ordinateurs qui ne sont pas dans l’instance d’exécution Windows PowerShell® autorisée, offrant ainsi une connexion plus sécurisée. Pour plus d’informations sur les configurations de session, consultez [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) ou [Installer et utiliser Accès Web Windows PowerShell](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>EXAMPLE 2

Cet exemple accorde l’accès à la configuration de session Windows PowerShell par défaut, `Microsoft.PowerShell`, sur *srv2* pour les utilisateurs nommés contoso\\user1, contoso\\user2 et contoso\\user3. Cette applet de commande crée trois règles (une par personne).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>EXEMPLE 3

Cet exemple montre comment entrer les valeurs des noms d’utilisateur via le pipeline.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>EXEMPLE 4

Cet exemple montre comment tous les paramètres prennent des valeurs du pipeline par nom de propriété.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>EXEMPLE 5

Cet exemple ajoute une règle pour autoriser l’utilisateur local nommé *PswaServer\\ChrisLocal* à accéder au serveur nommé *srv1.contoso.com*.

Cet exemple illustre un scénario dans lequel la passerelle est dans un groupe de travail et où l’ordinateur de destination est dans un domaine. La règle d’autorisation s’applique aux utilisateurs locaux sur la passerelle. Dans la page de connexion d’Accès Web Windows PowerShell, pour réussir à s’authentifier, l’utilisateur doit fournir un deuxième ensemble d’informations d’identification dans la zone **Paramètres de connexion facultatifs**. Le serveur de passerelle utilise l’ensemble supplémentaire d’informations d’identification pour authentifier l’utilisateur sur l’ordinateur de destination, un serveur nommé *srv1.contoso.com*.

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>EXEMPLE 6

Cet exemple autorise tous les utilisateurs à accéder à tous les points de terminaison sur tous les ordinateurs.
Ceci désactive en fait les règles d’autorisation.\
**Remarque** : L’utilisation du caractère générique `*` n’est pas recommandée pour les déploiements où la sécurité est sensible : son utilisation doit être envisagée seulement pour les environnements de test ou dans les déploiements où la sécurité peut être moins stricte.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Voir aussi

- [Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)
- [Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)
- [Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)
- [Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)
- [Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)