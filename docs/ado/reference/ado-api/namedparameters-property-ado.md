---
title: NamedParameters, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::NamedParameters
helpviewer_keywords:
- NamedParameters property [ADO]
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c63fb598630a30fd2616722146bb6737f17b82b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242410"
---
# <a name="namedparameters-property-ado"></a>NamedParameters, propriété (ADO)
Indique si les noms de paramètre doivent être transmis au fournisseur.  
  
## <a name="remarks"></a>Notes  
 Lorsque cette propriété est true, ADO transmet la valeur de la **nom** propriété de chaque paramètre dans le **paramètre** collection pour le [objet de commande](../../../ado/reference/ado-api/command-object-ado.md). Le fournisseur utilise un nom de paramètre pour correspondre aux paramètres dans le **CommandText** ou **CommandStream** propriétés. Si cette propriété a la valeur false (valeur par défaut), les noms de paramètre sont ignorées et le fournisseur utilise l’ordre des paramètres pour correspondre aux valeurs des paramètres dans le **CommandText** ou **CommandStream** propriétés.  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CommandText, propriété (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandStream, propriété (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
