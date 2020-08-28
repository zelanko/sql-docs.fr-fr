---
description: NamedParameters, propriété (ADO)
title: NamedParameters, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 18552a7d15a5dbe36a05c7391d0fd7e2ab3a6d94
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990490"
---
# <a name="namedparameters-property-ado"></a>NamedParameters, propriété (ADO)
Indique si les noms de paramètres doivent être passés au fournisseur.  
  
## <a name="remarks"></a>Notes  
 Lorsque cette propriété a la valeur true, ADO transmet la valeur de la propriété **Name** de chaque paramètre dans la collection de **paramètres** de l' [objet Command](./command-object-ado.md). Le fournisseur utilise un nom de paramètre pour faire correspondre les paramètres dans les propriétés **CommandText** ou **CommandStream** . Si cette propriété a la valeur false (valeur par défaut), les noms de paramètres sont ignorés et le fournisseur utilise l’ordre des paramètres pour faire correspondre les valeurs aux paramètres dans les propriétés **CommandText** ou **CommandStream** .  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CommandText, propriété (ADO)](./commandtext-property-ado.md)   
 [CommandStream, propriété (ADO)](./commandstream-property-ado.md)   
 [Parameters, collection (ADO)](./parameters-collection-ado.md)