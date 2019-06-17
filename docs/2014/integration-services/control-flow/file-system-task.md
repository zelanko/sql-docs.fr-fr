---
title: Système de fichiers, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.f1
helpviewer_keywords:
- File System task [Integration Services]
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c9a2244c5e6cddbc53ccd3aaec7faaaa3836a923
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62831744"
---
# <a name="file-system-task"></a>Tâches du système de fichiers
  La tâche de système de fichiers effectue des opérations sur les fichiers et les répertoires du système de fichiers. Par exemple, à l'aide de la tâche de système de fichiers, un package peut créer, déplacer ou supprimer des répertoires et des fichiers. Vous pouvez également utiliser la tâche de système de fichiers pour définir les attributs des fichiers et des répertoires. Par exemple, la tâche de système de fichiers peut rendre les fichiers cachés ou accessibles en lecture seule.  
  
 Toutes les opérations de la tâche de système de fichiers utilisent une source, qui peut être un fichier ou un répertoire. Par exemple, le fichier que la tâche copie, ou le répertoire qu'elle supprime, est une source. La source peut être spécifiée à l'aide d'un gestionnaire de connexions de fichiers qui pointe vers le répertoire ou vers le fichier, ou à l'aide du nom d'une variable qui contient le chemin d'accès source. Pour plus d’informations, consultez [Gestionnaire de connexions de fichiers](../connection-manager/file-connection-manager.md) et [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
 Les opérations qui copient et déplacent les fichiers et les répertoires, et qui renomment les fichiers, utilisent une destination et une source. La destination est spécifiée à l'aide d'un gestionnaire de connexions de fichiers ou d'une variable. Les opérations de la tâche de système de fichiers peuvent être configurées afin de permettre le remplacement des fichiers et des répertoires de destination. L'opération de création d'un nouveau répertoire peut être configurée de manière à utiliser un répertoire existant portant le nom spécifié au lieu d'échouer si le répertoire existe déjà.  
  
## <a name="predefined-file-system-operations"></a>Opérations prédéfinies sur le système de fichiers  
 La tâche de système de fichiers comprend un ensemble prédéfini d'opérations. Le tableau suivant décrit ces opérations.  
  
|Opération|Description|  
|---------------|-----------------|  
|Copier le répertoire|Copie un dossier d'un emplacement à l'autre.|  
|Copier le fichier|Copie un fichier d'un emplacement à l'autre.|  
|Créer un répertoire|Crée un dossier à un emplacement spécifié.|  
|Supprimer le répertoire|Supprime un dossier à un emplacement spécifié.|  
|Supprimer le contenu du répertoire|Supprime la totalité des fichiers et des dossiers d'un dossier.|  
|Supprimer le fichier|Supprime un fichier à un emplacement spécifié.|  
|Déplacer le répertoire|Déplace un dossier d'un emplacement à l'autre.|  
|Déplacer le fichier|Déplace un fichier d'un emplacement à l'autre.|  
|Renommer le fichier|Renomme un fichier à un emplacement spécifié.|  
|Définir les attributs|Définit les attributs des fichiers et des dossiers. Les attributs sont Archive, Caché, Normal, Lecture seule et Système. L'option Normal indique l'absence d'attributs et ne peut pas être combinée avec les autres attributs. Vous pouvez combiner tous les autres attributs.|  
  
 La tâche de système de fichiers s'exécute sur un seul fichier ou répertoire. Cette tâche ne prend donc pas en charge l'utilisation de caractères génériques pour effectuer la même opération sur plusieurs fichiers. Pour que la tâche de système de fichiers répète une même opération sur plusieurs fichiers ou répertoires, mettez la tâche de système de fichiers dans un conteneur de boucles Foreach, comme décrit dans les étapes suivantes :  
  
-   **Configuration du conteneur de boucles Foreach** : dans la page **Collection** de l’Éditeur de boucle Foreach, définissez l’énumérateur sur **Énumérateur Foreach File** et entrez l’expression générique comme configuration d’énumérateur pour **Fichiers**. Dans la page **Mappage de variables** de l’Éditeur de boucle Foreach, mappez la variable que vous voulez utiliser pour transmettre un par un les noms de fichiers à la tâche de système de fichiers.  
  
-   **Ajout et configuration d’une tâche de système de fichiers** : ajoutez une tâche de système de fichiers au conteneur de boucles Foreach. Dans la page **Général** de l’Éditeur de tâche de système de fichiers, affectez à la propriété **SourceVariable** ou **DestinationVariable** la variable que vous avez définie dans le conteneur de boucles Foreach.  
  
## <a name="custom-log-entries-available-on-the-file-system-task"></a>Entrées de journal personnalisées disponibles dans la tâche de système de fichiers  
 Le tableau suivant décrit l'entrée de journal personnalisée pour la tâche de système de fichiers. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`FileSystemOperation`|Indique l'opération que la tâche effectue. L'entrée de journal est écrite au démarrage de l'opération du système de fichiers et inclut des informations sur la source et la destination.|  
  
## <a name="configuring-the-file-system-task"></a>Configuration de la tâche de système de fichiers  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez les rubriques suivantes :  
  
-   [Éditeur de tâche de système de fichiers &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d’informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, consultez la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## <a name="related-tasks"></a>Tâches associées  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend une tâche qui télécharge et charge les fichiers de données et gère les répertoires sur les serveurs. Pour plus d’informations, consultez [Tâche FTP](ftp-task.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  
