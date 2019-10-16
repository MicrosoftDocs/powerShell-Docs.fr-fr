---
title: Comment écrire un module binaire PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367118"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Guide pratique pour écrire un module binaire PowerShell

Un module binaire peut être n’importe quel assembly (. dll) qui contient des classes d’applet de commande. Par défaut, toutes les applets de commande de l’assembly sont importées lors de l’importation du module binaire. Toutefois, vous pouvez restreindre les applets de commande importées en créant un manifeste de module dont le module racine est l’assembly. (Par exemple, la clé CmdletsToExport du manifeste peut être utilisée pour exporter uniquement les applets de commande nécessaires.) En outre, un module binaire peut contenir des fichiers supplémentaires, une structure de répertoires et d’autres éléments d’informations de gestion utiles qu’une applet de commande unique ne peut pas.

La procédure suivante décrit comment créer et installer un module binaire PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Comment créer et installer un module binaire PowerShell

1. Créez une solution PowerShell binaire (telle qu’une applet de commande C#écrite dans), avec les fonctionnalités dont vous avez besoin et assurez-vous qu’elle s’exécute correctement.

   Du point de vue du code, le cœur d’un module binaire est simplement un assembly d’applet de commande. En fait, PowerShell traitera un assembly d’applet de commande unique comme un module, en termes de chargement et de déchargement, sans effort supplémentaire de la part du développeur. Pour plus d’informations sur l’écriture d’une applet de commande, consultez [écriture d’une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Si nécessaire, créez le reste de votre solution : (applets de commande supplémentaires, fichiers XML, etc.) et décrivez-les à l’aide d’un manifeste de module.

   En plus de décrire les assemblys d’applet de commande dans votre solution, un manifeste de module peut décrire comment vous souhaitez exporter et importer votre module, les applets de commande exposées et les fichiers supplémentaires qui seront insérés dans le module.
   Comme indiqué précédemment, PowerShell peut traiter une applet de commande binaire comme un module sans effort supplémentaire.
   Par conséquent, un manifeste de module est utile principalement pour la combinaison de plusieurs fichiers dans un package unique, ou pour le contrôle explicite de la publication pour un assembly donné.
   Pour plus d’informations, consultez [Comment écrire un manifeste de module PowerShell](how-to-write-a-powershell-module-manifest.md).

   Le code suivant est un bloc de C# code extrêmement simple qui contient trois applets de commande dans le même fichier qui peuvent être utilisées en tant que module.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Empaquetez votre solution et enregistrez le package dans un chemin d’accès au module PowerShell.

   La variable d’environnement global `PSModulePath` décrit les chemins d’accès par défaut que PowerShell utilisera pour localiser votre module. Par exemple, un chemin d’accès commun pour enregistrer un module sur un système serait `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Si vous n’utilisez pas les chemins d’accès par défaut, vous devrez indiquer explicitement l’emplacement de votre module lors de l’installation. Veillez à créer un dossier pour enregistrer votre module dans, car vous aurez peut-être besoin du dossier pour stocker plusieurs assemblys et fichiers pour votre solution.

   Notez que techniquement, vous n’avez pas besoin d’installer votre module n’importe où sur le `PSModulePath` : il s’agit simplement des emplacements par défaut que PowerShell recherchera pour votre module. Toutefois, il est recommandé de le faire, sauf si vous avez une bonne raison de stocker votre module ailleurs. Pour plus d’informations, consultez [installation d’un module PowerShell](./installing-a-powershell-module.md) et [modification du chemin d’installation du module PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importez votre module dans PowerShell avec un appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   L’appel à [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) chargera votre module dans la mémoire active. Si vous utilisez PowerShell 3,0 et versions ultérieures, il vous suffit d’appeler le nom de votre module dans le code pour l’importer également. Pour plus d’informations, consultez [importation d’un module PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importation d’assemblys de composant logiciel enfichable en tant que modules

Les applets de commande et les fournisseurs qui existent dans les assemblys de composant logiciel enfichable peuvent être chargés en tant que modules binaires. Lorsque les assemblys du composant logiciel enfichable sont chargés en tant que modules binaires, les applets de commande et les fournisseurs du composant logiciel enfichable sont disponibles pour l’utilisateur, mais la classe de composant logiciel enfichable de l’assembly est ignorée et le composant logiciel enfichable n’est pas inscrit. Par conséquent, les applets de commande du composant logiciel enfichable fournies par Windows PowerShell ne peuvent pas détecter le composant logiciel enfichable, même si les applets de commande et les fournisseurs sont disponibles pour la session.

En outre, les fichiers de mise en forme ou de types référencés par le composant logiciel enfichable ne peuvent pas être importés dans le cadre d’un module binaire.
Pour importer les fichiers de mise en forme et de types, vous devez créer un manifeste de module.
Consultez [Comment écrire un manifeste de module PowerShell](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Voir aussi

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
