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
ms.openlocfilehash: 7094c2dba004e35593f5ab11b1162efbdf3283c1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925313"
---
# <a name="field-related-error-information"></a>Informations sur les erreurs liées aux champs
Si une erreur est directement liée à un champ (par exemple, si les données sont manquantes ou si le type est incorrect pour le champ), vous pouvez récupérer des informations supplémentaires sur la cause du problème en examinant la propriété **Status** de l’objet **Field** . Cette propriété a été améliorée pour fournir des informations spécifiques sur le problème. Ainsi, par exemple, lorsqu’un appel à **UpdateBatch** échoue, la cause du problème peut être déterminée en examinant la propriété **Status** des **champs** de chacun des enregistrements concernés. La propriété contient l’une des valeurs de la constante **FieldStatusEnum** . Le tableau suivant répertorie les valeurs qui présentent un intérêt particulier lorsqu’une erreur se produit.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adFieldCantConvertValue**|2|Indique que le champ ne peut pas être récupéré ou stocké sans perte de données.|  
|**adFieldDataOverflow**|6|Indique que les données retournées par le fournisseur ont débordé le type de données du champ.|  
|**adFieldDefault**|13|Indique que la valeur par défaut du champ a été utilisée lors de la définition des données.|  
|**adFieldIgnore**|15|Indique que ce champ a été ignoré lors de la définition des valeurs de données dans la source. Aucune valeur n’a été définie par le fournisseur.|  
|**adFieldIntegrityViolation**|10|Indique que le champ ne peut pas être modifié, car il s’agit d’une entité calculée ou dérivée.|  
|**adFieldIsNull**|3|Indique que le fournisseur a retourné une valeur null.|  
|**adFieldOutOfSpace**|22|Indique que le fournisseur ne peut pas obtenir suffisamment d’espace de stockage pour effectuer une opération de déplacement ou de copie.|
