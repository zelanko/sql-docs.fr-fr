---
title: SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bad2cc35a30f5c6f5855292ff73635cef6072b2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63067836"
---
# <a name="sqlcancel"></a>SQLCancel
  Le [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) rubrique indique que dans ODBC 2.x, si une application appelle `SQLCancel` lorsque aucun traitement n’est effectuée sur l’instruction, `SQLCancel` a le même effet que `SQLFreeStmt` avec la `SQL_CLOSE` option ; cela le comportement est défini uniquement par souci d’exhaustivité et les applications doivent appeler `SQLFreeStmt` ou `SQLCloseCursor` de fermeture des curseurs. Mais même si votre application [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit 3.5.x ou version ultérieure pour l'API ODBC, la fonction `SQLCancel` utilisera le comportement ODBC 2.x.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
