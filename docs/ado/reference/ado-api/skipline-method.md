---
description: SkipLine, méthode
title: SkipLine, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 840c0111aca8b202fd081d3f0250d17fd43e5bbb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989050"
---
# <a name="skipline-method"></a>SkipLine, méthode
Ignore une ligne entière lors de la lecture d’un [flux](./stream-object-ado.md)de texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Notes  
 Tous les caractères jusqu’à et y compris le séparateur de ligne suivant sont ignorés. Par défaut, [LineSeparator](./lineseparator-property-ado.md) est **adCRLF**. Si vous tentez d’ignorer la dernière [EOS](./eos-property.md), la position actuelle restera à **EOS**.  
  
 La méthode **SkipLine** est utilisée avec les flux de texte (le[type](./type-property-ado-stream.md) est **adTypeText**).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](./stream-object-ado.md)