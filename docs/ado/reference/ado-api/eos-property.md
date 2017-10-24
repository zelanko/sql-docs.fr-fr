---
title: "Propriété de la fin du support | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c29c72e9cd88ff5672b90aeab5da97c7742f5b30
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="eos-property"></a>Propriété de la fin du support
Indique si la position actuelle est à la fin de la [flux](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **booléenne** valeur qui indique si la position actuelle est à la fin du flux de données. **Fin du support** retourne **True** s’il existe plus d’octets dans le flux ; il retourne **False** s’il existe des octets après la position actuelle.  
  
 Pour définir la position de fin de flux de données, utilisez la [SetEOS](../../../ado/reference/ado-api/seteos-method.md) (méthode). Pour déterminer la position actuelle, utilisez la [Position](../../../ado/reference/ado-api/position-property-ado.md) propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet de flux de données (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fin du support et LineSeparator, propriétés et SkipLine, méthode-exemple (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Objet de flux de données (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

