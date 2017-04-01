---
title: "&#201;diteur de t&#226;che de syst&#232;me de fichiers (page G&#233;n&#233;ral) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.filesystemtask.general.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de système de fichiers"
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# &#201;diteur de t&#226;che de syst&#232;me de fichiers (page G&#233;n&#233;ral)
  Utilisez la page **Général** de l' **Éditeur de tâche de système de fichiers** pour configurer l'opération de système de fichiers qu'exécute la tâche.  
  
 Pour en savoir plus sur cette tâche, consultez [File System Task](../../integration-services/control-flow/file-system-task.md).  
  
 Vous devez spécifier un gestionnaire de connexions source et de destination en définissant les propriétés SourceConnection et DestinationConnection. Vous pouvez fournir les noms de gestionnaires de connexions de fichiers qui pointent sur les fichiers utilisés par la tâche comme source ou destination. Si les chemins de fichiers sont stockés dans des variables, vous pouvez également fournir le nom des variables. Pour utiliser des variables afin de stocker les chemins des fichiers, vous devez d’abord définir l’option IsSourcePathVariable de la connexion source et l’option IsDestinationPatheVariable de la connexion de destination sur **True**. Ensuite, vous pouvez créer de nouvelles variables ou choisir les variables existantes, système ou définies par l'utilisateur, à utiliser. Dans la boîte de dialogue **Ajouter une variable** , vous pouvez configurer et spécifier l'étendue des variables. L'étendue doit être la tâche de système de fichiers ou un conteneur parent. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md).  
  
> [!NOTE]  
>  Pour remplacer les variables sélectionnées pour les propriétés **SourceConnection** et **DestinationConnection** , entrez une expression pour les propriétés **Source** et **Destination** . Vous entrez les expressions sur la page **Expressions** de l' **Éditeur de tâche de système de fichiers**. Par exemple, pour définir le chemin d'accès des fichiers utilisés comme destination par la tâche, vous pouvez utiliser la variable A dans certaines conditions et la variables B dans d'autres conditions.  
  
> [!NOTE]  
>  La tâche de système de fichiers s'exécute sur un seul fichier ou répertoire. Cette tâche ne prend donc pas en charge l'utilisation de caractères génériques pour effectuer la même opération sur plusieurs fichiers ou répertoires. Pour que la tâche de système de fichiers répète une même opération sur plusieurs fichiers ou répertoires, placez-la dans un conteneur de boucles Foreach. Pour plus d’informations, consultez [File System Task](../../integration-services/control-flow/file-system-task.md).  
  
 Vous pouvez utiliser des expressions pour recourir à différentes variables.  
  
## Options  
 **IsDestinationPathVariable**  
 Indique si le chemin d'accès de destination est stocké dans une variable. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Le chemin d'accès de destination est stocké dans une variable. Cette valeur affiche l'option dynamique **DestinationVariable**.|  
|**False**|Le chemin d'accès de destination est défini dans un gestionnaire de connexions de fichiers. Cette valeur affiche l'option dynamique **DestinationConnection**.|  
  
 **OverwriteDestination**  
 Indiquez si l'opération peut remplacer les fichiers dans le répertoire de destination.  
  
 **Nom**  
 Fournissez un nom unique pour la tâche de système de fichiers. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Tapez la description de la tâche de système de fichiers.  
  
 **Opération**  
 Sélectionnez l'opération de système de fichiers à exécuter. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Copier le répertoire**|Copier un répertoire. Cette valeur affiche les options dynamiques d'une source et d'une destination.|  
|**Copier le fichier**|Copier un fichier. Cette valeur affiche les options dynamiques d'une source et d'une destination.|  
|**Créer un répertoire**|Créer un répertoire. Cette valeur affiche les options dynamiques d'un répertoire source et de destination.|  
|**Supprimer le répertoire**|Supprimer un répertoire. Cette valeur affiche les options dynamiques d'une source.|  
|**Supprimer le contenu du répertoire**|Supprimer le contenu d'un répertoire. Cette valeur affiche les options dynamiques d'une source.|  
|**Supprimer le fichier**|Supprimer un fichier. Cette valeur affiche les options dynamiques d'une source.|  
|**Déplacer le répertoire**|Déplacer un répertoire. Cette valeur affiche les options dynamiques d'une source et d'une destination.|  
|**Déplacer le fichier**|Déplacer un fichier. Cette valeur affiche les options dynamiques d'une source et d'une destination. Lorsque vous déplacez un fichier, n'incluez pas de nom de fichier dans le chemin d'accès au répertoire que vous fournissez comme destination.|  
|**Renommer le fichier**|Renommer un fichier. Cette valeur affiche les options dynamiques d'une source et d'une destination. Lorsque vous renommez un fichier, incluez le nouveau nom de fichier dans le chemin d'accès au répertoire que vous fournissez comme destination.|  
|**Définir les attributs**|Définir les attributs d'un fichier ou d'un répertoire. Cette valeur affiche les options dynamiques d'une source et d'une opération.|  
  
 **IsSourcePathVariable**  
 Indique si le chemin d'accès de destination est stocké dans une variable. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value||  
|-----------|-|  
|**True**|Le chemin d'accès de destination est stocké dans une variable. Sélectionnez cette valeur pour afficher l'option dynamique **SourceVariable**.|  
|**False**|Le chemin d'accès de destination est défini dans un gestionnaire de connexions de fichiers. Cette valeur affiche l'option dynamique **DestinationVariable**.|  
  
## Options dynamiques IsDestinationPathVariable  
  
### IsDestinationPathVariable = True  
 **DestinationVariable**  
 Sélectionnez le nom de variable dans la liste ou cliquez sur \<**Nouvelle variable...**> pour créer une variable.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](../Topic/Add%20Variable.md)  
  
### IsDestinationPathVariable = False  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## Options dynamiques IsSourcePathVariable  
  
### IsSourcePathVariable = True  
 **SourceVariable**  
 Sélectionnez le nom de variable dans la liste ou cliquez sur \<**Nouvelle variable...**> pour créer une variable.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](../Topic/Add%20Variable.md)  
  
### IsSourcePathVariable = False  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## Options dynamiques d'opération  
  
### Opération = Définir les attributs  
 **Hidden**  
 Indique si le fichier ou le répertoire est visible.  
  
 **En lecture seule**  
 Indique si le fichier est en lecture seule.  
  
 **Archive**  
 Indique si le fichier ou le répertoire est prêt pour l'archivage.  
  
 **Système**  
 Indique si le fichier est un fichier de système d'exploitation.  
  
### Opération = Créer un répertoire  
 **UseDirectoryIfExists**  
 Indique si l’option **Créer un répertoire** utilise un répertoire existant portant le nom spécifié au lieu de créer un nouveau répertoire.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  