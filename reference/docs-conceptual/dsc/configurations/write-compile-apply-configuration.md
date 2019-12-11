---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,service,installation
title: Écrire, compiler et appliquer une configuration
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953996"
---
> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Écrire, compiler et appliquer une configuration

Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.
Dans l’exemple suivant, vous allez apprendre à écrire et à appliquer une configuration très simple. La configuration vérifiera qu’il existe un fichier « HelloWorld.txt » sur votre ordinateur local. Si vous supprimez le fichier, DSC le recréera lors de sa prochaine fois mise à jour.

Pour obtenir une vue d’ensemble de DSC et de son fonctionnement, consultez [Présentation de Desired State Configuration pour les développeurs](../overview/overview.md).

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple, vous avez besoin d’un ordinateur exécutant PowerShell 4.0 ou version ultérieure.

## <a name="write-the-configuration"></a>Écrire la configuration

Une [configuration DSC](configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).

Dans PowerShell ISE ou un autre éditeur PowerShell, tapez la commande suivante :

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

> Important ! Dans les scénarios plus avancés où plusieurs modules doivent être importés afin que vous puissiez utiliser de nombreuses ressources DSC dans la même configuration, veillez à placer chaque module sur une ligne distincte à l’aide de `Import-DscResource`.
> Cela est plus facile à gérer dans le contrôle de code source et requis lors de l’utilisation de DSC dans Azure State Configuration.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Enregistrez le fichier en tant que « HelloWorld.ps1 ».

La définition d’une configuration s’apparente à celle d’une fonction. Le bloc **Nœud** spécifie le nœud cible à configurer, dans ce cas `localhost`.

La configuration appelle une [ressource](../resources/resources.md), la ressource `File`. Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.

## <a name="compile-the-configuration"></a>Compiler la configuration

Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.
L’exécution de la configuration, comme une fonction, compilera un fichier « .mof » pour chaque nœud défini par le bloc `Node`.
Pour exécuter la configuration, vous devez *dot sourcer* votre script « HelloWorld.ps1 » dans la portée actuelle.
Pour plus d’informations, consultez [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Dot sourcez* votre script « HelloWorld.ps1 » en tapant le chemin où vous l’avez stocké, après le `. ` (point, espace). Vous pouvez ensuite exécuter votre configuration en l’appelant comme une fonction.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
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

L’applet de commande `Start-DscConfiguration` indique au [Gestionnaire de configuration local](../managing-nodes/metaConfig.md), le moteur de DSC, qu’il doit appliquer la configuration.
Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.

Utilisez le code ci-dessous pour exécuter l’applet de commande `Start-DSCConfiguration`. Spécifiez le chemin du répertoire où est stocké votre fichier « localhost.mof » au paramètre `-Path`. L’applet de commande `Start-DSCConfiguration` recherche dans le répertoire spécifié pour tout fichier « \<nom_ordinateur\>.mof ». L’applet de commande `Start-DSCConfiguration` tente d’appliquer chaque fichier « .mof » trouvé au nom d’ordinateur spécifié par le nom de fichier (« localhost », « server01 », « dc-02 », etc.).

> [!NOTE]
> Si le paramètre `-Wait` n’est pas spécifié, `Start-DSCConfiguration` crée une tâche en arrière-plan pour exécuter l’opération. Le fait de spécifier le paramètre `-Verbose` vous permet de regarder la sortie **détaillée** de l’opération. `-Wait` et `-Verbose` sont tous deux des paramètres facultatifs.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Tester la configuration

Une fois l’applet de commande `Start-DSCConfiguration` terminée, vous devriez voir un fichier « HelloWorld.txt » à l’emplacement spécifié. Vous pouvez vérifier le contenu avec l’applet de commande [Get-Content](/powershell/module/microsoft.powershell.management/get-content).

Vous pouvez également *tester* l’état actuel à l’aide de [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

La sortie doit être « True » si le nœud est actuellement conforme à la configuration appliquée.

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

## <a name="re-applying-the-configuration"></a>Réapplication de la configuration

Pour voir votre configuration réappliquée, vous pouvez supprimer le fichier texte créé par votre configuration. Utilisez l’applet de commande `Start-DSCConfiguration` avec le paramètre `-UseExisting`. Le paramètre `-UseExisting` fait en sorte que `Start-DSCConfiguration` réapplique le fichier « current.mof », qui représente la dernière configuration correcte appliquée.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Étapes suivantes

- En savoir plus sur les configurations DSC sous [Configurations DSC](configurations.md).
- Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](../resources/resources.md).
- Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).
