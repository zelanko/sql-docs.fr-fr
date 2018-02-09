---
title: "Propriété StayInSync | Documents Microsoft"
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
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1edc5a35035ed8847dd26c13932b49e29b22dca
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="stayinsync-property"></a>StayInSync, propriété
Indique, dans une liste hiérarchique [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet, si la référence aux enregistrements enfants sous-jacents (autrement dit, le *chapitre*) change lorsque le changement de position de la ligne parente.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **booléenne** valeur. La valeur par défaut est **True**. Si **True**, le chapitre sera mise à jour si le parent **Recordset** objet change de position ; ligne si **False**, le chapitre continueront de faire référence à des données dans le chapitre précédent même si le parent **Recordset** objet a changé de position de ligne.  
  
## <a name="remarks"></a>Notes  
 Cette propriété s’applique aux jeux d’enregistrements, tels que ceux pris en charge par le [Service de mise en forme des données Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)et doit être définie sur le parent **Recordset** avant l’enfant  **Jeu d’enregistrements** est récupéré. Cette propriété simplifie la navigation dans les jeux d’enregistrements.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété StayInSync (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Données de Microsoft Service pour OLE DB (fournisseur de services ADO) de mise en forme](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
