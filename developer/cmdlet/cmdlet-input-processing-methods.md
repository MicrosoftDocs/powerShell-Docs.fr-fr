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
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059369"
---
# <a name="cmdlet-input-processing-methods"></a>Méthodes de traitement des entrées des applets de commande

Applets de commande doit remplacer une ou plusieurs des méthodes décrites dans cette rubrique pour effectuer leur travail de traitement d’entrée. Ces méthodes permettent de l’applet de commande effectuer le prétraitement opérations d’entrée opérations et le traitement après les opérations de traitement. Ces méthodes vous permettent également d’arrêter le traitement de l’applet de commande.

## <a name="pre-processing-tasks"></a>Tâches de prétraitement

Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) méthode pour ajouter des opérations de prétraitement sont valides pour tous les enregistrements qui seront traités ultérieurement par l’applet de commande. Lorsque Windows PowerShell traite un pipeline de commande, Windows PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline. Pour plus d’informations sur la façon dont Windows PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Le code suivant illustre une implémentation de la [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) (méthode).

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Pour obtenir un exemple plus détaillé de l’utilisation de la [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) (méthode), consultez [SelectStr didacticiel](./selectstr-tutorial.md). Dans ce didacticiel, le **sélectionnez-Str** applet de commande utilise le [System.Management.Automation.Cmdlet.Beginprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) méthode permettant de générer l’expression régulière qui est utilisée pour rechercher les enregistrements de traitement d’entrée.

## <a name="input-processing-tasks"></a>Tâches de traitement d’entrée

Applets de commande peut remplacer le [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) méthode pour traiter l’entrée qui est envoyée à l’applet de commande. Lorsque Windows PowerShell traite un pipeline de commande, Windows PowerShell appelle cette méthode pour chaque enregistrement d’entrée qui est traité par l’applet de commande. Pour plus d’informations sur la façon dont Windows PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Le code suivant illustre une implémentation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode).

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Pour obtenir un exemple plus détaillé de l’utilisation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode), consultez [SelectStr didacticiel](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Tâches de post-traitement

Applets de commande doit remplacer le [System.Management.Automation.Cmdlet.Endprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) méthode pour ajouter toutes les opérations post-traitement qui sont valides pour tous les enregistrements qui ont été traités par l’applet de commande. Par exemple, votre applet de commande peut avoir nettoyer les variables d’objet après la fin de l’installation de traitement.

Lorsque Windows PowerShell traite un pipeline de commande, Windows PowerShell appelle cette méthode une fois pour chaque instance de l’applet de commande dans le pipeline. Toutefois, il est important de se rappeler que le runtime Windows PowerShell n’appelle pas le [System.Management.Automation.Cmdlet.Endprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) méthode si l’applet de commande est annulée à mi-chemin via son traitement d’entrée ou si un arrêt de l’erreur se produit dans n’importe quelle partie de l’applet de commande. Pour cette raison, une applet de commande qui requiert un nettoyage de l’objet doit implémenter l’ensemble [System.IDisposable](/dotnet/api/System.IDisposable) modèle, y compris un finaliseur, afin que le runtime peut appeler à la fois le [ System.Management.Automation.Cmdlet.Endprocessing%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) et [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) méthodes à la fin du traitement. Pour plus d’informations sur la façon dont Windows PowerShell appelle le pipeline de commande, consultez [cycle de vie du traitement d’applet de commande](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Le code suivant illustre une implémentation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode).

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Pour obtenir un exemple plus détaillé de l’utilisation de la [System.Management.Automation.Cmdlet.Processrecord%2A ? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (méthode), consultez [SelectStr didacticiel](./selectstr-tutorial.md).

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Interpréteur de commandes Windows PowerShell SDK](../windows-powershell-reference.md)
