---
title: Les curseurs statiques | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 520c484bdaaa6eb59488900208993a607c5b0f7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924117"
---
# <a name="static-cursors"></a>Curseurs statiques
Le curseur statique affiche toujours le jeu de résultats comme sa première ouverture de curseur. En fonction de l’implémentation, les curseurs statiques sont en lecture seule ou lecture/écriture et fournir le défilement vers l’avant et vers l’arrière. Généralement, le curseur statique ne détecte pas les modifications apportées à l’appartenance, l’ordre ou les valeurs du jeu de résultats après l’ouverture du curseur. Les curseurs statiques peuvent détecter leurs propres mises à jour, suppressions et insertions, bien qu’ils ne soient pas obligés de le faire.  
  
 Les curseurs statiques détectent jamais autres mises à jour, suppressions et des insertions. Par exemple, supposez qu’un curseur statique extrait une ligne et qu’une autre application met ensuite à jour cette ligne. Si l’application réextrait la ligne à partir du curseur statique, les valeurs qu’elle voit sont inchangées, malgré les modifications apportées par l’autre application. Tous les types de défilement sont pris en charge, mais les fournisseurs peuvent ou ne peuvent pas prendre en charge les signets.  
  
 Si votre application n’a pas besoin de détecter les données changent et il nécessite le défilement, le curseur statique est le meilleur choix. Utiliser le **adOpenStatic CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur statique dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)   
 [Curseurs keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)
