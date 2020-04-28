---
title: Close, méthode (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 09e83fd8645a5c0ab604a640478c4cced4870742
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949813"
---
# <a name="close-method-ado-md"></a>Close, méthode (ADO MD)
Ferme un CellSet ouvert.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Notes  
 L’utilisation de la méthode **Close** pour fermer un objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) permet de libérer les données associées, y compris les données dans les [cellules](../../../ado/reference/ado-md-api/cell-object-ado-md.md), les [axes](../../../ado/reference/ado-md-api/axis-object-ado-md.md), les [positions](../../../ado/reference/ado-md-api/position-object-ado-md.md)ou les objets [membres](../../../ado/reference/ado-md-api/member-object-ado-md.md) associés. La fermeture d’un **Cellset** ne le supprime pas de la mémoire ; vous pouvez modifier ses paramètres de propriété et l’ouvrir à nouveau ultérieurement. Pour éliminer complètement un objet de la mémoire, affectez à la variable objet la valeur **Nothing**.  
  
 Vous pouvez appeler ultérieurement la méthode [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) pour rouvrir l' **Cellset** à l’aide de la même chaîne source ou d’une autre chaîne. Lorsque l’objet **Cellset** est fermé, la récupération de toutes les propriétés ou l’appel de toute méthode qui fait référence aux données ou métadonnées sous-jacentes génère une erreur.  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AXIS, objet (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Cell, objet (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Méthode Open (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Position, objet (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [State, propriété (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
