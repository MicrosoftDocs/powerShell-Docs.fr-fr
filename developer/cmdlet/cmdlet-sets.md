---
title: Jeux de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcf0739e-920e-4dd8-afca-2c6d6927bc2a
caps.latest.revision: 10
ms.openlocfilehash: e9c59474b7e2bbc07166df8a8b4fa8099edd360f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859195"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="56829-102">Ensembles d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="56829-102">Cmdlet Sets</span></span>

<span data-ttu-id="56829-103">Lorsque vous concevez vos applets de commande, vous pouvez rencontrer des cas dans lequel vous avez besoin d’exécuter plusieurs actions sur les mêmes données.</span><span class="sxs-lookup"><span data-stu-id="56829-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="56829-104">Par exemple, vous devrez peut-être obtenir et définir les données ou démarrer et arrêter un processus.</span><span class="sxs-lookup"><span data-stu-id="56829-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="56829-105">Bien que vous devrez créer des applets de commande distincte pour effectuer chaque action, votre conception de l’applet de commande doit inclure une classe de base à partir de laquelle sont dérivées les classes pour les applets de commande individuels.</span><span class="sxs-lookup"><span data-stu-id="56829-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="56829-106">Gardez les points suivants à l’esprit lors de l’implémentation d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="56829-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="56829-107">Déclarer des paramètres communs utilisés par toutes les applets de commande dérivées dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="56829-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="56829-108">Ajouter des paramètres spécifiques à l’applet de commande à la classe d’applet de commande approprié.</span><span class="sxs-lookup"><span data-stu-id="56829-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="56829-109">Substituez la méthode dans la classe de base de traitement d’entrée appropriée.</span><span class="sxs-lookup"><span data-stu-id="56829-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="56829-110">Déclarez le [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut sur toutes les classes de l’applet de commande, mais ne la déclarez pas sur la classe de base.</span><span class="sxs-lookup"><span data-stu-id="56829-110">Declare the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="56829-111">Implémentez un [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) ou [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe dont le nom et description reflète l’ensemble des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="56829-111">Implement a [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="56829-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="56829-112">Example</span></span>

<span data-ttu-id="56829-113">L’exemple suivant montre l’implémentation d’une classe de base qui est utilisée par Get-Process et l’applet de commande Stop-Process qui dérivent de la même classe de base.</span><span class="sxs-lookup"><span data-stu-id="56829-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProccessCommands

  /// <summary>
  /// This class implements a Stop-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>
  [Cmdlet(VerbsLifecycle.Stop, "Proc", SupportsShouldProcess = true)]
  public class StopProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      if (ShouldProcess(process.ProcessName, "Stop-Proc"))
      {
        process.Kill();
      }
    }
  }

  /// <summary>
  /// This class implements a Get-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>

  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      WriteObject(process);
    }
  }

  /// <summary>
  /// This class is the base class that defines the common
  /// functionality used by the Get-Proc and Stop-Proc
  /// cmdlets.
  /// </summary>
  public class BaseProcCommand : Cmdlet
  {
    #region Parameters

    // Defines the Name parameter that is used to
    // specify a process by its name.
    [Parameter(
               Position = 0,
               Mandatory = true,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true
    )]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    // Defines the Exclude parameter that is used to
    // specify which processes should be excluded when
    // the cmdlet performs its action.
    [Parameter()]
    public string[] Exclude
    {
      get { return excludeNames; }
      set { excludeNames = value; }
    }
    private string[] excludeNames = new string[0];
    #endregion Parameters

    public virtual void ProcessObject(Process process)
    {
      throw new NotImplementedException("This method should be overridden.");
    }

    #region Cmdlet Overrides
    // <summary>
    // For each of the requested process names, retrieve and write
    // the associated processes.
    // </summary>
    protected override void ProcessRecord()
    {
      // Set up the wildcard chracters used in resolving
      // the process names.
      WildcardOptions options = WildcardOptions.IgnoreCase |
                                WildcardOptions.Compiled;

      WildcardPattern[] include = new WildcardPattern[Name.Length];
      for (int i = 0; i < Name.Length; i++)
      {
        include[i] = new WildcardPattern(Name[i], options);
      }

      WildcardPattern[] exclude = new WildcardPattern[Exclude.Length];
      for (int i = 0; i < Exclude.Length; i++)
      {
        exclude[i] = new WildcardPattern(Exclude[i], options);
      }

      foreach (Process p in Process.GetProcesses())
      {
        foreach (WildcardPattern wIn in include)
        {
          if (wIn.IsMatch(p.ProcessName))
          {
            bool processThisOne = true;
            foreach (WildcardPattern wOut in exclude)
            {
              if (wOut.IsMatch(p.ProcessName))
              {
                processThisOne = false;
                break;
              }
            }
            if (processThisOne)
            {
              ProcessObject(p);
            }
            break;
          }
        }
      }
    }
    #endregion Cmdlet Overrides
  }
    #endregion ProcessCommands
}
```

## <a name="see-also"></a><span data-ttu-id="56829-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56829-114">See Also</span></span>

[<span data-ttu-id="56829-115">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="56829-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
