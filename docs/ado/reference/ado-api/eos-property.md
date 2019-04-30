---
title: EOS, propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47b3e48e612e0ee5595ada33127f016ee6b986f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180997"
---
# <a name="eos-property"></a>EOS, propriété
Indique si la position actuelle est à la fin de la [flux](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **booléenne** valeur qui indique si la position actuelle est à la fin du flux. **EOS** retourne **True** s’il existe davantage d’octets dans le flux de données ; elle retourne **False** s’il existe des octets après la position actuelle.  
  
 Pour définir la position de fin de flux de données, utilisez le [SetEOS](../../../ado/reference/ado-api/seteos-method.md) (méthode). Pour déterminer la position actuelle, utilisez la [Position](../../../ado/reference/ado-api/position-property-ado.md) propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [EOS et LineSeparator, propriétés et SkipLine, méthode, exemple (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
