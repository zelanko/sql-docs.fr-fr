---
title: "Tâche de système de fichiers Hadoop | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hadoopfiletask.f1
ms.assetid: 594aaf5d-7703-4788-897d-fb95aca798c5
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e86c35bf891b0e83a74c6e9b7cd30295b5e52d5f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="hadoop-file-system-task"></a>Tâche du système de fichiers Hadoop
  Une tâche du système de fichiers Hadoop permet à un package SSIS de copier des fichiers à partir d’un cluster Hadoop, vers un cluster Hadoop ou au sein d’un cluster Hadoop.  
  
 Pour ajouter une tâche du système de fichiers Hadoop, opérez un glisser-déplacer de cette tâche vers le concepteur. Double-cliquez ensuite sur la tâche ou cliquez avec le bouton droit et sélectionnez **Modifier**pour ouvrir la boîte de dialogue **Éditeur de tâches du système de fichiers Hadoop** .  
  
 ![Éditeur de tâches du système de fichiers Hadoop](../../integration-services/control-flow/media/hadoop-filesystem-task.png "Éditeur de tâches du système de fichiers Hadoop")  
  
## <a name="options"></a>Options  
 Configurez les options suivantes dans la boîte de dialogue **Éditeur de tâches du système de fichiers Hadoop** .  
  
|Champ|Description|  
|-----------|-----------------|  
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où se trouvent les fichiers de destination.|  
|**Chemin de fichier Hadoop**|Spécifiez le chemin d’accès du fichier ou du répertoire sur HDFS.|  
|**Type de fichier Hadoop**|Spécifiez si l’objet du système de fichiers HDFS est un fichier ou un répertoire.|  
|**Remplacer la destination**|Spécifiez s’il faut remplacer le fichier cible le cas échéant.|  
|**Opération**|Spécifiez l’opération. Les opérations disponibles sont **CopyToHDFS**, **CopyFromHDFS**et **CopyWithinHDFS**.|  
|**Connexion de fichiers locaux**|Spécifiez un gestionnaire de connexions de fichiers existant ou créez-en un. Ce gestionnaire de connexions indique où se trouvent les fichiers source.|  
|**Est récursif**|Indiquez si vous souhaitez copier tous les sous-dossiers de manière récursive.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager.md)  
  
  

