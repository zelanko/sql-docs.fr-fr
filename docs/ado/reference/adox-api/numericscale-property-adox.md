---
title: NumericScale, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::PutNumericScale
- _Column::GetNumericScale
- _Column::NumericScale
- _Column::put_NumericScale
- _Column::get_NumericScale
helpviewer_keywords:
- NumericScale property [ADOX]
ms.assetid: 573ee5d1-57c7-4a27-be79-a0e12944ad9b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 16fdefcb06d2b1b90dfc3da39aaf6b1c9659debc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965749"
---
# <a name="numericscale-property-adox"></a>NumericScale, propriété (ADOX)
Indique l’échelle d’une valeur numérique dans la colonne.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et retourne une valeur d' **octet** qui est l’échelle des valeurs de données dans la colonne lorsque la propriété de [type](../../../ado/reference/adox-api/type-property-column-adox.md) est **adNumeric** ou **adDecimal**. **NumericScale** est ignoré pour tous les autres types de données.  
  
## <a name="remarks"></a>Notes  
 La valeur par défaut est zéro (0).  
  
 **NumericScale** est en lecture seule pour les objets de [colonne](../../../ado/reference/adox-api/column-object-adox.md) déjà ajoutés à une collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de code ADOX : NumericScale et Precision, exemple de propriétés (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type, propriété (colonne) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
