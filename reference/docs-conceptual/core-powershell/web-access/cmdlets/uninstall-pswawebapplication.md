---
ms.topic: reference
keywords: powershell,applet de commande
ms.date: 12/12/2016
title: Uninstall-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221916"
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Désinstalle l’application Accès Windows PowerShell®.

## <a name="syntax"></a>SYNTAXE

### <a name="default"></a>Par défaut
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPTION

L’applet de commande **Uninstall-PswaWebApplication** désinstalle l’application web Windows PowerShell et supprime le site web d’IIS. L’applet de commande ne désinstalle pas IIS ni d’autres fonctionnalités installées car elles étaient nécessaires à l’exécution de Windows PowerShell.

## <a name="parameters"></a>PARAMÈTRES

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Indique que le certificat de test créé par l’applet de commande **Install\_PswaWebApplication** (avec le paramètre **UseTestCertificate**) est supprimé.
Seul le certificat de test avec le même nom que celui créé par l’applet de commande **Install-PswaWebApplication** est supprimé.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | true                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;Chaîne&gt;

Spécifie le nom de l’application web à désinstaller.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | 1                                    |
| Valeur par défaut                        | pswa                                 |
| Accepter l’entrée de pipeline ?               | false                                |
| Accepter les caractères génériques ?          | false                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;Chaîne&gt;

Spécifie le nom du site web où l’application web est installée.

|||
|-|-|
| Alias                              | none                                 |
| Obligatoire ?                            | false                                |
| Position ?                            | nommé                                |
| Valeur par défaut                        | Default Web Site                     |
| Accepter l’entrée de pipeline ?               | false                                |
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

Présente les conséquences éventuelles de l’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

Cette applet de commande ne prend pas d’entrée.

## <a name="outputs"></a>SORTIES

Cette applet de commande ne retourne pas de sortie.

## <a name="examples"></a>EXEMPLES

### <a name="example-1"></a>EXEMPLE 1

Cette commande désinstalle l’application web Windows PowerShell.
Vous pouvez utiliser cette applet de commande pour désinstaller l’application web Windows PowerShell si vous l’avez installée en utilisant les valeurs par défaut.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>EXAMPLE 2

Cette commande désinstalle l’application web Windows PowerShell et supprime le certificat de test associé à l’application.
Vous pouvez utiliser cette applet de commande pour désinstaller l’application web Windows PowerShell si vous l’avez installée en utilisant les valeurs par défaut et que vous avez créé un certificat de test.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>EXEMPLE 3 {#example-3 .subHeading}

Cette commande désinstalle l’application web Windows PowerShell quand un site web personnalisé et une application ont été spécifiés lors de l’installation.
La commande supprime le site Web nommé *MySite* et l’application nommée *TestApplication*, et spécifie que les certificats de test associés à l’application sont également supprimés.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Rubriques connexes

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)