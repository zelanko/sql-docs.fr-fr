---
title: "T&#226;che de t&#233;l&#233;chargement d’objet blob Azure | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpblobdltask.f1"
  - "sql14.dts.designer.afpblobdltask.f1"
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# T&#226;che de t&#233;l&#233;chargement d’objet blob Azure
  La tâche de téléchargement d’objet blob Azure permet à un package SSIS de télécharger des fichiers à partir d’un stockage d’objets blob Azure.

>   [!NOTE] Pour que le Gestionnaire de connexions Azure Storage et les composants qui l’utilisent, à savoir la source d’objet blob, la destination d’objet blob, la tâche de chargement d’objets blob et la tâche de téléchargement d’objets blob, puissent se connecter à la fois aux comptes de stockage à usage général et aux comptes de stockage d’objets blob, assurez-vous de télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). Pour plus d’informations sur ces deux types de comptes de stockage, consultez [Introduction à Microsoft Azure Storage](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts).
   
Pour ajouter une **tâche de téléchargement d’objet blob Azure**, faites-la glisser sur le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue **Éditeur de la tâche de téléchargement d’objet blob Azure**.  
  
 La **tâche de téléchargement d’objets blob Azure** est un composant de SQL Server Integration Services (SSIS) Feature Pack pour SQL Server 2016. Le Feature Pack est disponible en téléchargement [ici](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
 Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureStorageConnection|Spécifiez un gestionnaire de connexions Azure Storage existant ou créez-en un qui fait référence à un compte Azure Storage et pointe vers l’emplacement où les fichiers d’objets blob sont hébergés.|  
|BlobContainer|Spécifie le nom du conteneur d’objets blob qui contient les fichiers d’objets blob à télécharger.|  
|BlobDirectory|Spécifie le répertoire d’objets blob qui contient les fichiers d’objets blob à télécharger. Le répertoire d’objets blob est une structure hiérarchique virtuelle.|  
|LocalDirectory|Spécifie le répertoire local où les fichiers d’objets blob téléchargés seront stockés.|  
|FileName|Spécifie un filtre de nom pour sélectionner des fichiers avec le modèle de nom spécifié. Par ex. MySheet*.xls\* inclut les fichiers MySheet001.xls et MySheetABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Spécifie un filtre d’intervalle de temps. Les fichiers modifiés après **TimeRangeFrom** et avant **TimeRangeTo** seront inclus.|  
  
  