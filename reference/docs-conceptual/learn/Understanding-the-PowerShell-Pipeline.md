---
ms.date: 08/23/2018
keywords: powershell,applet de commande
title: Présentation des pipelines PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 05ab98b7261f4d41ade1788a924193eccda6318c
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623957"
---
# <a name="understanding-pipelines"></a>Présentation des pipelines

Les pipelines agissent comme une série de segments de canal connectés. Les éléments se déplaçant dans pipeline passent par chaque segment. Pour créer un pipeline dans PowerShell, vous interconnectez des commandes à l’aide de l’opérateur barre verticale « | » (pipe). La sortie de chaque commande est utilisée en tant qu’entrée pour la commande suivante.

La notation utilisée pour les pipelines est similaire celle utilisée dans d’autres interpréteurs de commandes. À première vue, les différences des pipelines dans PowerShell peuvent ne pas être évidentes. Même si vous voyez du texte à l’écran, PowerShell canalise des objets, pas du texte, entre les commandes.

## <a name="the-powershell-pipeline"></a>Le pipeline PowerShell

Les pipelines constituent indubitablement le concept plus important utilisé dans les interfaces de ligne de commande. Lorsqu’ils sont utilisés correctement, les pipelines réduisent l’effort lié à l’utilisation de commandes complexes et facilitent la visualisation du flux de travail pour les commandes. Chaque commande dans un pipeline (appelée élément de pipeline) transmet sa sortie à la commande suivante, élément par élément. Les commandes n’ont pas à gérer plusieurs éléments à la fois. Il en résulte une consommation réduite des ressources et la possibilité de commencer à recevoir la sortie immédiatement.

Par exemple, si vous utilisez la cmdlet `Out-Host` pour forcer un affichage page par page de la sortie d’une autre commande, la sortie ressemble exactement au texte normal affiché à l’écran, mais divisé en pages :

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

La pagination réduit également l’utilisation du processeur, car le traitement transfère à la cmdlet `Out-Host` lorsqu’il a une page complète prête à afficher. L’exécution des cmdlets qui la précèdent dans le pipeline est interrompue jusqu’à ce que la page suivante de la sortie soit disponible.

Vous pouvez voir la différence dans le Gestionnaire des tâches de Windows pour surveiller l’utilisation du processeur et de la mémoire par PowerShell. Exécutez la commande suivante : `Get-ChildItem C:\Windows -Recurse`. Comparez l’utilisation du processeur et de la mémoire avec cette commande : `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.

> [!NOTE]
> Tous les hôtes PowerShell ne prennent pas en charge le paramètre **Pagination**. Par exemple, lorsque vous tentez d’utiliser le paramètre **Pagination** dans PowerShell ISE, vous voyez l’erreur suivante :
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objets dans le pipeline

Lorsque vous exécutez une cmdlet dans PowerShell, vous voyez une sortie texte, car il est de nécessaire de représenter les objets sous forme de texte dans une fenêtre de console. La sortie texte peut ne pas afficher toutes les propriétés de l’objet en cours de sortie.

Prenez, par exemple, la cmdlet `Get-Location`. Si vous exécutez `Get-Location` alors que votre emplacement actuel est la racine du lecteur C, la sortie est la suivante :

```
PS> Get-Location

Path
----
C:\
```

La sortie texte est un résumé des informations, non une représentation complète de l’objet retourné par `Get-Location`. Le titre dans la sortie est ajouté par le processus qui met en forme les données pour l’affichage à l’écran.

Lorsque vous dirigez la sortie vers la cmdlet `Get-Member`, vous obtenez des informations sur l’objet retourné par `Get-Location`.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` retourne un objet **PathInfo** qui contient le chemin d’accès actuel et d’autres informations.
