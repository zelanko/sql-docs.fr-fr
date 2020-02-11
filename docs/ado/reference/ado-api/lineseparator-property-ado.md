---
title: LineSeparator, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0343954f549f2cba4b535b8ab4ebafec5a842015
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918282"
---
# <a name="lineseparator-property-ado"></a>LineSeparator, propriété (ADO)
Indique le caractère binaire à utiliser comme séparateur de lignes dans les objets de [flux](../../../ado/reference/ado-api/stream-object-ado.md) de texte.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) qui indique le caractère de séparation de ligne utilisé dans le **flux**. La valeur par défaut est **adCRLF**.  
  
## <a name="remarks"></a>Notes  
 **LineSeparator** est utilisé pour interpréter les lignes lors de la lecture du contenu d’un **flux**de texte. Les lignes peuvent être ignorées à l’aide de la méthode [SkipLine](../../../ado/reference/ado-api/skipline-method.md) .  
  
 **LineSeparator** est utilisé uniquement avec des objets de **flux** de texte (le[type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Cette propriété est ignorée si le **type** est **adTypeBinary**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
