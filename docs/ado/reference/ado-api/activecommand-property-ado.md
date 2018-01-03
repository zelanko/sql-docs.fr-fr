---
title: "ActiveCommand, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset20::ActiveCommand
helpviewer_keywords: ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e5384aff9ee8646493d26272cdeaae33ab49157
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="activecommand-property-ado"></a>ActiveCommand, propriété (ADO)
Indique le [commande](../../../ado/reference/ado-api/command-object-ado.md) objet créé associé [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **Variant** qui contient un **commande** objet. Valeur par défaut est une référence d’objet null.  
  
## <a name="remarks"></a>Notes   
 Le **ActiveCommand** propriété est en lecture seule.  
  
 Si un **commande** objet n’a pas été utilisé pour créer l’actuel **Recordset**, un **Null** référence d’objet est retourné.  
  
 Cette propriété permet de rechercher les informations associé **commande** lorsqu’il vous est proposé uniquement résultant de l’objet **Recordset** objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété ActiveCommand (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Exemple de propriété ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Exemple de propriété ActiveCommand (VC ++)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
