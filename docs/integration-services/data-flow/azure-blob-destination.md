---
title: "Destination d’objets Blob Azure | Documents Microsoft"
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
- sql13.dts.designer.afpblobdest.f1
- sql14.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 152d92859c2f4ce96d0cc1ba9b02ffb412d18fde
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="azure-blob-destination"></a>Destination d’objet blob Azure
 Le composant **Destination d’objet blob Azure** permet à un package SSIS d’écrire des données dans un objet blob Azure. Les formats de fichier pris en charge sont CSV et AVRO. 
   
 Faites glisser le composant **Destination d’objet blob Azure** vers le concepteur de flux de données et double-cliquez dessus pour visualiser l’éditeur.  
  
 Le **Azure Blob Destination** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
1.  Dans le champ **Gestionnaire de connexions Azure Storage** , spécifiez un gestionnaire de connexions Azure Storage existant ou créez-en un qui fera référence à un compte Azure Storage.  
  
2.  Dans le champ **Nom du conteneur d’objets blob** , spécifiez le nom du conteneur d’objets blob qui contient les fichiers sources.  
  
3.  Dans le champ **Nom de l’objet blob** , indiquez le chemin d’accès à l’objet blob.  
  
4.  Dans le champ **Format de fichier d’objet blob** , spécifiez le format d’objet blob à utiliser.  
  
5.  Si le format de fichier est CSV, vous devez renseigner le champ **Caractère séparateur de colonnes** . Sélectionnez également l’option **Noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonne.  
  
6.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination pour le flux de données SSIS.  
  
  

