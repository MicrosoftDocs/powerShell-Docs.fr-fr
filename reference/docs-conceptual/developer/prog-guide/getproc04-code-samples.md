---
title: Exemples de code GetProc04 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b90b7e96c1454e57df93863b526758f25d9be690
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771955"
---
# <a name="getproc04-code-samples"></a>Exemples de code GetProc04

Voici les exemples de code pour l’applet de commande GetProc04 Sample. Il s’agit de l' `Get-Process` exemple d’applet de commande décrit dans [Ajout de rapports d’erreurs de non-terminaison à votre applet de](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)commande. Cette `Get-Process` applet de commande appelle la méthode [System. Management. Automation. applet de commande. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) chaque fois qu’une exception d’opération non valide est levée lors de la récupération des informations sur le processus.

> [!NOTE]
> Vous pouvez télécharger le fichier source C# (getprov04.cs) pour cette applet de commande « obtenir-proc » à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers sources téléchargés sont disponibles dans le **\<PowerShell Samples>** répertoire.

Pour obtenir un exemple de code complet, consultez les rubriques suivantes.

|Langage|Rubrique|
|--------------|-----------|
|C#|[Exemple de code GetProc04 (C#)](./getproc04-csharp-sample-code.md)|
|VB.NET|[Exemple de code GetProc04 (VB.NET)](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
