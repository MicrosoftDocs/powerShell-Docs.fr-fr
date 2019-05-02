---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9af931a1a2b545ba36826246c4155f42052a16bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085698"
---
# <a name="mof-documents-are-encrypted-by-default"></a>Les documents MOF sont chiffrés par défaut

Les documents de configuration contiennent des informations sensibles. Dans les versions précédentes de DSC, vous deviez distribuer et gérer des certificats pour sécuriser les informations d’identification dans une configuration. Pour de nombreux utilisateurs il s’agissait d’une charge de travail élevée, et même avec tout le travail effectué, certaines informations de configuration n’était pas et ne pouvaient pas être sécurisées.

Ce n’est plus le cas, car **tous les documents MOF de configuration sont sécurisés par défaut**. Aucun certificat ou paramètre de métaconfiguration n’est nécessaire. Quand un document MOF de configuration est enregistré sur le disque par le gestionnaire de configuration local sur un nœud cible, il est chiffré. Les documents MOF sont chiffrés à l’aide de [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Remarque :** les fichiers MOF générés par un script de configuration ne sont pas chiffrés.

**Exemple :** Chiffrement en mode push ![Chiffrement MOF](../images/MOF_Encryption.jpg)

Si vous utilisez déjà la méthode par certificat pour le chiffrement des mots de passe ou si vous avez besoin d’une sécurité supplémentaire pour vos mots de passe, la [méthode de chiffrement par certificat existante](https://msdn.microsoft.com/powershell/dsc/securemof) continuera à fonctionner. Le résultat sera un document MOF entièrement chiffré à l’aide des DPAPI et qui intégrera des mots de passe chiffrés.

Ce chiffrement s’applique uniquement aux documents MOF de configuration (pending.mof, current.mof, previous.mof et fichiers MOF partiels). Les documents MOF de métaconfiguration sont toujours enregistrés en texte brut, car il est moins probable qu’ils contiennent des données confidentielles.
