---
ms.date: 07/08/2020
keywords: dsc,powershell,configuration,installation
title: Création d’une ressource DSC en C#
description: Cet article explique comment créer une ressource DSC en tant qu’applet de commande écrite en C# .
ms.openlocfilehash: 61c4d1e332a22f97a89cd740e03235ddfdcfabd2
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667162"
---
# <a name="authoring-a-dsc-resource-in-c"></a>Création d’une ressource DSC en C\#

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

En règle générale, une ressource DSC Windows PowerShell personnalisée est implémentée dans un script PowerShell. Toutefois, vous pouvez également implémenter la fonctionnalité d’une ressource DSC personnalisée en écrivant des applets de commande en C#. Pour une introduction à l’écriture des applets de commande en C#, consultez [Écriture d’une applet de commande Windows PowerShell](/powershell/scripting/developer/windows-powershell).

À part l’implémentation de la ressource en tant qu’applets de commande en langage C#, les processus de création du schéma MOF, de création de la structure de dossiers, et de l’importation et de l’utilisation de votre ressource DSC personnalisée, sont les mêmes que ceux décrits dans [Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md).

## <a name="writing-a-cmdlet-based-resource"></a>Écriture d’une ressource basée sur une applet de commande

Pour cet exemple, nous implémenterons une ressource simple qui gère un fichier texte et son contenu.

### <a name="writing-the-mof-schema"></a>Écriture du schéma MOF

Voici la définition de la ressource MOF.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
     [Key, Description("path")] String Path;
     [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
     [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a>Configuration du projet Visual Studio

#### <a name="setting-up-a-cmdlet-project"></a>Configuration d’un projet d’applet de commande

1. Ouvrez Visual Studio.
1. Créez un projet C# et donnez-lui un nom.
1. Sélectionnez **Bibliothèque de classes** dans les modèles de projet disponibles.
1. Cliquez sur **OK**.
1. Ajoutez une référence d’assembly à System.Automation.Management.dll dans votre projet.
1. Modifiez le nom d’assembly pour qu’il corresponde au nom de la ressource. Dans ce cas, l’assembly doit se nommer **MSFT_XDemoFile**.

### <a name="writing-the-cmdlet-code"></a>Écriture du code de l’applet de commande

Le code C# suivant implémente les applets de commande `Get-TargetResource`, `Set-TargetResource` et `Test-TargetResource`.

```C#
namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with
        /// keys being the resource properties and the values are the corresponding current
        /// value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a>Déploiement de la ressource

Le fichier .dll compilé doit être enregistré dans une structure de fichiers similaire à une ressource de script. Voici la structure de dossiers de cette ressource.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a>Voir aussi

#### <a name="concepts"></a>Concepts

[Écriture d’une ressource DSC personnalisée avec MOF](authoringResourceMOF.md)

#### <a name="other-resources"></a>Autres ressources

[Écriture d’une applet de commande Windows PowerShell](/powershell/scripting/developer/windows-powershell)
