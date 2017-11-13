---
title: "Informations sur l’erreur champ | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3a7609b4c4a0d67f1bade86c2e6ec3bb66b07553
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="field-related-error-information"></a>Informations sur l’erreur de champ
Si une erreur est directement liée à un champ, par exemple, si les données sont manquantes ou si elle est de type incorrect pour le champ, vous pouvez récupérer plus d’informations sur la cause du problème en examinant la **champ** l’objet **état**  propriété. Cette propriété a été améliorée pour fournir des informations spécifiques sur le problème. Ainsi, par exemple, lorsqu’un appel à **UpdateBatch** échoue, la cause du problème peut être déterminée en examinant le **état** propriété de la **champs** dans chacun du concernés enregistrements. La propriété contient une des valeurs dans le **FieldStatusEnum** constante. Le tableau suivant contient les valeurs qui présentent un intérêt particulier lorsqu’une erreur se produit.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|Indique que le champ ne peut pas être extraites ou stocké sans perte de données.|  
|**adFieldDataOverflow**|6|Indique que les données renvoyées par le fournisseur a dépassé le type de données du champ.|  
|**adFieldDefault**|13|Indique que la valeur par défaut pour le champ a été utilisée lors de la définition de données.|  
|**adFieldIgnore**|15|Indique que ce champ a été ignoré lorsque les valeurs de données de paramètre dans la source. Aucune valeur n’a été définie par le fournisseur.|  
|**adFieldIntegrityViolation**|10|Indique que le champ ne peut pas être modifié car il s’agit d’une entité calculée ou dérivée.|  
|**adFieldIsNull**|3|Indique que le fournisseur a retourné une valeur null.|  
|**adFieldOutOfSpace**|22|Indique que le fournisseur est impossible d’obtenir un espace de stockage suffisant pour terminer un déplacement ou de l’opération de copie.|

