---
description: AffectEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d67a4916328d5d6d435da1b8080be42e52b35f67
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776648"
---
# <a name="affectenum"></a>AffectEnum
Spécifie les enregistrements qui sont affectés par une opération.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|Si aucun [filtre](./filter-property.md) n’est appliqué à l’ensemble **d'** enregistrements, affecte tous les enregistrements.<br /><br /> Si la propriété **Filter** est définie sur un critère de chaîne (par exemple, « Author = 'Smith »), l’opération affecte les enregistrements visibles dans le chapitre actuel.<br /><br /> Si la propriété **Filter** est définie sur un membre de la propriété [FilterGroupEnum](./filtergroupenum.md) ou sur un tableau de signets, l’opération affecte toutes les lignes de l’ensemble d' **enregistrements**. **Remarque : adAffectAll** est masqué dans l’Explorateur d’objets Visual Basic.|  
|**adAffectAllChapters**|4|Affecte tous les enregistrements dans tous les chapitres frères du **Recordset**, y compris ceux qui ne sont pas visibles via un **filtre** qui est actuellement appliqué.|  
|**adAffectCurrent**|1|Affecte uniquement l’enregistrement actif.|  
|**adAffectGroup**|2|Affecte uniquement les enregistrements qui répondent au paramètre de propriété de [filtre](./filter-property.md) actuel. Vous devez définir la propriété **Filter** sur une valeur **FilterGroupEnum** ou un tableau de **signets** pour utiliser cette option.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums. affecte. ALL|  
|AdoEnums. affecte. ALLCHAPTERS|  
|AdoEnums. affecte. CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [CancelBatch, méthode (ADO)](./cancelbatch-method-ado.md)  
        [Delete, méthode (objet Recordset ADO)](./delete-method-ado-recordset.md)  
    :::column-end:::
    :::column:::
        [Resync, méthode](./resync-method.md)  
        [UpdateBatch, méthode](./updatebatch-method.md)  
    :::column-end:::
:::row-end:::