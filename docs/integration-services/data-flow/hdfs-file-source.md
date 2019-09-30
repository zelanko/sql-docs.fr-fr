---
title: Source de fichier HDFS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfilesrc.f1
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a06374e2803a5e482e6d5a7a665756e38cb7f2f
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71292447"
---
# <a name="hdfs-file-source"></a>HDFS File Source

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Le composant HDFS File Source permet à un package SSIS de lire les données provenant d’un fichier HDFS. Les formats de fichier pris en charge sont le format texte et Avro. (Les sources ORC ne sont pas prises en charge.)  
  
 Pour configurer HDFS File Source, opérez un glisser-déplacer de HDFS File Source vers le concepteur de flux de données, puis double-cliquez sur le composant pour ouvrir l’éditeur.  
  
 ![Éditeur de la source du fichier HDFS](../../integration-services/data-flow/media/hdfs-file-source.png "Éditeur de la source du fichier HDFS")  
  
## <a name="options"></a>Options  
 Configurez les options suivantes sur l’onglet **Général** de la boîte de dialogue **Hadoop File Source Editor** .  
  
|Champ|Description|  
|-----------|-----------------|  
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où se trouvent les fichiers HDFS.|  
|**Chemin d'accès au fichier**|Spécifiez le nom du fichier HDFS.|  
|**Format du fichier**|Spécifiez le format du fichier HDFS. Les options disponibles sont Texte et Avro. (Les sources ORC ne sont pas prises en charge.)|  
|**Caractère séparateur de colonnes**|Si vous avez sélectionné le format Texte, spécifiez le caractère délimiteur de colonne.|  
|**Noms de colonnes dans la première ligne de données**|Si vous avez sélectionné le format Texte, indiquez si la première ligne du fichier contient les noms de colonnes.|  
  
 Après avoir configuré ces options, sélectionnez l’onglet **Colonnes** pour mapper les colonnes source aux colonnes de destination dans le flux de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [HDFS File Destination](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  
