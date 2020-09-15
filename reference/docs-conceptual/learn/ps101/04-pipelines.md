---
title: Éléments à une ligne et pipeline
description: Un one-liner PowerShell est un pipeline continu, contenant plusieurs commandes, qui permet d’accomplir une tâche unique.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fd45e5e5dc408754ebac015757ef4241428978
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633343"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a>Chapitre 4 : One-liners et pipeline

À mes débuts avec PowerShell, quand je ne réussissais pas à accomplir une tâche avec un one-liner PowerShell, je repassais dans l’interface graphique utilisateur. J’ai appris au fur et à mesure et maintenant, je sais développer des scripts, des fonctions et des modules. Ne vous laissez pas décourager par certains exemples les plus avancés que vous pouvez voir sur Internet. Nul ne naît expert de PowerShell. Nous avons tous été débutants à un moment donné.

Je voudrais donner un petit conseil à ceux d’entre vous qui utilisent toujours l’interface utilisateur graphique pour l’administration : installez les outils de gestion sur votre station de travail d’administration et gérez vos serveurs à distance. De cette façon, cela n’aura pas d’importance si votre serveur exécute une installation GUI ou minimale du système d’exploitation.
Cela vous aidera à vous préparer à la gestion des serveurs à distance avec PowerShell.

Comme dans les chapitres précédents, assurez-vous de suivre ce chapitre sur votre ordinateur dans un environnement lab Windows 10.

## <a name="one-liners"></a>One-liners

Un one-liner PowerShell est un pipeline continu, mais pas obligatoirement une commande sur une seule ligne physique. Les commandes sur une seule ligne physique ne sont pas toutes des one-liners.

Par exemple, bien que la commande ci-dessous soit sur plusieurs lignes physiques, c’est un one-liner PowerShell, car il s’agit d’un pipeline continu. J’aurais pu l’écrire sur une seule ligne physique, mais j’ai choisi d’insérer un saut de ligne après le symbole de barre verticale. Le symbole de barre verticale est l’un des caractères où un saut de ligne naturel est autorisé dans PowerShell.

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

Des sauts de ligne naturels peuvent se produire avec des caractères fréquemment employés, comme les virgules (`,`), les crochets ouvrants (`[`), les accolades (`{`) et les parenthèses (`(`). D’autres caractères moins courants sont le point-virgule (`;`), le signe égal (`=`), et les guillemets ouvrants simples et doubles (`'`, `"`).

L’utilisation de l’apostrophe inversée (`` ` ``) ou accent grave comme caractère de continuation de ligne est contestée. Ma recommandation est d’éviter de l’utiliser autant que possible. Je vois souvent des commandes PowerShell où il y a une apostrophe inversée juste après un caractère de saut de ligne naturel.
Cette apostrophe n’a aucune raison d’être là.

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

Les commandes présentées dans les deux exemples précédents fonctionnent correctement dans la console PowerShell. Cependant, si vous essayez de les exécuter dans le volet console de PowerShell ISE, une erreur se produit. La raison est que le volet console de PowerShell ISE n’attend pas que le reste de la commande soit entré sur la ligne suivante comme le fait la console PowerShell. Pour éviter ce problème dans le volet console de PowerShell ISE, appuyez sur les deux touches <kbd>Maj</kbd>+<kbd>Entrée</kbd> au lieu d’appuyer seulement sur <kbd>Entrée</kbd> quand une commande doit continuer sur une autre ligne.

L’exemple suivant n’est pas un one-liner PowerShell, car ce n’est pas un pipeline continu. Il s’agit en fait de deux commandes distinctes sur une seule ligne, séparées par un point-virgule.

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Dans beaucoup de langages de programmation et de script, la présence d’un point-virgule à la fin de chaque ligne est obligatoire. Cela est possible de faire la même chose dans PowerShell, mais cela n’est pas recommandé car non nécessaire.

## <a name="filtering-left"></a>Filtrage à gauche

Les résultats des commandes présentées dans ce chapitre ont été filtrés afin que seule une partie soit affichée. Par exemple, `Get-Service` a été utilisé avec le paramètre **Name** pour filtrer la liste des services et retourner uniquement les données du service de temps Windows.

Filtrez toujours les résultats le plus tôt possible dans le pipeline pour les limiter aux données qui vous intéressent vraiment. Cela se fait en utilisant les paramètres dans la première commande ou celle à l’extrême gauche.
Cette méthode est parfois appelée _filtrage à gauche_.

L’exemple suivant utilise le paramètre **Name** de `Get-Service` pour filtrer immédiatement les résultats sur le service de temps Windows uniquement.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Il n’est pas rare de voir des exemples où la commande est redirigée vers `Where-Object` pour effectuer le filtrage.

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

Le premier exemple filtre à la source et retourne uniquement les résultats pour le service de temps Windows.
Le deuxième exemple retourne tous les services, puis il les redirige vers une autre commande qui effectuera le filtrage. Ce n’est pas un problème dans cet exemple, mais imaginez si vous faisiez une requête sur une liste d’utilisateurs Active Directory. Voudriez-vous vraiment retourner les informations de plusieurs milliers de comptes d’utilisateur à partir d’Active Directory dans le seul but de les rediriger vers une autre commande qui les filtrera pour en retourner seulement une petite partie ? Ma recommandation est de toujours filtrer à gauche, même si cela ne semble pas utile. En adoptant cette pratique, vous filtrerez automatiquement à gauche sans même y penser quand cela sera vraiment nécessaire.

Un jour, quelqu’un m’avait dit que l’ordre de spécification des commandes n’avait pas d’importance. Rien n’était plus faux. L’ordre dans lequel les commandes sont spécifiées est bien sûr important pour le filtrage. Imaginons le scénario dans lequel vous utilisez `Select-Object` pour sélectionner uniquement quelques propriétés et `Where-Object` pour filtrer sur des propriétés qui ne seront pas dans la sélection. Dans ce scénario, le filtrage doit être la première opération ; sinon, la propriété n’existera pas dans le pipeline au moment où vous tenterez d’effectuer le filtrage.

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

La commande dans l’exemple précédent ne retourne aucun résultat, car la propriété **CanStopAndContinue** n’existe pas quand les résultats de `Select-Object` sont redirigés vers `Where-Object`. Cette propriété particulière n’a pas été « sélectionnée ». En fait, elle a été filtrée. Il suffit d’inverser l’ordre de `Select-Object` et `Where-Object` pour obtenir les résultats souhaités.

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a>Pipeline

Comme vous l’avez vu dans la plupart des exemples de ce livre étudiés jusqu’ici, la sortie d’une commande peut souvent être utilisée comme entrée d’une autre commande. Dans le chapitre 3, `Get-Member` a été utilisé pour déterminer le type d’objet qu’une commande génère. Le chapitre 3 a également montré comment utiliser le paramètre **ParameterType** de `Get-Command` pour déterminer quelles commandes acceptaient ce type d’entrée, mais pas forcément en entrée de pipeline.

Si l’aide sur les commandes fournit des informations détaillées, elle peut inclure une section **INPUTS** et une section **OUTPUTS**.

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

Seule la section pertinente de l’aide est affichée dans les résultats précédents. Comme vous pouvez le voir, la section **INPUTS** indique qu’un objet **ServiceController** ou **String** peut être redirigé vers l’applet de commande `Stop-Service`. Elle ne précise pas quels paramètres acceptent ce type d’entrée. L’une des méthodes les plus simples pour avoir cette information est d’examiner les différents paramètres dans la version complète (Full) de l’aide sur l’applet de commande `Stop-Service`.

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

Là encore, seule la partie pertinente de l’aide est affichée dans le jeu de résultats précédent. Notez que le paramètre **DisplayName** n’accepte pas l’entrée de pipeline, que le paramètre **InputObject** accepte l’entrée de pipeline **par valeur** (ByValue) pour les objets **ServiceController**, et que le paramètre **Name** accepte l’entrée de pipeline **par valeur** pour les objets **String**. Il accepte également l’entrée de pipeline **par nom de propriété** (ByPropertyName).

Quand un paramètre accepte l’entrée de pipeline à la fois par nom de propriété et par valeur, il tente toujours l’entrée **par valeur** en premier. Si l’entrée **par valeur** échoue, il tente l’entrée **par nom de propriété**. Le terme **par valeur** est un peu trompeur. Je préfère l’appeler **par type**. Cela signifie que si vous redirigez les résultats d’une commande qui génère un type d’objet **ServiceController** vers `Stop-Service`, elle lie cette entrée au paramètre **InputObject**. Mais si vous redirigez les résultats d’une commande qui produit une sortie **String** vers `Stop-Service`, elle la lie au paramètre **Name**. Si vous redirigez les résultats d’une commande qui ne produit pas un objet **ServiceController** ou **String** vers `Stop-Service`, mais qui génère une sortie contenant une propriété appelée **Name**, elle lie la propriété **Name** de la sortie au paramètre **Name** de `Stop-Service`.

Déterminez le type de sortie que la commande `Get-Service` génère.

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

`Get-Service` produit un type d’objet ServiceController.

Comme vous l’avez vu précédemment dans l’aide, le paramètre **InputObject** de `Stop-Service` accepte les objets **ServiceController** via le pipeline **par valeur** (par type). Cela signifie que lorsque les résultats de l’applet de commande `Get-Service` sont redirigés vers `Stop-Service`, ils sont liés au paramètre **InputObject** de `Stop-Service`.

```powershell
Get-Service -Name w32time | Stop-Service
```

Essayons à présent avec une entrée de type chaîne. Redirigez `w32time` vers `Get-Member` simplement pour vérifier qu’il s’agit d’une chaîne.

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

Comme nous l’avons vu précédemment dans l’aide, le fait de rediriger une chaîne vers `Stop-Service` la lie **par valeur** au paramètre **Name** de `Stop-Service`. Testez-le en redirigeant `w32time` vers `Stop-Service`.

```powershell
'w32time' | Stop-Service
```

Notez que dans l’exemple précédent, j’ai mis des guillemets simples autour de la chaîne `w32time`. Dans PowerShell, vous devez toujours utiliser des guillemets simples au lieu de guillemets doubles, sauf si la chaîne entre guillemets contient une variable qui doit être développée à sa valeur réelle. Comme PowerShell n’a pas besoin d’analyser le contenu figurant entre des guillemets simples, votre code s’exécute un peu plus vite.

Créez un objet personnalisé pour tester l’entrée de pipeline par nom de propriété pour le paramètre **Name** de `Stop-Service`.

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

Le contenu de la variable **CustomObject** est un type d’objet **PSCustomObject** et inclut une propriété appelée **Name**.

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

Si vous placez la variable `$CustomObject` entre guillemets, vous devez utiliser des guillemets doubles.
Si vous utilisez des guillemets simples, la chaîne littérale `$CustomObject` sera redirigée vers `Get-Member` à la place de la valeur contenue dans la variable.

Rediriger le contenu de `$CustomObject` vers l’applet de commande `Stop-Service` le lie au paramètre **Name**, mais cette fois, il est lié **par nom de propriété** et pas **par valeur**, car le contenu de `$CustomObject` est un objet qui a une propriété appelée **Name**.

Dans cet exemple, je crée un autre objet personnalisé avec un nom de propriété différent, par exemple **Service**.

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

Une erreur est générée quand je tente de rediriger `$CustomObject` vers `Stop-Service`, car la commande ne produit pas d’objet **ServiceController** ou **String**, et ne comporte pas de propriété **Name**.

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

Si la sortie d’une commande n’est pas alignée avec les options d’entrée de pipeline définies pour une autre commande, `Select-Object` peut être utilisé pour renommer la propriété afin de faire correspondre les propriétés.

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

Dans cet exemple, `Select-Object` a été utilisé pour renommer la propriété **Service** en une propriété appelée **Name**.

La syntaxe de cet exemple peut paraître un peu compliquée de prime abord. Par expérience, je sais qu’on n’apprend pas la syntaxe simplement en copiant et en collant du code. Prenez le temps de taper vous-même le code. Après quelques temps, vous le ferez automatiquement. Travailler avec plusieurs moniteurs est très confortable, car vous pouvez afficher l’exemple de code sur un écran et taper votre code dans un autre.

Vous voudrez peut-être parfois utiliser un paramètre qui n’accepte pas d’entrée de pipeline. L’exemple suivant illustre l’utilisation de la sortie d’une commande comme entrée d’une autre commande. Commencez par enregistrer le nom complet de deux services Windows dans un fichier texte.

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

Vous pouvez exécuter la commande qui fournit la sortie nécessaire entre parenthèses comme valeur du paramètre de la commande qui doit utiliser l’entrée.

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

Pour ceux d’entre vous qui s’en souviennent, sachez que cela est similaire à l’ordre des opérations en algèbre. La commande entre parenthèses est toujours exécutée avant la partie externe de la commande.

## <a name="powershellget"></a>PowerShellGet

PowerShellGet est un module de PowerShell qui contient des commandes pour détecter, installer, publier et mettre à jour des modules PowerShell (et d’autres artefacts) vers ou à partir d’un dépôt NuGet. PowerShellGet est fourni avec PowerShell version 5.0 et versions ultérieures. Il est disponible en téléchargement pour PowerShell version 3.0 et versions ultérieures.

Microsoft héberge un dépôt NuGet en ligne appelé [PowerShell Gallery][]. Bien que ce dépôt soit hébergé par Microsoft, la majorité des modules contenus dans le dépôt ne sont pas développés par Microsoft. Tout code provenant du dépôt PowerShell Gallery doit être examiné minutieusement dans un environnement de test isolé avant d’être considéré comme approprié pour une utilisation dans un environnement de production.

La plupart des entreprises préfèrent héberger leur propre dépôt NuGet privé interne et l’utiliser pour publier leurs modules à usage interne uniquement, ainsi que les modules qu’ils ont téléchargés à partir d’autres sources une fois qu’ils ont été validés comme non malveillants.

Utilisez l’applet de commande `Find-Module` intégrée au module PowerShellGet pour rechercher dans le dépôt PowerShell Gallery un module que j’ai écrit et nommé MrToolkit.

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

La première fois que vous utilisez l’une des commandes du module PowerShellGet, vous êtes invité à installer le fournisseur NuGet.

Pour installer le module MrToolkit, redirigez la commande précédente vers `Install-Module`.

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

Étant donné que PowerShell Gallery est un dépôt non approuvé, vous êtes invité à approuver l’installation du module.

## <a name="finding-pipeline-input-the-easy-way"></a>Recherche d’une entrée de pipeline de manière simple

Le module MrToolkit contient une fonction nommée `Get-MrPipelineInput`. Cette applet de commande peut être utilisée pour déterminer facilement quels paramètres d’une commande acceptent l’entrée de pipeline, quel type d’objet ils acceptent et s’ils acceptent l’entrée de pipeline **par valeur** ou **par nom de propriété**.

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

Comme vous le voyez, cette fonction vous permet d’obtenir facilement les mêmes informations que celles que nous avons précédemment recherchées dans l’aide.

## <a name="summary"></a>Résumé

Dans ce chapitre, vous avez découvert ce que sont les one-liners PowerShell. Vous avez appris que le nombre de lignes physiques sur lesquelles une commande est spécifiée n’a rien à voir avec le fait qu’il s’agit ou non d’un one-liner PowerShell. Vous avez également appris en quoi consistent le filtrage à gauche, le pipeline et PowerShellGet.

## <a name="review"></a>Révision

1. Qu’est-ce qu’un one-liner PowerShell ?
1. Quels sont les caractères où des sauts de ligne naturels peuvent se produire dans PowerShell ?
1. Pourquoi faut-il filtrer à gauche ?
1. Quelles sont les deux façons dont une commande PowerShell peut accepter l’entrée de pipeline ?
1. Pourquoi ne devez-vous pas faire confiance aux commandes trouvées dans le dépôt PowerShell Gallery ?

## <a name="recommended-reading"></a>Lecture recommandée

- [about_Pipelines][]
- [about_Command_Syntax][]
- [about_Parameters][]
- [PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell Gallery]: https://www.powershellgallery.com/
