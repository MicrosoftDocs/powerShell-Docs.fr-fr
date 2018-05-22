---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxScript dans DSC pour Linux
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a>Ressource nxScript dans DSC pour Linux

La ressource **nxScript** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant d’exécuter des scripts Linux sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Description |
|---|---|
| GetScript| Fournit un script qui s’exécute quand vous appelez l’applet de commande [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx). Le script doit commencer par un shebang, tel que #!/bin/bash.|
| SetScript| Fournit un script. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), **TestScript** s’exécute en premier. Si le bloc **TestScript** retourne un code de sortie différent de 0, le bloc **SetScript** s’exécute. Si **TestScript** retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas. Le script doit commencer par un shebang, tel que `#!/bin/bash`.|
| TestScript| Fournit un script. Quand vous appelez l’applet de commande [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), ce script s’exécute. Si la propriété retourne un code de sortie différent de 0, SetScript s’exécute. Si la propriété retourne un code de sortie égal à 0, **SetScript** ne s’exécute pas. **TestScript** s’exécute également quand vous appelez l’applet de commande [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). Toutefois, dans ce cas, la propriété **SetScript** ne s’exécute pas, quel que soit le code de sortie retourné par **TestScript**. **TestScript** doit retourner le code de sortie 0 si la configuration réelle correspond à la configuration actuelle de l’état souhaité. Sinon, elle doit retourner un code de sortie différent de 0. (La configuration actuelle de l’état souhaité est la dernière configuration appliquée sur le nœud qui utilise DSC.) Le script doit commencer par un shebang, tel que 1#!/bin/bash.1|
| User| Nom d’utilisateur utilisé pour exécuter le script.|
| Group| Nom de groupe utilisé pour exécuter le script.|
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemple

L’exemple suivant utilise la ressource **nxScript** pour gérer une configuration supplémentaire.

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```