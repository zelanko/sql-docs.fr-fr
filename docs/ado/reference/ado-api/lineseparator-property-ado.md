---
description: LineSeparator, propriété (ADO)
title: LineSeparator, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd1e14d5c7ebc84ea4736da08296eca0e02ea38
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990720"
---
# <a name="lineseparator-property-ado"></a>LineSeparator, propriété (ADO)
Indique le caractère binaire à utiliser comme séparateur de lignes dans les objets de [flux](./stream-object-ado.md) de texte.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [LineSeparatorsEnum](./lineseparatorsenum.md) qui indique le caractère de séparation de ligne utilisé dans le **flux**. La valeur par défaut est **adCRLF**.  
  
## <a name="remarks"></a>Notes  
 **LineSeparator** est utilisé pour interpréter les lignes lors de la lecture du contenu d’un **flux**de texte. Les lignes peuvent être ignorées à l’aide de la méthode [SkipLine](./skipline-method.md) .  
  
 **LineSeparator** est utilisé uniquement avec des objets de **flux** de texte (le[type](./type-property-ado-stream.md) est **adTypeText**). Cette propriété est ignorée si le **type** est **adTypeBinary**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Stream, objet (ADO)](./stream-object-ado.md)