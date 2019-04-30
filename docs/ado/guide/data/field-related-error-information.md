---
title: Informations sur les erreurs liées aux champs | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- field-related errors [ADO]
- errors [ADO], field-related
ms.assetid: 5e7b1af4-996b-47c5-9161-c5575ad4fec9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2ba956d2e442c914ddc50f2f023f225252fb1295
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161568"
---
# <a name="field-related-error-information"></a>Informations sur les erreurs liées aux champs
Si une erreur est directement liée à un champ, par exemple, si les données sont manquantes ou si elle est de type incorrect pour le champ - vous pouvez récupérer plus d’informations sur la cause du problème en examinant le **champ** l’objet **état**  propriété. Cette propriété a été améliorée pour fournir des informations spécifiques sur le problème. Ainsi, par exemple, lorsqu’un appel à **UpdateBatch** échoue, la cause du problème peut être déterminé en examinant la **état** propriété de la **champs** dans chacune du concernés enregistrements. La propriété contient une des valeurs dans le **FieldStatusEnum** constante. Le tableau suivant contient les valeurs qui sont particulièrement intéressants lorsqu’une erreur se produit.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|Indique que le champ ne peut pas être récupéré ou stocké sans perte de données.|  
|**adFieldDataOverflow**|6|Indique que les données retournées par le fournisseur a dépassé le type de données du champ.|  
|**adFieldDefault**|13|Indique que la valeur par défaut pour le champ a été utilisée lors de la définition de données.|  
|**adFieldIgnore**|15|Indique que ce champ a été ignoré lorsque les valeurs de données de paramètre dans la source. Aucune valeur n’a été définie par le fournisseur.|  
|**adFieldIntegrityViolation**|10|Indique que le champ ne peut pas être modifié car il s’agit d’une entité calculée ou dérivée.|  
|**adFieldIsNull**|3|Indique que le fournisseur a retourné une valeur null.|  
|**adFieldOutOfSpace**|22|Indique que le fournisseur est impossible d’obtenir un espace de stockage suffisant pour terminer un déplacement ou de l’opération de copie.|
