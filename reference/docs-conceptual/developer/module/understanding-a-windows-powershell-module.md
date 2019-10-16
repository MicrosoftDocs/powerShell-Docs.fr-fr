---
title: Fonctionnement d’un module Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360638"
---
# <a name="understanding-a-windows-powershell-module"></a>Présentation d’un module Windows PowerShell

Un *module* est un ensemble de fonctionnalités Windows PowerShell associées, regroupées sous la forme d’une unité pratique (généralement enregistrée dans un répertoire unique). En définissant un ensemble de fichiers de script, d’assemblys et de ressources connexes en tant que module, vous pouvez faire référence, charger, conserver et partager votre code beaucoup plus facilement que vous ne le feriez autrement.

L’objectif principal d’un module est d’autoriser la modularisation (IE, réutilisation et abstraction) du code Windows PowerShell. Par exemple, la méthode la plus simple pour créer un module consiste simplement à enregistrer un script Windows PowerShell en tant que fichier. psm1. Cela vous permet de contrôler (par ex., rendre publiques ou privées) les fonctions et variables contenues dans le script. L’enregistrement du script sous la forme d’un fichier. psm1 vous permet également de contrôler la portée de certaines variables. Enfin, vous pouvez également utiliser des applets de commande, telles que [install-module](/powershell/module/PowershellGet/Install-Module) , pour organiser, installer et utiliser votre script comme des blocs de construction pour des solutions plus volumineuses.

## <a name="module-components-and-types"></a>Composants et types de module

Un module est constitué de quatre composants de base :

1. Une sorte de fichier de code (généralement un script PowerShell ou un assembly d’applet de commande géré).

2. Autre chose que le fichier de code ci-dessus peut avoir besoin, comme des assemblys supplémentaires, des fichiers d’aide ou des scripts.

3. Fichier manifeste qui décrit les fichiers ci-dessus, ainsi que stocke les métadonnées telles que les informations d’auteur et de contrôle de version.

4. Répertoire qui contient tout le contenu ci-dessus et qui se trouve là où PowerShell peut raisonnablement le trouver.

   Notez qu’aucun de ces composants n’est réellement nécessaire. Par exemple, un module peut techniquement être un script stocké dans un fichier. psm1. Vous pouvez également avoir un module qui n’est rien mais un fichier manifeste, qui est principalement utilisé à des fins d’organisation. Vous pouvez également écrire un script qui crée dynamiquement un module et, par conséquent, n’a pas besoin d’un répertoire pour stocker quoi que ce soit. Les sections suivantes décrivent les types de modules que vous pouvez obtenir en combinant et en faisant correspondre les différentes parties possibles d’un module.

### <a name="script-modules"></a>Modules de script

Comme son nom l’indique, un *module de script* est un fichier (. psm1) qui contient un code Windows PowerShell valide. Les développeurs de scripts et les administrateurs peuvent utiliser ce type de module pour créer des modules dont les membres incluent des fonctions, des variables, etc. Au coeur, un module de script est simplement un script Windows PowerShell avec une extension différente, qui permet aux administrateurs d’utiliser des fonctions d’importation, d’exportation et de gestion.

En outre, vous pouvez utiliser un fichier manifeste pour inclure d’autres ressources dans votre module, telles que des fichiers de données, d’autres modules dépendants ou des scripts d’exécution. Les fichiers manifestes sont également utiles pour le suivi des métadonnées telles que la création et la gestion des versions.

Enfin, un module de script, comme tout autre module qui n’est pas dynamiquement créé, doit être enregistré dans un dossier que PowerShell peut raisonnablement découvrir. En règle générale, il s’agit du chemin d’accès au module PowerShell ; mais si nécessaire, vous pouvez décrire explicitement l’emplacement d’installation de votre module. Pour plus d’informations, consultez [Comment écrire un module de script PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Modules binaires

Un *module binaire* est un assembly .NET Framework (. dll) qui contient le code compilé, C#tel que. Les développeurs d’applets de commande peuvent utiliser ce type de module pour partager des applets de commande, des fournisseurs, etc. (Les composants logiciels enfichables existants peuvent également être utilisés en tant que modules binaires.) Par rapport à un module de script, un module binaire vous permet de créer des applets de commande plus rapides ou utilisant des fonctionnalités (telles que le multithreading) qui ne sont pas aussi faciles à coder dans les scripts Windows PowerShell.

Comme avec les modules de script, vous pouvez inclure un fichier manifeste pour décrire les ressources supplémentaires utilisées par votre module et pour suivre les métadonnées relatives à votre module. De même, vous devez probablement installer votre module binaire dans un dossier situé dans le chemin d’accès du module PowerShell. Pour plus d’informations, consultez Comment [écrire un module binaire PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Modules de manifeste

Un *module de manifeste* est un module qui utilise un fichier manifeste pour décrire tous ses composants, mais qui n’a aucun type d’assembly ou de script principal. (Formellement, un module de manifeste laisse l’élément `ModuleToProcess` ou `RootModule` du manifeste vide.) Toutefois, vous pouvez toujours utiliser les autres fonctionnalités d’un module, telles que la possibilité de charger des assemblys dépendants ou d’exécuter automatiquement certains scripts de pré-traitement. Vous pouvez également utiliser un module de manifeste comme un moyen pratique d’empaqueter des ressources que d’autres modules utiliseront, telles que des modules imbriqués, des assemblys, des types ou des formats. Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Modules dynamiques

Un *module dynamique* est un module qui n’est pas chargé à partir d’un fichier, ou enregistré dans celui-ci. Au lieu de cela, ils sont créés dynamiquement par un script, à l’aide de l’applet [de commande New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) . Ce type de module permet à un script de créer un module à la demande qui n’a pas besoin d’être chargé ou enregistré dans un stockage persistant. Par nature, un module dynamique est destiné à être éphémère et, par conséquent, n’est pas accessible par l’applet de commande `Get-Module`. De même, ils n’ont généralement pas besoin de manifestes de module, pas plus qu’ils n’ont probablement besoin de dossiers permanents pour stocker leurs assemblys associés.

## <a name="module-manifests"></a>Manifestes de module

Un *manifeste de module* est un fichier. psd1 qui contient une table de hachage. Les clés et les valeurs de la table de hachage effectuent les opérations suivantes :

- Décrivez le contenu et les attributs du module.

- Définissez les conditions préalables.

- Déterminez la façon dont les composants sont traités.

  Les manifestes ne sont pas nécessaires pour un module. Les modules peuvent référencer des fichiers de script (. ps1), des fichiers de module de script (. psm1), des fichiers manifeste (. psd1), des fichiers de mise en forme et de type (. ps1xml), des assemblys de cmdlet et de fournisseur (. dll), des fichiers de ressources, des fichiers d’aide, des fichiers de localisation ou tout autre type de fichier est fourni dans le cadre du module. Pour un script international, le dossier du module contient également un ensemble de fichiers du catalogue de messages. Si vous ajoutez un fichier manifeste au dossier de module, vous pouvez référencer les fichiers multiples en tant qu’unité unique en référençant le manifeste.

  Le manifeste lui-même décrit les catégories d’informations suivantes :

- Métadonnées relatives au module, telles que le numéro de version du module, l’auteur et la description.

- Conditions préalables requises pour importer le module, telles que la version de Windows PowerShell, la version du common language runtime (CLR) et les modules requis.

- Les directives de traitement, telles que les scripts, les formats et les types à traiter.

- Restrictions sur les membres du module à exporter, telles que les alias, les fonctions, les variables et les applets de commande à exporter.

  Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Stockage et installation d’un module

Une fois que vous avez créé un script, un fichier binaire ou un module manifeste, vous pouvez enregistrer votre travail dans un emplacement auquel d’autres utilisateurs peuvent y accéder. Par exemple, votre module peut être stocké dans le dossier système où Windows PowerShell est installé, ou il peut être stocké dans un dossier utilisateur.

En règle générale, vous pouvez déterminer où vous devez installer votre module en utilisant l’un des chemins d’accès stockés dans la variable `$ENV:PSModulePath`. L’utilisation de l’un de ces chemins d’accès signifie que PowerShell peut rechercher et charger automatiquement votre module lorsqu’un utilisateur effectue un appel vers celui-ci dans son code. Si vous stockez votre module ailleurs, vous pouvez laisser PowerShell déterminer explicitement en passant l’emplacement de votre module en tant que paramètre lorsque vous appelez `Install-Module`.

Indépendamment, le chemin d’accès du dossier est appelé *base* du module (ModuleBase), et le nom du fichier de script, binaire ou du module de manifeste doit être le même que le nom du dossier de module, avec les exceptions suivantes :

- Les modules dynamiques créés par l’applet de commande `New-Module` peuvent être nommés à l’aide du paramètre `Name` de l’applet de commande.

- Les modules importés à partir d’objets assembly par la commande **`Import-Module`-assembly** sont nommés selon la syntaxe suivante : `"dynamic_code_module_" + assembly.GetName()`.

  Pour plus d’informations, consultez [installation d’un module PowerShell](./installing-a-powershell-module.md) et [modification du chemin d’installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Applets de commande et variables de module

Les applets de commande et les variables suivantes sont fournies par Windows PowerShell pour la création et la gestion des modules.

Applet [de commande New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cette applet de commande crée un module dynamique qui existe uniquement en mémoire. Le module est créé à partir d’un bloc de script, et ses membres exportés, tels que ses fonctions et variables, sont immédiatement disponibles dans la session et restent disponibles jusqu’à la fermeture de la session.

Applet [de commande New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cette applet de commande crée un fichier manifeste de module (. psd1), remplit ses valeurs et enregistre le fichier manifeste dans le chemin d’accès spécifié. Cette applet de commande peut également être utilisée pour créer un modèle de manifeste de module qui peut être rempli manuellement.

Applet [de commande Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cette applet de commande ajoute un ou plusieurs modules à la session active.

Applet [de commande obtenir-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cette applet de commande récupère des informations sur les modules qui ont été ou qui peuvent être importés dans la session active.

Applet [de commande Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cette applet de commande spécifie les membres du module (tels que les applets de commande, les fonctions, les variables et les alias) qui sont exportés à partir d’un fichier de module de script (. psm1) ou d’un module dynamique créé à l’aide de l’applet de commande `New-Module`.

Applet de commande [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cette applet de commande supprime les modules de la session active.

Applet de commande [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cette applet de commande vérifie qu’un manifeste de module décrit avec précision les composants d’un module en vérifiant que les fichiers répertoriés dans le fichier manifeste de module (. psd1) existent réellement dans les chemins d’accès spécifiés.

$PSScriptRoot cette variable contient le répertoire à partir duquel le module de script est en cours d’exécution. Il permet aux scripts d’utiliser le chemin d’accès du module pour accéder à d’autres ressources.

$env :P SModulePath cette variable d’environnement contient une liste des répertoires dans lesquels les modules Windows PowerShell sont stockés. Windows PowerShell utilise la valeur de cette variable lors de l’importation automatique de modules et de la mise à jour des rubriques d’aide pour les modules.

## <a name="see-also"></a>Voir aussi

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
