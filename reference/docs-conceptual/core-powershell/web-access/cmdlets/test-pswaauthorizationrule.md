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
ms.locfileid: "34190143"
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Vérifie si une règle existe pour un utilisateur, un ordinateur ou un point de terminaison spécifié.

## <a name="syntax"></a>SYNTAXE

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPTION

L’applet de commande **Test-PswaAuthorizationRule** vérifie si une règle existe pour un utilisateur, un ordinateur ou un point de terminaison spécifié.
Cette applet de commande peut également être utilisé pour tester les règles d’autorisation, ou pour vérifier qu’une demande d’accès d’un utilisateur, d’un ordinateur ou d’un point de terminaison particulier est autorisée.
Par défaut, cette applet de commande évalue toutes les règles du fichier d’autorisations.
Vous pouvez cependant spécifier un sous-ensemble de règles à tester.

Vous pouvez utiliser cette applet de commande pour résoudre les problèmes liés aux échecs d’authentification.

Les paramètres de cette applet de commande correspondent aux champs de la page de connexion d’Accès Web Windows PowerShell®.

## <a name="parameters"></a>PARAMÈTRES

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;Chaîne&gt;

Spécifie le nom de l’ordinateur à tester.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | 2                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;Chaîne&gt;

Spécifie le nom de la configuration de session Windows PowerShell, également appelée point de terminaison ou instance d’exécution, à tester.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | 3                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;URI&gt;

Spécifie l’URI de la connexion à tester.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | 2                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Spécifie un objet **PSCredential** pour un compte d’utilisateur que vous voulez utiliser pour tester les règles d’autorisation d’Accès Web Windows PowerShell. Si vous n’ajoutez pas ce paramètre, l’applet de commande utilise le compte d’utilisateur actuellement connecté. Pour obtenir un objet **PSCredential**, qui est nécessaire pour tester des règles d’autorisation à distance, exécutez l’applet de commande [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Spécifie un sous-ensemble de règles à tester. Si ce paramètre n’est pas spécifié, cette applet de commande teste en prenant en compte toutes les règles d’autorisation.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByValue)                       |
| Accepter les caractères génériques ?          | false                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;Chaîne&gt;

Spécifie le nom de l’utilisateur à tester.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | 1                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.
Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRÉES

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Cette applet de commande accepte un tableau d’objets PswaAuthorizationRule en entrée.

## <a name="outputs"></a>SORTIES

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Cette applet de commande produit un tableau d’objets PswaAuthorizationRule en sortie.

## <a name="examples"></a>EXEMPLES

### <a name="example-1"></a>EXEMPLE 1

Cet exemple teste toutes les règles d’autorisation pour afficher toutes les règles qui permettent à l’utilisateur *contoso\\mhanson* de se connecter à l’ordinateur *srv2* et d’utiliser une configuration de session Windows PowerShell nommée *test*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>EXAMPLE 2

Cet exemple teste toutes les règles d’autorisation pour déterminer quelles règles s’appliquent à l’utilisateur *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Rubriques connexes

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)