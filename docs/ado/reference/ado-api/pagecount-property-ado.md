---
title: PageCount, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ebb85eee8ea976f1ef078ebfe22eca195081bba
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762003"
---
# <a name="pagecount-property-ado"></a>PageCount, propriété (ADO)
Indique le nombre de pages de données que contient l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne une valeur de **type long** qui indique le nombre de pages dans le **Recordset**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **PageCount** pour déterminer le nombre de pages de données qui se trouvent dans l’objet **Recordset** . Les *pages* sont des groupes d’enregistrements dont la taille est égale au paramètre de la propriété [pageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) . Même si la dernière page est incomplète parce qu’il y a moins d’enregistrements que la valeur **pageSize** , elle est comptabilisée comme une page supplémentaire dans la valeur **PageCount** . Si l’objet **Recordset** ne prend pas en charge cette propriété, la valeur est-1 pour indiquer que l’objet **PageCount** est non déterminable.  
  
 Pour plus d’informations sur les fonctionnalités de page, consultez les propriétés **pageSize** et [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AbsolutePage, PageCount et PageSize, propriétés, exemple (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount et PageSize, propriétés, exemple (VC + +)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageSize, propriété (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [RecordCount, propriété (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
