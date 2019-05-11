---
title: Comment écrire un Module PowerShell binaire | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229332"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Guide pratique pour écrire un module binaire PowerShell

Un module binaire peut être n’importe quel assembly (.dll) qui contient des classes de l’applet de commande. Par défaut, toutes les applets de commande dans l’assembly sont importées lorsque le module binaire est importé. Toutefois, vous pouvez limiter les applets de commande sont importées en créant un manifeste de module dont le module racine est l’assembly. (Par exemple, la clé de CmdletsToExport du manifeste peut servir à exporter uniquement les applets de commande qui sont nécessaires.) En outre, un module binaire peut contenir des fichiers supplémentaires, une structure de répertoires et autres éléments d’information de gestion utiles qu’une seule applet de commande ne peut pas.

La procédure suivante décrit comment créer et installer un module binaire de PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Comment créer et installer un module binaire de PowerShell

1. Créer une solution PowerShell binaire (comme une applet de commande écrite C#), avec les capacités de votre choix et vous assurer qu’elle s’exécute correctement.

   À partir du point de vue du code, le cœur d’un module binaire est simplement un assembly de l’applet de commande. En fait, PowerShell traitent un assembly de l’applet de commande unique en tant que module, en termes de chargement et déchargement, sans aucun effort supplémentaire part du développeur. Pour plus d’informations sur l’écriture d’une applet de commande, consultez [écrire une applet de commande Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Si nécessaire, créez le reste de votre solution : (applets de commande supplémentaires, des fichiers XML et ainsi de suite) et les décrire avec un manifeste de module.

   En plus de décrire les assemblys de l’applet de commande dans votre solution, un manifeste de module peut décrire comment vous souhaitez que votre module exportées et importées, quelles applets de commande sera exposée, et ce qui passe des fichiers supplémentaires dans le module.
   Comme indiqué précédemment Toutefois, PowerShell peut traiter une applet de commande binaire comme un module sans aucun effort supplémentaire.
   Par conséquent, un manifeste de module est utile principalement pour la combinaison de plusieurs fichiers dans un package unique, ou pour contrôler explicitement la publication pour un assembly donné.
   Pour plus d’informations, consultez [comment écrire un manifeste de Module PowerShell](how-to-write-a-powershell-module-manifest.md).

   Le code suivant est extrêmement simple C# bloc de code qui contient les trois applets de commande dans le même fichier peut être utilisé en tant que module.

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

3. Empaqueter votre solution et enregistrer le package vers un endroit quelconque dans le chemin d’accès du module PowerShell.

   Le `PSModulePath` variable d’environnement globale décrit les chemins d’accès par défaut que PowerShell utilisera pour localiser votre module. Par exemple, un chemin d’accès commun pour enregistrer un module sur un système serait `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Si vous n’utilisez pas les chemins d’accès par défaut, vous devez déclarer explicitement l’emplacement de votre module pendant l’installation. Veillez à créer un dossier pour enregistrer votre module, vous pouvez avoir besoin du dossier pour stocker plusieurs assemblys et les fichiers de votre solution.

   Notez que techniquement il est inutile d’installer votre module de n’importe où sur le `PSModulePath` -ce sont simplement les emplacements par défaut qui recherche pour votre module PowerShell. Toutefois, il est considéré comme bonne pratique consiste à le faire, sauf si vous avez une bonne raison pour le stockage de votre module vers un autre emplacement. Pour plus d’informations, consultez [installation d’un PowerShell Module](./installing-a-powershell-module.md) et [modifier le chemin d’Installation du Module PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importer le module PowerShell avec un appel à [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   L’appel à [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) chargera votre module dans la mémoire active. Si vous utilisez PowerShell 3.0 ou version ultérieure, appelant simplement le nom de votre module de code est également importer Pour plus d’informations, consultez [importation d’un PowerShell Module](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importation des assemblys Snap-in en tant que Modules

Applets de commande et les fournisseurs qui existent dans le composant logiciel enfichable dans les assemblys peuvent être chargés en tant que modules binaires. Lorsque les assemblys sont chargés en tant que modules binaires, les applets de commande et les fournisseurs dans le composant logiciel enfichable sont disponibles à l’utilisateur, mais la classe snap-in dans l’assembly est ignorée, et le composant logiciel enfichable n’est pas inscrit. Par conséquent, les applets de commande enfichable fourni par Windows PowerShell ne peut pas détecter le composant logiciel enfichable même si les fournisseurs et applets de commande sont disponibles à la session.

En outre, les fichiers de mise en forme ou de types qui sont référencés par le composant logiciel enfichable ne peut pas être importés dans le cadre d’un module binaire.
Pour importer les fichiers de mise en forme et de types, vous devez créer un manifeste de module.
Consultez, [comment écrire un manifeste de Module PowerShell](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Voir aussi

[Écrire un Module PowerShell de Windows](./writing-a-windows-powershell-module.md)
