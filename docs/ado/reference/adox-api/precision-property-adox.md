---
title: Precision, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::put_Precision
- _Column::PutPrecision
- _Column::GetPrecision
- _Column::get_Precision
- _Column::Precision
helpviewer_keywords:
- Precision property [ADOX]
ms.assetid: 0e0ecbbf-d7de-49d4-a128-5a519ecd54ba
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d1416842f3c122e9e5e5e28b8a14310b679697cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965564"
---
# <a name="precision-property-adox"></a>Precision, propriété (ADOX)
Indique la précision maximale des valeurs de données dans la [colonne](../../../ado/reference/adox-api/column-object-adox.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et retourne une valeur de type **long** qui correspond à la précision maximale des valeurs de données dans la colonne lorsque la propriété de [type](../../../ado/reference/adox-api/type-property-column-adox.md) est un type numérique. La **précision** est ignorée pour tous les autres types de données.  
  
## <a name="remarks"></a>Notes  
 La valeur par défaut est zéro (**0**).  
  
 Cette propriété est en lecture seule pour les objets de [colonne](../../../ado/reference/adox-api/column-object-adox.md) déjà ajoutés à une collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de code ADOX : NumericScale et Precision, exemple de propriétés (VB)](../../../ado/reference/adox-api/adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type, propriété (Column) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)   
 [Column, objet (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)
