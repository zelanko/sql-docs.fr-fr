---
title: "T&#226;che de chargement d’objets blob Azure | Microsoft Docs"
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
  - "sql13.dts.designer.afpblobuptask.f1"
  - "sql14.dts.designer.afpblobuptask.f1"
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# T&#226;che de chargement d’objets blob Azure
  La **tâche de chargement d’objets blob Azure** permet à un package SSIS de charger des fichiers sur un stockage d’objets blob Azure.
  
>   [!NOTE] Pour que le Gestionnaire de connexions Azure Storage et les composants qui l’utilisent, à savoir la source d’objet blob, la destination d’objet blob, la tâche de chargement d’objets blob et la tâche de téléchargement d’objets blob, puissent se connecter à la fois aux comptes de stockage à usage général et aux comptes de stockage d’objets blob, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). Pour plus d’informations sur ces deux types de comptes de stockage, consultez [Introduction à Microsoft Azure Storage](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts). 
    
Pour ajouter une **tâche de chargement d’objets blob Azure**, faites-la glisser vers le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue de **l’Éditeur de tâche de chargement d’objets blob Azure**.  
  
 La **tâche de chargement d’objets blob Azure** est un composant de SQL Server Integration Services (SSIS) Feature Pack pour Azure pour SQL Server 2016. Le Feature Pack est disponible en téléchargement [ici](http://go.microsoft.com/fwlink/?LinkID=626967).  
  
 Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureStorageConnection|Spécifiez un gestionnaire de connexions Azure Storage existant ou créez-en un qui fait référence à un compte Azure Storage et pointe vers l’emplacement où les fichiers d’objets blob sont hébergés.|  
|BlobContainer|Spécifie le nom du conteneur d’objets blob qui contiendra les fichiers chargés en tant qu’objets blob.|  
|BlobDirectory|Spécifie le répertoire d’objets blob dans lequel le fichier chargé sera stocké en tant qu’objet blob de bloc. Le répertoire d’objets blob est une structure hiérarchique virtuelle. Si l’objet blob existe déjà, il sera remplacé.|  
|LocalDirectory|Spécifie le répertoire local qui contient les fichiers à charger.|  
|FileName|Spécifie un filtre de nom pour sélectionner des fichiers avec le modèle de nom spécifié. Par ex. MaFeuille*.xls\* comprend des fichiers, tels que MaFeuille001.xls et MaFeuilleABC.xlsx.|  
|TimeRangeFrom/TimeRangeTo|Spécifie un filtre d’intervalle de temps. Les fichiers modifiés après **TimeRangeFrom** et avant **TimeRangeTo** sont inclus.|  
  
  