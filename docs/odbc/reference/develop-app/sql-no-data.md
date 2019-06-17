---
title: SQL_NO_DATA | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 749351694a41764b9b5cc8bf3421340d62626aaf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62445961"
---
# <a name="sqlnodata"></a>SQL_NO_DATA
Lorsqu’une application ODBC 3. *x* application appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** dans un ODBC 2. *x* pilote à exécuter une recherche de la mise à jour ou supprimer l’instruction qui affecte toutes les lignes à la source de données, le pilote doit retourner SQL_SUCCESS, pas SQL_NO_DATA. Lorsqu’une application ODBC 2. *x* ou ODBC 3. *x* application fonctionne avec un ODBC 3. *x* pilote appelle **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** avec le même résultat, le ODBC 3. *x* pilote doit retourner SQL_NO_DATA.
