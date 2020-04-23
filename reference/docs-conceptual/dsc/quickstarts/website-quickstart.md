---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Démarrage rapide - Créer un site web avec DSC
ms.openlocfilehash: 08ca25604998ce8c913ef8112b5342f2e0216b6e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75416131"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a>Démarrage rapide : créer un site Web avec Desired State Configuration (DSC)

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

Cet exercice vous guide dans la création et l’application d’une configuration DSC (Configuration d’état souhaité) du début à la fin.
L’exemple que nous utiliserons garantit qu’un serveur dispose de la fonctionnalité `Web-Server` (IIS) activée et que le contenu d’un site Web « Hello World » simple est présent dans le répertoire `inetpub\wwwroot` de ce serveur.

Pour une vue d’ensemble de DSC et de son fonctionnement, consultez [Présentation de la configuration de l’état souhaité pour les décideurs](../overview/decisionMaker.md).

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple, vous avez besoin d’un ordinateur exécutant Windows Server 2012 ou une version ultérieure et PowerShell version 4.0 ou ultérieure.

## <a name="write-and-place-the-indexhtm-file"></a>Écrire et placer le fichier index.htm

Tout d’abord, nous allons créer le fichier HTML qui va nous servir de contenu du site Web.

Dans votre dossier racine, créez un dossier nommé `test`.

Dans un éditeur de texte, tapez le texte suivant :

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Enregistrez-le en tant que `index.htm` dans le dossier `test` que vous avez créé précédemment.

## <a name="write-the-configuration"></a>Écrire la configuration

Une [configuration DSC](../configurations/configurations.md) est une fonction PowerShell spéciale qui définit la façon dont vous souhaitez configurer un ou plusieurs ordinateurs cibles (nœuds).

Dans l’ISE PowerShell, tapez ce qui suit :

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Enregistrez le fichier sous le nom `WebsiteTest.ps1`.

Vous pouvez voir qu’il ressemble à une fonction PowerShell, avec l’ajout du mot clé **Configuration** utilisé avant le nom de la fonction.

Le bloc **Nœud** spécifie le nœud cible à configurer. Dans ce cas, `localhost`.

La configuration appelle deux [ressources](../resources/resources.md), **WindowsFeature** et **File**.
Les ressources s’assurent que le nœud cible est dans l’état défini par la configuration.

## <a name="compile-the-configuration"></a>Compiler la configuration

Pour qu’une configuration DSC soit appliquée à un nœud, elle doit tout d’abord être compilée dans un fichier MOF.
Pour ce faire, vous exécutez la configuration comme une fonction.
Dans une console PowerShell, accédez au dossier où vous avez enregistré votre configuration et exécutez les commandes suivantes pour compiler la configuration dans un fichier MOF :

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Cela génère la sortie suivante :

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

La première ligne rend la fonction de configuration disponible dans la console.
La deuxième ligne exécute la configuration.
Il en résulte qu’un nouveau dossier, nommé `WebsiteTest` est créé en tant que sous-dossier du dossier actif.
Le dossier `WebsiteTest` contient un fichier nommé `localhost.mof`.
C’est ce fichier qui peut ensuite être appliqué au nœud cible.

## <a name="apply-the-configuration"></a>Appliquer la configuration

Maintenant que vous disposez du fichier MOF compilé, vous pouvez appliquer la configuration au nœud cible (dans ce cas, l’ordinateur local) en appelant l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

L’applet de commande `Start-DscConfiguration` indique au [LCM (Local Configuration Manager, gestionnaire de configuration local)](../managing-nodes/metaConfig.md), le moteur de DSC, d’appliquer la configuration.
Le LCM est chargé d’appeler les ressources DSC pour appliquer la configuration.

> [!NOTE]
> Pour permettre l’exécution de DSC, Windows doit être configuré pour recevoir des commandes à distance PowerShell, même lorsque vous exécutez une configuration `localhost`. Pour configurer facilement et correctement votre environnement, exécutez simplement `Set-WsManQuickConfig -Force` dans un terminal PowerShell avec élévation de privilèges.

Dans une console PowerShell, accédez au dossier où vous avez enregistré votre configuration et exécutez la commande suivante :

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Tester la configuration

Vous pouvez appeler l’applet de commande [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) pour vérifier si la configuration a réussi.

Vous pouvez également tester les résultats directement, dans ce cas en accédant à `http://localhost/` dans un navigateur web.
Vous devez voir la page HTML « Hello World » que vous avez créée lors de la première étape dans cet exemple.

## <a name="next-steps"></a>Étapes suivantes

- En savoir plus sur les configurations DSC sous [Configurations DSC](../configurations/configurations.md).
- Consultez les ressources DSC disponibles et découvrez comment créer des ressources DSC personnalisées sous [Ressources DSC](../resources/resources.md).
- Recherchez des configurations et des ressources DSC dans la [galerie PowerShell](https://www.powershellgallery.com/).
