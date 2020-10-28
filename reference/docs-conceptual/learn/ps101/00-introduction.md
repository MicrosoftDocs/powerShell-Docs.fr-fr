---
title: Introduction
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: Il s’agit de l’introduction du livre « PowerShell 101 » de Mike F. Robbins.
ms.openlocfilehash: d85590c2ef34c4e8b5cb7f2707bd9d6dd9b84b89
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501505"
---
# <a name="introduction"></a><span data-ttu-id="39dfa-103">Introduction</span><span class="sxs-lookup"><span data-stu-id="39dfa-103">Introduction</span></span>

<table>
  <tr><td>
  <a href="https://leanpub.com/powershell101">
  <img src="media/powershell101-150x194.png" alt="PowerShell 101 (the book)" />
  </a>
  </td>
  <td colspan=2>
<span data-ttu-id="39dfa-104">Ce contenu est tiré du livre <em>PowerShell 101</em> écrit par Mike F Robbins.</span><span class="sxs-lookup"><span data-stu-id="39dfa-104">This content originally appeared in the book <em>PowerShell 101</em> by Mike F Robbins.</span></span> <span data-ttu-id="39dfa-105">Nous remercions Mike de nous avoir autorisés à reprendre son contenu ici.</span><span class="sxs-lookup"><span data-stu-id="39dfa-105">We thank Mike for granting us permission to reuse his content here.</span></span> <span data-ttu-id="39dfa-106">Le contenu a été modifié par rapport à la publication initiale.</span><span class="sxs-lookup"><span data-stu-id="39dfa-106">The content has been edited from the original publication.</span></span> <span data-ttu-id="39dfa-107">Le livre original <a href="https://leanpub.com/powershell101">PowerShell 101</a> est encore disponible sur le Store Leanpub.</span><span class="sxs-lookup"><span data-stu-id="39dfa-107">You can still get the original book from Leanpub at <a href="https://leanpub.com/powershell101">PowerShell 101</a>.</span></span>
  </td></tr>
</table>

## <a name="who-is-this-book-for"></a><span data-ttu-id="39dfa-108">À qui s’adresse ce livre ?</span><span class="sxs-lookup"><span data-stu-id="39dfa-108">Who is this book for?</span></span>

<span data-ttu-id="39dfa-109">Il s’agit d’un ouvrage général qui s’adresse à quiconque souhaite découvrir PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39dfa-109">This is an entry-level book for anyone wanting to learn PowerShell.</span></span>

<span data-ttu-id="39dfa-110">Ce livre est axé sur la version 5.1 de PowerShell exécutée sur Windows 10 et Windows Server 2016 dans un environnement de domaine Microsoft Active Directory.</span><span class="sxs-lookup"><span data-stu-id="39dfa-110">This book focuses on PowerShell version 5.1 running on Windows 10 and Windows Server 2016 in a Microsoft Active Directory domain environment.</span></span> <span data-ttu-id="39dfa-111">Toutefois, les concepts de base qui y sont expliqués s’appliquent à toutes les versions de PowerShell exécutées sur des plateformes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="39dfa-111">However, the basic concepts apply to all versions of PowerShell running on any supported platform.</span></span>

## <a name="about-this-book"></a><span data-ttu-id="39dfa-112">À propos de ce livre</span><span class="sxs-lookup"><span data-stu-id="39dfa-112">About this book</span></span>

<span data-ttu-id="39dfa-113">Ce livre regroupe les informations que j’aurais aimé avoir lorsque j’ai commencé à découvrir PowerShell, ainsi que les conseils, les astuces et les bonnes pratiques que j’ai expérimentés au cours des dix dernières années où j’ai utilisé PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39dfa-113">This book is a collection of what I wish someone would have told me when I started learning PowerShell, along with the tips, tricks, and best practices that I've learned while using PowerShell during the past 10 years.</span></span>

<span data-ttu-id="39dfa-114">Plutôt que de submerger le lecteur d’informations, ce livre s’attache à donner la juste quantité d’informations nécessaires aux débutants pour bien démarrer avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39dfa-114">Instead of providing an enormous amount of information, this book attempts to provide a balance of enough information to be successful for someone who is just getting started with PowerShell.</span></span> <span data-ttu-id="39dfa-115">Chaque chapitre contient des liens vers des rubriques d’aide qui seront utiles à ceux qui souhaitent approfondir les sujets abordés dans le chapitre.</span><span class="sxs-lookup"><span data-stu-id="39dfa-115">Each chapter contains links to specific help topics for those who want more information about the topics covered in that chapter.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="39dfa-116">À propos de l’auteur</span><span class="sxs-lookup"><span data-stu-id="39dfa-116">About the author</span></span>

<span data-ttu-id="39dfa-117">Ancien Microsoft MVP, Mike F Robbins est coauteur de _Windows PowerShell TFM 4th Edition_ et auteur collaborateur du livre _PowerShell Deep Dives_ .</span><span class="sxs-lookup"><span data-stu-id="39dfa-117">Mike F Robbins is a former Microsoft MVP, co-author of _Windows PowerShell TFM 4th Edition_ , and a contributing author in the _PowerShell Deep Dives_ book.</span></span> <span data-ttu-id="39dfa-118">Mike est un fervent partisan de la communauté PowerShell et est maintenant le principal rédacteur pour [Azure PowerShell][] chez Microsoft.</span><span class="sxs-lookup"><span data-stu-id="39dfa-118">Mike has been a strong supporter of the PowerShell community and is now the lead writer for [Azure PowerShell][] at Microsoft.</span></span> <span data-ttu-id="39dfa-119">Il écrit sur son blog [mikefrobbins.com][] et est présent sur Twitter sous le nom de [@mikefrobbins][].</span><span class="sxs-lookup"><span data-stu-id="39dfa-119">He blogs at [mikefrobbins.com][] and can be found on twitter [@mikefrobbins][].</span></span>

## <a name="lab-environment"></a><span data-ttu-id="39dfa-120">Environnement lab</span><span class="sxs-lookup"><span data-stu-id="39dfa-120">Lab environment</span></span>

<span data-ttu-id="39dfa-121">Les exemples de cet ouvrage ont été conçus et testés avec PowerShell version 5.1 sur Windows 10 Anniversaire (build 1607) et Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="39dfa-121">The examples in this book were designed and tested on Windows 10 Anniversary Edition (build 1607) and Windows Server 2016 using PowerShell version 5.1.</span></span> <span data-ttu-id="39dfa-122">Si vous utilisez une autre version de PowerShell ou du système d’exploitation, vos résultats pourront différer de ceux présentés ici.</span><span class="sxs-lookup"><span data-stu-id="39dfa-122">If you're using a different version of PowerShell or operating system, your results may differ from those shown here.</span></span>

<!-- link references -->
[@mikefrobbins]: https://twitter.com/mikefrobbins
[mikefrobbins.com]: http://mikefrobbins.com/
[PowerShell 101]: https://leanpub.com/powershell101
[Azure PowerShell]: /powershell/azure
