---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Objet ISESnippetCollection
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030498"
---
# <a name="the-isesnippetcollection-object"></a>Objet ISESnippetCollection

L’objet **ISESnippetCollection** est une collection d’objets **ISESnippet**. La collection de fichiers qui est associée à un objet **PowerShellTab** est un membre de cette classe. La collection **$psISE.CurrentPowerShellTab.Files** en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Charge un fichier .snippets.ps1xml qui contient des extraits de code défini par l’utilisateur. L’applet de commande New-IseSnippet est le moyen le plus simple de créer des extraits de code, car elle les stocke automatiquement dans votre dossier de profil pour qu’ils se chargent à chaque démarrage de Windows PowerShell ISE.

**FilePathName** : chaîne Chemin et nom d’un fichier .snippets.ps1xml qui contient les définitions des extraits de code.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Voir aussi

- [Objet ISESnippet](The-ISESnippetObject.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
