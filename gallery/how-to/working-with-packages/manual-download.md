---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery
title: Téléchargement manuel de package
ms.openlocfilehash: 0952aa4ec474850af5219fb2e0e9ee3e954b0f9a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003701"
---
# <a name="manual-package-download"></a>Téléchargement manuel de package

Powershell Gallery permet de télécharger un package directement à partir du site web, sans utiliser les applets de commande PowerShellGet. Le package est téléchargé sous forme de fichier de package NuGet (.nupkg), qui peut être copié facilement dans un référentiel interne.

> [!NOTE]
> Le téléchargement manuel de package n’est **pas** censé se substituer à l’applet de commande Install-Module.
> Le téléchargement du package n’installe pas le module ou le script. Les dépendances ne sont pas incluses dans le package NuGet téléchargé. Les instructions suivantes sont fournies à titre de référence uniquement.

## <a name="using-manual-download-to-acquire-a-package"></a>Utilisation du téléchargement manuel pour obtenir un package

Chaque page comporte un lien Téléchargement manuel, comme illustré ici :

![Téléchargement manuel](../../Images/packagedisplaypagewithpseditions.png)

Pour télécharger manuellement, cliquez sur **Télécharger le fichier nupkg brut**. Une copie du package est copiée dans le dossier de téléchargement de votre navigateur sous le nom `<name>.<version>.nupkg`.

Un package NuGet est une archive ZIP composée de fichiers supplémentaires contenant des informations sur le contenu du package. Certains navigateurs, comme Internet Explorer, remplacent automatiquement l’extension de fichier `.nupkg` par `.zip`. Pour développer le package, renommez le fichier `.nupkg` en `.zip`, si nécessaire, puis extrayez le contenu dans un dossier local.

Un fichier de package NuGet comprend les éléments spécifiques NuGet suivants qui ne font pas partie du code empaqueté d’origine :

- Un dossier nommé `_rels` contenant un fichier `.rels` qui répertorie les dépendances
- Un dossier nommé `package` contenant les données spécifiques NuGet
- Un fichier nommé `[Content_Types].xml` décrivant la façon dont les extensions comme PowerShellGet fonctionnent avec NuGet
- Un fichier nommé `<name>.nuspec` contenant la majeure partie des métadonnées

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Installation de modules PowerShell à partir d’un package NuGet

> [!NOTE]
> Ces instructions **NE donnent PAS** les mêmes résultats qu’une exécution de `Install-Module`. Ces instructions répondent aux exigences minimales. Elles ne sont pas destinées à se substituer à `Install-Module`. Certaines étapes effectuées par `Install-Module` ne sont pas incluses.

L’approche la plus simple consiste à supprimer les éléments spécifiques NuGet du dossier. Le code PowerShell créé par l’auteur du package est ainsi conservé. Les étapes à suivre sont les suivantes :

1. Extrayez le contenu du package NuGet dans un dossier local.
2. Supprimez les éléments spécifiques NuGet du dossier.
3. Renommez le dossier. Le nom de dossier par défaut est généralement `<name>.<version>`. La version peut inclure « -prerelease » si le module est marqué comme étant une version préliminaire. Renommez le dossier en conservant uniquement le nom du module. Par exemple, « azurerm.storage.5.0.4-preview » devient « azurerm.storage ».
4. Copiez le dossier dans votre chemin PSModulePath.

> [!IMPORTANT]
> Le téléchargement manuel n’inclut pas les dépendances nécessaires au module. Si le package a des dépendances, elles doivent être installées sur le système pour permettre à ce module de fonctionner correctement. PowerShell Gallery affiche toutes les dépendances nécessaires au package.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Installation de scripts PowerShell à partir d’un package NuGet

> [!NOTE]
> Ces instructions **NE donnent PAS** les mêmes résultats qu’une exécution de `Install-Script`. Ces instructions répondent aux exigences minimales. Elles ne sont pas destinées à se substituer à `Install-Script`.

L’approche la plus simple consiste à extraire le package NuGet, puis à utiliser le script directement. Les étapes à suivre sont les suivantes :

1. Extrayez le contenu du package NuGet.
2. Le fichier `.PS1` contenu dans le dossier peut être utilisé directement à partir de cet emplacement.
3. Vous pouvez supprimer les éléments spécifiques NuGet du dossier.

> [!IMPORTANT]
> Le téléchargement manuel n’inclut pas les dépendances nécessaires au module. Si le package a des dépendances, elles doivent être installées sur le système pour permettre à ce module de fonctionner correctement. PowerShell Gallery affiche toutes les dépendances nécessaires au package.