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
manager: jroth
ms.openlocfilehash: fef3eac34a624925401eeac2fd82b2f34eaa3a1f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704047"
---
# <a name="activecommand-property-ado"></a>ActiveCommand, propriété (ADO)
Indique le [commande](../../../ado/reference/ado-api/command-object-ado.md) objet qui a créé l’associé [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Variant** qui contient un **commande** objet. Valeur par défaut est une référence d’objet null.  
  
## <a name="remarks"></a>Notes  
 Le **ActiveCommand** propriété est en lecture seule.  
  
 Si un **commande** objet n’a pas été utilisé pour créer des cours **Recordset**, puis un **Null** référence d’objet est retournée.  
  
 Cette propriété permet de trouver associé **commande** lorsque vous obtenez uniquement résultant de l’objet **Recordset** objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveCommand, propriété-Exemple (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [ActiveCommand, propriété-Exemple (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [ActiveCommand, propriété-Exemple (VC ++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
