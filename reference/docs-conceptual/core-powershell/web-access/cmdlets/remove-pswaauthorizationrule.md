---
ms.topic: reference
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Supprime une règle d’autorisation spécifiée d’Accès Web Windows PowerShell®.

## <a name="syntax"></a>SYNTAXE

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Règle
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPTION

Supprime une règle d’autorisation spécifiée d’Accès Web Windows PowerShell.

## <a name="parameters"></a>PARAMÈTRES

### <a name="-force"></a>-Force

Exécute l'applet de commande sans demander confirmation. Par défaut, l’applet de commande demande confirmation avant de continuer.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Spécifie les identificateurs (ID) d’une ou plusieurs règles à supprimer.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | 2                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByValue, ByPropertyName)       |
| Accepter les caractères génériques ?          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Spécifie les règles à supprimer.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | true                                 |
| Position ?                            | 2                                    |
| Valeur par défaut                        | none                                 |
| Accepter l’entrée de pipeline ?               | True (ByValue)                       |
| Accepter les caractères génériques ?          | false                                |

### <a name="-confirm"></a>-Confirm

Votre confirmation sera requise avant l’exécution de l’applet de commande.

|||
|-|-|
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | false                                |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-whatif"></a>-WhatIf

Présente les conséquences éventuelles de l’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

|||
|-|-|
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | false                                |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Cette applet de commande prend en charge les paramètres courants : -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer et -OutVariable.
Pour plus d’informations, consultez [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRÉES

### <a name="int"></a>int\[\]

Cette applet de commande accepte un tableau d’entiers ou un tableau d’objets PswaAuthorizationRule.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Cette applet de commande accepte un tableau d’entiers ou un tableau d’objets PswaAuthorizationRule.

## <a name="outputs"></a>SORTIES

Cette applet de commande ne produit pas de sortie.

## <a name="examples"></a>EXEMPLES

### <a name="example-1"></a>EXEMPLE 1

Cet exemple supprime la règle d’autorisation avec l’ID *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>EXEMPLE 2 {#example-2 .subHeading}

Cet exemple supprime toutes les règles d’autorisation et demande une confirmation à l’utilisateur.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>Rubriques connexes

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)