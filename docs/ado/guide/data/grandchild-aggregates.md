---
title: Agrégats petit-enfant | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
author: rothja
ms.author: jroth
ms.openlocfilehash: 148a2798d04bc7ec41832e5103d8ec097ffa9a0c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764820"
---
# <a name="grandchild-aggregates"></a>Agrégats de petits-enfants
La colonne de chapitre créée dans une clause d’une commande SHAPE peut recevoir un *nom d’alias de chapitre* (généralement avec le mot clé As). Vous pouvez identifier toute colonne dans n’importe quel chapitre du **Recordset** mis en forme avec un nom complet qui identifie l’enfant contenant la colonne. Par exemple, si le chapitre parent, chap1, contient un chapitre enfant, Chap2, qui a une colonne Amount, AMT, le nom qualifié est chap1. Chap2. AMT. Le nom qualifié peut ensuite être utilisé comme argument pour l’une des fonctions d’agrégation (SUM, AVG, MAX, MIN, COUNT, STDEV ou ANY).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)
