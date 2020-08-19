---
description: Index, propriété
title: Index, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
author: rothja
ms.author: jroth
ms.openlocfilehash: 80d15588279e584ec4d63d4336239952f22405cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443461"
---
# <a name="index-property"></a>Index, propriété
Indique le nom de l’index actuellement en vigueur pour un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** , qui est le nom de l’index.  
  
## <a name="remarks"></a>Notes  
 L’index nommé par la propriété **index** doit avoir été précédemment déclaré sur la table de base sous-jacente à l’objet **Recordset** . Autrement dit, l’index doit avoir été déclaré par programmation comme un objet d' [index](../../../ado/reference/adox-api/index-object-adox.md) ADOX ou lors de la création de la table de base.  
  
 Une erreur d’exécution se produit si l’index ne peut pas être défini. La propriété d' **index** ne peut pas être définie dans les conditions suivantes :  
  
-   Dans un gestionnaire d’événements [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) ou **RecordsetChangeComplete** .  
  
-   Si le **jeu d’enregistrements** est toujours en cours d’exécution d’une opération (ce qui peut être déterminé par la propriété [State](../../../ado/reference/ado-api/state-property-ado.md) ).  
  
-   Si un filtre a été défini sur le **jeu d’enregistrements** avec la propriété [Filter](../../../ado/reference/ado-api/filter-property.md) .  
  
 La propriété **index** peut toujours être définie correctement si le **jeu d’enregistrements** est fermé, mais que l' **objet Recordset** ne s’ouvre pas correctement, ou l’index ne peut pas être utilisé si le fournisseur sous-jacent ne prend pas en charge les index.  
  
 Si l’index peut être défini, la position de la ligne actuelle peut changer. Cela entraînera une mise à jour de la propriété [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) et déclenchera les événements **WillChangeRecordset**, **RecordsetChangeComplete**, [WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)et [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) .  
  
 Si l’index peut être défini et si la propriété [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) est **adLockPessimistic** ou **adLockOptimistic**, une opération [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) implicite est effectuée. Cela libère les groupes actuels et affectés. Tout filtre existant est libéré, et la position de ligne actuelle est remplacée par la première ligne de l’ensemble d' **enregistrements**réorganisé.  
  
 La propriété **index** est utilisée conjointement avec la méthode [Seek](../../../ado/reference/ado-api/seek-method.md) . Si le fournisseur sous-jacent ne prend pas en charge la propriété d' **index** , et donc la méthode **Seek** , envisagez d’utiliser la méthode [Find](../../../ado/reference/ado-api/find-method-ado.md) à la place. Déterminez si l’objet **Recordset** prend en charge les index avec la méthode [prend en charge](../../../ado/reference/ado-api/supports-method.md)**(adIndex)** .  
  
 La propriété d' **index** intégrée n’est pas liée à la propriété d' [optimisation](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) dynamique, bien qu’elle traite les deux index.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode Seek et index, exemple de propriété (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Index, objet (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek, méthode](../../../ado/reference/ado-api/seek-method.md)
