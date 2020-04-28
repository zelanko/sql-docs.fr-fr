---
title: ActiveCommand, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2a2f23360cf3ce032d14af7ca475d5c2c3ea638
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921677"
---
# <a name="activecommand-property-ado"></a>ActiveCommand, propriété (ADO)
Indique l’objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) qui a créé l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) associé.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type Variant** qui contient un objet **Command** . La valeur par défaut est une référence d’objet null.  
  
## <a name="remarks"></a>Notes  
 La propriété **ActiveCommand** est en lecture seule.  
  
 Si un objet **Command** n’a pas été utilisé pour créer le **Recordset**actuel, une référence d’objet **null** est retournée.  
  
 Utilisez cette propriété pour Rechercher l’objet de **commande** associé lorsque vous n’avez donné que l’objet **Recordset** résultant.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveCommand, exemple de propriété (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [ActiveCommand, exemple de propriété (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [ActiveCommand, exemple de propriété (VC + +)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
