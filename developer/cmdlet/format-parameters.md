---
title: Mettre en forme paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068111"
---
# <a name="format-parameters"></a><span data-ttu-id="dce65-102">Paramètres de format</span><span class="sxs-lookup"><span data-stu-id="dce65-102">Format Parameters</span></span>

<span data-ttu-id="dce65-103">Le tableau suivant répertorie les noms recommandés et les fonctionnalités pour les paramètres qui sont utilisées pour mettre en forme ou pour générer des données.</span><span class="sxs-lookup"><span data-stu-id="dce65-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="dce65-104">Paramètre</span><span class="sxs-lookup"><span data-stu-id="dce65-104">Parameter</span></span>|<span data-ttu-id="dce65-105">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="dce65-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="dce65-106">**en tant que**</span><span class="sxs-lookup"><span data-stu-id="dce65-106">**As**</span></span><br><span data-ttu-id="dce65-107">Type de données : Mot clé</span><span class="sxs-lookup"><span data-stu-id="dce65-107">Data type: Keyword</span></span>|<span data-ttu-id="dce65-108">Implémentez ce paramètre pour spécifier le format de sortie d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="dce65-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="dce65-109">Par exemple, les valeurs possibles peut être texte ou un Script.</span><span class="sxs-lookup"><span data-stu-id="dce65-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="dce65-110">**fichier binaire**</span><span class="sxs-lookup"><span data-stu-id="dce65-110">**Binary**</span></span><br><span data-ttu-id="dce65-111">Type de données : SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dce65-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="dce65-112">Implémentez ce paramètre pour indiquer que l’applet de commande gère les valeurs binaires.</span><span class="sxs-lookup"><span data-stu-id="dce65-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="dce65-113">**Encodage**</span><span class="sxs-lookup"><span data-stu-id="dce65-113">**Encoding**</span></span><br><span data-ttu-id="dce65-114">Type de données : Mot clé</span><span class="sxs-lookup"><span data-stu-id="dce65-114">Data type: Keyword</span></span>|<span data-ttu-id="dce65-115">Implémentez ce paramètre pour spécifier le type de codage pris en charge.</span><span class="sxs-lookup"><span data-stu-id="dce65-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="dce65-116">Par exemple, les valeurs possibles peut être ASCII, UTF-8, Unicode, UTF7, BigEndianUnicode, octets et chaîne.</span><span class="sxs-lookup"><span data-stu-id="dce65-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="dce65-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="dce65-117">**NewLine**</span></span><br><span data-ttu-id="dce65-118">Type de données : SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dce65-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="dce65-119">Implémentez ce paramètre afin que les caractères de saut de ligne sont pris en charge lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="dce65-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="dce65-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="dce65-120">**ShortName**</span></span><br><span data-ttu-id="dce65-121">Type de données : SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dce65-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="dce65-122">Implémentez ce paramètre afin que les noms courts sont pris en charge lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="dce65-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="dce65-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="dce65-123">**Width**</span></span><br><span data-ttu-id="dce65-124">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="dce65-124">Data type: Int32</span></span>|<span data-ttu-id="dce65-125">Implémentez ce paramètre afin que l’utilisateur peut spécifier la largeur du périphérique de sortie.</span><span class="sxs-lookup"><span data-stu-id="dce65-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="dce65-126">**Retour à la ligne**</span><span class="sxs-lookup"><span data-stu-id="dce65-126">**Wrap**</span></span><br><span data-ttu-id="dce65-127">Type de données : SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dce65-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="dce65-128">Implémentez ce paramètre afin que l’habillage du texte est pris en charge lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="dce65-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="dce65-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dce65-129">See Also</span></span>

[<span data-ttu-id="dce65-130">Paramètres de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="dce65-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="dce65-131">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dce65-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="dce65-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dce65-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
