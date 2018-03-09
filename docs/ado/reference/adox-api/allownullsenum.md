---
title: AllowNullsEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- AllowNullsEnum
helpviewer_keywords:
- AllowNullsEnum enumeration [ADOX]
ms.assetid: 6acf3689-1a7f-4379-9d7f-df452ccbac27
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75bb6aa82ec26e74675a2ccf6ff803abd9d24f6c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="allownullsenum"></a>AllowNullsEnum
Spécifie si les enregistrements avec des valeurs null sont indexés.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|L’index autorise les entrées dans lesquelles les colonnes clés sont null. Si une valeur null est entrée dans une colonne clé, l’entrée est insérée dans l’index.|  
|**adIndexNullsDisallow**|1|Valeur par défaut. L’index n’autorise pas les entrées dans lesquelles les colonnes clés sont null. Si une valeur null est entrée dans une colonne clé, une erreur se produit.|  
|**adIndexNullsIgnore**|2|L’index n’insère pas les entrées contenant des clés null. Si une valeur null est entrée dans une colonne clé, l’entrée est ignorée et aucune erreur ne se produit.|  
|**adIndexNullsIgnoreAny**|4|L’index n’insère pas d’entrée où une colonne clé a la valeur null. Un index possédant un plusieurs colonnes clés, si une valeur null est entrée dans une colonne, l’entrée est ignorée et aucune erreur ne se produit.|  
  
## <a name="applies-to"></a>S'applique à  
 [IndexNulls, propriété (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
