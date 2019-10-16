---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource nxFile dans DSC pour Linux
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954826"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="03a54-103">Ressource nxFile dans DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="03a54-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="03a54-104">La ressource **nxFile** dans DSC PowerShell fournit un mécanisme permettant de gérer les fichiers et les répertoires sur un nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="03a54-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="03a54-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03a54-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="03a54-106">Propriétés</span><span class="sxs-lookup"><span data-stu-id="03a54-106">Properties</span></span>

|<span data-ttu-id="03a54-107">Propriété</span><span class="sxs-lookup"><span data-stu-id="03a54-107">Property</span></span> |<span data-ttu-id="03a54-108">Description</span><span class="sxs-lookup"><span data-stu-id="03a54-108">Description</span></span> |
|---|---|
|<span data-ttu-id="03a54-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="03a54-109">DestinationPath</span></span> |<span data-ttu-id="03a54-110">Spécifie l’emplacement d’un fichier ou d’un répertoire dont vous voulez garantir l’état.</span><span class="sxs-lookup"><span data-stu-id="03a54-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="03a54-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="03a54-111">SourcePath</span></span> |<span data-ttu-id="03a54-112">Spécifie le chemin à partir duquel copier la ressource de fichier ou de dossier.</span><span class="sxs-lookup"><span data-stu-id="03a54-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="03a54-113">Ce chemin peut être un chemin local ou une URL `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="03a54-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="03a54-114">Les URL `http/https/ftp` distantes sont uniquement prises en charge quand la valeur de la propriété **Type** est **file**.</span><span class="sxs-lookup"><span data-stu-id="03a54-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="03a54-115">Type</span><span class="sxs-lookup"><span data-stu-id="03a54-115">Type</span></span> |<span data-ttu-id="03a54-116">Spécifie si la ressource actuellement configurée est un répertoire ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="03a54-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="03a54-117">Définissez cette propriété sur **directory** pour indiquer que la ressource est un répertoire.</span><span class="sxs-lookup"><span data-stu-id="03a54-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="03a54-118">Affectez-lui la valeur **file** pour indiquer que la ressource est un fichier.</span><span class="sxs-lookup"><span data-stu-id="03a54-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="03a54-119">La valeur par défaut est **file**.</span><span class="sxs-lookup"><span data-stu-id="03a54-119">The default value is **file**.</span></span> |
|<span data-ttu-id="03a54-120">Contents</span><span class="sxs-lookup"><span data-stu-id="03a54-120">Contents</span></span> |<span data-ttu-id="03a54-121">Spécifie le contenu d’un fichier, tel qu’une chaîne spécifique.</span><span class="sxs-lookup"><span data-stu-id="03a54-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="03a54-122">Checksum</span><span class="sxs-lookup"><span data-stu-id="03a54-122">Checksum</span></span> |<span data-ttu-id="03a54-123">Définit le type à utiliser pour déterminer si deux fichiers sont identiques.</span><span class="sxs-lookup"><span data-stu-id="03a54-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="03a54-124">Si **Checksum** n’est pas spécifié, seul le nom du fichier ou du répertoire est utilisé pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="03a54-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="03a54-125">Les valeurs sont **ctime**, **mtime** ou **md5**.</span><span class="sxs-lookup"><span data-stu-id="03a54-125">Values are: **ctime**, **mtime**, or **md5**.</span></span> |
|<span data-ttu-id="03a54-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="03a54-126">Recurse</span></span> |<span data-ttu-id="03a54-127">Indique si des sous-répertoires sont inclus.</span><span class="sxs-lookup"><span data-stu-id="03a54-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="03a54-128">Définissez cette propriété sur `$true` pour indiquer que vous voulez inclure des sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="03a54-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="03a54-129">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="03a54-129">The default is `$false`.</span></span> <span data-ttu-id="03a54-130">Cette propriété est valide uniquement quand la propriété **Type** est définie sur **directory**.</span><span class="sxs-lookup"><span data-stu-id="03a54-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="03a54-131">Force</span><span class="sxs-lookup"><span data-stu-id="03a54-131">Force</span></span> |<span data-ttu-id="03a54-132">Certaines opérations de fichier (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire non vide) entraînent une erreur.</span><span class="sxs-lookup"><span data-stu-id="03a54-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="03a54-133">La propriété **Force** permet d’ignorer ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="03a54-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="03a54-134">La valeur par défaut est `$false`.</span><span class="sxs-lookup"><span data-stu-id="03a54-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="03a54-135">Links</span><span class="sxs-lookup"><span data-stu-id="03a54-135">Links</span></span> |<span data-ttu-id="03a54-136">Spécifie le comportement souhaité pour les liens symboliques.</span><span class="sxs-lookup"><span data-stu-id="03a54-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="03a54-137">Définissez cette propriété sur **follow** pour suivre les liens symboliques et agir sur la cible des liens.</span><span class="sxs-lookup"><span data-stu-id="03a54-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="03a54-138">Par exemple, copiez le fichier au lieu du lien.</span><span class="sxs-lookup"><span data-stu-id="03a54-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="03a54-139">Définissez cette propriété sur **manage** pour agir sur le lien.</span><span class="sxs-lookup"><span data-stu-id="03a54-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="03a54-140">Par exemple, copiez le lien lui-même.</span><span class="sxs-lookup"><span data-stu-id="03a54-140">For example, copy the link itself.</span></span> <span data-ttu-id="03a54-141">Définissez cette propriété sur **ignore** pour ignorer les liens symboliques.</span><span class="sxs-lookup"><span data-stu-id="03a54-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="03a54-142">Group</span><span class="sxs-lookup"><span data-stu-id="03a54-142">Group</span></span> |<span data-ttu-id="03a54-143">Nom du **groupe** qui doit avoir les autorisations sur le fichier ou le répertoire.</span><span class="sxs-lookup"><span data-stu-id="03a54-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="03a54-144">Mode</span><span class="sxs-lookup"><span data-stu-id="03a54-144">Mode</span></span> |<span data-ttu-id="03a54-145">Spécifie les autorisations souhaitées pour la ressource, en notation octale ou symbolique</span><span class="sxs-lookup"><span data-stu-id="03a54-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="03a54-146">Par exemple, **777** ou **rwxrwxrwx**.</span><span class="sxs-lookup"><span data-stu-id="03a54-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="03a54-147">Si vous utilisez la notation symbolique, n’entrez pas le premier caractère qui indique le répertoire ou le fichier.</span><span class="sxs-lookup"><span data-stu-id="03a54-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="03a54-148">Propriétaire</span><span class="sxs-lookup"><span data-stu-id="03a54-148">Owner</span></span> |<span data-ttu-id="03a54-149">Nom du groupe qui possède le fichier ou le répertoire.</span><span class="sxs-lookup"><span data-stu-id="03a54-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="03a54-150">Propriétés communes</span><span class="sxs-lookup"><span data-stu-id="03a54-150">Common properties</span></span>

|<span data-ttu-id="03a54-151">Propriété</span><span class="sxs-lookup"><span data-stu-id="03a54-151">Property</span></span> |<span data-ttu-id="03a54-152">Description</span><span class="sxs-lookup"><span data-stu-id="03a54-152">Description</span></span> |
|---|---|
|<span data-ttu-id="03a54-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="03a54-153">DependsOn</span></span> |<span data-ttu-id="03a54-154">Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource.</span><span class="sxs-lookup"><span data-stu-id="03a54-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="03a54-155">Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="03a54-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="03a54-156">Ensure</span><span class="sxs-lookup"><span data-stu-id="03a54-156">Ensure</span></span> |<span data-ttu-id="03a54-157">Détermine si l’existence du fichier doit être vérifiée.</span><span class="sxs-lookup"><span data-stu-id="03a54-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="03a54-158">Définissez cette propriété sur **Present** pour vous assurer que le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="03a54-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="03a54-159">Définissez la propriété sur **Absent** pour vous assurer que le fichier n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="03a54-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="03a54-160">La valeur par défaut est **Present**.</span><span class="sxs-lookup"><span data-stu-id="03a54-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="03a54-161">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="03a54-161">Additional Information</span></span>

<span data-ttu-id="03a54-162">Linux et Windows utilisent des caractères de saut de ligne différents dans les fichiers texte par défaut, ce qui peut entraîner des résultats inattendus quand vous configurez des fichiers sur un ordinateur Linux avec **nxFile**.</span><span class="sxs-lookup"><span data-stu-id="03a54-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="03a54-163">Il existe plusieurs manières de gérer le contenu d’un fichier Linux tout en évitant les problèmes provoqués par les caractères de saut de ligne inattendus :</span><span class="sxs-lookup"><span data-stu-id="03a54-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="03a54-164">Copier le fichier à partir d’une source distante (HTTP, HTTPS ou FTP)</span><span class="sxs-lookup"><span data-stu-id="03a54-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="03a54-165">Créez un fichier sur Linux avec le contenu de votre choix et effectuez une copie intermédiaire vers un serveur web ou FTP accessible aux nœuds que vous allez configurer.</span><span class="sxs-lookup"><span data-stu-id="03a54-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="03a54-166">Définissez la propriété **SourcePath** de la ressource **nxFile** sur l’URL web ou FTP du fichier.</span><span class="sxs-lookup"><span data-stu-id="03a54-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
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

1. <span data-ttu-id="03a54-167">Lire le contenu du fichier de script PowerShell avec [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) après avoir défini la propriété **$OFS** pour utiliser le caractère de saut de ligne Linux.</span><span class="sxs-lookup"><span data-stu-id="03a54-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
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

1. <span data-ttu-id="03a54-168">utiliser une fonction PowerShell pour remplacer les sauts de ligne Windows par des caractères de saut de ligne Linux.</span><span class="sxs-lookup"><span data-stu-id="03a54-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
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

## <a name="example"></a><span data-ttu-id="03a54-169">Exemple</span><span class="sxs-lookup"><span data-stu-id="03a54-169">Example</span></span>

<span data-ttu-id="03a54-170">L’exemple suivant vérifie que le répertoire `/opt/mydir` existe et qu’un fichier avec le contenu spécifié se trouve dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="03a54-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
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
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```