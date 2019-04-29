---
title: Mode de validation automatique | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 491fb8db9e37cfb3bfa07881958fe7828e6bb911
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63048424"
---
# <a name="auto-commit-mode"></a>Mode de validation automatique
*En mode de validation automatique,* chaque opération de base de données est une transaction est validée lorsque effectuée. Ce mode est approprié pour le nombre réel de transactions qui se composent d’une instruction SQL unique. Il est inutile de délimiter ou spécifier l’achèvement de ces transactions. Dans les bases de données sans prise en charge de la transaction, mode de validation automatique est le seul mode pris en charge. Dans ces bases de données, les instructions sont validées lors de leur exécution et il n’existe aucun moyen pour les annuler ; ils sont donc toujours en mode de validation automatique.  
  
 Si le SGBD sous-jacent ne prend pas en charge les transactions de mode de validation automatique, le pilote peut les émuler en validant manuellement chaque instruction SQL qu’elle est exécutée.  
  
 Si un lot d’instructions SQL est exécuté en mode de validation automatique, il est spécifique à la source de données lorsque les instructions dans le lot sont validées. Ils peuvent être validées car elles sont exécutées ou dans sa globalité après l’exécution de l’ensemble du lot. Certaines sources de données peuvent prendre en charge les deux de ces comportements et peuvent fournir un moyen de la sélection d’une ou les autres. En particulier, si une erreur se produit au milieu du lot, il est spécifique à la source de données si les instructions déjà exécutées soient validées ou annulées. Par conséquent, des applications interopérables qui utilisent des lots et de lui demander à être validée ou restaurée dans son ensemble doivent s’exécuter lots uniquement en mode de validation manuelle.
