---
title: Nouveautés de PowerShell Core 6.0
description: Nouvelles fonctionnalités et modifications publiées dans PowerShell Core 6.0
ms.date: 08/06/2018
ms.openlocfilehash: 18650733117d81e3b8d714960b95b4921122ed32
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96833794"
---
# <a name="whats-new-in-powershell-core-60"></a>Nouveautés de PowerShell Core 6.0

[PowerShell Core 6.0][github] est une nouvelle édition de PowerShell multiplateforme (Windows, macOS et Linux), open source et conçue pour des environnements hétérogènes et le cloud hybride.

## <a name="moved-from-net-framework-to-net-core"></a>Passage du .NET Framework à .NET Core

PowerShell Core utilise [.NET Core 2.0][] comme runtime. .NET Core 2.0 permet à PowerShell Core de fonctionner sur plusieurs plateformes (Windows, macOS et Linux). PowerShell Core expose également l’ensemble d’API offert par .NET Core 2.0 à utiliser dans les scripts et les applets de commande PowerShell.

Windows PowerShell utilisait le runtime .NET Framework pour héberger le moteur PowerShell. Cela signifie que Windows PowerShell expose l’ensemble d’API offert par le .NET Framework.

Les API partagées entre .NET Core et le .NET Framework sont définies dans le cadre de [.NET Standard][].

Pour plus d’informations sur la manière dont cela affecte la compatibilité des modules/scripts entre PowerShell Core et Windows PowerShell, consultez [Compatibilité descendante avec Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Prise en charge de macOS et Linux

PowerShell prend désormais officiellement en charge macOS et Linux, notamment :

- Windows 7, 8.1 et 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Canal semi-annuel Windows Server][semi-annual]
- Ubuntu 14.04, 16.04 et 17.04
- Debian 8.7+ et 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

Notre communauté a également proposé des packages pour les plateformes suivantes, mais ils ne sont pas officiellement pris en charge :

- Arch Linux
- Kali Linux
- AppImage (fonctionne sur plusieurs plateformes Linux)

Nous avons également des versions expérimentales (non prises en charge) pour les plateformes suivantes :

- Windows sur ARM32/ARM64
- Raspbian (Stretch)

Un certain nombre de modifications ont été apportées à PowerShell Core 6.0 pour qu’il fonctionne mieux sur les systèmes autres que Windows. Certaines de ces modifications étant avec rupture, elles affectent également Windows. D’autres sont uniquement présentes ou applicables dans des installations non-Windows de PowerShell Core.

- Ajout de la prise en charge du globbing des commandes natives sur les plateformes Unix.
- La fonctionnalité `more` respecte l’élément `$PAGER` Linux et a comme valeur par défaut `less`. Cela signifie que vous pouvez maintenant utiliser des caractères génériques avec les fichiers binaires/commandes natifs (par exemple, `ls *.txt`). (#3463)
- La barre oblique inverse de fin est automatiquement placée dans une séquence d’échappement quand vous traitez des arguments de commande native. (#4965)
- Le commutateur `-ExecutionPolicy` doit être ignoré lors de l’exécution de PowerShell sur les plateformes non-Windows, car la signature de script n’est actuellement pas prise en charge. (#3481)
- Correction de ConsoleHost pour honorer `NoEcho` sur les plateformes Unix. (#3801)
- Correction de `Get-Help` pour prendre en charge les critères spéciaux ne respectant par la casse sur les plateformes Unix. (#3852)
- Page man `powershell` ajoutée au package

### <a name="logging"></a>Journalisation

Sur macOS, PowerShell utilise les API `os_log` natives pour se connecter au [système de journalisation unifiée][os_log] d’Apple. Sur Linux, PowerShell utilise [Syslog][], une solution de journalisation très répandue.

### <a name="filesystem"></a>FileSystem

Un certain nombre de modifications ont été apportées à macOS et Linux pour prendre en charge les caractères de nom de fichier généralement non pris en charge sur Windows :

- Les chemins associés aux applets de commande sont désormais indépendants des barres obliques (/ et \ fonctionnent tous deux comme séparateur de répertoire)
- La spécification de répertoire de base XDG est maintenant respectée et utilisée par défaut :
  - Le chemin du profil Linux/macOS se trouve dans `~/.config/powershell/profile.ps1`
  - Le chemin d’enregistrement de l’historique se trouve dans `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Le chemin du module utilisateur se trouve dans `~/.local/share/powershell/Modules`
- Prise en charge des noms de fichier et de dossier qui contiennent le caractère deux-points sous Unix. (#4959)
- Prise en charge des noms de script ou des chemins complets qui contiennent des virgules. (#4136) (merci à [@TimCurwick](https://github.com/TimCurwick) !)
- Détection de l’utilisation de `-LiteralPath` afin de supprimer le développement des caractères génériques pour les applets de commande de navigation. (#5038)
- Mise à jour de `Get-ChildItem` pour fonctionner de manière plus similaire aux commandes natives *nix `ls -R` et Windows `DIR /S`. `Get-ChildItem` retourne désormais les liens symboliques rencontrés lors d’une recherche récursive et n’effectue aucune recherche dans les répertoires ciblés par ces liens. (#3780)

### <a name="case-sensitivity"></a>Respect de la casse

Linux et macOS ont tendance à respecter la casse, tandis que Windows ne la respecte pas, tout en la préservant.
En règle générale, PowerShell ne respecte pas la casse.

Par exemple, les variables d’environnement respectant la casse sur macOS et Linux, la casse de la variable d’environnement `PSModulePath` a été normalisée. (#3255) `Import-Module` ne respecte pas la casse quand il utilise un chemin de fichier pour déterminer le nom du module. (#5097)

## <a name="support-for-side-by-side-installations"></a>Prise en charge des installations côte à côte

PowerShell Core est installé, configuré et exécuté séparément de Windows PowerShell.
PowerShell Core possède un package ZIP « portable ». À l’aide du package ZIP, vous pouvez installer un nombre quelconque de versions n’importe où sur le disque, notamment en local sur une application qui accepte PowerShell en tant que dépendance.
Une installation côte à côte facilite le test de nouvelles versions de PowerShell et la migration de scripts existants au fil du temps. Elle permet également une compatibilité descendante, car les scripts peuvent être épinglés aux versions spécifiques dont ils ont besoin.

> [!NOTE]
> Par défaut, le programme d’installation MSI sur Windows effectue une installation de mise à jour sur place.

## <a name="renamed-powershellexe-to-pwshexe"></a>`powershell(.exe)` renommé en `pwsh(.exe)`

Le nom binaire pour PowerShell Core `powershell(.exe)` a été remplacé par `pwsh(.exe)`. Cette modification fournit aux utilisateurs un moyen déterministe d’exécuter PowerShell Core sur les ordinateurs pour prendre en charge les installations Windows PowerShell et PowerShell Core côte à côte. `pwsh` est également beaucoup plus court et facile à taper.

Autres modifications apportées à `pwsh(.exe)` par rapport à `powershell.exe` :

- Remplacement du premier paramètre positionnel `-Command` par `-File`. Cette modification résout l’utilisation de `#!` (également appelé shebang) dans les scripts PowerShell qui sont exécutés à partir de shells autres que PowerShell sur des plateformes non-Windows. Cela signifie également que vous pouvez exécuter des commandes telles que `pwsh foo.ps1` ou `pwsh fooScript` sans spécifier `-File`. Toutefois, cette modification nécessite que vous indiquiez explicitement `-c` ou `-Command` quand vous essayez d’exécuter des commandes telles que `pwsh.exe -Command Get-Command`.
  (#4019)
- PowerShell Core accepte le commutateur `-i` (ou `-Interactive`) pour indiquer un shell interactif.
  (#3558) Cela permet d’utiliser PowerShell comme shell par défaut sur les plateformes Unix.
- Paramètres `-importsystemmodules` et `-psconsoleFile` supprimés de `pwsh.exe`. (#4995)
- Modification de `pwsh -version` et de l’aide intégrée pour `pwsh.exe` afin de s’aligner sur les autres outils natifs. (#4958 & #4931) (merci [@iSazonov](https://github.com/iSazonov))
- Messages d’erreur d’arguments non valides pour `-File` et `-Command`, et codes de sortie conformes aux normes Unix (#4573)
- Ajout du paramètre `-WindowStyle` sur Windows. (#4573) De même, les mises à jour des installations basées sur le package sur des plateformes non-Windows sont des mises à jour sur place.

## <a name="backwards-compatibility-with-windows-powershell"></a>Compatibilité descendante avec Windows PowerShell

L’objectif de PowerShell Core est de rester aussi compatible que possible avec Windows PowerShell.
PowerShell Core utilise [.NET Standard][] 2.0 pour assurer la compatibilité binaire avec des assemblys .NET existants. Comme un grand nombre de modules PowerShell dépendent de ces assemblys (souvent des DLL), .NET Standard leur permet de continuer à utiliser .NET Core. PowerShell Core inclut également une heuristique pour examiner les dossiers connus (comme celui où se trouve généralement le Global Assembly Cache sur le disque) et rechercher les dépendances des DLL .NET Framework.

Vous pouvez en savoir plus sur .NET Standard sur le [Blog .NET][], dans cette vidéo [YouTube][] et via ce [FORUM AUX QUESTIONS][] sur GitHub.

Tout a été mis en œuvre pour garantir que le langage PowerShell et les modules « intégrés » (comme `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, etc.) fonctionnent de la même manière que dans Windows PowerShell. Dans de nombreux cas, avec l’aide de la communauté, nous avons ajouté de nouvelles fonctionnalités et des résolutions de bogues à ces applets de commande. Dans certains cas, en raison d’une dépendance manquante dans les couches .NET sous-jacentes, la fonctionnalité a été supprimée ou n’est pas disponible.

La plupart des modules qui font partie de Windows (par exemple, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, etc.) et d’autres produits Microsoft, dont Azure et Office, n’ont pas encore été *explicitement* déplacés vers. NET Core. L’équipe PowerShell travaille avec ces équipes et groupes de produits pour valider et déplacer leurs modules existants vers PowerShell Core. Avec .NET Standard et [CDXML][], la plupart de ces modules Windows PowerShell classiques semblent fonctionner dans PowerShell Core, mais ils n’ont pas été clairement validés et ne sont pas formellement pris en charge.

En installant le module [`WindowsPSModulePath`][windowspsmodulepath], vous pouvez utiliser des modules Windows PowerShell en ajoutant `PSModulePath` Windows PowerShell à `PSModulePath` PowerShell Core.

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

## <a name="docker-support"></a>Prise en charge de Docker

PowerShell Core ajoute la prise en charge des conteneurs Docker pour toutes les principales plateformes que nous prenons en charge (dont plusieurs distributions Linux, Windows Server Core et Nano Server).

Pour obtenir la liste complète, consultez les étiquettes sur [`microsoft/powershell` sur Docker Hub][docker-hub]. Pour plus d’informations sur Docker et PowerShell Core, consultez [Docker][] sur GitHub.

## <a name="ssh-based-powershell-remoting"></a>Communication à distance PowerShell SSH

Le protocole de communication à distance PowerShell fonctionne désormais avec le protocole SSH (Secure Shell) en plus du protocole de communication à distance PowerShell WinRM classique.

Cela signifie que vous pouvez utiliser des applets de commande comme `Enter-PSSession` et `New-PSSession`, et vous authentifier à l’aide de SSH. Il vous suffit d’inscrire PowerShell comme un sous-système avec un serveur SSH basé sur OpenSSH, et vous pouvez utiliser vos mécanismes d’authentification SSH existants (tels que les mots de passe ou les clés privées) avec la sémantique `PSSession` classique.

Pour plus d’informations sur la configuration et l’utilisation de la communication à distance SSH, consultez [Communication à distance PowerShell via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>L’encodage par défaut est UTF-8 sans marque d’ordre d’octet à l’exception de New-ModuleManifest

Dans le passé, les applets de commande Windows PowerShell telles que `Get-Content` ou `Set-Content` utilisaient des encodages différents comme ASCII et UTF-16. Le changement des valeurs par défaut d’encodage générait des problèmes lors de l’association d’applets de commande sans spécifier d’encodage.

Les plateformes autres que Windows utilisent en général UTF-8 sans marque d’ordre d’octet comme encodage par défaut pour les fichiers texte. D’autres outils et applications Windows passent de l’encodage UTF-16 à l’encodage UTF-8 sans marque d’ordre d’octet. PowerShell Core modifie l’encodage par défaut pour se conformer aux plus larges écosystèmes.

Cela signifie que toutes les applets de commande intégrées qui utilisent le paramètre `-Encoding` utilisent la valeur par défaut `UTF8NoBOM`. Les applets de commande suivantes sont affectées par cette modification :

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

Ces applets de commande ont également été mises à jour afin que le paramètre `-Encoding` accepte universellement `System.Text.Encoding`.

La valeur par défaut `$OutputEncoding` a également été remplacée par UTF-8.

Comme bonne pratique, vous devez définir explicitement des encodages dans les scripts à l’aide du paramètre `-Encoding` pour produire un comportement déterministe sur plusieurs plateformes.

La cmdlet `New-ModuleManifest` ne dispose pas du paramètre **Encodage**. L’encodage du fichier de manifeste (.psd1) du module créé avec la cmdlet `New-ModuleManifest` dépend de l’environnement : s’il s’agit de PowerShell Core exécuté sur Linux, alors l’encodage est UTF-8 (sans marque d’ordre d’octet) ; sinon, l’encodage est UTF-16 (avec marque d’ordre d’octet). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Prendre en charge le lancement en arrière-plan des pipelines avec l’esperluette (`&`) (#3360)

Le caractère `&` placé à la fin d’un pipeline entraîne l’exécution du pipeline comme une tâche PowerShell. Quand un pipeline est lancé en arrière-plan, un objet de traitement est retourné. Une fois que le pipeline est exécuté en tant que tâche, toutes les applets de commande `*-Job` standard peuvent être utilisées pour gérer la tâche. Les variables (en ignorant celles spécifiques au processus) utilisées dans le pipeline étant automatiquement copiées dans la tâche, `Copy-Item $foo $bar &` fonctionne tout simplement. La tâche est également exécutée dans le répertoire actuel au lieu du répertoire de base de l’utilisateur. Pour plus d’informations sur les tâches PowerShell, consultez [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

## <a name="semantic-versioning"></a>Gestion sémantique de version

- `SemanticVersion` est devenu compatible avec `SemVer 2.0`. (#5037) (merci [@iSazonov](https://github.com/iSazonov) !)
- Remplacement de la valeur `ModuleVersion` par défaut dans `New-ModuleManifest` par `0.0.1` pour s’aligner sur SemVer. (#4842) (merci [@LDSpits](https://github.com/LDSpits))
- Ajout de `semver` comme accélérateur de type pour `System.Management.Automation.SemanticVersion`. (#4142) (merci à [@oising](https://github.com/oising) !)
- Activation de la comparaison entre une instance `SemanticVersion` et une instance `Version` qui est construite uniquement avec les valeurs de version `Major` et `Minor`.

## <a name="language-updates"></a>Mises à jour du langage

- Implémentation de l’analyse de la séquence d’échappement Unicode afin que les utilisateurs puissent utiliser des caractères Unicode comme arguments, chaînes ou noms de variables. (#3958) (merci à [@rkeithhill](https://github.com/rkeithhill) !)
- Ajout d’un nouveau caractère d’échappement pour Échap :`` `e``
- Ajout de la prise en charge de la conversion des enums en chaîne (#4318) (merci [@KirkMunro](https://github.com/KirkMunro))
- Correction du cast d’un seul tableau d’éléments en une collection générique. (#3170)
- Ajout d’une surcharge de plage de caractères à l’opérateur `..` de sorte que `'a'..'z'` retourne les caractères 'a' à 'z'. (#5026) (merci [@IISResetMe](https://github.com/IISResetMe) !)
- Correction d’une attribution de variable pour ne pas écraser des variables en lecture seule
- Transmission des variables locales de variables automatiques à 'DottedScopes' lors de l’exécution des applets de commande de script dans l’étendue actuelle (#4709)
- Activation de l’utilisation de l’option « Singleline, Multiline » dans l’opérateur de fractionnement (#4721) (merci [@iSazonov](https://github.com/iSazonov))

## <a name="engine-updates"></a>Mises à jour du moteur

- `$PSVersionTable` a quatre nouvelles propriétés :
  - `PSEdition`: sa valeur est `Core` sur PowerShell Core et `Desktop` sur Windows PowerShell
  - `GitCommitId`: il s’agit de l’ID de validation Git de la branche ou balise Git où PowerShell a été généré.
    Sur les versions publiées, il est probable qu’il soit identique à `PSVersion`.
  - `OS`: il s’agit d’une chaîne de version du système d’exploitation retournée par `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: valeur retournée par `[System.Environment]::OSVersion.Platform` qui est égale à `Win32NT` sur Windows, `Unix` sur macOS et `Unix` sur Linux.
- Suppression de la propriété `BuildVersion` de `$PSVersionTable`. Cette propriété était fortement liée à la version de build Windows. Au lieu de cela, nous vous recommandons d’utiliser `GitCommitId` pour récupérer la version de build exacte de PowerShell Core. (#3877) (merci à [@iSazonov](https://github.com/iSazonov) !)
- Suppression de la propriété `ClrVersion` de `$PSVersionTable`. Cette propriété n’est pas pertinente pour .NET Core et y a été conservée uniquement pour des raisons d’héritage spécifiques qui ne s’appliquent pas à PowerShell.
- Ajout de trois nouvelles variables automatiques pour déterminer si PowerShell est exécuté dans un système d’exploitation particulier : `$IsWindows`, `$IsMacOs` et `$IsLinux`.
- Ajout de `GitCommitId` à la bannière PowerShell Core. Maintenant, vous n’êtes pas obligé d’exécuter `$PSVersionTable` dès que vous démarrez PowerShell pour obtenir la version ! (#3916) (merci à [@iSazonov](https://github.com/iSazonov) !)
- Ajout d’un fichier de configuration JSON appelé `powershell.config.json` dans `$PSHome` pour stocker des paramètres requis avant l’heure de démarrage (par exemple, `ExecutionPolicy`).
- Pas de blocage du pipeline lors de l’exécution des fichiers EXE Windows
- Activation de l’énumération des collections COM. (#4553)

## <a name="cmdlet-updates"></a>Mises à jour des applets de commande

### <a name="new-cmdlets"></a>Nouvelles applets de commande

- Ajout de `Get-Uptime` à `Microsoft.PowerShell.Utility`.
- Ajout de la commande `Remove-Alias`. (#5143) (merci [@PowershellNinja](https://github.com/PowershellNinja) !)
- Ajout de `Remove-Service` au module de gestion. (#4858) (merci [@joandrsn](https://github.com/joandrsn) !)

### <a name="web-cmdlets"></a>Applets de commande web

- Ajout de la prise en charge de l’authentification par certificat pour les applets de commande web. (#4646) (merci [@markekraus](https://github.com/markekraus))
- Ajout de la prise en charge des en-têtes de contenu aux applets de commande web. (#4494 & #4640) (merci [@markekraus](https://github.com/markekraus))
- Ajout de la prise en charge de plusieurs en-têtes de liens aux applets de commande web. (#5265) (merci [@markekraus](https://github.com/markekraus) !)
- Prise en charge de la pagination des en-têtes de liens dans les applets de commande web (#3828)
  - Pour `Invoke-WebRequest`, quand la réponse inclut un en-tête de lien, nous créons une propriété RelationLink sous forme d’un dictionnaire qui représente les URL et les attributs `rel`, puis vérifions que les URL sont absolues pour que le développeur puisse les utiliser plus facilement.
  - Pour `Invoke-RestMethod`, quand la réponse inclut un en-tête de lien, nous présentons un commutateur `-FollowRelLink` pour suivre automatiquement les liens `next` `rel` jusqu’à ce qu’ils n’existent plus ou que nous ayons atteint la valeur du paramètre `-MaximumFollowRelLink` facultative.
- Ajout du paramètre `-CustomMethod` aux applets de commande web pour autoriser les verbes de méthode non standard. (#3142) (merci à @Lee303 !)
- Ajout de la prise en charge de `SslProtocol` aux applets de commande web. (#5329) (merci [@markekraus](https://github.com/markekraus) !)
- Ajout de la prise en charge de Multipart aux applets de commande web. (#4782) (merci [@markekraus](https://github.com/markekraus))
- Ajout de `-NoProxy` aux applets de commande web afin qu’elles ignorent le paramètre de proxy à l’échelle du système. (#3447) (merci à [@TheFlyingCorpse](https://github.com/TheFlyingCorpse) !)
- L’agent utilisateur des applets de commande web signale désormais la plateforme du système d’exploitation (#4937) (merci [@LDSpits](https://github.com/LDSpits))
- Ajout du commutateur `-SkipHeaderValidation` aux applets de commande web pour prendre en charge l’ajout d’en-têtes sans valider la valeur d’en-tête. (#4085)
- Autorisation aux applets de commande web de ne pas valider le certificat HTTPS du serveur si nécessaire.
- Ajout de paramètres d’authentification aux applets de commande web. (#5052) (merci [@markekraus](https://github.com/markekraus))
  - Ajout de `-Authentication`, qui offre trois options : Basic, OAuth et Bearer.
  - Ajout de `-Token` pour obtenir le jeton du porteur pour les options OAuth et Bearer.
  - Ajout de `-AllowUnencryptedAuthentication` pour contourner l’authentification qui est fournie pour n’importe quel schéma de transport autre que HTTPS.
- Ajout de `-ResponseHeadersVariable` à `Invoke-RestMethod` pour activer la capture des en-têtes de réponse.
  (#4888) (merci [@markekraus](https://github.com/markekraus))
- Correction des applets de commande web pour inclure la réponse HTTP dans l’exception quand le code d’état de réponse n’indique pas une réussite. (#3201)
- Remplacement des applets de commande web `UserAgent``WindowsPowerShell` par `PowerShell`. (#4914) (merci [@markekraus](https://github.com/markekraus))
- Ajout d’une détection `ContentType` explicite à `Invoke-RestMethod` (#4692)
- Correction des applets de commande web `-SkipHeaderValidation` pour utiliser des en-têtes d’agent utilisateur non standard. (#4479 &
  #<a name="4512-thanks-markekraus"></a>4512) (merci [@markekraus](https://github.com/markekraus))

### <a name="json-cmdlets"></a>Applets de commande JSON

- Ajout de `-AsHashtable` à `ConvertFrom-Json` pour retourner `Hashtable` à la place. (#5043) (merci [@bergmeister](https://github.com/bergmeister) !)
- Utilisation d’un formateur amélioré avec une sortie `ConvertTo-Json`. (#2787) (merci à @kittholland !)
- Ajout de la prise en charge de sérialisation `Jobject` à `ConvertTo-Json`. (#5141)
- Correction de `ConvertFrom-Json` pour désérialiser un tableau de chaînes provenant du pipeline qui créent ensemble une chaîne JSON complète. Cela résout certains cas où les nouvelles lignes pourraient arrêter l’analyse JSON.
  (#3823)
- Suppression de la propriété `AliasProperty "Count"` définie pour `System.Array`. Cette opération supprime la propriété `Count` superflue sur certaines sorties `ConvertFrom-Json`. (#3231) (merci à [@PetSerAl](https://github.com/PetSerAl) !)

### <a name="csv-cmdlets"></a>Applets de commande CSV

- `Import-Csv` prend maintenant en charge le format de fichier journal étendu W3C (#2482) (Merci à [@iSazonov](https://github.com/iSazonov) !)
- Ajout de la prise en charge de `PSTypeName` pour `Import-Csv` et `ConvertFrom-Csv`. (#5389) (merci [@markekraus](https://github.com/markekraus) !)
- `Import-Csv` doit prendre en charge `CR`, `LF` et `CRLF` comme séparateurs de ligne. (#5363) (merci [@iSazonov](https://github.com/iSazonov) !)
- `-NoTypeInformation` doit être la valeur par défaut sur `Export-Csv` et `ConvertTo-Csv`. (#5164) (Merci à [@markekraus](https://github.com/markekraus) !)

### <a name="service-cmdlets"></a>Applets de commande de service

- Ajout des propriétés `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName` et `StartupType` aux objets `ServiceController` retournés par `Get-Service`. (#4907) (merci [@joandrsn](https://github.com/joandrsn))
- Ajout de fonctionnalités pour définir les informations d’identification sur la commande `Set-Service`. (#4844) (merci [@joandrsn](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Autres applets de commande

- Ajout d’un paramètre à `Get-ChildItem` appelé `-FollowSymlink` qui traverse les liens symboliques à la demande, avec des recherches de boucles de liens. (#4020)
- Mise à jour de `Add-Type` pour prendre en charge `CSharpVersion7`. (#3933) (merci à [@iSazonov](https://github.com/iSazonov))
- Suppression du module `Microsoft.PowerShell.LocalAccounts` en raison de l’utilisation des API non prises en charge jusqu’à ce qu’une meilleure solution soit trouvée. (#4302)
- Suppression des applets de commande `*-Counter` dans `Microsoft.PowerShell.Diagnostics` en raison de l’utilisation des API non prises en charge jusqu’à ce qu’une meilleure solution soit trouvée. (#4303)
- Ajout de la prise en charge de `Invoke-Item -Path <folder>`. (#4262)
- Ajout des commutateurs `-Extension` et `-LeafBase` à `Split-Path` afin que vous puissiez fractionner les chemins entre l’extension de nom de fichier et le reste du nom de fichier. (#2721) (merci à [@powercode](https://github.com/powercode) !)
- Ajout des paramètres `-Top` et `-Bottom` à `Sort-Object` pour un tri N haut/bas
- Exposition du processus parent d’un processus en ajoutant `CodeProperty "Parent"` à `System.Diagnostics.Process`. (#2850) (merci à [@powercode](https://github.com/powercode) !)
- Utilisation de Mo au lieu de Ko pour les colonnes de mémoire de `Get-Process`
- Ajout du commutateur `-NoNewLine` pour `Out-String`. (#5056) (merci [@raghav710](https://github.com/raghav710))
- L’applet de commande `Move-Item` honore les paramètres `-Include`, `-Exclude` et `-Filter`. (#3878)
- Autorisation d’utiliser `*` dans le chemin du Registre pour `Remove-Item`. (#4866)
- Ajout de `-Title` à `Get-Credential` et unification de l’expérience des invites sur plusieurs plateformes.
- Ajout du paramètre `-TimeOut` à `Test-Connection`. (#2492)
- Les applets de commande `Get-AuthenticodeSignature` peuvent désormais obtenir un horodatage de signature de fichier. (#4061)
- Suppression du commutateur `-ShowWindow` non pris en charge de `Get-Help`. (#4903)
- Correction de `Get-Content -Delimiter` pour ne pas inclure le séparateur dans les éléments de tableau retournés (#3706) (merci [@mklement0](https://github.com/mklement0))
- Ajout des paramètres `Meta`, `Charset` et `Transitional` à `ConvertTo-HTML` (#4184) (merci [@ergo3114](https://github.com/ergo3114))
- Ajout des propriétés `WindowsUBR` et `WindowsVersion` au résultat `Get-ComputerInfo`
- Ajout du paramètre `-Group` à `Get-Verb`
- Ajout de la prise en charge de `ShouldProcess` à `New-FileCatalog` et `Test-FileCatalog` (correctifs `-WhatIf` et `-Confirm`). (#3074) (merci à [@iSazonov](https://github.com/iSazonov) !)
- Ajout du commutateur `-WhatIf` à l’applet de commande `Start-Process` (#4735) (merci [@sarithsutha](https://github.com/sarithsutha))
- Ajout de `ValidateNotNullOrEmpty` à de nombreux paramètres existants.

## <a name="tab-completion"></a>Saisie semi-automatique via la touche Tab

- Inférence de type améliorée dans la saisie semi-automatique via la touche Tab en fonction des valeurs de variables d’exécution. (#2744) (merci à [@powercode](https://github.com/powercode) !) Cela permet la saisie semi-automatique via la touche Tab dans des situations comme :

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Ajout de la saisie semi-automatique via la touche Tab de table de hachage pour `-Property` de `Select-Object`. (#3625) (merci à [@powercode](https://github.com/powercode))
- Activation de la saisie semi-automatique d’argument pour `-ExcludeProperty` et `-ExpandProperty` de `Select-Object`.
  (#3443) (merci à [@iSazonov](https://github.com/iSazonov) !)
- Correction d’un bogue dans la saisie semi-automatique via la touche Tab pour que `native.exe --<tab>` puisse appeler l’intégralité du code natif. (#3633) (merci à [@powercode](https://github.com/powercode) !)

## <a name="breaking-changes"></a>Changements cassants

Nous avons introduit un certain nombre de modifications avec rupture dans PowerShell Core 6.0.
Pour plus d’informations sur ces modifications, consultez [Modifications cassantes dans PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Débogage

- Prise en charge du débogage pas à pas distant pour `Invoke-Command -ComputerName`. (#3015)
- Activation de la journalisation de débogage Binder dans PowerShell Core

## <a name="filesystem-updates"></a>Mises à jour de Filesystem

- Activation de l’utilisation du fournisseur Filesystem à partir d’un chemin UNC. ($4998)
- `Split-Path` fonctionne désormais avec des racines UNC
- `cd` sans argument se comporte maintenant comme `cd ~`
- Correction de PowerShell Core pour autoriser l’utilisation de chemins qui ont une longueur de plus de 260 caractères. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Résolutions de bogues et améliorations des performances

Nous avons apporté de *nombreuses* améliorations aux performances dans PowerShell, notamment dans le temps de démarrage, les diverses applets de commande intégrées et l’interaction avec des fichiers binaires natifs.

Nous avons également résolu un certain nombre de bogues dans PowerShell Core. Pour obtenir une liste complète des correctifs et modifications, consultez notre [journal des modifications][] sur GitHub.

## <a name="telemetry"></a>Télémétrie

- PowerShell Core 6.0 a ajouté la télémétrie à l’hôte de la console pour signaler deux valeurs (#3620) :
  - la plateforme du système d’exploitation (`$PSVersionTable.OSDescription`)
  - la version exacte de PowerShell (`$PSVersionTable.GitCommitId`)

Si vous souhaitez désactiver cette télémétrie, créez simplement une variable d’environnement `POWERSHELL_TELEMETRY_OPTOUT` avec l’une des valeurs suivantes : `true`, `1` ou `yes`. La création de la variable permet d’ignorer toutes les données de télémétrie avant même la première exécution de PowerShell. Nous prévoyons également d’exposer ces données de télémétrie et les insights tirés de la télémétrie dans le [tableau de bord de la communauté][community-dashboard]. Vous trouverez plus d’informations sur la façon dont nous utilisons ces données dans ce [billet de blog][telemetry-blog].

[Blog .NET]: https://devblogs.microsoft.com/dotnet/introducing-net-standard/
[.NET Core 2.0]: /dotnet/core/
[.NET Standard]: /dotnet/standard/net-standard
[breaking-changes]: breaking-changes-ps6.md
[CDXML]: /previous-versions/windows/desktop/wmi_v2/getting-started-with-cdxml
[journal des modifications]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[Questions fréquentes (FAQ)]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[github]: https://github.com/PowerShell/PowerShell
[os_log]: https://developer.apple.com/documentation/os/logging
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[ssh-remoting]: /powershell/scripting/learn/remoting/SSH-Remoting-in-PowerShell-Core
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[telemetry-blog]: https://devblogs.microsoft.com/powershell/powershell-open-source-community-dashboard/
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
