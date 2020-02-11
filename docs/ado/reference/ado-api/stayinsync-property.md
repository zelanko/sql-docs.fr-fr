---
title: StayInSync, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18d17e0a761fe03053ba90b8ff1ef87f3067df76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67930748"
---
# <a name="stayinsync-property"></a>StayInSync, propriété
Indique, dans un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) hiérarchique, si la référence aux enregistrements enfants sous-jacents (autrement dit, le *chapitre*) change lorsque la position de la ligne parente change.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur **booléenne** . La valeur par défaut est **True**. Si la **valeur est true**, le chapitre sera mis à jour si l’objet du **jeu d’enregistrements** parent change de position de ligne ; Si la **valeur est false**, le chapitre continuera à faire référence aux données du chapitre précédent, même si l’objet **Recordset** parent a modifié la position de ligne.  
  
## <a name="remarks"></a>Notes  
 Cette propriété s’applique aux recordsets hiérarchiques, tels que ceux pris en charge par le [service de mise en forme de données Microsoft pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), et doit être défini sur le **jeu d’enregistrements** parent avant que le **jeu d’enregistrements** enfant soit récupéré. Cette propriété simplifie la navigation dans les jeux d’enregistrements hiérarchiques.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [StayInSync, exemple de propriété (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
