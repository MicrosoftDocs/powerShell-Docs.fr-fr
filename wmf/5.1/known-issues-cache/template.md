---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.topic: conceptual
title: exemple de modèle d’un problème ou limitation connu
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055545"
---
 >Remarque : fournir un titre descriptif proposé et une brève description

## <a name="example-erroneous-executionpolicy-errors"></a>Exemple : erreurs ExecutionPolicy erronées
Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.

### <a name="resolution"></a>Solution

Pour résoudre le problème, affectez la valeur **RemoteSigned** à **ExecutionPolicy** en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :

```powershell
Set-ExecutionPolicy RemoteSigned
```
