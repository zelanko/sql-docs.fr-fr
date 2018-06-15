---
title: PageSize, propriété (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aea2e9510f80f8cd0d15bfbc2f7f544055b65884
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280058"
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
