---
ms.date: 12/31/2019
keywords: powershell,applet de commande
title: Objet ISESnippetCollection
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736043"
---
# <a name="the-isesnippetcollection-object"></a>Objet ISESnippetCollection

L’objet **ISESnippetCollection** est une collection d’objets **ISESnippet**. La collection de fichiers qui est associée à un objet **PowerShellTab** est un membre de cette classe. La collection `$psISE.CurrentPowerShellTab.Files` en est un exemple.

## <a name="methods"></a>Méthodes

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Prise en charge dans Windows PowerShell ISE 3.0 et versions ultérieures, ne figure pas dans les versions antérieures.

Charge un fichier `.snippets.ps1xml` qui contient des extraits de code définis par l’utilisateur. L’utilisation de la cmdlet `New-IseSnippet` est le moyen le plus simple de créer des extraits de code, car elle les stocke automatiquement dans votre dossier de profil pour qu’ils se chargent à chaque démarrage de Windows PowerShell ISE.

**FilePathName** : chaîne Chemin et nom d’un fichier .snippets.ps1xml qui contient les définitions des extraits de code.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Voir aussi

- [Objet ISESnippet](The-ISESnippetObject.md)
- [Objectif du modèle objet de script Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hiérarchie du modèle objet ISE](The-ISE-Object-Model-Hierarchy.md)
