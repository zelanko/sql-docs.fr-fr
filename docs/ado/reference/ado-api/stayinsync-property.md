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
manager: jroth
ms.openlocfilehash: 98a0cc1df12f905cd0d22d05b162983742d0f355
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710791"
---
# <a name="stayinsync-property"></a>StayInSync, propriété
Indique, dans une liste hiérarchique [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet, si la référence aux enregistrements enfants sous-jacents (autrement dit, le *chapitre*) change lorsque le changement de position de la ligne parente.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **booléenne** valeur. La valeur par défaut est **True**. Si **True**, le chapitre est mis à jour si le parent **Recordset** modifications de l’objet position de ligne ; si **False**, le chapitre continueront de faire référence à des données dans le chapitre précédent même si le parent **Recordset** objet a changé de position de ligne.  
  
## <a name="remarks"></a>Notes  
 Cette propriété s’applique aux recordsets hiérarchiques, tels que ceux pris en charge par le [Microsoft Data Shaping Service pour OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)et doit être définie sur le parent **Recordset** avant l’enfant  **Jeu d’enregistrements** est récupéré. Cette propriété simplifie la navigation dans les jeux d’enregistrements.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [StayInSync, propriété-Exemple (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft Data Shaping Service pour OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
