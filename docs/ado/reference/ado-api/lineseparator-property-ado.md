---
title: "LineSeparator, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3742653b10e98c7608557da86a2975b24e472b9c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="lineseparator-property-ado"></a>LineSeparator, propriété (ADO)
Indique le caractère binaire à utiliser comme séparateur de ligne dans le texte [flux](../../../ado/reference/ado-api/stream-object-ado.md) objets.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) valeur qui indique le caractère de séparation de ligne utilisé dans le **flux**. La valeur par défaut est **adCRLF**.  
  
## <a name="remarks"></a>Notes  
 **LineSeparator** est utilisé pour interpréter les lignes lors de la lecture du contenu d’un texte **flux**. Lignes peuvent être ignorées en cliquant sur le [SkipLine](../../../ado/reference/ado-api/skipline-method.md) (méthode).  
  
 **LineSeparator** est utilisé qu’avec du texte **flux** objets ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Cette propriété est ignorée si **Type** est **adTypeBinary**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
