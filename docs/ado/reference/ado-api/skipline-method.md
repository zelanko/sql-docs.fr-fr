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
manager: craigg
ms.openlocfilehash: b0e96900fdac55e97e3481ba5198e0f51d659877
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713757"
---
# <a name="skipline-method"></a>SkipLine, méthode
Ignore une ligne complète lors de la lecture d’un texte [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Notes  
 Tous les caractères jusqu'à et y compris le séparateur de ligne suivant sont ignorés. Par défaut, le [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) est **adCRLF**. Si vous tentez d’ignorer [EOS](../../../ado/reference/ado-api/eos-property.md), la position actuelle restera à **EOS**.  
  
 Le **SkipLine** méthode est utilisée avec des flux de texte ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
