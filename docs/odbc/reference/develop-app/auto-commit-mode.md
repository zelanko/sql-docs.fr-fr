---
title: Mode Auto-Commit (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f19053eec7a48eba7a51425b01744f3acd10015
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285109"
---
# <a name="auto-commit-mode"></a>Mode de validation automatique
*En mode auto-commit,* chaque opération de base de données est une transaction qui est validée lorsqu’elle est effectuée. Ce mode convient à de nombreuses transactions réelles qui se composent d’une seule déclaration SQL. Il n’est pas nécessaire de délimiter ou de spécifier l’achèvement de ces transactions. Dans les bases de données sans support transactionnel, le mode auto-commit est le seul mode pris en charge. Dans ces bases de données, les déclarations sont commises lorsqu’elles sont exécutées et qu’il n’y a aucun moyen de les faire reculer; ils sont donc toujours en mode auto-commit.  
  
 Si le DBMS sous-jacent ne prend pas en charge les transactions en mode auto-commit, le conducteur peut les imiter en commettant manuellement chaque relevé SQL au fur et à mesure qu’il est exécuté.  
  
 Si un lot de relevés SQL est exécuté en mode auto-commit, il est spécifique à la source des données lorsque les relevés du lot sont validés. Ils peuvent être commis car ils sont exécutés ou dans leur ensemble après l’exécution de l’ensemble du lot. Certaines sources de données peuvent prendre en charge ces deux comportements et peuvent fournir un moyen de choisir l’un ou l’autre. En particulier, si une erreur se produit au milieu du lot, il est spécifique aux données si les déclarations déjà exécutées sont commises ou annulées. Ainsi, les applications interopérables qui utilisent des lots et qui exigent qu’elles soient validées ou annulées dans leur ensemble ne doivent exécuter des lots qu’en mode de validation manuelle.
