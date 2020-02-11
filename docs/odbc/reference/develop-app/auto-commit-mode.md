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
ms.openlocfilehash: a8a02d58309f123e6cc8b29d41188ba5bebb26f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67909893"
---
# <a name="auto-commit-mode"></a>Mode de validation automatique
*En mode de validation automatique,* chaque opération de base de données est une transaction validée lors de l’exécution. Ce mode convient pour de nombreuses transactions réelles qui se composent d’une seule instruction SQL. Il est inutile de délimiter ou de spécifier l’achèvement de ces transactions. Dans les bases de données sans prise en charge des transactions, le mode de validation automatique est le seul mode pris en charge. Dans ces bases de données, les instructions sont validées lorsqu’elles sont exécutées et il n’existe aucun moyen de les restaurer. ils sont donc toujours en mode de validation automatique.  
  
 Si le SGBD sous-jacent ne prend pas en charge les transactions en mode de validation automatique, le pilote peut les émuler en validant manuellement chaque instruction SQL au fur et à mesure de son exécution.  
  
 Si un lot d’instructions SQL est exécuté en mode de validation automatique, il est spécifique à la source de données lorsque les instructions du lot sont validées. Elles peuvent être validées lorsqu’elles sont exécutées ou dans leur ensemble une fois que l’ensemble du lot a été exécuté. Certaines sources de données peuvent prendre en charge ces deux comportements et fournir un moyen de sélectionner l’un ou l’autre. En particulier, si une erreur se produit au milieu du lot, elle est spécifique à la source de données, que les instructions déjà exécutées soient validées ou restaurées. Ainsi, les applications interopérables qui utilisent des lots et exigent qu’elles soient validées ou restaurées dans leur ensemble doivent exécuter des lots uniquement en mode de validation manuelle.
