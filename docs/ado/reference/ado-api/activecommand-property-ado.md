---
description: ActiveCommand, propriété (ADO)
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
ms.openlocfilehash: 38c0a0955e934b4f303937d978f739e00ac6c120
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451741"
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
