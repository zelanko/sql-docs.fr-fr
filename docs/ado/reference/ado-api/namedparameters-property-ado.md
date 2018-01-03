---
title: "NamedParameters, propriété (ADO) | Documents Microsoft"
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
f1_keywords: _Command::NamedParameters
helpviewer_keywords: NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 357cfc37c90822ca97ae5ca1349f0bc6743d4859
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="namedparameters-property-ado"></a>NamedParameters, propriété (ADO)
Indique si les noms de paramètre doivent être passés au fournisseur.  
  
## <a name="remarks"></a>Notes   
 Lorsque cette propriété est true, ADO transmet la valeur de la **nom** propriété de chaque paramètre dans le **paramètre** collection pour le [objet de commande](../../../ado/reference/ado-api/command-object-ado.md). Le fournisseur utilise un nom de paramètre pour faire correspondre les paramètres dans le **CommandText** ou **CommandStream** propriétés. Si cette propriété a la valeur false (valeur par défaut), les noms de paramètres sont ignorés et le fournisseur utilise l’ordre des paramètres pour correspondre aux valeurs des paramètres dans le **CommandText** ou **CommandStream** propriétés.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CommandText, propriété (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandStream, propriété (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
