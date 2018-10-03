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
manager: craigg
ms.openlocfilehash: ca61f383198207223abf30ce25d9c922909f6526
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683689"
---
# <a name="close-method-ado-md"></a>Close, méthode (ADO MD)
Ferme un ensemble de cellules ouvert.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **fermer** méthode pour fermer un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objet publiera les données associées, y compris les données dans les liés [cellule](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [axe](../../../ado/reference/ado-md-api/axis-object-ado-md.md), [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md), ou [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objets. Fermeture d’un **Cellset** ne le supprime pas de la mémoire ; vous pouvez modifier ses paramètres de propriété et ouvrez à nouveau ultérieurement. Pour éliminer complètement un objet de la mémoire, la valeur est la variable objet **rien**.  
  
 Vous pouvez appeler ultérieurement la [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) méthode pour rouvrir la **Cellset** en utilisant le même ou un autre chaîne source. Bien que le **Cellset** objet est fermé, récupération de toutes les propriétés ou appelez des méthodes qui référencent les données sous-jacentes ou de métadonnées génère une erreur.  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Axis, objet (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Cellule, objet (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Membre objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)   
 [Open, méthode (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)   
 [Position, objet (ADO MD)](../../../ado/reference/ado-md-api/position-object-ado-md.md)   
 [State, propriété (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
