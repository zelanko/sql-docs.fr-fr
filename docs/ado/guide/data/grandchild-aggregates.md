---
title: "Agrégats petits-enfants | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0785bede442b0f89a9a8a1efacaac03c1aedf2d3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="grandchild-aggregates"></a>Agrégats petits-enfants
La colonne de chapitre créée dans une clause d’une commande de la forme peut être attribuée à un *nom d’alias-chapitre* (généralement avec le mot clé AS). Vous pouvez identifier toute colonne de n’importe quel chapitre de la forme **Recordset** avec un nom qualifié complet qui identifie l’enfant contenant la colonne. Par exemple, si le chapitre parent, chap1, contient un chapitre enfant, chap2, qui possède une colonne de montant, amt, puis le nom qualifié serait Chap1.Chap2.mnt. Le nom qualifié peut ensuite être utilisé en tant qu’argument à une des fonctions d’agrégation (SUM, AVG, MAX, MIN, COUNT, STDEV ou un).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)
