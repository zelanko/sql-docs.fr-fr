---
description: NumericScale, propriété (ADOX)
title: NumericScale, propriété (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 161b6049ca5392eafacaf0fd97db653070f105e0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983890"
---
# <a name="numericscale-property-adox"></a>NumericScale, propriété (ADOX)
Indique l’échelle d’une valeur numérique dans la colonne.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et retourne une valeur d' **octet** qui est l’échelle des valeurs de données dans la colonne lorsque la propriété de [type](./type-property-column-adox.md) est **adNumeric** ou **adDecimal**. **NumericScale** est ignoré pour tous les autres types de données.  
  
## <a name="remarks"></a>Notes  
 La valeur par défaut est zéro (0).  
  
 **NumericScale** est en lecture seule pour les objets de [colonne](./column-object-adox.md) déjà ajoutés à une collection.  
  
## <a name="applies-to"></a>S'applique à  
 [Column, objet (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de code ADOX : NumericScale et Precision, exemple de propriétés (VB)](./adox-code-example-numericscale-and-precision-properties-example-vb.md)   
 [Type, propriété (colonne) (ADOX)](./type-property-column-adox.md)