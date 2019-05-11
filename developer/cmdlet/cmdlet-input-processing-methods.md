---
title: Méthodes de traitement des entrées d’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670307"
---
# <a name="cmdlet-input-processing-methods"></a>Méthodes de traitement des entrées des applets de commande

Applets de commande doit remplacer une ou plusieurs des méthodes décrites dans cette rubrique pour effectuer leur travail de traitement d’entrée.
Ces méthodes permettent de l’applet de commande effectuer des opérations de prétraitement, traitement d’entrée et de post-traitement.
Ces méthodes vous permettent également d’arrêter le traitement de l’applet de commande.
Pour obtenir un exemple plus détaillé de l’utilisation de ces méthodes, consultez [SelectStr didacticiel](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Opérations de prétraitement

Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) méthode pour ajouter des opérations de prétraitement sont valides pour tous les enregistrements qui seront traités ultérieurement par l’applet de commande.
Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.
Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](/previous-versions/ms714429(v=vs.85)).

Le code suivant illustre une implémentation de la méthode BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Traitement des opérations d’entrée

Applets de commande peut remplacer le [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) méthode pour traiter l’entrée qui est envoyée à l’applet de commande.
Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode pour chaque enregistrement d’entrée qui est traité par l’applet de commande.
Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](/previous-versions/ms714429(v=vs.85)).

Le code suivant illustre une implémentation de la méthode ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Opérations post-traitement

Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) méthode pour ajouter toutes les opérations post-traitement qui sont valides pour tous les enregistrements qui ont été traités par l’applet de commande.
Par exemple, votre applet de commande peut avoir nettoyer les variables d’objet après la fin de l’installation de traitement.

Lorsque PowerShell traite un pipeline de commande, PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline.
Toutefois, il est important de se rappeler que le runtime PowerShell n’appelle pas la méthode EndProcessing si l’applet de commande est annulée à mi-chemin via son traitement d’entrée ou si une erreur avec fin d’exécution se produit dans n’importe quelle partie de l’applet de commande.
Pour cette raison, une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.IDisposable](/dotnet/api/System.IDisposable) modèle, y compris un finaliseur, afin que le runtime peut appeler à la fois le EndProcessing et [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) méthodes à la fin du traitement.
Pour plus d’informations sur la façon dont PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](/previous-versions/ms714429(v=vs.85)).

Le code suivant illustre une implémentation de la méthode EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Didacticiel de SelectStr](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
