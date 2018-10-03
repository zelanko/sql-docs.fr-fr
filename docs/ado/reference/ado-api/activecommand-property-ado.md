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
manager: craigg
ms.openlocfilehash: 4dfdb60f9a394fa4d11e9b66ffb1f4b205881293
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705537"
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
