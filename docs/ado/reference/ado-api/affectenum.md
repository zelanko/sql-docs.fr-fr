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
ms.openlocfilehash: a936eb39583afff34dd317b85bc4198022b15e7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920758"
---
# <a name="affectenum"></a>AffectEnum
Spécifie les enregistrements qui sont affectés par une opération.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Si aucun [filtre](../../../ado/reference/ado-api/filter-property.md) n’est appliqué à l’ensemble **d'** enregistrements, affecte tous les enregistrements.<br /><br /> Si la propriété **Filter** est définie sur un critère de chaîne (par exemple, « Author = 'Smith »), l’opération affecte les enregistrements visibles dans le chapitre actuel.<br /><br /> Si la propriété **Filter** est définie sur un membre de la propriété [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) ou sur un tableau de signets, l’opération affecte toutes les lignes de l’ensemble d' **enregistrements**. **Remarque : adAffectAll** est masqué dans l’Explorateur d’objets Visual Basic.|  
|**adAffectAllChapters**|4|Affecte tous les enregistrements dans tous les chapitres frères du **Recordset**, y compris ceux qui ne sont pas visibles via un **filtre** qui est actuellement appliqué.|  
|**adAffectCurrent**|1|Affecte uniquement l’enregistrement actif.|  
|**adAffectGroup**|2|Affecte uniquement les enregistrements qui répondent au paramètre de propriété de [filtre](../../../ado/reference/ado-api/filter-property.md) actuel. Vous devez définir la propriété **Filter** sur une valeur **FilterGroupEnum** ou un tableau de **signets** pour utiliser cette option.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums. affecte. ALL|  
|AdoEnums. affecte. ALLCHAPTERS|  
|AdoEnums. affecte. CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[CancelBatch, méthode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Resync, méthode](../../../ado/reference/ado-api/resync-method.md)|[UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)|
