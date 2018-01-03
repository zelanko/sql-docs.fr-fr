---
title: Les curseurs statiques | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0347981e324fe8aa80d1707cd8919890c955aec6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="static-cursors"></a>Curseurs statiques
Le curseur statique affiche toujours le jeu que lors de l’ouverture du curseur tout d’abord de résultats. En fonction de l’implémentation, les curseurs statiques sont en lecture seule ou lecture/écriture et fournir le défilement vers l’avant et vers l’arrière. Généralement, le curseur statique ne détecte pas les modifications apportées à l’appartenance, l’ordre ou les valeurs du jeu de résultats après l’ouverture du curseur. Les curseurs statiques peuvent détecter leurs propres mises à jour, suppressions et insertions, bien qu’ils ne doivent pas à le faire.  
  
 Les curseurs statiques détectent jamais les autres mises à jour, supprime et insère. Par exemple, un curseur statique extrait une ligne et une autre application, puis met à jour cette ligne. Si l’application réextrait la ligne à partir du curseur statique, les valeurs sont identiques, malgré les modifications apportées par l’autre application. Tous les types de défilement sont pris en charge, mais les fournisseurs peuvent ou ne peuvent pas prendre en charge les signets.  
  
 Si votre application n’a pas besoin détecter les modifications de données et requiert le défilement, le curseur statique est le meilleur choix. Utilisez le **adOpenStatic CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur statique dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)   
 [Curseurs keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)
