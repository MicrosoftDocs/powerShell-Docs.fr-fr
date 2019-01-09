---
ms.date: 12/12/2018
keywords: DSC, powershell, configuration, service, le programme d’installation
title: Écrire, compiler et appliquer une configuration
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401275"
---
> S'applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Écrire, compiler et appliquer une configuration

Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.
Dans l’exemple suivant, vous allez apprendre à écrire et appliquer une Configuration très simple. La Configuration garantit qu'un fichier « HelloWorld.txt » existe sur votre ordinateur local. Si vous supprimez le fichier, DSC il recrée la prochaine fois qu’il met à jour.

Pour une vue d’ensemble de DSC et de son fonctionnement, consultez [Desired State Configuration de présentation pour les développeurs](../overview/overview.md).

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple, vous devez un ordinateur qui exécute PowerShell 4.0 ou version ultérieure.

## <a name="write-the-configuration"></a>Écrire la configuration

Une [configuration DSC](configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).

Dans PowerShell ISE, ou un autre éditeur de PowerShell, tapez la commande suivante :

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Enregistrez le fichier en tant que « HelloWorld.ps1 ».

La définition d’une Configuration est comme la définition d’une fonction. Le bloc **Nœud** spécifie le nœud cible à configurer, dans ce cas `localhost`.

La configuration appelle une [ressources](../resources/resources.md), le `File` ressource. Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.

## <a name="compile-the-configuration"></a>Compiler la configuration

Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.
Exécution de la configuration, comme une fonction, compilera un fichier « .mof » pour chaque nœud défini par le `Node` bloc.
Pour exécuter la configuration, vous devez *source de point* votre script de « HelloWorld.ps1 » dans la portée actuelle.
Pour plus d’informations, consultez [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

*Source de point* votre script de « HelloWorld.ps1 » en tapant dans le chemin d’accès où vous avez stocké, après le `. ` (point, espace). Vous pouvez ensuite exécuter votre configuration en l’appelant comme une fonction.

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Cela génère la sortie suivante :

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Appliquer la configuration

Maintenant que vous disposez du fichier MOF compilé, vous pouvez appliquer la configuration au nœud cible (dans ce cas, l’ordinateur local) en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

Le `Start-DscConfiguration` applet de commande indique le [Gestionnaire de Configuration Local (LCM)](../managing-nodes/metaConfig.md), le moteur de DSC, pour appliquer la configuration.
Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.

Le code ci-dessous permet d’exécuter le `Start-DSCConfiguration` applet de commande. Spécifiez le chemin du répertoire où se trouve votre « localhost.mof » à la `-Path` paramètre. Le `Start-DSCConfiguration` applet de commande recherche dans le répertoire spécifié pour les «\<computername\>.mof « fichiers. Le `Start-DSCConfiguration` applet de commande tente d’appliquer chaque fichier « .mof » trouvé pour le nom d’ordinateur spécifié par le nom de fichier (« localhost », « server01 », « dc-02 », etc.).

> [!NOTE]
> Si le `-Wait` paramètre n’est pas spécifié, `Start-DSCConfiguration` crée une tâche en arrière-plan pour exécuter l’opération. En spécifiant le `-Verbose` paramètre vous permet de regarder le **Verbose** sortie de l’opération. `-Wait`, et `-Verbose` sont les deux paramètres facultatifs.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Tester la configuration

Une fois le `Start-DSCConfiguration` applet de commande est terminée, vous devriez voir un fichier « HelloWorld.txt » dans l’emplacement spécifié. Vous pouvez vérifier le contenu avec le [Get-Content](/powershell/module/microsoft.powershell.management/get-content) applet de commande.

Vous pouvez également *tester* l’état actuel à l’aide [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

La sortie doit être « True » si le nœud est actuellement compatible avec la Configuration appliquée.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Ré-appliquer la configuration

Pour afficher votre configuration sont appliquées à nouveau, vous pouvez supprimer le fichier texte créé par votre Configuration. L’utilisation du `Start-DSCConfiguration` applet de commande avec le `-UseExisting` paramètre. Le `-UseExisting` paramètre demande à `Start-DSCConfiguration` pour ré-appliquer le fichier « current.mof », qui représente le plus récemment correctement appliqué configuration.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Étapes suivantes

- En savoir plus sur les configurations DSC sous [Configurations DSC](configurations.md).
- Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](../resources/resources.md).
- Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).
