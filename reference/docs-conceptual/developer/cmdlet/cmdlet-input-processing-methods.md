---
ms.date: 09/13/2016
ms.topic: reference
title: Méthodes de traitement des entrées des applets de commande
description: Méthodes de traitement des entrées des applets de commande
ms.openlocfilehash: e1a7b58517d6285250edbf16d14810388c242218
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653391"
---
# <a name="cmdlet-input-processing-methods"></a>Méthodes de traitement des entrées des applets de commande

Les applets de commande doivent remplacer une ou plusieurs des méthodes de traitement d’entrée décrites dans cette rubrique pour effectuer leur travail.
Ces méthodes permettent à l’applet de commande d’effectuer des opérations de pré-traitement, de traitement d’entrée et de traitement.
Ces méthodes vous permettent également d’arrêter le traitement des applets de commande.
Pour obtenir un exemple plus détaillé de l’utilisation de ces méthodes, consultez le [didacticiel SelectStr](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Opérations de prétraitement

Les applets de commande doivent remplacer la méthode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) pour ajouter des opérations de prétraitement valides pour tous les enregistrements qui seront traités ultérieurement par l’applet de commande.
Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.
Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement des applets](/previous-versions/ms714429(v=vs.85))de commande.

Le code suivant illustre une implémentation de la méthode BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Opérations de traitement d’entrée

Les applets de commande peuvent remplacer la méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) pour traiter l’entrée envoyée à l’applet de commande.
Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode pour chaque enregistrement d’entrée traité par l’applet de commande.
Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement des applets](/previous-versions/ms714429(v=vs.85))de commande.

Le code suivant illustre une implémentation de la méthode ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Opérations de postérieure au traitement

Les applets de commande doivent remplacer la méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) pour ajouter toutes les opérations de publication qui sont valides pour tous les enregistrements traités par l’applet de commande.
Par exemple, votre applet de commande peut être obligée de nettoyer les variables d’objet une fois le traitement terminé.

Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.
Toutefois, il est important de se souvenir que le runtime PowerShell n’appellera pas la méthode EndProcessing si l’applet de commande est annulée à mi-chemin dans son traitement d’entrée ou si une erreur d’arrêt se produit dans n’importe quelle partie de l’applet de commande.
Pour cette raison, une applet de commande qui requiert le nettoyage d’objets doit implémenter le modèle [System. IDisposable](/dotnet/api/System.IDisposable) complet, y compris un finaliseur, afin que le runtime puisse appeler à la fois les méthodes EndProcessing et [System. IDisposable. dispose](/dotnet/api/System.IDisposable.Dispose) à la fin du traitement.
Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement des applets](/previous-versions/ms714429(v=vs.85))de commande.

Le code suivant illustre une implémentation de la méthode EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Tutoriel SelectStr](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Kit SDK Windows PowerShell](../windows-powershell-reference.md)
