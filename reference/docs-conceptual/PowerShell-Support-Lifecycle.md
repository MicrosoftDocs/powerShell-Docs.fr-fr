---
title: Cycle de vie de support de PowerShell Core
description: Politiques régissant le support de PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854374"
---
# <a name="powershell-core-support-lifecycle"></a>Cycle de vie de support de PowerShell Core

PowerShell Core est un ensemble d’outils et de composants distinct livré, installé et configuré séparément de Windows PowerShell.
PowerShell Core n’est donc pas inclus dans les contrats de licence Windows 7/8.1/10 ou Windows Server.

Toutefois, PowerShell Core est pris en charge dans des contrats de support Microsoft classiques, dont [Premier][], les [contrats Entreprise Microsoft ][enterprise-agreement] et [Microsoft Software Assurance][assurance].
Vous pouvez également payer pour obtenir un [support assisté][] pour PowerShell Core en faisant une demande de support pour votre problème.

## <a name="community-support"></a>Support de la communauté

Nous proposons également un [support de la communauté][] sur GitHub, où vous pouvez signaler un problème, un bogue ou une demande de fonctionnalité.
Vous pouvez également bénéficier de l’aide d’autres membres de la communauté sur la [Communauté Microsoft][] générale ou la [Communauté technique PowerShell][] Microsoft.
Nous ne garantissons pas que la communauté traitera ou résoudra votre problème en temps voulu.
Si vous avez un problème nécessitant une attention immédiate, vous devez utiliser les options de support payantes classiques.

## <a name="lifecycle-of-powershell-core"></a>Cycle de vie de PowerShell Core

PowerShell Core adopte la [politique de support moderne Microsoft][modern].
Cette politique de support est destinée à maintenir les clients à jour avec les dernières versions.

La branche PowerShell Core version 6.x sera mise à jour environ une fois tous les six mois (par exemple : 6.0, 6.1, 6.2, etc.)

> [!IMPORTANT]
> Vous devez effectuer la mise à jour dans les six mois après la publication de chaque nouvelle version mineure pour continuer à recevoir un support.

Par exemple, si PowerShell Core 6.1 est publié le 1er juillet 2018, vous êtes supposé effectuer la mise à jour vers PowerShell Core 6.1 avant le 1er janvier 2019 pour continuer à bénéficier du support.

> [!IMPORTANT]
> Vous devez effectuer la mise à jour dans les 30 jours après la publication de chaque nouvelle version de correctif pour continuer à recevoir un support.

Par exemple, si vous exécutez PowerShell Core 6.1 et que la version 6.1.3 a été publiée le 19 février 2019, vous êtes censé mettre à jour vers PowerShell Core 6.1.3 d’ici le 21 mars 2019, soit 30 jours après la publication, pour continuer à bénéficier du support.
Si des correctifs sont identifiés comme étant obligatoires, ils seront publiés dans notre prochaine mise à jour cumulative.

La stratégie de cycle de vie moderne exige également que Microsoft prévienne les clients 12 mois avant de mettre fin au support d’un produit (par exemple, PowerShell Core).

A terme, nous pensons que PowerShell Core adoptera l'approche du « service à long terme ».
Dans ce cas, nous exigerons uniquement les mises à jour de maintenance et de sécurité pour continuer à bénéficier du support pour une branche/version spécifique de 6.x.

## <a name="supported-platforms"></a>Plateformes prises en charge

Le tableau suivant indique quelle plateforme est officiellement prise en charge par la version de PowerShell Core que vous utilisez.

Notre communauté a également proposé des packages pour certaines plateformes, mais ils ne sont pas officiellement pris en charge.
Ces packages sont marqués `Community` dans la table.

Les plateformes répertoriées en tant que `Experimental` ne sont pas officiellement prises en charge, mais sont disponibles pour l’expérimentation et les commentaires.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 et 10                            | Pris en charge   | Pris en charge   |
| Windows Server 2008 R2, 2012 R2, 2016             | Pris en charge   | Pris en charge   |
| [Canal semi-annuel Windows Server][semi-annual] | Pris en charge   | Pris en charge   |
| Ubuntu 16.04 et 18.04                            | Pris en charge   | Pris en charge   |
| Ubuntu 18.10 (via Snap Package)                   | Communauté   | Communauté   |
| Debian 9                                          | Pris en charge   | Pris en charge   |
| CentOS 7                                          | Pris en charge   | Pris en charge   |
| Red Hat Enterprise Linux 7                        | Pris en charge   | Pris en charge   |
| openSUSE 42.3                                     | Pris en charge   | Pris en charge   |
| Fedora 28                                         | Pris en charge   | Pris en charge   |
| macOS 10.12+                                      | Pris en charge   | Pris en charge   |
| Arch                                              | Communauté   | Communauté   |
| Raspbian                                          | Communauté   | Communauté   |
| Kali                                              | Communauté   | Communauté   |
| AppImage (fonctionne sur plusieurs plateformes Linux)     | Communauté   | Communauté   |
| [Snap Package](https://snapcraft.io/powershell)   | Voir la remarque    | Voir la remarque    |

> [!NOTE]
> Les packages Snap sont pris en charge de la même manière que la distribution sur laquelle vous exécutez le package.

## <a name="powershell-release-end-of-life"></a>Fin de vie de versions de PowerShell

Sur la base du [cycle de vie de PowerShell Core](#lifecycle-of-powershell-core), le tableau suivant répertorie les dates auxquelles les différentes versions ne seront plus prises en charge.

| Version | Fin de vie                   |
|---------|-------------------------------|
| 6.0     | 13 février 2019             |
| 6.1     | 28 septembre 2019            |
| 6.2     | 6 mois après la publication de la version 7     |

## <a name="platforms-which-are-out-of-support"></a>Plateformes qui ne sont plus prises en charge

Lorsqu’une version de plateforme arrive en fin de vie conformément à la définition du propriétaire de la plateforme, PowerShell Core cesse également de prendre en charge cette version de la plateforme.
Les packages précédemment publiés resteront à la disposition des clients ayant besoin d’y accéder, mais il n’y aura plus ni prise en charge formelle ni mise à jour d’aucune sorte.

Les propriétaires de distribution ont donc mis fin au support pour les versions suivantes, qui ne sont plus prises en charge.

| Système d’exploitation       | Version | Fin de vie                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Août 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Décembre 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Mai 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| OpenSUSE | 42.1    | [Mai 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| OpenSUSE | 42.2    | [Janvier 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Juillet 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Janvier 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Juillet 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Juin 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Novembre 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Avril 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Remarques sur les licences

PowerShell Core est publié sous la [licence MIT][].
Sous cette licence et en l’absence d’un contrat de support payant, les utilisateurs sont limités au [support de la communauté][].
Dans le cadre du support de la communauté, Microsoft ne garantit pas la réactivité ni les correctifs.

## <a name="windows-powershell-module"></a>Module Windows PowerShell

Le support de PowerShell Core n’inclut pas de modules du produit, sauf si ces modules prennent explicitement en charge PowerShell Core.
Par exemple, l’utilisation du module `ActiveDirectory` qui est fourni dans le cadre de Windows Server est un scénario non pris en charge.

Toutefois, les modules qui ne prennent pas explicitement en charge PowerShell Core peuvent être compatibles dans certains cas.
En installant le module [`WindowsPSModulePath`][] vous pouvez ajouter Windows PowerShell `PSModulePath` à PowerShell Core `PSModulePath`.

Installez d’abord le module `WindowsPSModulePath` à partir de PowerShell Gallery :

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Après avoir installé ce module, exécutez l’applet de commande `Add-WindowsPSModulePath` pour ajouter Windows PowerShell `PSModulePath` à PowerShell Core :

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Fonctionnalités expérimentales

Les [fonctionnalités expérimentales][] sont limitées au [support de la communauté](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[support de la communauté]: https://github.com/powershell/powershell/issues
[Communauté Microsoft]: https://answers.microsoft.com/
[Communauté technique PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[support assisté]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licence MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Fonctionnalités expérimentales]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
