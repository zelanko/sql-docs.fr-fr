---
title: AffectEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: AffectEnum
helpviewer_keywords: AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f3378f54473498b1b1988f11868f5f21497a5309
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="affectenum"></a>AffectEnum
Spécifie quels enregistrements sont affectés par une opération.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|S’il n’est pas un [filtre](../../../ado/reference/ado-api/filter-property.md) appliquée à la **Recordset**, affecte tous les enregistrements.<br /><br /> Si le **filtre** est définie sur un critère de chaîne (tel que « auteur = 'Smith' »), l’opération affecte les enregistrements visibles dans le chapitre actuel.<br /><br /> Si le **filtre** est définie sur un membre de la [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) ou un tableau de signets, l’opération affectera toutes les lignes de la **Recordset**. **Remarque :****adAffectAll** est masqué dans l’Explorateur d’objets Visual Basic.|  
|**adAffectAllChapters**|4|Affecte tous les enregistrements dans tous les chapitres frère de la **Recordset**, y compris ceux non visibles par les **filtre** qui est actuellement appliqué.|  
|**adAffectCurrent**| 1|Affecte uniquement l’enregistrement actif.|  
|**adAffectGroup**|2|Affecte uniquement les enregistrements qui répondent aux actuel [filtre](../../../ado/reference/ado-api/filter-property.md) paramètre de propriété. Vous devez définir le **filtre** propriété un **FilterGroupEnum** valeur ou un tableau de **signets** pour utiliser cette option.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.Affect.ALL|  
|AdoEnums.Affect.ALLCHAPTERS|  
|AdoEnums.Affect.CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[CancelBatch, méthode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Resync, méthode](../../../ado/reference/ado-api/resync-method.md)|[UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)|
