---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Ressource nxFile dans DSC pour Linux
ms.openlocfilehash: 14f1ae31a8409b8874d76a91b8b29595e30fbb46
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="745c9-103">Ressource nxFile dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="745c9-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="745c9-104">La ressource **nxFile** dans DSC PowerShell fournit un mécanisme permettant de gérer les fichiers et les répertoires sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="745c9-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="745c9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="745c9-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="745c9-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="745c9-106">Properties</span></span>

|  <span data-ttu-id="745c9-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="745c9-107">Property</span></span> |  <span data-ttu-id="745c9-108">Description</span><span class="sxs-lookup"><span data-stu-id="745c9-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="745c9-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="745c9-109">DestinationPath</span></span>| <span data-ttu-id="745c9-110">Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état.</span><span class="sxs-lookup"><span data-stu-id="745c9-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>| 
| <span data-ttu-id="745c9-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="745c9-111">SourcePath</span></span>| <span data-ttu-id="745c9-112">Spécifie le chemin à partir duquel copier la ressource de fichier ou de dossier.</span><span class="sxs-lookup"><span data-stu-id="745c9-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="745c9-113">Ce chemin peut être un chemin local ou une URL `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="745c9-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="745c9-114">Les URL `http/https/ftp` distantes sont uniquement prises en charge quand la valeur de la propriété **Type** est File.</span><span class="sxs-lookup"><span data-stu-id="745c9-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>| 
| <span data-ttu-id="745c9-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="745c9-115">Ensure</span></span>| <span data-ttu-id="745c9-116">Détermine si l’existence du fichier doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="745c9-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="745c9-117">Définissez cette propriété sur « Present » pour vous assurer que le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="745c9-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="745c9-118">Définissez la propriété sur « Absent » pour vous assurer que le fichier n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="745c9-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="745c9-119">La valeur par défaut est « Present ».</span><span class="sxs-lookup"><span data-stu-id="745c9-119">The default value is "Present".</span></span>| 
| <span data-ttu-id="745c9-120">Type</span><span class="sxs-lookup"><span data-stu-id="745c9-120">Type</span></span>| <span data-ttu-id="745c9-121">Spécifie si la ressource actuellement configurée est un répertoire ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="745c9-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="745c9-122">Définissez cette propriété sur Directory pour indiquer que la ressource est un répertoire.</span><span class="sxs-lookup"><span data-stu-id="745c9-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="745c9-123">Affectez-lui la valeur File pour indiquer que la ressource est un fichier.</span><span class="sxs-lookup"><span data-stu-id="745c9-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="745c9-124">La valeur par défaut est File.</span><span class="sxs-lookup"><span data-stu-id="745c9-124">The default value is "file"</span></span>| 
| <span data-ttu-id="745c9-125">Contents</span><span class="sxs-lookup"><span data-stu-id="745c9-125">Contents</span></span>| <span data-ttu-id="745c9-126">Spécifie le contenu d’un fichier, tel qu’une chaîne spécifique.</span><span class="sxs-lookup"><span data-stu-id="745c9-126">Specifies the contents of a file, such as a particular string.</span></span>| 
| <span data-ttu-id="745c9-127">Checksum</span><span class="sxs-lookup"><span data-stu-id="745c9-127">Checksum</span></span>| <span data-ttu-id="745c9-128">Définit le type à utiliser pour déterminer si deux fichiers sont identiques.</span><span class="sxs-lookup"><span data-stu-id="745c9-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="745c9-129">Si **Checksum** n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="745c9-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="745c9-130">Les valeurs sont « ctime », « mtime » et « md5 ».</span><span class="sxs-lookup"><span data-stu-id="745c9-130">Values are: "ctime", "mtime", or "md5".</span></span>| 
| <span data-ttu-id="745c9-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="745c9-131">Recurse</span></span>| <span data-ttu-id="745c9-132">Indique si des sous-répertoires sont inclus.</span><span class="sxs-lookup"><span data-stu-id="745c9-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="745c9-133">Définissez cette propriété sur **$true** pour indiquer que vous voulez inclure des sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="745c9-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="745c9-134">La valeur par défaut est **$false**.</span><span class="sxs-lookup"><span data-stu-id="745c9-134">The default is **$false**.</span></span> <span data-ttu-id="745c9-135">**Remarque** : Cette propriété est valide uniquement quand la propriété **Type** est définie sur Directory.</span><span class="sxs-lookup"><span data-stu-id="745c9-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>| 
| <span data-ttu-id="745c9-136">Force</span><span class="sxs-lookup"><span data-stu-id="745c9-136">Force</span></span>| <span data-ttu-id="745c9-137">Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur.</span><span class="sxs-lookup"><span data-stu-id="745c9-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="745c9-138">La propriété **Force** permet d’ignorer ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="745c9-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="745c9-139">La valeur par défaut est **$false**.</span><span class="sxs-lookup"><span data-stu-id="745c9-139">The default value is **$false**.</span></span>| 
| <span data-ttu-id="745c9-140">Links</span><span class="sxs-lookup"><span data-stu-id="745c9-140">Links</span></span>| <span data-ttu-id="745c9-141">Spécifie le comportement souhaité pour les liens symboliques.</span><span class="sxs-lookup"><span data-stu-id="745c9-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="745c9-142">Définissez cette propriété sur Follow pour suivre les liens symboliques et agir sur la cible des liens (par exemple,</span><span class="sxs-lookup"><span data-stu-id="745c9-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="745c9-143">pour copier le fichier au lieu du lien).</span><span class="sxs-lookup"><span data-stu-id="745c9-143">copy the file instead of the link).</span></span> <span data-ttu-id="745c9-144">Définissez cette propriété sur Manage pour agir sur le lien (par exemple,</span><span class="sxs-lookup"><span data-stu-id="745c9-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="745c9-145">pour copier le lien).</span><span class="sxs-lookup"><span data-stu-id="745c9-145">copy the link itself).</span></span> <span data-ttu-id="745c9-146">Définissez cette propriété sur Ignore pour ignorer les liens symboliques.</span><span class="sxs-lookup"><span data-stu-id="745c9-146">Set this property to "ignore" to ignore symbolic links.</span></span>| 
| <span data-ttu-id="745c9-147">Group</span><span class="sxs-lookup"><span data-stu-id="745c9-147">Group</span></span>| <span data-ttu-id="745c9-148">Nom du **groupe** qui possède le fichier ou le répertoire.</span><span class="sxs-lookup"><span data-stu-id="745c9-148">The name of the **Group** to own the file or directory.</span></span>| 
| <span data-ttu-id="745c9-149">Mode</span><span class="sxs-lookup"><span data-stu-id="745c9-149">Mode</span></span>| <span data-ttu-id="745c9-150">Spécifie les autorisations souhaitées pour la ressource, en notation octale ou symbolique</span><span class="sxs-lookup"><span data-stu-id="745c9-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="745c9-151">(par exemple, 777 ou rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="745c9-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="745c9-152">Si vous utilisez la notation symbolique, n’entrez pas le premier caractère qui indique le répertoire ou le fichier.</span><span class="sxs-lookup"><span data-stu-id="745c9-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>| 
| <span data-ttu-id="745c9-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="745c9-153">DependsOn</span></span> | <span data-ttu-id="745c9-154">Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="745c9-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="745c9-155">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="745c9-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="additional-information"></a><span data-ttu-id="745c9-156">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="745c9-156">Additional Information</span></span>


<span data-ttu-id="745c9-157">Linux et Windows utilisent des caractères de saut de ligne différents dans les fichiers texte par défaut, ce qui peut entraîner des résultats inattendus quand vous configurez des fichiers sur un ordinateur Linux avec __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="745c9-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="745c9-158">Il existe plusieurs manières de gérer le contenu d’un fichier Linux tout en évitant les problèmes provoqués par les caractères de saut de ligne inattendus :</span><span class="sxs-lookup"><span data-stu-id="745c9-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="745c9-159">Étape 1 - Copier le fichier à partir d’une source distante (http, https ou ftp) : créez un fichier sur Linux avec le contenu de votre choix et effectuez une copie intermédiaire vers un serveur web ou FTP accessible aux nœuds que vous allez configurer.</span><span class="sxs-lookup"><span data-stu-id="745c9-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="745c9-160">Définissez la propriété __SourcePath__ de la ressource __nxFile__ sur l’URL web ou FTP du fichier.</span><span class="sxs-lookup"><span data-stu-id="745c9-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    
}
        
}
```


<span data-ttu-id="745c9-161">Étape 2 : Lire le contenu du fichier de script PowerShell avec [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) après avoir défini la propriété __$OFS__ pour utiliser le caractère de saut de ligne Linux.</span><span class="sxs-lookup"><span data-stu-id="745c9-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="745c9-162">Étape 3 : Utiliser une fonction PowerShell pour remplacer les sauts de ligne Windows par des caractères de saut de ligne Linux.</span><span class="sxs-lookup"><span data-stu-id="745c9-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = $Contents
    
}
}
```

## <a name="example"></a><span data-ttu-id="745c9-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="745c9-163">Example</span></span>

<span data-ttu-id="745c9-164">L’exemple suivant vérifie que le répertoire `/opt/mydir` existe et qu’un fichier avec le contenu spécifié se trouve dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="745c9-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx 

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@ 
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```

