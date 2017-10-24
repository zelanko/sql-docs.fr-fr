---
title: ADCPROP_UPDATECRITERIA_ENUM | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 730a97c27d4aa57632ecf14b0f5cbddffb689d70
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="adcpropupdatecriteriaenum"></a>ADCPROP_UPDATECRITERIA_ENUM
Spécifie les champs qui peuvent être utilisés pour détecter les conflits pendant une mise à jour optimiste d’une ligne de la source de données avec un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
 Utilisez ces constantes avec la **Recordset** »**les critères de mise à jour**« propriété dynamique, qui est référencée dans le [Index des propriétés dynamiques ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) et documentées dans les [ Le Service de curseur Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) documentation.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adCriteriaAllCols**|1|Détecte les conflits si n’importe quelle colonne de la ligne de source de données a été modifiée.|  
|**adCriteriaKey**|0|Détecte les conflits si la ligne de source de la colonne de clé des données a été modifié, ce qui signifie que la ligne a été supprimée.|  
|**adCriteriaTimeStamp**|3|Détecte les conflits si l’horodatage des données de ligne source a été modifié, ce qui signifie que la ligne a été accédée après le **Recordset** a été obtenu.|  
|**adCriteriaUpdCols**|2|Détecte les conflits si les colonnes de la source de données de ligne qui correspondent aux champs mis à jour de la **Recordset** ont été modifiés.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums.AdcPropUpdateCriteria.KEY|  
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP|  
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS|

