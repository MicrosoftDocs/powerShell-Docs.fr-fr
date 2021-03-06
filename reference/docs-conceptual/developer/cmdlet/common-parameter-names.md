---
ms.date: 09/13/2016
ms.topic: reference
title: Noms de paramètres courants
description: Noms de paramètres courants
ms.openlocfilehash: 506aab290abdb97a6e26c340ac4bd0051244f54b
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860877"
---
# <a name="common-parameter-names"></a>Noms de paramètres courants

Les paramètres décrits dans cette rubrique sont appelés **paramètres communs**. Ils sont ajoutés aux applets de commande par le runtime Windows PowerShell et ne peuvent pas être déclarés par l’applet de commande.

> [!NOTE]
> Ces paramètres sont également ajoutés aux applets de commande du fournisseur et aux fonctions qui sont décorées avec l' `CmdletBinding` attribut.

## <a name="general-common-parameters"></a>Paramètres communs généraux

Les paramètres suivants sont ajoutés à toutes les applets de commande et sont accessibles chaque fois que l’applet de commande est exécutée.
Ces paramètres sont définis par la classe [System. Management. Automation. Internal. paramètres_courants](/dotnet/api/System.Management.Automation.Internal.CommonParameters) .

### <a name="confirm-alias-cf"></a>Confirmer (alias : CF)

Type de données : Paramètre_booléen

Ce paramètre spécifie si l’applet de commande affiche une invite demandant si l’utilisateur est sûr qu’il souhaite continuer.

### <a name="debug-alias-db"></a>Débogage (alias : DB)

Type de données : Paramètre_booléen

Ce paramètre spécifie si les messages de débogage au niveau du programmeur peuvent être affichés sur la ligne de commande. Ces messages sont destinés à résoudre les problèmes liés au fonctionnement de l’applet de commande et sont générés par les appels à la méthode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . Il n’est pas nécessaire de localiser les messages de débogage.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias : EA)

Type de données : énumération

Ce paramètre spécifie l’action qui doit être exécutée lorsqu’une erreur se produit. Les valeurs possibles pour ce paramètre sont définies par l’énumération [System. Management. Automation. PréférenceAction](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias : ev)

Type de données : Chaîne

Ce paramètre spécifie la variable dans laquelle placer les objets lorsqu’une erreur se produit. Pour ajouter à cette variable, utilisez +_varname_ plutôt que d’effacer et de définir la variable.

### <a name="outbuffer-alias-ob"></a>Buffer (alias : OB)

Type de données : Int32

Ce paramètre définit le nombre d’objets à stocker dans la mémoire tampon de sortie avant que tous les objets ne soient passés dans le pipeline. Par défaut, les objets sont passés immédiatement en dessous du pipeline.

### <a name="outvariable-alias-ov"></a>Dévariable (alias : OV)

Type de données : Chaîne

Ce paramètre spécifie la variable dans laquelle placer tous les objets de sortie générés par l’applet de commande.
Pour ajouter à cette variable, utilisez +_varname_ plutôt que d’effacer et de définir la variable.

### <a name="pipelinevariable-alias-pv"></a>PipelineVariable (alias : PV)

Type de données : Chaîne

Ce paramètre stocke la valeur de l’élément de pipeline actuel en tant que variable pour toute commande nommée à mesure qu’il traverse le pipeline.

## <a name="verbose-alias-vb"></a>Verbose (alias : VB)

Type de données : Paramètre_booléen

Ce paramètre spécifie si l’applet de commande écrit des messages explicatifs qui peuvent être affichés sur la ligne de commande. Ces messages sont destinés à fournir de l’aide supplémentaire à l’utilisateur et sont générés par les appels à la méthode [System. Management. Automation. applet de commande. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

### <a name="warningaction-alias-wa"></a>WarningAction (alias : WA)

Type de données : énumération

Ce paramètre spécifie l’action qui doit être effectuée lorsque l’applet de commande écrit un message d’avertissement. Les valeurs possibles pour ce paramètre sont définies par l’énumération [System. Management. Automation. PréférenceAction](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias : WV)

Type de données : Chaîne

Ce paramètre spécifie la variable dans laquelle les messages d’avertissement peuvent être enregistrés. Pour ajouter à cette variable, utilisez +_varname_ plutôt que d’effacer et de définir la variable.

## <a name="risk-mitigation-parameters"></a>Paramètres Risk-Mitigation

Les paramètres suivants sont ajoutés aux applets de commande qui demandent une confirmation avant d’exécuter leur action. Pour plus d’informations sur les demandes de confirmation, consultez [demande de confirmation](./requesting-confirmation-from-cmdlets.md).
Ces paramètres sont définis par la classe [System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) .

### <a name="whatif-alias-wi"></a>WhatIf (alias : Wi)

Type de données : Paramètre_booléen

Ce paramètre spécifie si l’applet de commande écrit un message qui décrit les effets de l’exécution de l’applet de commande sans effectuer d’action.

## <a name="transaction-parameters"></a>Paramètres de transaction

Le paramètre suivant est ajouté aux applets de commande qui prennent en charge les transactions. Ces paramètres sont définis par la classe [System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) . La prise en charge des transactions a été introduite dans PowerShell 3,0 et supprimée dans PowerShell 6,0.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias : UseTX)

Type de données : Paramètre_booléen

Ce paramètre spécifie si l’applet de commande utilise la transaction actuelle pour effectuer son action.

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. Internal. Paramètres_courants](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
