---
title: Concepts de signalement d’erreurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068179"
---
# <a name="error-reporting-concepts"></a>Concepts des rapports d’erreurs

Windows PowerShell fournit deux mécanismes pour signaler les erreurs : un mécanisme pour *arrêt erreurs* et un autre mécanisme pour *erreurs sans fin d’exécution*. Il est important pour votre applet de commande pour signaler des erreurs correctement afin que l’application hôte qui exécute vos applets de commande peut réagir de manière appropriée.

Votre applet de commande doit appeler le [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) méthode lorsqu’une erreur produit qui n’est pas ou ne doit pas autoriser l’applet de commande continuer à traiter ses objets d’entrée. Votre applet de commande doit appeler le [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode pour signaler les erreurs sans fin d’exécution lors de l’applet de commande peut continuer à traiter les objets d’entrée. Les deux méthodes fournissent un enregistrement d’erreur que l’application hôte peut utiliser pour rechercher la cause de l’erreur.

Utilisez les instructions suivantes pour déterminer si une erreur est une fin ou une erreur sans fin d’exécution.

- Une erreur est une erreur avec fin si elle empêche votre applet de commande de continuer à traiter l’objet en cours ou de traiter correctement les objets davantage d’entrée, quel que soit leur contenu.

- Une erreur est une erreur avec fin d’exécution si vous ne souhaitez pas votre applet de commande continuer le traitement de l’objet actuel ou tous les objets davantage d’entrée, quel que soit leur contenu.

- Une erreur est une erreur avec fin s’il se produit dans une applet de commande qui ne pas accepter ou retourner un objet ou si elle se produit dans une applet de commande qui accepte ou retourne qu’un seul objet.

- Une erreur est une erreur sans fin d’exécution si vous souhaitez que votre applet de commande pour continuer le traitement de l’objet actuel et tous les objets davantage d’entrée.

- Une erreur est une erreur sans fin d’exécution si elle est liée à un objet d’entrée spécifique ou un sous-ensemble d’objets d’entrée.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell erreur enregistrements](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
