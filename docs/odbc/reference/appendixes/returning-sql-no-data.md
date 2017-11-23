---
title: Retournant SQL_NO_DATA | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf27a50915d9af31eaa280525736cacf7faf06db
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="returning-sqlnodata"></a>Retournant SQL_NO_DATA
Lorsqu’une application ODBC 2. *x* application workingwith un ODBC 3*.x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData**, et une recherche de mise à jour ou d’une instruction delete a été exécutée mais n’a affecté aucune ligne à la source de données, les ODBC 3*.x* pilote doit retourner SQL_SUCCESS. Lorsqu’un ODBC 3*.x* application utilisant une ODBC 3*.x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** avec le même résultat, la version 3 ODBC*.x* pilote doit retourner SQL_NO_DATA.  
  
 Si une recherche de mise à jour ou de supprimer l’instruction dans un lot d’instructions n’affecte pas les lignes à la source de données **SQLMoreResults** retourne SQL_SUCCESS. Il ne peut pas retourner SQL_NO_DATA, car cela équivaudrait qu’il n’y a plus aucun résultat, pas qu’il est un résultat à partir d’une mise à jour/delete par recherche qui a n’affecté aucune ligne.
