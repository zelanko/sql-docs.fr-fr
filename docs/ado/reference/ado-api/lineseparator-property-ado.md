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
manager: craigg
ms.openlocfilehash: 0b55f82e92ff74ba359074613205bc8086af81b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639357"
---
# <a name="lineseparator-property-ado"></a>LineSeparator, propriété (ADO)
Indique le caractère binaire à utiliser comme séparateur de ligne dans le texte [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objets.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) valeur qui indique le caractère de séparateur de ligne utilisé dans le **Stream**. La valeur par défaut est **adCRLF**.  
  
## <a name="remarks"></a>Notes  
 **LineSeparator** est utilisé pour interpréter les lignes à la lecture du contenu d’un texte **Stream**. Lignes peuvent être ignorées par le [SkipLine](../../../ado/reference/ado-api/skipline-method.md) (méthode).  
  
 **LineSeparator** est utilisé uniquement avec le texte **Stream** objets ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Cette propriété est ignorée si **Type** est **adTypeBinary**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
