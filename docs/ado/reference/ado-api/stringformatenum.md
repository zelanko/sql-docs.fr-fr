---
title: StringFormatEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: StringFormatEnum
helpviewer_keywords: StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e2d5b9159798855e75217f105122025092e25c06
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="stringformatenum"></a>StringFormatEnum
Spécifie le format lors de la récupération une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sous forme de chaîne.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|Délimite les lignes par *RowDelimiter*, les colonnes par *ColumnDelimiter*et les valeurs par null *NullExpr*. Ces trois paramètres de la [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) méthode sont valides uniquement avec un *StringFormat* de **adClipString**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>S'applique à  
 [GetString, méthode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
