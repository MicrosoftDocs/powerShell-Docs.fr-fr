---
title: Concepts du rapport d’erreurs | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.openlocfilehash: ff010bbe1a87daa351ec13ed249ffc899781a8c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774505"
---
# <a name="error-reporting-concepts"></a>Concepts des rapports d’erreurs

Windows PowerShell fournit deux mécanismes pour signaler les erreurs : un mécanisme pour mettre *fin aux erreurs* et un autre mécanisme pour les *Erreurs sans fin d’achèvement*. Il est important que votre applet de commande signale les erreurs correctement pour que l’application hôte qui exécute vos applets de commande puisse réagir de manière appropriée.

Votre applet de commande doit appeler la méthode [System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) lorsqu’une erreur qui n’est pas ou ne doit pas permettre à l’applet de commande de continuer à traiter ses objets d’entrée. Votre applet de commande doit appeler la méthode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) pour signaler les erreurs sans fin d’exécution lorsque l’applet de commande peut poursuivre le traitement des objets d’entrée. Les deux méthodes fournissent un enregistrement d’erreur que l’application hôte peut utiliser pour rechercher la cause de l’erreur.

Utilisez les instructions suivantes pour déterminer si une erreur est une erreur de fin ou sans fin d’achèvement.

- Une erreur est une erreur de fin si elle empêche votre applet de commande de continuer à traiter l’objet actuel ou de traiter correctement les autres objets d’entrée, quel que soit leur contenu.

- Une erreur est une erreur de fin si vous ne souhaitez pas que votre applet de commande continue à traiter l’objet en cours ou tout autre objet d’entrée, quel que soit son contenu.

- Une erreur se termine par une erreur si elle se produit dans une applet de commande qui n’accepte pas ou ne retourne pas d’objet ou si elle se produit dans une applet de commande qui accepte ou retourne un seul objet.

- Une erreur est une erreur sans fin d’exécution si vous souhaitez que votre applet de commande continue à traiter l’objet actuel et tous les autres objets d’entrée.

- Une erreur est une erreur sans fin d’opération si elle est liée à un objet d’entrée spécifique ou à un sous-ensemble d’objets d’entrée.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. applet de commande. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Enregistrements d’erreurs Windows PowerShell](./windows-powershell-error-records.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
