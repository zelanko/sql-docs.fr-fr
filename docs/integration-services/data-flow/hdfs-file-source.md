---
title: "HDFS File Source | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.hdfsfilesrc.f1"
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# HDFS File Source
  Le composant HDFS File Source permet à un package SSIS de lire les données provenant d’un fichier HDFS. Les formats de fichier pris en charge sont le format texte et Avro. (Les sources ORC ne sont pas prises en charge.)  
  
 Pour configurer HDFS File Source, opérez un glisser-déplacer de HDFS File Source vers le concepteur de flux de données, puis double-cliquez sur le composant pour ouvrir l’éditeur.  
  
 ![HDFS File Source Editor](../../integration-services/data-flow/media/hdfs-file-source.png "HDFS File Source Editor")  
  
## Options  
 Configurez les options suivantes sur l’onglet **Général** de la boîte de dialogue **Hadoop File Source Editor** .  
  
|Champ|Description|  
|-----------|-----------------|  
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où se trouvent les fichiers HDFS.|  
|**Chemin d'accès au fichier**|Spécifiez le nom du fichier HDFS.|  
|**Format du fichier**|Spécifiez le format du fichier HDFS. Les options disponibles sont Texte et Avro. (Les sources ORC ne sont pas prises en charge.)|  
|**Caractère séparateur de colonnes**|Si vous avez sélectionné le format Texte, spécifiez le caractère délimiteur de colonne.|  
|**Noms de colonnes dans la première ligne de données**|Si vous avez sélectionné le format Texte, indiquez si la première ligne du fichier contient les noms de colonnes.|  
  
 Après avoir configuré ces options, sélectionnez l’onglet **Colonnes** pour mapper les colonnes source aux colonnes de destination dans le flux de données.  
  
## Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [HDFS File Destination](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  