---
title: "Télécharger des objets Blob Azure tâche | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/25/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpblobuptask.f1
- sql14.dts.designer.afpblobuptask.f1
ms.assetid: 6ea068b0-4cd8-45b5-b89d-09b8f25040c0
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cec51398ac521abc0345e90b3c6ed156b542b5f1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="azure-blob-upload-task"></a>Tâche de chargement d’objets blob Azure
La **tâche de chargement d’objets blob Azure** permet à un package SSIS de charger des fichiers sur un stockage d’objets blob Azure.
    
Pour ajouter une **tâche de chargement d’objets blob Azure**, faites-la glisser vers le concepteur SSIS, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue de **l’Éditeur de tâche de chargement d’objets blob Azure** .  
  
 Le **tâche de chargement d’objets Blob Azure** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
 Le tableau suivant décrit les champs de cette boîte de dialogue.  
  
|||  
|-|-|  
|**Champ**|**Description**|  
|AzureStorageConnection|Spécifiez un gestionnaire de connexions Azure Storage existant ou créez-en un qui fait référence à un compte Azure Storage et pointe vers l’emplacement où les fichiers d’objets blob sont hébergés.|  
|BlobContainer|Spécifie le nom du conteneur d’objet blob qui contient les fichiers téléchargés en tant qu’objets BLOB.|  
|BlobDirectory|Spécifie le répertoire d’objets blob où le fichier téléchargé est stocké en tant qu’objet blob de blocs. Le répertoire d’objets blob est une structure hiérarchique virtuelle. Si l’objet blob existe déjà, il est remplacé.|  
|LocalDirectory|Spécifie le répertoire local qui contient les fichiers à charger.|  
|FileName|Spécifie un filtre de nom pour sélectionner des fichiers avec le modèle de nom spécifié. Par exemple, `MySheet*.xls\*` inclut des fichiers tels que `MySheet001.xls` et `MySheetABC.xlsx`.|  
|TimeRangeFrom/TimeRangeTo|Spécifie un filtre d’intervalle de temps. Fichiers modifiés après **TimeRangeFrom** et avant **TimeRangeTo** sont inclus.|  
  
  

