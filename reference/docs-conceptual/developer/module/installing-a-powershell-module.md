---
title: Installation d’un module PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367068"
---
# <a name="installing-a-powershell-module"></a>Installation d’un module PowerShell

Une fois que vous avez créé votre module PowerShell, vous souhaiterez probablement installer le module sur un système, afin que vous ou d’autres utilisateurs puissent l’utiliser. En règle générale, cela consiste à copier les fichiers de module (IE, le fichier. psm1 ou l’assembly binaire, le manifeste de module et tous les autres fichiers associés) sur un répertoire sur cet ordinateur. Pour un très petit projet, cela peut être aussi simple que la copie et le collage des fichiers avec l’Explorateur Windows sur un ordinateur distant unique. Toutefois, pour les solutions plus grandes, vous souhaiterez peut-être utiliser un processus d’installation plus sophistiqué. Quelle que soit la façon dont vous obtenez votre module sur le système, PowerShell peut utiliser un certain nombre de techniques qui permettront aux utilisateurs de trouver et d’utiliser vos modules. Par conséquent, le problème principal d’installation consiste à s’assurer que PowerShell sera en mesure de trouver votre module. Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md).

## <a name="rules-for-installing-modules"></a>Règles d’installation des modules

Les informations suivantes se rapportent à tous les modules, y compris les modules que vous créez pour votre propre usage, les modules que vous recevez d’autres parties et les modules que vous distribuez à d’autres tiers.

### <a name="install-modules-in-psmodulepath"></a>Installer les modules dans PSModulePath

Dans la mesure du possible, installez tous les modules dans un chemin d’accès qui est listé dans la variable d’environnement **PSModulePath** ou ajoutez le chemin d’accès du module à la valeur de la variable d’environnement **PSModulePath** .

La variable d’environnement **PSModulePath** ($env :P smodulepath) contient les emplacements des modules Windows PowerShell. Les applets de commande s’appuient sur la valeur de cette variable d’environnement pour rechercher des modules.

Par défaut, la valeur de la variable d’environnement **PSModulePath** contient les répertoires du module système et utilisateur suivants, mais vous pouvez ajouter et modifier la valeur.

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Cet emplacement est réservé aux modules fournis avec Windows. N’installez pas les modules à cet emplacement.

- `$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  Pour récupérer la valeur de la variable d’environnement **PSModulePath** , utilisez l’une des commandes suivantes.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Pour ajouter un chemin de module à la valeur de la variable d’environnement **PSModulePath** , utilisez le format de commande suivant. Ce format utilise la méthode **SetEnvironmentVariable ne contient** de la classe **System. Environment** pour apporter une modification indépendante de la session à la variable d’environnement **PSModulePath** .

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Une fois que vous avez ajouté le chemin d’accès à **PSModulePath**, vous devez diffuser un message d’environnement sur la modification. La diffusion de la modification permet à d’autres applications, telles que l’interpréteur de commandes, de récupérer la modification. Pour diffuser la modification, faire en sorte que le code d’installation de votre produit envoie un message **WM_SETTINGCHANGE** avec `lParam` défini sur la chaîne « environnement ». Veillez à envoyer le message une fois que le code d’installation de votre module a mis à jour **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Utiliser le nom de répertoire du module correct

Un module bien formé est un module qui est stocké dans un répertoire portant le même nom que le nom de base d’au moins un fichier dans le répertoire du module. Si un module n’est pas bien formé, Windows PowerShell ne le reconnaît pas comme un module.

Le « nom de base » d’un fichier est le nom sans l’extension de nom de fichier. Dans un module bien formé, le nom du répertoire qui contient les fichiers de module doit correspondre au nom de base d’au moins un fichier dans le module.

Par exemple, dans l’exemple de module Fabrikam, le répertoire qui contient les fichiers de module est nommé « Fabrikam » et au moins un fichier a le nom de base « fabrikam ». Dans ce cas, fabrikam. psd1 et fabrikam. dll ont tous les deux le nom de base « fabrikam ».

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

Si le module n’est pas bien formé et que son emplacement n’est pas inclus dans la valeur de la variable d’environnement **PSModulePath** , les fonctionnalités de découverte de base de Windows PowerShell, comme ci-dessous, ne fonctionnent pas.

- La fonctionnalité de chargement automatique de module ne peut pas importer le module automatiquement.

- Le paramètre `ListAvailable` de l’applet de commande [obtenir-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) ne peut pas trouver le module.

- L’applet [de commande Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ne trouve pas le module. Pour importer le module, vous devez fournir le chemin d’accès complet au fichier de module racine ou au fichier manifeste du module.

  Les fonctionnalités supplémentaires, telles que les suivantes, ne fonctionnent pas, sauf si le module est importé dans la session. Dans les modules bien formés de la variable d’environnement **PSModulePath** , ces fonctionnalités fonctionnent même si le module n’est pas importé dans la session.

- L’applet de [commande obtenir-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) ne peut pas trouver de commandes dans le module.

- Les applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) ne peuvent pas mettre à jour ou enregistrer l’aide du module.

- L’applet de [commande show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) ne peut pas trouver et afficher les commandes du module.

  Les commandes du module sont manquantes dans la fenêtre `Show-Command` dans Environnement d’écriture de scripts intégré de Windows PowerShell (ISE).

## <a name="where-to-install-modules"></a>Emplacement d’installation des modules

Cette section explique où dans le système de fichiers pour installer les modules Windows PowerShell. L’emplacement dépend de la façon dont le module est utilisé.

### <a name="installing-modules-for-a-specific-user"></a>Installation de modules pour un utilisateur spécifique

Si vous créez votre propre module ou si vous recevez un module d’un autre tiers, tel qu’un site Web de la communauté Windows PowerShell, et que vous souhaitez que le module soit disponible uniquement pour votre compte d’utilisateur, installez le module dans votre répertoire de modules spécifiques à l’utilisateur.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

Le répertoire modules spécifiques à l’utilisateur est ajouté à la valeur de la variable d’environnement **PSModulePath** par défaut.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installation de modules pour tous les utilisateurs dans Program Files

Si vous souhaitez qu’un module soit disponible pour tous les comptes d’utilisateur sur l’ordinateur, installez le module à l’emplacement Program Files.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> L’emplacement des fichiers programme est ajouté à la valeur de la variable d’environnement PSModulePath par défaut dans Windows PowerShell 4,0 et versions ultérieures. Pour les versions antérieures de Windows PowerShell, vous pouvez créer manuellement l’emplacement des fichiers programme ((%ProgramFiles%\WindowsPowerShell\Modules) et ajouter ce chemin d’accès à votre variable d’environnement PSModulePath comme décrit ci-dessus.

### <a name="installing-modules-in-a-product-directory"></a>Installation de modules dans un répertoire de produit

Si vous distribuez le module à d’autres tiers, utilisez l’emplacement par défaut des fichiers programme décrit ci-dessus, ou créez votre propre sous-répertoire spécifique à la société ou au produit du répertoire% ProgramFiles%.

Par exemple, Fabrikam technologies, une société fictive, expédie un module Windows PowerShell pour son produit Fabrikam Manager. Le programme d’installation de leur module crée un sous-répertoire Modules dans le sous-répertoire du produit de Fabrikam Manager.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Pour activer les fonctionnalités de détection des modules Windows PowerShell afin de rechercher le module Fabrikam, le programme d’installation du module Fabrikam ajoute l’emplacement du module à la valeur de la variable d’environnement **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installation des modules dans le répertoire des fichiers communs

Si un module est utilisé par plusieurs composants d’un produit ou par plusieurs versions d’un produit, installez le module dans un sous-répertoire spécifique au module du sous-répertoire%ProgramFiles%\Common Files\Modules.

Dans l’exemple suivant, le module Fabrikam est installé dans un sous-répertoire Fabrikam du sous-répertoire `%ProgramFiles%\Common Files\Modules`. Notez que chaque module réside dans son propre sous-répertoire dans le sous-répertoire Modules.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

Ensuite, le programme d’installation vérifie que la valeur de la variable d’environnement **PSModulePath** comprend le chemin d’accès du sous-répertoire des modules de fichiers communs.

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

Pour installer plusieurs versions du même module, utilisez la procédure suivante.

1. Créez un répertoire pour chaque version du module. Incluez le numéro de version dans le nom du répertoire.
2. Créez un manifeste de module pour chaque version du module. Dans la valeur de la clé **ModuleVersion** dans le manifeste, entrez le numéro de version du module. Enregistrez le fichier manifeste (. psd1) dans le répertoire spécifique à la version du module.
3. Ajoutez le chemin d’accès au dossier racine du module à la valeur de la variable d’environnement **PSModulePath** , comme indiqué dans les exemples suivants.

Pour importer une version particulière du module, l’utilisateur final peut utiliser les paramètres `MinimumVersion` ou `RequiredVersion` de l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Par exemple, si le module Fabrikam est disponible dans les versions 8,0 et 9,0, la structure de répertoires du module Fabrikam peut ressembler à ce qui suit.

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

Le programme d’installation ajoute les deux chemins d’accès au module à la valeur de la variable d’environnement **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Une fois ces étapes terminées, le paramètre **listAvailable** de l’applet de commande [obtenir-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) obtient les deux modules fabrikam. Pour importer un module particulier, utilisez les paramètres `MinimumVersion` ou `RequiredVersion` de l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Si les deux modules sont importés dans la même session et que les modules contiennent des applets de commande portant le même nom, les applets de commande importées en dernier sont effectives dans la session.

## <a name="handling-command-name-conflicts"></a>Gestion des conflits de noms de commande

Les conflits de noms de commande peuvent se produire lorsque les commandes exportées par un module ont le même nom que les commandes dans la session de l’utilisateur.

Quand une session contient deux commandes qui portent le même nom, Windows PowerShell exécute le type de commande qui est prioritaire. Quand une session contient deux commandes qui ont le même nom et le même type, Windows PowerShell exécute la commande qui a été ajoutée à la session la plus récente. Pour exécuter une commande qui n’est pas exécutée par défaut, les utilisateurs peuvent qualifier le nom de la commande avec le nom du module.

Par exemple, si la session contient une fonction `Get-Date` et l’applet de commande `Get-Date`, Windows PowerShell exécute la fonction par défaut. Pour exécuter l’applet de commande, faites précéder la commande du nom du module, par exemple :

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Pour éviter les conflits de noms, les auteurs de modules peuvent utiliser la clé **DefaultCommandPrefix** dans le manifeste de module pour spécifier un préfixe substantif pour toutes les commandes exportées à partir du module.

Les utilisateurs peuvent utiliser le paramètre **prefix** de l’applet de commande `Import-Module` pour utiliser un autre préfixe. La valeur du paramètre **prefix** est prioritaire sur la valeur de la clé **DefaultCommandPrefix** .

## <a name="see-also"></a>Voir aussi

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
