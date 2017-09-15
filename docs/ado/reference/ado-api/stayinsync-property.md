---
title: "Propriété StayInSync | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3951725cd3463af5cc4348cdb7803fe760345854
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="stayinsync-property"></a>StayInSync, propriété
Indique, dans une liste hiérarchique [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet, si la référence aux enregistrements enfants sous-jacents (autrement dit, le *chapitre*) change lorsque le changement de position de la ligne parente.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **booléenne** valeur. La valeur par défaut est **True**. Si **True**, le chapitre sera mise à jour si le parent **Recordset** objet change de position ; ligne si **False**, le chapitre continueront de faire référence à des données dans le chapitre précédent même si le parent **Recordset** objet a changé de position de ligne.  
  
## <a name="remarks"></a>Notes  
 Cette propriété s’applique aux jeux d’enregistrements, tels que ceux pris en charge par le [Service de mise en forme des données Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)et doit être définie sur le parent **Recordset** avant l’enfant ** Jeu d’enregistrements** est récupéré. Cette propriété simplifie la navigation dans les jeux d’enregistrements.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété StayInSync (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Données de Microsoft Service pour OLE DB (fournisseur de services ADO) de mise en forme](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
