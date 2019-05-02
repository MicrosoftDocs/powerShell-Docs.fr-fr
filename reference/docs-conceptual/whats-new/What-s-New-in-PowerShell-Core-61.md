---
title: Nouveautés de PowerShell Core 6.1
description: Nouvelles fonctionnalités et modifications de PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086106"
---
# <a name="whats-new-in-powershell-core-61"></a>Nouveautés de PowerShell Core 6.1

Vous trouverez dans cet article certaines des plus importantes modifications et nouvelles fonctionnalités de PowerShell Core 6.1.

Mais il y a aussi des **tonnes** d’autres « choses ennuyeuses » qui rendent PowerShell plus rapide et plus stable (ainsi que de nombreux correctifs de bogues) !
Pour obtenir la liste complète des modifications, consultez le [journal des modifications sur GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Nous profitons pour remercier [l’ensemble de la communauté des contributeurs](https://github.com/PowerShell/PowerShell/graphs/contributors) qui ont permis à cette version de voir le jour.

## <a name="net-core-21"></a>.NET Core 2.1

PowerShell Core 6.1 est passé à .NET Core 2.1 après sa [publication en mai](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), ce qui a permis plusieurs améliorations, notamment :

- Améliorations des performances (voir [ci-dessous](#performance-improvements))
- Prise en charge de Linux Alpine (préversion)
- [Prise en charge de l’outil global .NET](/dotnet/core/tools/global-tools) - bientôt disponible dans PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Pack de compatibilité Windows pour .NET Core

L’équipe .NET a publié le [Pack de compatibilité Windows pour .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), qui est un ensemble d’assemblys permettant de restaurer certaines API supprimées dans .NET Core sur Windows.

Nous avons ajouté le Pack de compatibilité Windows à PowerShell Core 6.1 pour que tous les modules et scripts qui utilisent ces API puissent compter sur leur disponibilité.

Le Pack de compatibilité Windows permet à PowerShell Core d’utiliser **plus de 1 900 applets de commande fournies avec la mise à jour d’octobre 2018 de Windows 10 et avec Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Prise en charge de la mise en liste verte des applications

Tout comme Windows PowerShell 5.1, PowerShell Core 6.1 prend en charge la mise en liste verte des applications pour [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) et [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).
La mise en liste verte des applications permet de contrôler précisément quels fichiers binaires peuvent être exécutés avec le [mode de langage limité](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) de PowerShell.

## <a name="performance-improvements"></a>Améliorations apportées aux performances

D’importantes améliorations avaient été apportées à PowerShell Core 6.0 au niveau des performances.
PowerShell Core 6.1 améliore encore davantage la vitesse de certaines opérations.

Par exemple, la vitesse d’exécution de `Group-Object` a augmenté de 66 % :

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Durée (s)   | 25,178                 | 19,653              | 6,641               |
| Accélération (en %) | Non applicable                    | 21,9 %               | 66,2 %               |

De même, les scénarios de tri similaires à celui-ci ont connu une amélioration de plus de 15 % :

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Durée (s)   | 12,170                 | 8,493               | 7,08                |
| Accélération (en %) | Non applicable                    | 30,2 %               | 16,6 %               |

L’exécution de l’opération `Import-Csv` a été considérablement accélérée après une régression de Windows PowerShell.
L’exemple suivant utilise un fichier CSV de test contenant 26 616 lignes et six colonnes :

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Durée (s)   | 0,441                  | 1,069               | 0,268                  |
| Accélération (en %) | Non applicable                    | -142,4 %             | 74,9 % (39,2 % sur WPS) |

Enfin, la conversion de code JSON en `PSObject` a été accélérée de plus de 50 % par rapport à Windows PowerShell.
L’exemple suivant utilise un fichier JSON de test d’environ 2 Mo :

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Durée (s)   | 0,259                  | 0,577               | 0,125                  |
| Accélération (en %) | Non applicable                    | -122,8 %             | 78,3 % (51,7 % sur WPS) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Consulter `system32` pour connaître les modules compatibles fournis avec Windows

Dans la mise à jour 1809 de Windows 10 et dans Windows Server 2019, nous avons mis à jour plusieurs des modules PowerShell fournis avec Windows, afin de les marquer comme compatibles avec PowerShell Core.

Lorsque PowerShell Core 6.1 démarre, il inclut automatiquement `$windir\System32` dans la variable d’environnement `PSModulePath`.
Toutefois, il expose uniquement les modules à `Get-Module` et `Import-Module` si son `CompatiblePSEdition` est marqué comme étant compatible avec `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Les modules qui sont disponibles peuvent varier selon les rôles et les fonctionnalités installés.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Vous pouvez remplacer ce comportement pour afficher tous les modules à l’aide du paramètre de commutateur `-SkipEditionCheck`.
Nous avons également ajouté une propriété `PSEdition` à la sortie de la table.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Pour plus d’informations sur ce comportement, consultez[PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Applets de commande de Markdown et de rendu

Le standard Markdown permet de créer des documents en texte clair avec une mise en forme de base qui peuvent être affichés en HTML.

Nous avons ajouté des applets de commande à la version 6.1 qui vous permettent de convertir et de restituer des documents Markdown dans la console, notamment :

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Par exemple, `Show-Markdown` restitue un fichier Markdown dans la console :

![Exemple Show-Markdown](./images/markdown_example.png)

Pour plus d’informations sur le fonctionnement de ces applets de commande, consultez [ce document RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Indicateurs de fonctionnalités expérimentales

Nous avons activé la prise en charge des [fonctionnalités expérimentales][]. Cela permet aux développeurs PowerShell de fournir de nouvelles fonctionnalités et d’obtenir des commentaires avant la fin de la conception. Cela nous évite ainsi d’avoir à apporter d’importantes modifications à mesure que la conception évolue.

Utilisez `Get-ExperimentalFeature` pour obtenir la liste des fonctionnalités expérimentales disponibles. Vous pouvez activer ou désactiver ces fonctionnalités avec `Enable-ExperimentalFeature` et `Disable-ExperimentalFeature`.

Pour plus d’informations sur ces fonctionnalités, consultez [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Améliorations apportées aux applets de commande web

Grâce à [@markekraus](https://github.com/markekraus), une myriade d’améliorations ont été apportées à nos applets de commande web [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
et [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [Demande de tirage #6109](https://github.com/PowerShell/PowerShell/pull/6109) - encodage par défaut défini sur UTF-8 pour les réponses `application-json`
- [Demande de tirage #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  paramètre `-SkipHeaderValidation`pour autoriser les en-têtes `Content-Type` qui ne sont pas conformes aux normes
- [Demande de tirage #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  paramètre `Form`permettant la prise en charge simplifiée de `multipart/form-data`
- [Demande de tirage #6338](https://github.com/PowerShell/PowerShell/pull/6338) - gestion des clés de relation conforme et ne respectant pas la casse
- [Demande de tirage #6447](https://github.com/PowerShell/PowerShell/pull/6447) - ajouter le paramètre `-Resume` pour les applets de commande web

## <a name="remoting-improvements"></a>Améliorations de la communication à distance

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>PowerShell Direct pour les conteneurs tente d’abord d’utiliser PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) est une fonctionnalité PowerShell et Hyper-V, qui vous permet de vous connecter à une machine virtuelle Hyper-V ou à un conteneur sans connectivité réseau ni service de gestion à distance.

Auparavant, PowerShell Direct se connectait à l’aide de l’instance Windows PowerShell fournie dans le conteneur.
À présent, PowerShell Direct tente d’abord de se connecter à l’aide de l’un des `pwsh.exe` disponibles dans la variable d’environnement `PATH`.
Si aucun `pwsh.exe` n’est disponible, PowerShell Direct utilise à nouveau `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>À présent, `Enable-PSRemoting` crée des points de terminaison de communication à distance distincts pour chaque préversion

À présent, `Enable-PSRemoting` crée deux configurations de session de communication à distance :

- Une pour la version principale de PowerShell. Par exemple, `PowerShell.6`. Pour les mises à jour de la version secondaire, ce point de terminaison peut correspondre à la configuration de session PowerShell 6 qui est appliquée à l’échelle du système
- Une configuration de session spécifique à une version, par exemple : `PowerShell.6.1.0`

Ce comportement est utile si vous souhaitez que plusieurs versions de PowerShell 6 soient installées et accessibles sur un même ordinateur.

En outre, les préversions de PowerShell peuvent désormais obtenir leurs propres configurations de session de communication à distance en exécutant l’applet de commande `Enable-PSRemoting` :

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

Votre sortie peut être différente si vous n’avez pas configuré WinRM au préalable.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Ensuite, vous pouvez voir les différentes configurations de session PowerShell pour la préversion et les builds stables de PowerShell 6, ainsi que pour chaque version.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>Syntaxe `user@host:port` prise en charge pour le protocole SSH

Les clients SSH prennent généralement en charge une chaîne de connexion au format `user@host:port`.
Avec l’ajout du protocole SSH pour la communication à distance PowerShell, nous permettons désormais la prise en charge de ce format de chaîne de connexion :

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Option MSI pour ajouter un menu contextuel de shell dans l’Explorateur Windows

Grâce à [@bergmeister](https://github.com/bergmeister), vous pouvez désormais activer un menu contextuel dans Windows. Vous pouvez ouvrir votre installation de PowerShell 6.1 à l’échelle du système à partir de n’importe quel dossier de l’Explorateur Windows :

![Menu contextuel de shell pour PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Avantages

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>Option « Exécuter en tant qu’administrateur » dans la liste de raccourcis Windows

Grâce à [@bergmeister](https://github.com/bergmeister), la liste de raccourcis de PowerShell Core comprend désormais l’option « Exécuter en tant qu’administrateur » :

![Option Exécuter en tant qu’administrateur dans la liste de raccourcis PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` retourne au répertoire précédent

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Sur Linux :

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

En outre, `cd` et `cd --` sont remplacés par `$HOME`.

### `Test-Connection`

Grâce à [@iSazonov](https://github.com/iSazonov), l’applet de commande [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) a été déplacée vers PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` en tant que non administrateur

À la demande générale, il n’est plus obligatoire d’exécuter `Update-Help` en tant qu’administrateur.
Par défaut, `Update-Help` enregistre l’aide dans un dossier de portée utilisateur.

### <a name="new-methodsproperties-on-pscustomobject"></a>Nouvelles méthodes et propriétés de `PSCustomObject`

Grâce à [@iSazonov](https://github.com/iSazonov), nous avons ajouté de nouvelles méthodes et propriétés à `PSCustomObject`.
`PSCustomObject` inclut désormais une propriété `Count`/`Length`, comme les autres objets.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

Cela inclut également les méthodes `ForEach` et `Where` qui vous permettent d’utiliser et de filtrer les éléments `PSCustomObject` :

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

Grâce à @SimonWahlin, nous avons ajouté le paramètre `-Not` à `Where-Object`.
Vous pouvez désormais filtrer un objet au niveau du pipeline pour y voir l’absence d’une propriété, ou la présence d’une valeur de propriété Null ou vide.

Par exemple, cette commande retourne tous les services dans lesquels aucun service dépendant n’est défini :

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` crée un document UTF-8 sans marque d’ordre d’octet

Compte tenu du passage au UTF-8 sans marque d’ordre d’octet dans PowerShell 6.0, nous avons mis à jour l’applet de commande `New-ModuleManifest` pour créer un document UTF-8 sans marque d’ordre d’octet, au lieu d’un document UTF-16.

### <a name="conversions-from-psmethod-to-delegate"></a>Conversions de PSMethod en Delegate

Grâce à [@powercode](https://github.com/powercode), nous prenons désormais en charge la conversion d’un `PSMethod` en un délégué.
Vous pouvez ainsi effectuer des opérations comme passer `PSMethod` `[M]::DoubleStrLen` en tant que valeur de délégué dans `[M]::AggregateString` :

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Pour plus d’informations sur cette modification, consultez [Demande de tirage #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Écart type dans `Measure-Object`

Grâce à [@CloudyDino](https://github.com/CloudyDino), nous avons ajouté une propriété `StandardDeviation` à `Measure-Object` :

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Grâce à [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` comprend désormais le paramètre `Password`, qui accepte un `SecureString`. Cela vous permet de l’utiliser de manière non interactive :

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Suppression de la fonction `more`

Auparavant, PowerShell fournissait une fonction appelée `more` dans Windows qui wrappait `more.com`.
Cette fonction a été supprimée.

En outre, la fonction `help` utilise désormais `more.com` dans Windows, ou un récepteur système par défaut spécifié par `$env:PAGER` sur les plateformes non Windows.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` renvoie désormais les utilisateurs au répertoire de travail actuel du lecteur

Auparavant, l’utilisation de `Set-Location` ou de `cd` pour retourner à un PSDrive avait pour effet d’envoyer les utilisateurs à l’emplacement par défaut du lecteur.

Grâce à [@mcbobke](https://github.com/mcbobke), les utilisateurs sont désormais envoyés vers le dernier répertoire de travail connu pour cette session.

### <a name="windows-powershell-type-accelerators"></a>Accélérateurs de type Windows PowerShell

Dans Windows PowerShell, nous avons inclus les accélérateurs de type suivants afin de faciliter l’utilisation des différents types :

- `[adsi]` : `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]` : `System.DirectoryServices.DirectorySearcher`
- `[wmi]` : `System.Management.ManagementObject`
- `[wmiclass]` : `System.Management.ManagementClass`
- `[wmisearcher]` : `System.Management.ManagementObjectSearcher`

Ces accélérateurs de type n’étaient pas inclus dans PowerShell 6. Ils sont désormais disponibles dans PowerShell 6.1 pour Windows.

Ces types facilitent la construction d’objets AD et WMI.

Par exemple, vous pouvez exécuter des requêtes avec LDAP :

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

L’exemple suivant crée un objet CIM Win32_OperatingSystem :

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

Cet exemple retourne un objet ManagementClass pour la classe Win32_OperatingSystem.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>Alias `-lp` pour tous les paramètres `-LiteralPath`

Grâce à [@kvprasoon](https://github.com/kvprasoon), nous disposons désormais d’un alias de paramètre `-lp` pour toutes les applets de commande PowerShell intégrées qui ont un paramètre `-LiteralPath`.

## <a name="breaking-changes"></a>Modifications importantes

### <a name="msi-based-installation-paths-on-windows"></a>Chemins d’installation MSI dans Windows

Dans Windows, le package MSI est désormais installé au chemin suivant :

- `$env:ProgramFiles\PowerShell\6\` pour l’installation stable de 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` pour l’installation de la préversion de 6.x

Cette modification garantit que PowerShell Core pourra faire l’objet de mises à jour et de maintenances par Microsoft Update.

Pour plus d’informations, consultez [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Les données de télémétrie peuvent uniquement être désactivées avec une variable d’environnement

PowerShell Core envoie des données de télémétrie de base à Microsoft au lancement de celui-ci. Les données incluent le nom du système d’exploitation, la version du système d’exploitation et la version de PowerShell. Ces données nous permettent de mieux comprendre les environnements dans lesquels PowerShell est utilisé, ainsi que de classer par ordre de priorité les correctifs et les nouvelles fonctionnalités.

Pour refuser la collecte de ces données de télémétrie, définissez la variable d’environnement `POWERSHELL_TELEMETRY_OPTOUT` sur `true`, `yes` ou `1`. Il n’est plus possible de supprimer le fichier `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` pour désactiver la télémétrie.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Interdiction de l’authentification de base via HTTP pour la communication à distance PowerShell sur les plateformes Unix

Pour empêcher l’utilisation de trafic non chiffré, la communication à distance PowerShell sur les plateformes Unix exige désormais une authentification NTLM/Negotiate ou HTTPS.

Pour plus d’informations sur ces modifications, consultez [Problème #6779](https://github.com/PowerShell/PowerShell/issues/6779).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Suppression de `VisualBasic` comme langage pris en charge dans Add-Type

Auparavant, vous pouviez compiler du code Visual Basic à l’aide de l’applet de commande `Add-Type`.
Visual Basic était rarement utilisé avec `Add-Type`. Nous avons supprimé cette fonctionnalité afin de réduire la taille de PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Nettoyage des utilisations de `CommandTypes.Workflow` et `WorkflowInfoCleaned`

Pour plus d’informations sur ces modifications, consultez [Demande de tirage #6708](https://github.com/PowerShell/PowerShell/pull/6708).

### <a name="group-object-now-sorts-the-groups"></a>Group-Object trie désormais les groupes

Dans le cadre de l’amélioration des performances, `Group-Object` renvoie désormais une liste triée des groupes.
Bien que vous ne deviez pas vous fier à l’ordre, vous pouvez être désactivé à cause de cette modification si vous souhaitiez le premier groupe. Nous avons décidé que l’amélioration des performances valait cette modification dans la mesure où l’impact de la dépendance sur le comportement précédent est faible.

Pour plus d’informations sur cette modification, consultez le [Problème #7409](https://github.com/PowerShell/PowerShell/issues/7409).

<!-- URL references -->
[Fonctionnalités expérimentales]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
