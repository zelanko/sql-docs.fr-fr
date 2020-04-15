---
title: SQL_NO_DATA Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a399a270eb1cd2f3daf9449c53b1f577a6b9545
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299789"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
Quand un ODBC 3. *x* application appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** dans un ODBC 2. *x* pilote pour exécuter une mise à jour recherchée ou supprimer l’instruction qui n’affecte pas les lignes à la source de données, le pilote doit retourner SQL_SUCCESS, pas SQL_NO_DATA. Quand un ODBC 2. *x* ou ODBC 3. *x* application fonctionnant avec un ODBC 3. *x* conducteur appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** avec le même résultat, l’ODBC 3. *x* le conducteur doit retourner SQL_NO_DATA.
