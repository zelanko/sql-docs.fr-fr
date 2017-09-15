---
title: Mode de validation automatique | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fb9b6d354657578f7188481a2e7ff7566f725c80
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="auto-commit-mode"></a>Mode de validation automatique
*En mode de validation automatique,* chaque opération de base de données est une transaction est validée lorsque effectuée. Ce mode est approprié pour le nombre réel de transactions qui se composent d’une instruction SQL unique. Il est inutile de le délimiter ou spécifiez l’achèvement de ces transactions. Dans les bases de données sans prise en charge des transactions, le mode de validation automatique est le seul mode de prise en charge. Dans ces bases de données, les instructions sont validées quand elles sont exécutées et il n’existe aucun moyen de les annuler ; ils sont donc toujours en mode de validation automatique.  
  
 Si le SGBD sous-jacent ne prend pas en charge les transactions en mode de validation automatique, le pilote peut émuler les en validant manuellement chaque instruction SQL qu’elle est exécutée.  
  
 Si un lot d’instructions SQL est exécuté en mode de validation automatique, il est spécifique à la source de données lorsque les instructions dans le lot sont validées. Ils peuvent être validées quand elles sont exécutées ou un ensemble d’après l’exécution de l’ensemble du lot. Certaines sources de données peuvent prendre en charge les deux de ces comportements et peuvent fournir un moyen de sélectionner une ou les autres. En particulier, si une erreur se produit au milieu du lot, il est spécifique à la source de données si les instructions déjà exécutées soient validées ou annulées. Par conséquent, les applications interopérables qui utilisent des lots et leur demander d’être validée ou restaurée en tant qu’ensemble doivent s’exécuter lots uniquement en mode de validation manuelle.
