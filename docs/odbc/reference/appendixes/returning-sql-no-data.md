---
title: Retournant SQL_NO_DATA | Documents Microsoft
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
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5539f9d2951913163ac6011695709e3664d8acb1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="returning-sqlnodata"></a>Retournant SQL_NO_DATA
Lorsqu’une application ODBC 2. *x* application workingwith un ODBC 3*.x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData**, et une recherche de mise à jour ou d’une instruction delete a été exécutée mais n’a affecté aucune ligne à la source de données, les ODBC 3*.x* pilote doit retourner SQL_SUCCESS. Lorsqu’un ODBC 3*.x* application utilisant une ODBC 3*.x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** avec le même résultat, la version 3 ODBC*.x* pilote doit retourner SQL_NO_DATA.  
  
 Si une recherche de mise à jour ou de supprimer l’instruction dans un lot d’instructions n’affecte pas les lignes à la source de données **SQLMoreResults** retourne SQL_SUCCESS. Il ne peut pas retourner SQL_NO_DATA, car cela équivaudrait qu’il n’y a plus aucun résultat, pas qu’il est un résultat à partir d’une mise à jour/delete par recherche qui a n’affecté aucune ligne.

