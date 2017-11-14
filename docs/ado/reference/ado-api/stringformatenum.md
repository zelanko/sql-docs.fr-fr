---
title: StringFormatEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 86a1f884f237596895dce6671d3dc42fb6461b1e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="stringformatenum"></a>StringFormatEnum
Spécifie le format lors de la récupération une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sous forme de chaîne.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Délimite les lignes par *RowDelimiter*, les colonnes par *ColumnDelimiter*et les valeurs par null *NullExpr*. Ces trois paramètres de la [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) méthode sont valides uniquement avec un *StringFormat* de **adClipString**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>S'applique à  
 [GetString, méthode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)

