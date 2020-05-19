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
author: rothja
ms.author: jroth
ms.openlocfilehash: b89876366c80d20bde110da9e9d86414873e86bc
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747478"
---
# <a name="activecommand-property-ado"></a>ActiveCommand, propriété (ADO)
Indique l’objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) qui a créé l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) associé.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne une valeur de **type Variant** qui contient un objet **Command** . La valeur par défaut est une référence d’objet null.  
  
## <a name="remarks"></a>Remarques  
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
