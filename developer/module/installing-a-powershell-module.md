---
title: Installation d’un Module PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: f7899713dd273b793017adfa0a20b3ff3352b62a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862165"
---
# <a name="installing-a-powershell-module"></a>Installation d’un module PowerShell

Une fois que vous avez créé votre module PowerShell, vous pouvez installer le module sur un système, afin que vous ou autres utilisateurs peuvent l’utiliser. En règle générale, cela se compose simplement de copier les fichiers de module (Internet Explorer, le .psm1, ou l’assembly binaire, le manifeste de module et tous les autres fichiers associés) sur un répertoire sur cet ordinateur. Pour un très petit projet, cela peut être aussi simple que de copier et coller les fichiers avec l’Explorateur Windows sur un seul ordinateur distant ; Toutefois, pour les solutions plus volumineuses, vous souhaiterez utiliser un processus d’installation plus sophistiqué. Quelle que soit la façon dont vous obtenez votre module sur le système, PowerShell peut utiliser un certain nombre de techniques qui permettent aux utilisateurs de trouver et utiliser vos modules. (Pour plus d’informations, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md).) Par conséquent, le problème principal pour l’installation consiste à s’assurer que PowerShell sera en mesure de trouver votre module.

Cette rubrique contient les sections suivantes :

- Règles pour l’installation de Modules

- Où installer les Modules

- Installation de plusieurs Versions d’un Module

- Gestion des conflits de nom de commande

## <a name="rules-for-installing-modules"></a>Règles pour l’installation de Modules

Les informations suivantes se rapportent à tous les modules, y compris les modules que vous créez pour votre propre utilisation, les modules que vous obtenez d’autres parties et les modules que vous distribuez à d’autres personnes.

### <a name="install-modules-in-psmodulepath"></a>Installer des Modules de PSModulePath

Si possible, installez tous les modules dans un chemin d’accès qui est répertorié dans le **PSModulePath** variable d’environnement ou ajouter le chemin d’accès de module pour le **PSModulePath** valeur de variable d’environnement.

Le **PSModulePath** variable d’environnement ($Env : PSModulePath) contient les emplacements des modules Windows PowerShell. Applets de commande s’appuient sur la valeur de cette variable d’environnement pour rechercher des modules.

Par défaut, le **PSModulePath** valeur de la variable contient le système suivantes et les répertoires de module d’utilisateur, mais vous pouvez ajouter à et modifier la valeur.

- $PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Cet emplacement est réservé pour les modules fournis avec Windows. N’installez pas de modules à cet emplacement.

- $Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)

  Pour obtenir la valeur de la **PSModulePath** variable d’environnement, utilisez une des commandes suivantes.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Pour ajouter un chemin d’accès du module à la valeur de la **PSModulePath** variable d’environnement, utilisez le format de commande suivant. Ce format utilise le **SetEnvironmentVariable ne contient pas** méthode de la **System.Environment** classe pour apporter une modification de session indépendante au **PSModulePath** environnement variable.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Une fois que vous avez ajouté le chemin d’accès à **PSModulePath**, vous devez diffuser un message d’environnement sur la modification. Diffusion de la modification permet aux autres applications, telles que l’interpréteur de commandes, la modification. Pour diffuser la modification, que votre code d’installation de produit envoie un **WM_SETTINGCHANGE** message avec `lParam` défini sur la chaîne « Environnement ». Veillez à envoyer le message une fois que votre code d’installation de module a mis à jour **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Utilisez le nom de répertoire de Module approprié

Un module « correct » est un module qui est stocké dans un répertoire portant le même nom que le nom de base d’au moins un fichier dans le répertoire de module. Si un module n’est pas bien formé, Windows PowerShell ne le reconnaît pas en tant que module.

Le nom « base » d’un fichier est le nom sans l’extension de nom de fichier. Dans un module bien formé, le nom du répertoire qui contient les fichiers de module doit correspondre au nom de base d’au moins un fichier dans le module.

Par exemple, dans l’exemple de module de Fabrikam, le répertoire qui contient les fichiers de module est nommé « Fabrikam » et au moins un fichier a le nom de base « Fabrikam ». Dans ce cas, Fabrikam.psd1 et Fabrikam.dll ont le nom de base « Fabrikam ».

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Effet de l’Installation incorrecte

Si le module n’est pas bien formé et son emplacement n’est pas inclus dans la valeur de la **PSModulePath** variable d’environnement, fonctionnalités élémentaires de découverte de Windows PowerShell, comme celle ci-dessous, ne fonctionnent pas.

- La fonctionnalité de chargement automatique de Module ne peut pas importer le module automatiquement.

- Le `ListAvailable` paramètre de la [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande ne peut pas trouver le module.

- Le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande ne peut pas trouver le module. Pour importer le module, vous devez fournir le chemin d’accès complet au fichier de module racine ou au fichier manifeste de module.

  Des fonctionnalités supplémentaires, telles que la commande suivante, ne fonctionnent pas, sauf si le module est importé dans la session. Dans les modules bien formés dans le **PSModulePath** variable d’environnement, ces fonctionnalités fonctionnent même lorsque le module n’est pas importé dans la session.

- Le [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) applet de commande ne peut pas trouver les commandes dans le module.

- Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applets de commande ne peut pas mettre à jour ou enregistrer l’aide du module.

- Le [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) applet de commande ne peut pas rechercher et afficher les commandes dans le module.

  Les commandes du module sont manquants dans le `Show-Command` fenêtre dans Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Où installer les Modules

Cette section explique où dans le système de fichiers pour installer les modules Windows PowerShell. L’emplacement dépend de la façon dont le module est utilisé.

### <a name="installing-modules-for-a-specific-user"></a>Installation de Modules pour un utilisateur spécifique

Si vous créez votre propre module ou obtenez un module à partir d’une autre partie, par exemple un site Web communautaire de Windows PowerShell, et que le module soit disponible pour votre compte d’utilisateur, installer le module dans votre répertoire de Modules spécifiques à l’utilisateur.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

Le répertoire de Modules spécifiques à l’utilisateur est ajouté à la valeur de la **PSModulePath** variable d’environnement par défaut.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installation de Modules pour tous les utilisateurs dans les fichiers programme

Si vous souhaitez un module soit disponible pour tous les comptes d’utilisateur sur l’ordinateur, installez le module dans l’emplacement des fichiers de programme.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> L’emplacement des fichiers de programme est ajouté à la valeur de la variable d’environnement PSModulePath par défaut dans Windows PowerShell 4.0 et versions ultérieures. Pour les versions antérieures de Windows PowerShell, vous pouvez manuellement créer la ((%ProgramFiles%\WindowsPowerShell\Modules) emplacement Program Files et ajouter ce chemin d’accès à votre variable d’environnement PSModulePath, comme décrit ci-dessus.

### <a name="installing-modules-in-a-product-directory"></a>Installation de Modules dans un répertoire de produit

Si vous voulez distribuer le module à d’autres parties, utiliser l’emplacement des fichiers de programme par défaut décrit ci-dessus, ou créez votre propre sous-répertoire spécifique à la société ou spécifiques au produit du répertoire % ProgramFiles%.

Par exemple, Fabrikam Technologies, une société fictive, est prévu pour fonctionner un module Windows PowerShell pour leur produit Manager de Fabrikam. Leur programme d’installation du module crée également un sous-répertoire de Modules dans le sous-répertoire de product Manager de Fabrikam.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Pour activer les fonctionnalités de découverte de module Windows PowerShell rechercher le module de Fabrikam, le programme d’installation du module de Fabrikam ajoute l’emplacement de module à la valeur de la **PSModulePath** variable d’environnement.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technolgies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installation de Modules dans le répertoire des fichiers communs

Si un module est utilisé par plusieurs composants d’un produit ou par plusieurs versions d’un produit, installez le module dans un sous-répertoire spécifique au module du sous-répertoire Files\Modules %ProgramFiles%\Common.

Dans l’exemple suivant, le module de Fabrikam est installé dans un sous-répertoire de Fabrikam du sous-répertoire Files\Modules %ProgramFiles%\Common. Notez que chaque module réside dans son propre sous-répertoire dans le sous-répertoire de Modules.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Ensuite, le programme d’installation garantit la valeur de la **PSModulePath** variable d’environnement inclut le chemin d’accès du sous-répertoire de modules de fichiers courants.

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

## <a name="installing-multiple-versions-of-a-module"></a>Installation de plusieurs Versions d’un Module

Pour installer plusieurs versions du même module, utilisez la procédure suivante.

1. Créez un répertoire pour chaque version du module. Inclure le numéro de version dans le nom du répertoire.

2. Créez un manifeste de module pour chaque version du module. Dans la valeur de la **ModuleVersion** dans le manifeste de clé, entrez le numéro de version du module. Enregistrez le fichier manifest (.psd1) dans le répertoire spécifique à la version du module.

3. Ajouter le chemin de dossier de module racine à la valeur de la **PSModulePath** variable d’environnement, comme indiqué dans les exemples suivants.

Pour importer une version particulière du module, l’utilisateur final peut utiliser le `MinimumVersion` ou `RequiredVersion` paramètres de le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande.

Par exemple, si le module de Fabrikam est disponible dans les versions 8.0 et 9.0, la structure de répertoire de module de Fabrikam peut se présenter comme suit.

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

Le programme d’installation ajoute les deux les chemins d’accès de module pour le **PSModulePath** valeur de variable d’environnement.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Une fois ces étapes terminées, le **ListAvailable** paramètre de la [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande Obtient les deux modules de Fabrikam. Pour importer un module particulier, utilisez le `MiminumVersion` ou `RequiredVersion` paramètres de le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande.

Si les deux modules sont importés dans la même session, et les modules contiennent des applets de commande avec les mêmes noms, les applets de commande sont importés en dernier sont efficaces dans la session.

## <a name="handling-command-name-conflicts"></a>Gestion des conflits de nom de commande

Conflits de noms de commande peuvent se produire lorsque les commandes exportées par un module possèdent le même nom que les commandes dans la session utilisateur.

Lorsqu’une session contient deux commandes qui ont le même nom, Windows PowerShell s’exécute le type de commande qui est prioritaire. Lorsqu’une session contient deux commandes qui ont le même nom et le même type, Windows PowerShell exécute la commande qui a été ajoutée à la session la plus récemment. Pour exécuter une commande qui n’est pas exécutée par défaut, les utilisateurs peuvent qualifier le nom de commande avec le nom du module.

Par exemple, si la session contient un `Get-Date` (fonction) et le `Get-Date` applet de commande Windows PowerShell exécute la fonction par défaut. Pour exécuter l’applet de commande, la faire précéder le nom du module, tel que :

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Pour éviter les conflits de noms, les auteurs de modules peuvent utiliser le **DefaultCommandPrefix** clé dans le manifeste de module pour spécifier un préfixe pour toutes les commandes exportées à partir du module.

Les utilisateurs peuvent utiliser le **préfixe** paramètre de la `Import-Module` applet de commande à utiliser un autre préfixe. La valeur de la **préfixe** paramètre est prioritaire sur la valeur de la **DefaultCommandPrefix** clé.

## <a name="see-also"></a>Voir aussi

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Écrire un Module PowerShell de Windows](./writing-a-windows-powershell-module.md)
