---
title: Créer une aide XML à l’aide de PlatyPS
description: Utiliser PlatyPS est la méthode rapide et efficace pour créer une aide XML.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972573"
---
# <a name="create-xml-based-help-using-platyps"></a>Créer une aide XML à l’aide de PlatyPS

Quand vous créez un module PowerShell, il est toujours recommandé d’inclure une aide détaillée sur les applets de commande que vous créez. Si vos applets de commande sont implémentées dans du code compilé, vous devez utiliser l’aide XML. Ce format XML est connu sous le nom de MAML (Microsoft Assistance Markup Language).

La documentation du SDK PowerShell hérité décrit en détail la création d’une aide pour des applets de commande PowerShell empaquetées dans des modules. En revanche, PowerShell ne fournit pas d’outils pour créer cette aide XML. La documentation du SDK explique la structure de l’aide MAML, mais vous laisse la tâche de créer manuellement le contenu MAML complexe et profondément imbriqué.

C’est là que le module [PlatyPS][] peut vous aider.

## <a name="what-is-platyps"></a>Qu’est-ce que PlatyPS ?

PlatyPS est un outil [open source][platyps-repo] qui a démarré sous la forme d’un projet _hackathon_ visant à faciliter la création et la maintenance de MAML. PlatyPS documente la syntaxe des jeux de paramètres et les paramètres individuels de chaque applet de commande incluse dans votre module. PlatyPS crée des fichiers [Markdown][] structurés qui contiennent les informations sur la syntaxe. Il ne permet pas de créer des descriptions ni de fournir des exemples.

PlatyPS crée des espaces réservés pour vous permettre de renseigner des descriptions et des exemples. Après avoir ajouté les informations nécessaires, PlatyPS compile les fichiers Markdown dans des fichiers MAML. Le système d’aide de PowerShell autorise aussi les fichiers d’aide conceptuelle en texte brut (rubriques À propos de). PlatyPS dispose d’une applet de commande pour créer un modèle Markdown structuré pour un nouveau fichier _À propos de_, mais ces fichiers `about_*.help.txt` doivent être gérés manuellement.

Vous pouvez inclure les fichiers d’aide MAML et texte dans votre module. Vous pouvez également utiliser PlatyPS pour compiler les fichiers d’aide dans un package CAB que vous pouvez héberger pour une aide modifiable.

## <a name="get-started-using-platyps"></a>Démarrer avec PlatyPS

Tout d’abord, vous devez installer PlatyPS à partir de PowerShell Gallery.

```powershell
Install-Module platyps -Force
Import-Module platyps
```

L’organigramme suivant décrit le processus de création ou de mise à jour du contenu de référence PowerShell.

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="Workflow de la création d’une aide XML à l’aide de PlatyPS":::

##  <a name="create-markdown-content-for-a-powershell-module"></a>Créer du contenu Markdown pour un module PowerShell

1. Importez votre nouveau module dans la session. Répétez cette étape pour chaque module à documenter.

   Exécutez la commande suivante pour importer vos modules :

   ```powershell
   Import-Module <your module name>
   ```

1. Utilisez PlatyPS pour générer des fichiers Markdown pour votre page de module et toutes les applets de commande associées dans le module. Répétez cette étape pour chaque module à documenter.

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   Si le dossier de sortie n’existe pas, `New-MarkdownHelp` le crée. Dans cet exemple, `New-MarkdownHelp` crée un fichier Markdown pour chaque applet de commande dans le module. La _page de module_ est également créée dans un fichier nommé `<ModuleName>.md`. Cette page de module contient la liste des applets de commande contenues dans le module et des espaces réservés pour la description de **Synopsis**. Les métadonnées de la page de module proviennent du manifeste du module. PlatyPS les utilise pour créer le fichier XML HelpInfo (comme expliqué [ci-dessous](#creating-an-updateable-help-package)).

   `New-MarkdownAboutHelp` crée un fichier _about_ nommé `about_topic_name.md`.

   Pour plus d’informations, consultez [New-MarkdownHelp][] et [New-MarkdownAboutHelp][].

### <a name="update-existing-markdown-content-when-the-module-changes"></a>Mettre à jour le contenu Markdown existant quand le module change

PlatyPS peut également mettre à jour les fichiers Markdown existants pour un module. Utilisez cette étape pour mettre à jour des modules existants qui incluent de nouvelles applets de commande, de nouveaux paramètres ou des paramètres modifiés.

1. Importez votre nouveau module dans la session. Répétez cette étape pour chaque module à documenter.

   Exécutez la commande suivante pour importer vos modules :

   ```powershell
   Import-Module <your module name>
   ```

1. Utilisez PlatyPS pour mettre à jour les fichiers Markdown de la page d’arrivée de votre module et toutes les applets de commande associées dans le module. Répétez cette étape pour chaque module à documenter.

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   `Update-MarkdownHelpModule` met à jour l’applet de commande et les fichiers Markdown du module dans le dossier spécifié.
   Cette commande ne met pas à jour les fichiers `about_*.md`. Le fichier du module (`ModuleName.md`) reçoit tout nouveau texte **Synopsis** ajouté aux fichiers d’applet de commande. Les mises à jour apportées aux fichiers d’applet de commande incluent les modifications suivantes :

   - Nouveaux jeux de paramètres
   - Nouveaux paramètres
   - Métadonnées de paramètre mises à jour
   - Informations de type d’entrée et de sortie mises à jour

   Pour plus d’informations, consultez [Update-MarkdownHelpModule][].

## <a name="edit-the-new-or-updated-markdown-files"></a>Modifier les fichiers Markdown nouveaux ou mis à jour

PlatyPS documente la syntaxe des jeux de paramètres et les paramètres individuels. L’outil ne permet pas de créer des descriptions ni de fournir des exemples. Les zones spécifiques dans lesquelles du contenu est nécessaire sont indiquées entre accolades. Par exemple : `{{ Fill in the Description }}`

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="Modèle Markdown présentant des espaces réservés dans VS Code":::

Vous avez besoin d’ajouter un synopsis, une description de l’applet de commande, des descriptions pour chaque paramètre et au moins un exemple.

Pour plus d’informations sur l’écriture de contenu PowerShell, consultez les articles suivants :

- [Guide de style PowerShell](/powershell/scripting/community/contributing/powershell-style-guide)
- [Modification des articles de référence](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> PlatyPS inclut un schéma spécifique utilisé pour les informations de référence des applets de commande. Ce schéma autorise uniquement certains blocs Markdown dans des sections spécifiques du document. Si vous placez du contenu au mauvais endroit, l’étape de génération PlatyPS échoue. Pour plus d’informations, consultez la documentation sur le [schéma][] dans le référentiel PlatyPS. Pour obtenir un exemple complet d’informations de référence sur une applet de commande bien formée, consultez [Get-Item][].

Une fois que vous avez fourni le contenu nécessaire pour chacune de vos applets de commande, vous devez veiller à mettre à jour la page d’arrivée du module. Vérifiez que votre module a les valeurs `Module Guid` et `Download Help Link` appropriées dans les métadonnées YAML du fichier `<module-name>.md`. Ajoutez toutes les métadonnées manquantes.

De plus, vous pouvez remarquer que certaines applets de commande n’ont pas de **Synopsis** (_description brève_). La commande suivante met à jour la page d’arrivée du module avec votre texte de description **Synopsis**. Ouvrez la page d’arrivée du module pour vérifier les descriptions.

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

Maintenant que vous avez entré tout le contenu, vous pouvez créer les fichiers d’aide MAML que `Get-Help` va permettre d’afficher dans la console PowerShell.

## <a name="create-the-external-help-files"></a>Créer les fichiers d’aide externes

Cette étape crée les fichiers d’aide MAML affichés par `Get-Help` dans la console PowerShell.

Pour générer les fichiers MAML, exécutez la commande suivante :

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

`New-ExternalHelp` convertit tous les fichiers Markdown d’applet de commande en un ou plusieurs fichiers MAML. Les fichiers À propos de sont convertis en fichiers texte brut avec le format de nom suivant : `about_topic_name.help.txt`.
Le contenu Markdown doit satisfaire aux exigences du schéma PlatyPS. `New-ExternalHelp` se termine avec des erreurs quand le contenu ne suit pas le schéma. Vous devez modifier les fichiers pour corriger les violations de schéma.

> [!CAUTION]
> PlatyPS ne parvient pas à convertir correctement les fichiers `about_*.md` en texte brut. Pour obtenir des résultats acceptables, vous devez utiliser un langage Markdown très simple. Envisagez éventuellement de garder les fichiers au format texte brut `about_topic_name.help.txt`, plutôt que d’autoriser PlatyPS à les convertir.

Une fois cette étape terminée, les fichiers `*-help.xml` et `about_*.help.txt` apparaissent dans le dossier de sortie cible.

Pour plus d’informations, consultez [New-ExternalHelp][].

### <a name="test-the-compiled-help-files"></a>Tester les fichiers d’aide compilés

Vous pouvez vérifier le contenu à l’aide de l’applet de commande [Get-HelpPreview][] :

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

L’applet de commande lit le fichier MAML compilé et génère le contenu dans le même format que celui que vous recevez de `Get-Help`. Ainsi, vous pouvez inspecter les résultats pour vérifier que les fichiers Markdown ont été compilés correctement et qu’ils produisent les résultats voulus. Si vous trouvez une erreur, remodifiez les fichiers Markdown et recompilez le MAML.

Vous pouvez à présent publier vos fichiers d’aide.

## <a name="publishing-your-help"></a>Publication de votre aide

Maintenant que vous avez compilé les fichiers Markdown dans des fichiers d’aide PowerShell, vous êtes prêt à les mettre à la disposition des utilisateurs. Deux possibilités s’offrent à vous pour fournir de l’aide dans la console PowerShell.

- Empaqueter les fichiers d’aide avec le module
- Créer un package d’aide modifiable que les utilisateurs installent avec l’applet de commande `Update-Help`

### <a name="packaging-help-with-the-module"></a>Empaquetage de l’aide avec le module

Les fichiers d’aide peuvent être empaquetés avec votre module. Pour plus d’informations sur la structure des dossiers, consultez [Écriture d’aide pour les modules][]. Vous devez inclure la liste des fichiers d’aide dans la valeur de la clé **FileList** qui se trouve dans le manifeste du module.

### <a name="creating-an-updateable-help-package"></a>Création d’un package d’aide modifiable

En règle générale, les étapes permettant de créer une aide modifiable sont les suivantes :

1. Trouver un site Internet pour héberger vos fichiers d’aide
1. Ajouter une clé **HelpInfoURI** au manifeste de votre module
1. Créer un fichier XML HelpInfo
1. Créer des fichiers CAB
1. Charger vos fichiers

Pour plus d’informations, consultez [Prise en charge de l’aide modifiable : procédure pas à pas][step-by-step].

PlatyPS vous accompagne tout au long d’une partie de ces étapes.

**HelpInfoURI** correspond à une URL qui pointe vers l’emplacement où vos fichiers d’aide sont hébergés sur Internet. Cette valeur est configurée dans le manifeste du module. `Update-Help` lit le manifeste du module pour obtenir cette URL et télécharger le contenu de l’aide modifiable. Cette URL doit uniquement pointer vers l’emplacement du dossier et non celui de fichiers individuels. `Update-Help` construit les noms de fichiers à télécharger en fonction d’autres informations issues du manifeste du module et du fichier XML HelpInfo.

> [!IMPORTANT]
> **HelpInfoURI** doit se terminer par une barre oblique (`/`). Sans ce caractère, `Update-Help` ne peut pas construire les chemins de fichier corrects pour télécharger le contenu. De plus, la plupart des services de fichiers HTTP sont sensibles à la casse. Il est important que les métadonnées du module dans le fichier XML HelpInfo contiennent la bonne casse.

L’applet de commande `New-ExternalHelp` crée le fichier XML HelpInfo dans le dossier de sortie. Le fichier XML HelpInfo est généré à l’aide des métadonnées YAML contenues dans les fichiers Markdown du module (`ModuleName.md`).

L’applet de commande `New-ExternalHelpCab` crée des fichiers ZIP et CAB qui contiennent les fichiers MAML et `about_*.help.txt` que vous avez compilés. Les fichiers CAB sont compatibles avec toutes les versions de PowerShell.
PowerShell 6 et ses versions ultérieures peuvent utiliser des fichiers ZIP.

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

Après avoir créé les fichiers ZIP et CAB, chargez les fichiers ZIP, CAB et XML HelpInfo sur votre serveur de fichiers HTTP. Placez les fichiers à l’emplacement indiqué par **HelpInfoURI**.

Pour plus d’informations, consultez [New-ExternalHelpCab][].

### <a name="other-publishing-options"></a>Autres options de publication

Markdown est un format polyvalent facile à transformer en d’autres formats à des fins de publication. À l’aide d’un outil comme [Pandoc][], vous pouvez convertir vos fichiers d’aide Markdown en de nombreux autres formats de document, notamment les formats texte brut, HTML, PDF et Office.

De plus, les applets de commande [ConvertFrom-Markdown][] et [Show-Markdown][] dans PowerShell 6 et ses versions ultérieures peuvent être utilisées pour convertir le format Markdown au format HTML ou créer un affichage en couleurs dans la console PowerShell.

## <a name="known-issues"></a>Problèmes connus

PlatyPS est très sensible au [schéma][] pour la structure des fichiers Markdown qu’il crée et compile. Il est très facile d’écrire du langage Markdown valide qui enfreint ce schéma. Pour plus d’informations, consultez [Guide de style PowerShell][] et [Modification des articles de référence][].

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[Guide de style PowerShell]: /powershell/scripting/community/contributing/powershell-style-guide
[Modification des articles de référence]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Écriture d’aide pour les modules]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
