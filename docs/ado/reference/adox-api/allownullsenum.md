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
ms.openlocfilehash: 48e9d8c40d2ab76b902d285526fcd9e9abf7be07
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67967336"
---
# <a name="allownullsenum"></a>AllowNullsEnum
Spécifie si les enregistrements avec des valeurs NULL sont indexés.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adIndexNullsAllow**|0|L’index autorise les entrées dans lesquelles les colonnes clés ont la valeur null. Si une valeur null est entrée dans une colonne clé, l’entrée est insérée dans l’index.|  
|**adIndexNullsDisallow**|1|Par défaut. L’index n’autorise pas les entrées dans lesquelles les colonnes clés ont la valeur null. Si vous entrez une valeur null dans une colonne clé, une erreur se produit.|  
|**adIndexNullsIgnore**|2|L’index n’insère pas d’entrées contenant des clés NULL. Si une valeur null est entrée dans une colonne clé, l’entrée est ignorée et aucune erreur ne se produit.|  
|**adIndexNullsIgnoreAny**|4|L’index n’insère pas d’entrées pour lesquelles une colonne clé a une valeur null. Pour un index ayant une clé à plusieurs colonnes, si une valeur null est entrée dans une colonne, l’entrée est ignorée et aucune erreur ne se produit.|  
  
## <a name="applies-to"></a>S'applique à  
 [IndexNulls, propriété (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
