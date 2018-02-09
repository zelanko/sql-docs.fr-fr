---
title: "PageSize, propriété (ADO) | Documents Microsoft"
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
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f611c47acb81b661e7c99422a785d6fb1c0d489
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="pagesize-property-ado"></a>PageSize, propriété (ADO)
Indique le nombre d’enregistrements constitue une page dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur qui indique le nombre d’enregistrements sur une page. La valeur par défaut est **10**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **PageSize** propriété pour déterminer le nombre d’enregistrements constituant une page logique de données. L’établissement d’une taille de page vous permet d’utiliser le [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) propriété pour accéder au premier enregistrement d’une page particulière. Cela est utile dans les scénarios de serveur Web lorsque vous souhaitez autoriser l’utilisateur à parcourir les données, affichage d’un certain nombre d’enregistrements à la fois.  
  
 Cette propriété peut être définie à tout moment, et sa valeur sera utilisée pour le calcul de l’emplacement du premier enregistrement d’une page particulière.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AbsolutePage, PageCount et PageSize, propriétés-exemple (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount et PageSize, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageCount, propriété (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
