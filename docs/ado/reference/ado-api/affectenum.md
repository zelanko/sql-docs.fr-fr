---
title: AffectEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d6ff6704ca12fbb20c93133d7e73f29a5f72c9e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696573"
---
# <a name="affectenum"></a>AffectEnum
Spécifie les enregistrements affectés par une opération.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|S’il n’est pas un [filtre](../../../ado/reference/ado-api/filter-property.md) appliqué à la **Recordset**, affecte tous les enregistrements.<br /><br /> Si le **filtre** propriété est définie sur un critère de chaîne (tel que « auteur = 'Smith' »), l’opération affecte les enregistrements visibles dans le chapitre actuel.<br /><br /> Si le **filtre** propriété est définie à un membre de la [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) ou un tableau de signets, l’opération affectera toutes les lignes de la **Recordset**. **Remarque : adAffectAll** est masqué dans l’Explorateur d’objets Visual Basic.|  
|**adAffectAllChapters**|4|Affecte tous les enregistrements dans tous les chapitres frère de la **Recordset**, y compris ceux non visibles par les **filtre** qui est actuellement appliqué.|  
|**adAffectCurrent**|1|Affecte uniquement l’enregistrement actif.|  
|**adAffectGroup**|2|Affecte uniquement les enregistrements qui répondent à des cours [filtre](../../../ado/reference/ado-api/filter-property.md) paramètre de propriété. Vous devez définir le **filtre** propriété à un **FilterGroupEnum** valeur ou un tableau de **signets** pour utiliser cette option.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
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
