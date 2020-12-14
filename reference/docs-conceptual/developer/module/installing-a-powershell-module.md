---
ms.date: 09/13/2016
ms.topic: reference
title: Installation d’un module PowerShell
description: Installation d’un module PowerShell
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645334"
---
# <a name="installing-a-powershell-module"></a>Installation d’un module PowerShell

Après avoir créé votre module PowerShell, vous souhaitez probablement l’installer sur un système, afin que vous ou d’autres utilisateurs puissiez l’utiliser. En règle générale, l’opération consiste à copier les fichiers de module (soit le fichier .psm1 ou l’assembly binaire, le manifeste du module et tous les fichiers associés) dans un répertoire sur cet ordinateur. Pour un très petit projet, il peut suffire de copier et de coller les fichiers avec l’Explorateur Windows sur un seul ordinateur distant. Pour les plus grosses solutions toutefois, il peut être préférable de suivre un processus d’installation plus élaboré. Quelle que soit la façon dont le module est ajouté sur le système, PowerShell peut utiliser un certain nombre de techniques qui permettront aux utilisateurs de le trouver et de l’utiliser. Par conséquent, le problème principal de l’installation consiste à faire en sorte que PowerShell soit en mesure de le localiser. Pour plus d’informations, consultez [Importation d’un module PowerShell](./importing-a-powershell-module.md).

## <a name="rules-for-installing-modules"></a>Règles d’installation des modules

Les informations suivantes se rapportent à tous les modules, y compris ceux que vous créez pour votre propre usage, ceux que vous recevez d’autres parties et ceux que vous distribuez à des tiers.

### <a name="install-modules-in-psmodulepath"></a>Installation de modules dans PSModulePath

Dans la mesure du possible, installez tous les modules dans un chemin qui figure dans la variable d’environnement **PSModulePath** ou ajoutez le chemin du module à la valeur de cette variable d’environnement.

La variable d’environnement **PSModulePath** ($Env:PSModulePath) contient les emplacements des modules Windows PowerShell. Les cmdlets s’appuient sur la valeur de cette variable d’environnement pour rechercher des modules.

Par défaut, la valeur de la variable d’environnement **PSModulePath** contient les répertoires de modules système et utilisateur suivants. Vous pouvez toutefois les modifier et en ajouter d’autres.

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Cet emplacement est réservé aux modules fournis avec Windows. N’installez pas de modules à cet emplacement.

- `$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  Pour récupérer la valeur de la variable d’environnement **PSModulePath**, utilisez l’une des commandes suivantes.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Pour ajouter un chemin de module à la valeur de la variable d’environnement **PSModulePath**, suivez le format de commande ci-dessous. Ce format utilise la méthode **SetEnvironmentVariable** de la classe **System.Environment** pour appliquer une modification indépendante de la session à la variable d’environnement **PSModulePath**.

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Une fois que vous avez ajouté le chemin à **PSModulePath**, diffusez un message d’environnement au sujet de cette modification pour permettre à d’autres applications (notamment l’interpréteur de commandes) de la récupérer. Pour diffuser la modification, faites en sorte que le code d’installation de votre produit envoie un message **WM_SETTINGCHANGE** avec `lParam` défini sur la chaîne « Environment ». Veillez à envoyer le message une fois que le code d’installation de votre module a mis à jour **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Choix du nom de répertoire du module

Un module bien formé est un module stocké dans un répertoire portant le même nom que le nom de base d’au moins un des fichiers du répertoire du module. Windows PowerShell ne reconnaît pas comme modules les modules qui ne sont pas bien formés.

Le « nom de base » d’un fichier correspond au nom sans l’extension de nom de fichier. Dans un module bien formé, le nom du répertoire contenant les fichiers du module doit correspondre au nom de base d’au moins un des fichiers du module.

Dans l’exemple de module Fabrikam, le répertoire qui contient les fichiers du module est nommé « Fabrikam » et au moins un fichier possède le nom de base « Fabrikam ». Dans ce cas, Fabrikam.psd1 et Fabrikam.dll présentent tous les deux le nom de base « Fabrikam ».

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Effet d’une installation incorrecte

Si le module n’est pas bien formé et que son emplacement n’est pas inclus dans la valeur de la variable d’environnement **PSModulePath**, les fonctionnalités de découverte de base de Windows PowerShell, et notamment les suivantes, ne fonctionnent pas.

- La fonctionnalité de chargement automatique de module ne peut pas importer le module automatiquement.

- Le paramètre `ListAvailable` de la cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) ne trouve pas le module.

- La cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ne trouve pas le module. Pour importer le module, vous devez indique le chemin complet du fichier de module racine ou du fichier manifeste du module.

  Les fonctionnalités supplémentaires, et notamment les suivantes, ne fonctionnent pas tant que le module n’est pas importé dans la session. Dans les modules bien formés présents dans la variable d’environnement **PSModulePath**, elles fonctionnent même si le module n’est pas importé dans la session.

- La cmdlet [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) ne trouve pas de commandes dans le module.

- Les cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) ne parviennent pas à mettre à jour/enregistrer l’aide du module.

- La cmdlet [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) ne parvient pas à localiser ni à afficher les commandes du module.

  Les commandes du module sont absentes de la fenêtre `Show-Command` dans l’Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).

## <a name="where-to-install-modules"></a>Emplacement d’installation des modules

Cette section explique où installer les modules Windows PowerShell dans le système de fichiers. L’emplacement dépend de l’utilisation du module.

### <a name="installing-modules-for-a-specific-user"></a>Installation de modules pour un utilisateur spécifique

Si vous créez votre propre module ou que vous en recevez un d’un tiers (par exemple, un site web de la communauté Windows PowerShell) et que vous souhaitez qu’il ne soit accessible qu’à votre compte d’utilisateur, installez-le dans votre répertoire Modules propre à l’utilisateur.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

Le répertoire Modules propre à l’utilisateur est ajouté à la valeur de la variable d’environnement **PSModulePath** par défaut.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installation de modules pour tous les utilisateurs dans Program Files

Si vous souhaitez qu’un module soit accessible à tous les comptes d’utilisateur de l’ordinateur, installez-le à l’emplacement Program Files.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> L’emplacement Program Files est ajouté à la valeur de la variable d’environnement PSModulePath par défaut dans la version 4.0 et les versions ultérieures de Windows PowerShell. Dans les versions antérieures de Windows PowerShell, vous pouvez créer manuellement l’emplacement Program Files (%ProgramFiles%\WindowsPowerShell\Modules) et ajouter ce chemin à votre variable d’environnement PSModulePath (cf. plus haut).

### <a name="installing-modules-in-a-product-directory"></a>Installation de modules dans un répertoire de produit

Si vous distribuez le module à des tiers, choisissez l’emplacement Program Files par défaut décrit ci-dessus ou créez votre propre sous-répertoire propre à la société ou au produit du répertoire %ProgramFiles%.

Par exemple, Fabrikam Technologies, une société fictive, livre un module Windows PowerShell pour son produit Fabrikam Manager. Le programme d’installation du module crée un sous-répertoire Modules dans le sous-répertoire du produit Fabrikam Manager.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Pour permettre aux fonctionnalités de découverte de modules Windows PowerShell de trouver le module Fabrikam, le programme d’installation de ce dernier ajoute l’emplacement du module à la valeur de la variable d’environnement **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installation de modules dans le répertoire Common Files

Si un module est utilisé par plusieurs composants ou plusieurs versions d’un produit, installez-le dans un sous-répertoire propre au module du sous-répertoire %ProgramFiles%\Common Files\Modules.

Dans l’exemple suivant, le module Fabrikam est installé dans un sous-répertoire Fabrikam du sous-répertoire `%ProgramFiles%\Common Files\Modules`. À savoir : chaque module se trouve dans son propre sous-répertoire au sein du sous-répertoire Modules.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

Le programme d’installation fait alors en sorte que la valeur de la variable d’environnement **PSModulePath** comprenne le chemin du sous-répertoire Common Files\Modules.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Installation de plusieurs versions d’un module

Pour installer plusieurs versions du même module, procédez comme suit.

1. Créez un répertoire pour chaque version du module. Ajoutez le numéro de version dans le nom du répertoire.
2. Créez un manifeste de module pour chaque version du module. Dans la valeur de la clé **ModuleVersion** qui se trouve dans le manifeste, entrez le numéro de version du module. Enregistrez le fichier manifeste (.psd1) dans le répertoire propre à la version du module.
3. Ajoutez le chemin du dossier racine du module à la valeur de la variable d’environnement **PSModulePath** (cf. exemples suivants).

Pour importer une version particulière du module, l’utilisateur final peut utiliser le paramètre `MinimumVersion` ou le paramètre `RequiredVersion` de la cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Par exemple, si le module Fabrikam est disponible dans les versions 8.0 et 9.0, la structure de répertoires du module Fabrikam peut se présenter ainsi :

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

Le programme d’installation ajoute les deux chemins de module à la valeur de la variable d’environnement **PSModulePath**.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

À l’issue de cette procédure, le paramètre **ListAvailable** de la cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) récupère les deux modules Fabrikam. Pour importer un module en particulier, utilisez le paramètre `MinimumVersion` ou le paramètre `RequiredVersion` de la cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Si les deux modules sont importés dans la même session et qu’ils contiennent des cmdlets portant le même nom, sont effectives dans la session les cmdlets importées en dernier.

## <a name="handling-command-name-conflicts"></a>Gestion des conflits de noms de commandes

Des conflits de noms de commandes peuvent se produire lorsque les commandes exportées par un module portent le même nom que les commandes de la session de l’utilisateur.

Si une session contient deux commandes du même nom, Windows PowerShell exécute le type de commande prioritaire. Si une session contient deux commandes du même nom et du même type, Windows PowerShell exécute la dernière commande ajoutée à la session. Pour exécuter une commande qui n’est pas exécutée par défaut, les utilisateurs peuvent qualifier le nom de la commande avec celui du module.

Par exemple, si la session comprend une fonction `Get-Date` et la cmdlet `Get-Date`, Windows PowerShell exécute par défaut la fonction. Pour exécuter la cmdlet, faites précéder la commande du nom du module :

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Pour éviter les conflits de noms, les auteurs de modules peuvent utiliser la clé **DefaultCommandPrefix** dans le manifeste de module afin de spécifier un préfixe substantif pour toutes les commandes exportées à partir du module.

Les utilisateurs peuvent se servir du paramètre **Prefix** de la cmdlet `Import-Module` pour utiliser un autre préfixe. La valeur du paramètre **Prefix** est prioritaire sur la valeur de la clé **DefaultCommandPrefix**.

## <a name="see-also"></a>Voir aussi

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
