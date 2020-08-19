---
description: ADCPROP_UPDATECRITERIA_ENUM
title: ADCPROP_UPDATECRITERIA_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
author: rothja
ms.author: jroth
ms.openlocfilehash: 31205bbe32dd3c09d70fe4baeb41261be985096c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451601"
---
# <a name="adcprop_updatecriteria_enum"></a>ADCPROP_UPDATECRITERIA_ENUM
Spécifie les champs qui peuvent être utilisés pour détecter les conflits pendant une mise à jour optimiste d’une ligne de la source de données avec un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
 Utilisez ces constantes avec la propriété dynamique «**critères de mise à jour**» du **jeu d’enregistrements** , qui est référencée dans l' [index de propriété dynamique ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) et documentée dans la documentation du [service de curseur Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) .  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adCriteriaAllCols**|1|Détecte les conflits si une colonne de la ligne de la source de données a été modifiée.|  
|**adCriteriaKey**|0|Détecte les conflits si la colonne clé de la ligne de la source de données a été modifiée, ce qui signifie que la ligne a été supprimée.|  
|**adCriteriaTimeStamp**|3|Détecte les conflits si l’horodateur de la ligne de la source de données a été modifié, ce qui signifie que la ligne a fait l’objet d’un accès après l’obtention du **Recordset** .|  
|**adCriteriaUpdCols**|2|Détecte les conflits si des colonnes de la ligne de source de données qui correspondent à des champs mis à jour du **Recordset** ont été modifiées.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums. AdcPropUpdateCriteria. KEY|  
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP|  
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS|
