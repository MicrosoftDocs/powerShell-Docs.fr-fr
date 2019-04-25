---
title: Les noms de paramètres courants | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068420"
---
# <a name="common-parameter-names"></a>Noms de paramètres courants

Les paramètres décrits dans cette rubrique sont appelés *paramètres communs*. Ils sont ajoutés aux applets de commande par le runtime de Windows PowerShell et ne peut pas être déclarés par l’applet de commande.

> [!NOTE]
> Ces paramètres sont également ajoutés aux applets de commande fournisseur et aux fonctions qui sont décorées avec le `CmdletBinding` attribut.

## <a name="general-common-parameters"></a>Paramètres courants de générale

Les paramètres suivants sont ajoutés à toutes les applets de commande et est accessible à chaque exécution de l’applet de commande. Ces paramètres sont définis par le [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) classe.

### <a name="debug-alias-db"></a>Déboguer (alias : db)

Type de données : SwitchParameter

Ce paramètre spécifie si le débogage au niveau du programmeur messages qui peuvent être affichés à la ligne de commande. Ces messages sont destinés à la résolution des problèmes de l’opération de l’applet de commande et sont générés par les appels à la [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) (méthode). Les messages de débogage est inutile à localiser.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias : ea)

Type de données : Énumération

Ce paramètre spécifie l’action qui doit avoir lieu lorsqu’une erreur se produit. Les valeurs possibles pour ce paramètre sont définis par le [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) énumération.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias : ev)

Type de données : String

Ce paramètre spécifie la variable dans laquelle placer les objets lorsqu’une erreur se produit. Pour ajouter à cette variable, utilisez +*varname* plutôt que la suppression et la définition de la variable.

### <a name="outvariable-alias-ov"></a>OutVariable (alias : ov)

Type de données : String

Ce paramètre spécifie la variable dans laquelle placer tous les objets générés par l’applet de commande de sortie. Pour ajouter à cette variable, utilisez +*varname* plutôt que la suppression et la définition de la variable.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias : ob)

Type de données : Int32

Ce paramètre définit le nombre d’objets à stocker dans la mémoire tampon de sortie avant tous les objets sont passés dans le pipeline. Par défaut, les objets sont transmis immédiatement dans le pipeline.

### <a name="verbose-alias-vb"></a>Verbose (alias : vb)

Type de données : SwitchParameter

Ce paramètre spécifie si l’applet de commande écrit les messages d’explicatifs qui peuvent être affichés à la ligne de commande. Ces messages sont conçues pour fournir une aide supplémentaire à l’utilisateur et sont générés par les appels à la [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (méthode).

### <a name="warningaction-alias-wa"></a>WarningAction (alias : wa)

Type de données : Énumération

Ce paramètre spécifie l’action qui doit avoir lieu lors de l’applet de commande écrit un message d’avertissement. Les valeurs possibles pour ce paramètre sont définis par le [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) énumération.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias : wv)

Type de données : String

Ce paramètre spécifie la variable dans laquelle les messages d’avertissement peuvent être enregistrées. Pour ajouter à cette variable, utilisez +*varname* plutôt que la suppression et la définition de la variable.

## <a name="risk-mitigation-parameters"></a>Paramètres d’atténuation des risques

Les paramètres suivants sont ajoutés aux applets de commande qui demande confirmation avant d’exécuter leur action. Pour plus d’informations sur les demandes de confirmation, consultez [demande une Confirmation](./requesting-confirmation-from-cmdlets.md). Ces paramètres sont définis par le [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) classe.

### <a name="confirm-alias-cf"></a>Confirmer (alias : cf)

Type de données : SwitchParameter

Ce paramètre spécifie si l’applet de commande affiche une invite vous demandant si l’utilisateur est sûr qu’ils souhaitent continuer.

### <a name="whatif-alias-wi"></a>WhatIf (alias : wi)

Type de données : SwitchParameter

Ce paramètre spécifie si l’applet de commande écrit un message qui décrit les effets de l’exécution de l’applet de commande sans effectuer aucune action.

## <a name="transaction-parameters"></a>Paramètres de transaction

Le paramètre suivant est ajouté aux applets de commande qui prennent en charge des transactions. Ces paramètres sont définis par le [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) classe.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias : usetx)

Type de données : SwitchParameter

Ce paramètre spécifie si l’applet de commande utilisera la transaction en cours pour exécuter son action.

## <a name="see-also"></a>Voir aussi

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
