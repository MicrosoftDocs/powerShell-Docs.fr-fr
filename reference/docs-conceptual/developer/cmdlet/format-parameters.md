---
title: Paramètres de format | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369748"
---
# <a name="format-parameters"></a><span data-ttu-id="fba11-102">Paramètres de format</span><span class="sxs-lookup"><span data-stu-id="fba11-102">Format Parameters</span></span>

<span data-ttu-id="fba11-103">Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres utilisés pour mettre en forme ou générer des données.</span><span class="sxs-lookup"><span data-stu-id="fba11-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="fba11-104">Paramètre</span><span class="sxs-lookup"><span data-stu-id="fba11-104">Parameter</span></span>|<span data-ttu-id="fba11-105">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="fba11-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="fba11-106">**As**</span><span class="sxs-lookup"><span data-stu-id="fba11-106">**As**</span></span><br><span data-ttu-id="fba11-107">Type de données : mot clé</span><span class="sxs-lookup"><span data-stu-id="fba11-107">Data type: Keyword</span></span>|<span data-ttu-id="fba11-108">Implémentez ce paramètre pour spécifier le format de sortie de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="fba11-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="fba11-109">Par exemple, les valeurs possibles peuvent être du texte ou des scripts.</span><span class="sxs-lookup"><span data-stu-id="fba11-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="fba11-110">**Binaire**</span><span class="sxs-lookup"><span data-stu-id="fba11-110">**Binary**</span></span><br><span data-ttu-id="fba11-111">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="fba11-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="fba11-112">Implémentez ce paramètre pour indiquer que l’applet de commande gère les valeurs binaires.</span><span class="sxs-lookup"><span data-stu-id="fba11-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="fba11-113">**Encoding**</span><span class="sxs-lookup"><span data-stu-id="fba11-113">**Encoding**</span></span><br><span data-ttu-id="fba11-114">Type de données : mot clé</span><span class="sxs-lookup"><span data-stu-id="fba11-114">Data type: Keyword</span></span>|<span data-ttu-id="fba11-115">Implémentez ce paramètre pour spécifier le type d’encodage pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fba11-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="fba11-116">Par exemple, les valeurs possibles sont ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte et String.</span><span class="sxs-lookup"><span data-stu-id="fba11-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="fba11-117">**Caractère**</span><span class="sxs-lookup"><span data-stu-id="fba11-117">**NewLine**</span></span><br><span data-ttu-id="fba11-118">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="fba11-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="fba11-119">Implémentez ce paramètre afin que les caractères de saut de ligne soient pris en charge lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="fba11-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="fba11-120">**Nom court**</span><span class="sxs-lookup"><span data-stu-id="fba11-120">**ShortName**</span></span><br><span data-ttu-id="fba11-121">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="fba11-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="fba11-122">Implémentez ce paramètre afin que les noms courts soient pris en charge lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="fba11-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="fba11-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="fba11-123">**Width**</span></span><br><span data-ttu-id="fba11-124">Type de données : Int32</span><span class="sxs-lookup"><span data-stu-id="fba11-124">Data type: Int32</span></span>|<span data-ttu-id="fba11-125">Implémentez ce paramètre afin que l’utilisateur puisse spécifier la largeur du périphérique de sortie.</span><span class="sxs-lookup"><span data-stu-id="fba11-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="fba11-126">**Collier**</span><span class="sxs-lookup"><span data-stu-id="fba11-126">**Wrap**</span></span><br><span data-ttu-id="fba11-127">Type de données : Paramètre_booléen</span><span class="sxs-lookup"><span data-stu-id="fba11-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="fba11-128">Implémentez ce paramètre pour que l’habillage du texte soit pris en charge lorsque le paramètre est spécifié.</span><span class="sxs-lookup"><span data-stu-id="fba11-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="fba11-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fba11-129">See Also</span></span>

[<span data-ttu-id="fba11-130">Paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="fba11-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="fba11-131">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fba11-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="fba11-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fba11-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
