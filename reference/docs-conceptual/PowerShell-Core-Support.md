# <a name="powershell-core-support-lifecycle"></a>Cycle de vie de support de PowerShell Core

PowerShell Core est un ensemble d’outils et de composants distinct livré, installé et configuré séparément de Windows PowerShell.
Par conséquent, PowerShell Core n’est pas inclus dans les contrats de licence Windows 7/8.1/10 ni Windows Server.

Toutefois, PowerShell Core est pris en charge dans des contrats de support Microsoft classiques, dont [Premier][], les [contrats Entreprise Microsoft ][enterprise-agreement] et [Microsoft Software Assurance][assurance].
Vous pouvez également payer pour obtenir un [support assisté][] pour PowerShell Core en faisant une demande de support pour votre problème.

Nous proposons également un [support de la communauté][] sur GitHub, où vous pouvez signaler un problème, un bogue ou une demande de fonctionnalité.
Vous pouvez également obtenir de l’aide auprès d’autres membres de la communauté sur la [Communauté Microsoft][] générale ou la [Communauté technique PowerShell][] Microsoft.
Nous n’offrons aucune garantie que votre problème y sera traité ou résolu en temps voulu.
Si vous avez un problème nécessitant une attention immédiate, vous devez utiliser les options de support payantes classiques.

## <a name="lifecycle-of-powershell-core"></a>Cycle de vie de PowerShell Core

PowerShell Core adopte la [politique de support moderne Microsoft][modern].
Cette politique de support est destinée à maintenir les clients à jour avec les dernières versions.

La branche PowerShell Core version 6.x sera mise à jour environ une fois tous les six mois (par exemple, 6.0, 6.1, 6.2, etc.)

> [!IMPORTANT]
> Vous devez effectuer la mise à jour dans les six mois après la publication de chaque nouvelle version mineure pour continuer à recevoir un support.

Par exemple, si PowerShell Core 6.1 est publié le 1er juillet 2018, vous êtes supposé effectuer la mise à jour vers PowerShell Core 6.1 avant le 1er janvier 2019 pour continuer à bénéficier du support.

![Cycle de vie de branche PowerShell Core][lifecycle-chart]

La politique de support moderne nécessite également que Microsoft prévienne les clients 12 mois avant de mettre fin au support d’un produit (par exemple, PowerShell Core).

Au final, PowerShell Core devrait suivre l’approche de « maintenance à long terme » où seules la maintenance et les mises à jour de sécurité resteront en support sur une branche/version spécifique de 6.x.

## <a name="supported-platforms"></a>Plateformes prises en charge

Consultez le tableau suivant pour voir quelle plateforme est officiellement prise en charge par la version de PowerShell Core que vous utilisez.

Notre communauté a également proposé des packages pour certaines plateformes, mais ils ne sont pas officiellement pris en charge.
Ces packages sont marqués `Community` dans la table.

Les plateformes répertoriées en tant que `Experimental` ne sont pas officiellement prises en charge, mais sont disponibles pour l’expérimentation et les commentaires.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 et 10                            | Prise en charge   | Prise en charge   |
| Windows Server 2008 R2, 2012 R2, 2016             | Prise en charge   | Prise en charge   |
| [Canal semi-annuel Windows Server][semi-annual] | Prise en charge   | Prise en charge   |
| Ubuntu 14.04 et 16.04                           | Prise en charge   | Prise en charge   |
| Ubuntu 17.10 et 18.04                           |             | Prise en charge   |
| Debian 8.7+ et 9                                | Prise en charge   | Prise en charge   |
| CentOS 7                                          | Prise en charge   | Prise en charge   |
| Red Hat Enterprise Linux 7                        | Prise en charge   | Prise en charge   |
| OpenSUSE 42.3                                     | Prise en charge   | Prise en charge   |
| Fedora 27                                         | Prise en charge   | Prise en charge   |
| Fedora 28                                         |             | Prise en charge   |
| macOS 10.12+                                      | Prise en charge   | Prise en charge   |
| Arch                                              | Communauté   | Communauté   |
| Raspbian                                          | Expérimental| Communauté   |
| Kali                                              | Communauté   | Communauté   |
| AppImage (fonctionne sur plusieurs plateformes Linux)     | Communauté   | Communauté   |

## <a name="platform-which-are-out-of-support"></a>Plateformes qui ne sont plus prises en charge

Lorsqu’une version de plateforme atteint la fin de vie comme défini par le propriétaire de la plateforme, PowerShell Core cesse également de prendre en charge cette version de la plateforme. Les packages précédemment publiés resteront à la disposition des clients ayant besoin d’y accéder, mais il n’y aura plus ni prise en charge formelle ni mise à jour d’aucune sorte.

Par conséquent, la prise en charge des versions suivantes a été interrompue par les propriétaires de distribution et n’est plus assurée.

| Système d’exploitation       | Version | Fin de vie                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 26      | [Mai 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| Fedora   | 25      | [Décembre 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 24      | [Août 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| OpenSUSE | 42.2    | [Janvier 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| OpenSUSE | 42.1    | [Mai 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| Ubuntu   | 17.04   | [Janvier 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 16.10   | [Juillet 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |

## <a name="notes-on-licensing"></a>Remarques sur les licences

PowerShell Core est publié sous la [licence MIT][].
Sous cette licence et en l’absence d’un contrat de support payant, les utilisateurs sont limités au [support de la communauté][].
Dans le cadre du support de la communauté, Microsoft ne garantit pas la réactivité ni les correctifs.

## <a name="windows-powershell-module"></a>Module Windows PowerShell

Le support de PowerShell Core ne s’étend pas aux autres modules du produit, sauf si ces modules prennent explicitement en charge PowerShell Core.
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
