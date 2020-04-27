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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067836"
---
# <a name="sqlcancel"></a>SQLCancel
  La rubrique [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) indique que dans ODBC 2. x, si une application appelle `SQLCancel` quand aucun traitement n’est effectué sur l’instruction, `SQLCancel` a le même effet qu' `SQLFreeStmt` avec l' `SQL_CLOSE` option ; ce comportement est défini uniquement pour l’exhaustivité et les applications `SQLFreeStmt` doivent `SQLCloseCursor` appeler ou pour fermer les curseurs. Mais même si votre application [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit 3.5.x ou version ultérieure pour l'API ODBC, la fonction `SQLCancel` utilisera le comportement ODBC 2.x.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
