---
title: "GetString, méthode (ADO) | Documents Microsoft"
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
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords: GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6f92e1be67ce0eb26f300cde4b1ef53bfc5dc49c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="getstring-method-ado"></a>GetString, méthode (ADO)
Retourne le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) sous forme de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne le **Recordset** comme une valeur de chaîne **Variant** (BSTR).  
  
#### <a name="parameters"></a>Paramètres  
 *StringFormat*  
 A [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) valeur qui spécifie comment la **Recordset** doit être convertie en une chaîne. Le *RowDelimiter*, *ColumnDelimiter*, et *NullExpr* paramètres sont utilisés uniquement avec un *StringFormat* de  **adClipString**.  
  
 *NumRows*  
 Facultatif. Le nombre de lignes à convertir dans le **Recordset**. Si *NumRows* n’est pas spécifié, ou si elle est supérieure au nombre total de lignes dans le **Recordset**, puis toutes les lignes de la **Recordset** sont convertis.  
  
 *ColumnDelimiter*  
 Facultatif. Un délimiteur utilisé entre les colonnes, si spécifié, sinon le caractère de tabulation.  
  
 *RowDelimiter*  
 Facultatif. Délimiteur utilisé entre les lignes, dans le cas contraire, le caractère de retour chariot.  
  
 *NullExpr*  
 Facultatif. Une expression utilisée à la place d’une valeur null, si spécifié, sinon retourne la chaîne vide.  
  
## <a name="remarks"></a>Notes   
 Données de ligne, mais aucune donnée de schéma, est enregistré dans la chaîne. Par conséquent, un **Recordset** ne peut pas être rouverte à l’aide de cette chaîne.  
  
 Cette méthode est équivalente à la RDO **GetClipString** (méthode).  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [GetString, exemple de méthode (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
