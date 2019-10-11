---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utilisation des données de configuration
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954186"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="34437-103">Utilisation des données de configuration dans DSC</span><span class="sxs-lookup"><span data-stu-id="34437-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="34437-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="34437-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="34437-105">À l’aide du paramètre DSC intégré **ConfigurationData**, vous pouvez définir les données qui peuvent être utilisées dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="34437-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="34437-106">Cela vous permet de créer une configuration unique utilisée pour plusieurs nœuds ou différents environnements.</span><span class="sxs-lookup"><span data-stu-id="34437-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="34437-107">Par exemple, si vous développez une application, vous pouvez utiliser une seule configuration pour les environnements de développement et de production et utiliser les données de configuration pour spécifier les données de chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="34437-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="34437-108">Cette rubrique décrit la structure de la table de hachage **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="34437-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="34437-109">Pour des exemples d’utilisation des données de configuration, consultez [Séparation des données de configuration et d’environnement](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="34437-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="34437-110">Le paramètre commun ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="34437-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="34437-111">Une configuration DSC prend un paramètre commun, **ConfigurationData**, que vous spécifiez lorsque vous compilez la configuration.</span><span class="sxs-lookup"><span data-stu-id="34437-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="34437-112">Pour plus d’informations sur la compilation de configurations, voir [Configurations DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="34437-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="34437-113">Le paramètre **ConfigurationData** est une table de hachage qui doit contenir au moins une clé nommée **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="34437-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="34437-114">Il peut également avoir une ou plusieurs autres clés.</span><span class="sxs-lookup"><span data-stu-id="34437-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="34437-115">Les exemples de cette rubrique utilisent une seule clé supplémentaire (autres que la clé nommée **AllNodes**) appelée `NonNodeData`, mais vous pouvez inclure n’importe quel nombre de clés supplémentaires et les nommer comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="34437-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="34437-116">La valeur de la clé **AllNodes** est un tableau.</span><span class="sxs-lookup"><span data-stu-id="34437-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="34437-117">Chaque élément de ce tableau est également une table de hachage qui doit contenir au moins une clé nommée **NodeName** :</span><span class="sxs-lookup"><span data-stu-id="34437-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="34437-118">Vous pouvez ajouter d’autres clés à chaque table de hachage :</span><span class="sxs-lookup"><span data-stu-id="34437-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="34437-119">Pour appliquer une propriété à tous les nœuds, vous pouvez créer un membre du tableau **AllNodes** dont un **NodeName** a la valeur `*`.</span><span class="sxs-lookup"><span data-stu-id="34437-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="34437-120">Par exemple, pour attribuer la propriété `LogPath` à tous les nœuds, vous pouvez procéder ainsi :</span><span class="sxs-lookup"><span data-stu-id="34437-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="34437-121">Ceci équivaut à ajouter une propriété portant le nom `LogPath` avec la valeur `"C:\Logs"` à chacun des autres blocs (`VM-1`, `VM-2` et `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="34437-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="34437-122">Définition de la table de hachage ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="34437-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="34437-123">Vous pouvez définir **ConfigurationData** soit comme variable dans le même fichier de script qu’une configuration (comme dans nos exemples précédents), soit dans un fichier `.psd1` distinct.</span><span class="sxs-lookup"><span data-stu-id="34437-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="34437-124">Pour définir **ConfigurationData** dans un fichier `.psd1`, créez un fichier contenant uniquement la table de hachage qui représente les données de configuration.</span><span class="sxs-lookup"><span data-stu-id="34437-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="34437-125">Par exemple, vous pouvez créer un fichier nommé `MyData.psd1` avec le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="34437-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="34437-126">Compilation d’une configuration avec des données de configuration</span><span class="sxs-lookup"><span data-stu-id="34437-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="34437-127">Pour compiler une configuration pour laquelle vous avez défini des données de configuration, vous passez les données de configuration en tant que valeur du paramètre **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="34437-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="34437-128">Cela crée un fichier MOF pour chaque entrée dans le tableau **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="34437-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="34437-129">Chaque fichier MOF est nommé avec la propriété `NodeName` de l’entrée correspondante du tableau.</span><span class="sxs-lookup"><span data-stu-id="34437-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="34437-130">Par exemple, si vous définissez des données de configuration comme dans le fichier `MyData.psd1` ci-dessus, la compilation d’une configuration créerait à la fois des fichiers `VM-1.mof` et `VM-2.mof`.</span><span class="sxs-lookup"><span data-stu-id="34437-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="34437-131">Compilation d’une configuration avec des données de configuration à l’aide d’une variable</span><span class="sxs-lookup"><span data-stu-id="34437-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="34437-132">Pour utiliser les données de configuration qui sont définies comme une variable dans le même fichier `.ps1` que la configuration, vous passez le nom de la variable comme valeur du paramètre **ConfigurationData** lors de la compilation de la configuration :</span><span class="sxs-lookup"><span data-stu-id="34437-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="34437-133">Compilation d’une configuration avec des données de configuration à l’aide d’un fichier de données</span><span class="sxs-lookup"><span data-stu-id="34437-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="34437-134">Pour utiliser les données de configuration qui sont définies dans un fichier .psd1, vous passez le chemin et le nom de ce fichier comme valeur du paramètre **ConfigurationData** lors de la compilation de la configuration :</span><span class="sxs-lookup"><span data-stu-id="34437-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="34437-135">Utilisation de variables ConfigurationData dans une configuration</span><span class="sxs-lookup"><span data-stu-id="34437-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="34437-136">DSC fournit les variables spéciales suivantes, qui peuvent être utilisées dans un script de configuration :</span><span class="sxs-lookup"><span data-stu-id="34437-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="34437-137">**$AllNodes** fait référence à l’ensemble de la collection de nœuds définis dans **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="34437-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="34437-138">Vous pouvez filtrer la collection **AllNodes** à l’aide de **.Where()** et **.ForEach()** .</span><span class="sxs-lookup"><span data-stu-id="34437-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="34437-139">**ConfigurationData** fait référence à la table de hachage entière qui est passée comme paramètre lors de la compilation d’une configuration.</span><span class="sxs-lookup"><span data-stu-id="34437-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="34437-140">**MyTypeName** contient le nom de la [configuration](configurations.md) dans laquelle la variable est utilisée.</span><span class="sxs-lookup"><span data-stu-id="34437-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="34437-141">Par exemple, dans la configuration `MyDscConfiguration`, `$MyTypeName` aura la valeur `MyDscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="34437-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="34437-142">**Node** fait référence à une entrée particulière dans la collection **AllNodes** une fois qu’elle a été filtrée à l’aide de **.Where()** ou **.ForEach()** .</span><span class="sxs-lookup"><span data-stu-id="34437-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="34437-143">Vous pouvez en savoir plus sur ces méthodes dans [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span><span class="sxs-lookup"><span data-stu-id="34437-143">You can read more about these methods in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="34437-144">Utilisation des données n’appartenant pas à un nœud</span><span class="sxs-lookup"><span data-stu-id="34437-144">Using non-node data</span></span>

<span data-ttu-id="34437-145">Comme nous l’avons vu dans les exemples précédents, la table de hachage **ConfigurationData** peut avoir une ou plusieurs clés en plus de la clé **AllNodes** requise.</span><span class="sxs-lookup"><span data-stu-id="34437-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="34437-146">Dans les exemples de cette rubrique, nous avons utilisé un seul nœud supplémentaire et l’avons nommé `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="34437-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="34437-147">Toutefois, vous pouvez définir n’importe quel nombre de clés supplémentaires et les nommer comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="34437-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="34437-148">Pour obtenir un exemple d’utilisation des données n’appartenant pas à un nœud, consultez [Séparation des données de configuration et d’environnement](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="34437-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34437-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34437-149">See Also</span></span>

- [<span data-ttu-id="34437-150">Options relatives aux informations d’identification dans les données de configuration</span><span class="sxs-lookup"><span data-stu-id="34437-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="34437-151">Configurations DSC</span><span class="sxs-lookup"><span data-stu-id="34437-151">DSC Configurations</span></span>](configurations.md)