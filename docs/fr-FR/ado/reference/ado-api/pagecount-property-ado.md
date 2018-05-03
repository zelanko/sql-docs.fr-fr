---
title: PageCount, propriété (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageCount
helpviewer_keywords:
- PageCount property [ADO]
ms.assetid: b601b56c-0ac4-44ee-bc91-c3d2d104f00a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0de2e6f7d1865821ec3ff29f0b7d0b8a47ad0856
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="pagecount-property-ado"></a>PageCount, propriété (ADO)
Indique le nombre de pages de données le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet contient.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **Long** valeur qui indique le nombre de pages dans le **Recordset**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **PageCount** propriété pour déterminer le nombre de pages de données dans le **Recordset** objet. *Pages* sont des groupes d’enregistrements dont la taille est égale à la [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) paramètre de propriété. Même si la dernière page est incomplète, car il existe moins d’enregistrements que le **PageSize** valeur, elle est considérée comme une page supplémentaire dans le **PageCount** valeur. Si le **Recordset** objet ne prend pas en charge cette propriété, la valeur sera -1 pour indiquer que le **PageCount** est indéterminable.  
  
 Consultez le **PageSize** et [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) plus sur les fonctionnalités page Propriétés.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AbsolutePage, PageCount et PageSize, propriétés-exemple (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount et PageSize, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageSize, propriété (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)   
 [RecordCount, propriété (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
