---
title: AllowNullsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 53fadcddd49ebf68949da0a7dca3cb37da0b5d93
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66708603"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Spécifie si les enregistrements avec des valeurs null sont indexés.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|L’index n’autorise pas les entrées dans lequel les colonnes clés sont null. Si une valeur null est entrée dans une colonne clé, l’entrée est insérée dans l’index.|  
|**adIndexNullsDisallow**|1|Valeur par défaut. L’index n’autorise pas les entrées dans lequel les colonnes clés sont null. Si une valeur null est entrée dans une colonne clé, une erreur se produit.|  
|**adIndexNullsIgnore**|2|L’index n’insère pas les entrées contenant des clés null. Si une valeur null est entrée dans une colonne clé, l’entrée est ignorée et aucune erreur ne se produit.|  
|**adIndexNullsIgnoreAny**|4|L’index n’insère pas d’entrées où une colonne clé contient une valeur null. Pour un index ayant un plusieurs colonnes clés, si une valeur null est entrée dans une colonne, l’entrée est ignorée et aucune erreur ne se produit.|  
  
## <a name="applies-to"></a>S'applique à  
 [IndexNulls, propriété (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
