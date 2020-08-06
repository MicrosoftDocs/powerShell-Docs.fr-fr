---
title: Élément TypeName pour SelectionCondition pour les contrôles de configuration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2db856d1b84dded315204d8c8574ae86acb63515
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780064"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="fc548-102">TypeName, élément pour SelectionCondition pour Controls pour Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="fc548-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="fc548-103">Spécifie un type .NET qui déclenche la condition.</span><span class="sxs-lookup"><span data-stu-id="fc548-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="fc548-104">Cet élément est utilisé lors de la définition d’un contrôle commun qui peut être utilisé par toutes les vues dans le fichier de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="fc548-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="fc548-105">Élément de configuration (format) contrôle l’élément de configuration (format) élément de contrôle pour les contrôles de configuration (format) CustomControl élément de contrôle pour la configuration (format) élément CustomEntries pour CustomControl pour les contrôles de configuration (format) élément CustomEntry pour CustomControl pour les contrôles de configuration (format), élément EntrySelectedBy pour CustomEntry pour les contrôles de configuration (format) SelectionCondition élément pour EntrySelectedBy pour CustomEntry pour la configuration (format) élément TypeName pour SelectionCondition pour les contrôles de configuration (format)</span><span class="sxs-lookup"><span data-stu-id="fc548-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc548-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc548-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc548-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fc548-107">Attributes and Elements</span></span>

<span data-ttu-id="fc548-108">Les sections suivantes décrivent les attributs, les éléments enfants et l’élément parent de l' `TypeName` élément.</span><span class="sxs-lookup"><span data-stu-id="fc548-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc548-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="fc548-109">Attributes</span></span>

<span data-ttu-id="fc548-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fc548-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc548-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fc548-111">Child Elements</span></span>

<span data-ttu-id="fc548-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fc548-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc548-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fc548-113">Parent Elements</span></span>

|<span data-ttu-id="fc548-114">Élément</span><span class="sxs-lookup"><span data-stu-id="fc548-114">Element</span></span>|<span data-ttu-id="fc548-115">Description</span><span class="sxs-lookup"><span data-stu-id="fc548-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc548-116">Élément SelectionCondition pour EntrySelectedBy pour CustomEntry pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="fc548-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="fc548-117">Définit une condition qui doit exister pour que la définition de contrôle soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="fc548-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fc548-118">Valeur texte</span><span class="sxs-lookup"><span data-stu-id="fc548-118">Text Value</span></span>

<span data-ttu-id="fc548-119">Spécifiez le nom qualifié complet du type .NET, par exemple `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="fc548-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc548-120">Notes</span><span class="sxs-lookup"><span data-stu-id="fc548-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="fc548-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc548-121">See Also</span></span>

[<span data-ttu-id="fc548-122">Élément SelectionCondition pour EntrySelectedBy pour CustomEntry pour la configuration (format)</span><span class="sxs-lookup"><span data-stu-id="fc548-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="fc548-123">Écriture d’un fichier de mise en forme PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc548-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
