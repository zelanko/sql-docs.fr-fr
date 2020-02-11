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
ms.openlocfilehash: 5a19856c957ee0c003e934ff8b2632aa28e32d33
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918924"
---
# <a name="eos-property"></a>EOS, propriété
Indique si la position actuelle est à la fin du [flux](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne une valeur **booléenne** qui indique si la position actuelle est à la fin du flux. **EOS** retourne la **valeur true** s’il n’y a plus d’octets dans le flux ; elle retourne la **valeur false** s’il y a plus d’octets après la position actuelle.  
  
 Pour définir la fin de la position du flux, utilisez la méthode [SetEOS](../../../ado/reference/ado-api/seteos-method.md) . Pour déterminer la position actuelle, utilisez la propriété [position](../../../ado/reference/ado-api/position-property-ado.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés EOS et LineSeparator et SkipLine, exemple de méthode (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
