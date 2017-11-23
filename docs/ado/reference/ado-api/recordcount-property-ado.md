---
title: "RecordCount, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::RecordCount
- Recordset15::GetRecordCount
- Recordset15::get_RecordCount
helpviewer_keywords: RecordCount property [ADO]
ms.assetid: 834f0121-394a-44d4-ad7d-999b43a6fe63
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 950b53501f84bdaebc1cdc0ce554d13860d894bd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="recordcount-property-ado"></a>RecordCount, propriété (ADO)
Indique le nombre d’enregistrements dans une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **Long** valeur qui indique le nombre d’enregistrements dans la **Recordset**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **RecordCount** propriété pour déterminer le nombre d’enregistrements se trouvent dans un **Recordset** objet. La propriété renvoie -1 quand ADO ne peut pas déterminer le nombre d’enregistrements ou si le type de curseur ou le fournisseur ne prend pas en charge **RecordCount**. La lecture de la **RecordCount** propriété sur un fermé **Recordset** provoque une erreur.  
  
 Si le **Recordset** objet prend en charge le positionnement approximatif ou les signets ??? Autrement dit, **prend en charge (adApproxPosition)** ou **prend en charge (adBookmark)**, respectivement, retourner **True**??? Cette valeur sera le nombre exact d’enregistrements dans la **Recordset**, indépendamment de si elle a été entièrement remplie. Si le **Recordset** objet ne prend pas en charge le positionnement approximatif, cette propriété peut être une charge importante pour les ressources, car tous les enregistrements doivent être récupérées et comptées pour renvoyer un **RecordCount** valeur.  
  
> [!NOTE]
>  Dans les versions ADO 2.8 et les versions antérieures, le fournisseur SQLOLEDB extrait tous les enregistrements lorsqu’un curseur côté serveur est utilisé, en dépit du fait qu’elle retourne **True** pour les deux **prend en charge (adApproxPosition)** et **Prend en charge (adBookmark)**.  
  
 Le type de curseur de la **Recordset** objet selon le nombre d’enregistrements peut être déterminé. Le **RecordCount** propriété retourne -1 pour un curseur avant uniquement ; le nombre réel pour une analyse statique ou curseur de jeu de clés et soit -1 ou le nombre réel pour un curseur dynamique, en fonction de la source de données.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Filter et RecordCount propriétés exemple (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
 [Filter et RecordCount, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
 [AbsolutePosition, propriété (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [PageCount, propriété (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
