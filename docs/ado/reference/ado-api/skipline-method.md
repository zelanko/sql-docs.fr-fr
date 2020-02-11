---
title: SkipLine, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8439f7d8fabc5675e43fca5bba006b22574b992
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931047"
---
# <a name="skipline-method"></a>SkipLine, méthode
Ignore une ligne entière lors de la lecture d’un [flux](../../../ado/reference/ado-api/stream-object-ado.md)de texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Notes  
 Tous les caractères jusqu’à et y compris le séparateur de ligne suivant sont ignorés. Par défaut, [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) est **adCRLF**. Si vous tentez d’ignorer la dernière [EOS](../../../ado/reference/ado-api/eos-property.md), la position actuelle restera à **EOS**.  
  
 La méthode **SkipLine** est utilisée avec les flux de texte (le[type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
