---
title: Comment substituer les méthodes de traitement d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067941"
---
# <a name="how-to-override-input-processing-methods"></a>Guide pratique pour remplacer des méthodes de traitement des entrées

Ces exemples montrent comment remplacer les méthodes au sein d’une applet de commande de traitement d’entrée. Ces méthodes sont utilisées pour effectuer les opérations suivantes :

- Le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) méthode est utilisée pour effectuer des opérations de démarrage à usage unique qui sont valides pour tous les objets traités par l’applet de commande. Le runtime Windows PowerShell appelle cette méthode une seule fois.

- Le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode est utilisée pour traiter les objets passés à l’applet de commande. Le runtime Windows PowerShell appelle cette méthode pour chaque objet passé à l’applet de commande.

- Le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode est utilisée pour effectuer des opérations de traitement de billet à usage unique. Le runtime Windows PowerShell appelle cette méthode une seule fois.

## <a name="to-override-the-beginprocessing-method"></a>Pour substituer la méthode BeginProcessing

- Déclarez une substitution protégée de la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode).

La classe suivante imprime un exemple de message. Pour utiliser cette classe, modifiez le verbe et un nom dans l’attribut de l’applet de commande, modifier le nom de la classe afin de refléter le nouveau verbe et substantif, puis ajouter les fonctionnalités requises pour la substitution de la [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (méthode).

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>Pour substituer la méthode ProcessRecord

- Déclarez une substitution protégée de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).

La classe suivante imprime un exemple de message. Pour utiliser cette classe, modifiez le verbe et un nom dans l’attribut de l’applet de commande, modifier le nom de la classe afin de refléter le nouveau verbe et substantif, puis ajouter les fonctionnalités requises pour la substitution de la [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (méthode).

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>Pour substituer la méthode EndProcessing

- Déclarez une substitution protégée de la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode).

La classe suivante imprime un exemple. Pour utiliser cette classe, modifiez le verbe et un nom dans l’attribut de l’applet de commande, modifier le nom de la classe afin de refléter le nouveau verbe et substantif, puis ajouter les fonctionnalités requises pour la substitution de la [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (méthode).

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
