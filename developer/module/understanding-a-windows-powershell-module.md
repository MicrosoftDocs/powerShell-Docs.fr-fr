---
title: Comprendre un Module PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: cff50d415c4c90182fa1cf015a5a5ba84d4d613a
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470776"
---
# <a name="understanding-a-windows-powershell-module"></a>Présentation d’un module Windows PowerShell

Un *module* est un ensemble de fonctionnalités de Windows PowerShell connexes, regroupés sous la forme d’une unité pratique (généralement enregistrée dans un répertoire unique). En définissant un ensemble de fichiers de script associées, les assemblys et les ressources associées en tant que module, vous pouvez référencer, charger, conserver et partager votre code beaucoup plus facile que vous le feriez dans le cas contraire.

L’objectif principal d’un module consiste à autoriser la modularisation (Internet Explorer, réutilisation et l’abstraction) du code Windows PowerShell. Par exemple, la façon la plus simple de création d’un module est simplement enregistrer un script Windows PowerShell sous la forme d’un fichier .psm1. Vous pouvez ainsi au contrôle (Internet Explorer, rendre publique ou privée) les fonctions et les variables contenues dans le script. L’enregistrement du script sous forme de fichier .psm1 vous permet également de contrôler la portée de certaines variables. Enfin, vous pouvez également utiliser applets de commande comme [Install-Module](/powershell/module/PowershellGet/Install-Module) pour organiser, installer et utiliser votre script en tant que blocs de construction pour les solutions plus volumineuses.

## <a name="module-components-and-types"></a>Types et les composants de module

Un module est constitué de quatre composants fondamentaux :

1. Certains trier du fichier de code, généralement un script PowerShell ou un assembly managé applet de commande.

2. Tout autre élément que le fichier de code ci-dessus peut besoin, telles que des assemblys supplémentaires, d’aide des scripts ou des fichiers.

3. Un fichier manifeste qui décrit les fichiers ci-dessus, mais aussi stocke des métadonnées telles que des informations d’auteur et le contrôle de version...

4. Un répertoire qui contient tous les éléments ci-dessus et se trouve où PowerShell peut raisonnablement le trouver.

   Notez qu’aucune de ces composants, par eux-mêmes, sont réellement nécessaires. Par exemple, un module peut être techniquement uniquement un script stocké dans un fichier .psm1. Vous pouvez également avoir un module qui n’est rien d’autre qu’un fichier manifeste, qui sert principalement à des fins d’organisation. Vous pouvez également écrire un script qui crée dynamiquement un module et par conséquent, n’a pas besoin en fait un répertoire pour stocker n’importe quel élément. Les sections suivantes décrivent les types de modules que vous pouvez obtenir mélanger et associer les différentes parties possibles d’un module ensemble.

### <a name="script-modules"></a>Modules de script

Comme son nom l’indique, un *module de script* est un fichier (.psm1) qui contient un code de Windows PowerShell valid. Les administrateurs et développeurs de script peuvent utiliser ce type de module pour créer des modules dont les membres incluent des fonctions, variables et bien plus encore. Au fond, un module de script est simplement un script Windows PowerShell avec une autre extension, ce qui permet aux administrateurs d’utiliser des fonctions d’importation, d’exportation et de gestion sur ce dernier.

En outre, vous pouvez utiliser un fichier manifeste pour inclure d’autres ressources dans votre module, tels que les fichiers de données, autres modules dépendants ou des scripts d’exécution. Fichiers manifeste sont également utiles pour le suivi des métadonnées telles que les informations de création et le contrôle de version.

Enfin, un module de script, comme tout autre module qui n’est pas créé dynamiquement, doit être enregistrée dans un dossier PowerShell peut raisonnablement découvrir. En règle générale, il s’agit du chemin d’accès du module PowerShell ; mais si nécessaire vous pouvez décrire de façon explicite où votre module est installé. Pour plus d’informations, consultez [comment écrire un Module de Script PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Modules binaires

Un *module binaire* est un assembly .NET Framework (.dll) qui contient le code compilé, tel que C#. Les développeurs d’applet de commande permettent ce type de module de partager des applets de commande, fournisseurs et bien plus encore. (Composants logiciel enfichables existants peuvent également servir en tant que modules binaires.) Par rapport à un module de script, un module binaire vous permet de créer des applets de commande qui sont plus rapides ou utiliser les fonctionnalités (telles que le multithreading) qui ne sont pas aussi facile à coder dans les scripts Windows PowerShell.

Comme avec les modules de script, vous pouvez inclure un fichier manifeste pour décrire des ressources supplémentaires qui utilise votre module et pour effectuer le suivi des métadonnées relatives à votre module. De même, vous probablement devez installer votre module binaire dans un dossier quelque part sur le chemin d’accès du module PowerShell. Pour plus d’informations, consultez Comment [comment écrire un Module binaire PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Modules de manifeste

Un *module de manifeste* est un module qui utilise un fichier manifeste pour décrire tous ses composants, mais n’a pas une forme quelconque d’assembly principal ou un script. (Formellement, un module de manifeste quitte le `ModuleToProcess` ou `RootModule` élément du manifeste vide.) Toutefois, vous pouvez toujours utiliser les autres fonctionnalités d’un module, telles que la possibilité de charger des assemblys dépendants ou exécuter automatiquement certains scripts de pré-traitement. Vous pouvez également utiliser un module de manifeste comme un moyen pratique pour empaqueter des ressources autres modules utilisera, telles que les modules imbriqués, assemblys, types ou formats. Pour plus d’informations, consultez [comment écrire un manifeste de Module PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Modules dynamiques

Un *module dynamique* est un module qui n’est pas chargé à partir ou enregistré dans un fichier. Au lieu de cela, elles sont créées dynamiquement par un script, à l’aide de la [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) applet de commande. Ce type de module permet un script créer un module à la demande ne devant pas être chargé ou enregistré vers le stockage persistant. Par sa nature, un module dynamique est destiné à être de courte durée et par conséquent ne peut pas être accessible par le `Get-Module` applet de commande. De même, ils ne doivent généralement pas de manifestes de module, ni qu’elles probablement dossiers permanents pour stocker leurs assemblys associés.

## <a name="module-manifests"></a>Manifestes de module

Un *manifeste de module* est un fichier .psd1 qui contient une table de hachage. Les clés et valeurs dans la table de hachage, procédez comme suit :

- Décrire le contenu et les attributs du module.

- Définissent les conditions préalables.

- Déterminer comment les composants sont traités.

  Les manifestes ne sont pas nécessaires pour un module. Modules peuvent référencer des fichiers de script (.ps1), fichiers de module (.psm1), les fichiers manifeste (.psd1), mise en forme de script et tapez les fichiers (.ps1xml), applet de commande et fournisseur assemblys (.dll), fichiers de ressources, fichiers d’aide, les fichiers de localisation ou tout autre type de fichier ou une ressource qui est fourni en tant que partie du module. Pour un script internationaux, le dossier de module contient également un ensemble de fichiers de catalogue de messages. Si vous ajoutez un fichier manifeste dans le dossier de module, vous pouvez référencer plusieurs fichiers comme une seule unité en référençant le manifeste.

  Le manifeste lui-même décrit les catégories d’informations suivantes :

- Métadonnées sur le module, tels que le numéro de version du module, l’auteur et la description.

- Conditions requises pour importer le module, tels que la version de Windows PowerShell, la version du common language runtime (CLR) et les modules requis.

- Directives de traitement, telles que les scripts, les formats et les types à traiter.

- Restrictions sur les membres du module à exporter, telles que des alias, des fonctions, des variables et des applets de commande pour exporter.

  Pour plus d’informations, consultez [comment écrire un manifeste de Module PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Stockage et l’installation d’un Module

Une fois que vous avez créé un script, le module binaire ou manifest, vous pouvez enregistrer votre travail dans un emplacement que d’autres utilisateurs puissent y accéder. Par exemple, votre module peut être stocké dans le dossier système où Windows PowerShell est installé, ou il peut être stocké dans un dossier de l’utilisateur.

En règle générale, vous pouvez déterminer où vous devez installer le module à l’aide d’un des chemins d’accès stockées dans le `$ENV:PSModulePath` variable. En utilisant l’une de ces chemins d’accès signifie que PowerShell peut automatiquement rechercher et charger votre module quand un utilisateur effectue un appel à celui-ci dans leur code. Si vous stockez votre module vers un autre emplacement, vous pouvez faire explicitement PowerShell savoir en passant à l’emplacement de votre module en tant que paramètre lorsque vous appelez `Install-Module`.

Tous les cas, le chemin d’accès du dossier est appelé le *base* du module (ModuleBase) et le nom du script, fichier binaire ou le manifeste de module doit être le même que le nom du dossier de module, avec les exceptions suivantes :

- Les modules dynamiques qui sont créés par le `New-Module` applet de commande peut être nommé à l’aide de le `Name` paramètre de l’applet de commande.

- Modules importés à partir d’objets de l’assembly par le  **`Import-Module` -Assembly** commande sont nommées en fonction de la syntaxe suivante : `"dynamic_code_module_" + assembly.GetName()`.

  Pour plus d’informations, consultez [installation d’un PowerShell Module](./installing-a-powershell-module.md) et [modifier le chemin d’Installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Variables et des applets de commande de module

Les applets de commande et les variables suivantes sont fournies par Windows PowerShell pour la création et la gestion des modules.

[Nouveau Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) applet de commande cette applet de commande crée un nouveau module dynamique qui existe uniquement en mémoire. Le module est créé à partir d’un bloc de script et ses membres exportés, telles que ses fonctions et variables, sont immédiatement disponibles dans la session et restent disponibles jusqu'à ce que la session est fermée.

[Nouveau-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) applet de commande cette applet de commande crée un nouveau fichier de manifeste (.psd1) du module, remplit ses valeurs et enregistre le fichier manifeste dans le chemin d’accès spécifié. Cette applet de commande peut également être utilisé pour créer un modèle de manifeste de module qui peut être renseigné manuellement.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande cette applet de commande ajoute un ou plusieurs modules à la session active.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) applet de commande cette applet de commande récupère des informations sur les modules qui ont été ou qui peuvent être importés dans la session active.

[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) applet de commande cette applet de commande spécifie les membres de module (par exemple, les applets de commande, fonctions, variables et les alias) qui sont exportés à partir d’un fichier de module (.psm1) de script ou d’un module dynamique créé à l’aide de la `New-Module` applet de commande.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) applet de commande cette applet de commande supprime les modules à partir de la session active.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) applet de commande cette applet de commande vérifie qu’un manifeste de module décrit précisément les composants d’un module en vérifiant que les fichiers qui sont répertoriés dans le fichier de manifeste de module (.psd1) existent réellement dans les chemins d’accès spécifiés.

$PSScriptRoot cette variable contient le répertoire à partir de laquelle le module de script est en cours d’exécution. Il permet aux scripts d’utiliser le chemin d’accès du module pour accéder aux autres ressources.

$env : PSModulePath cette variable d’environnement contient une liste des répertoires dans les PowerShell Windows modules sont stockés. Windows PowerShell utilise la valeur de cette variable lors de l’importation automatique des modules et des rubriques d’aide pour les modules de la mise à jour.

## <a name="see-also"></a>Voir aussi

[Écrire un Module PowerShell de Windows](./writing-a-windows-powershell-module.md)
