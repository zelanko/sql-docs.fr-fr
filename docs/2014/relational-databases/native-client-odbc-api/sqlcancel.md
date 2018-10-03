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
ms.openlocfilehash: 816e93c7cf65d622bcd48cbf5a93eb5abba32adb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077793"
---
# <a name="sqlcancel"></a>SQLCancel
  Le [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) rubrique indique que dans ODBC 2.x, si une application appelle `SQLCancel` lorsque aucun traitement n’est effectuée sur l’instruction, `SQLCancel` a le même effet que `SQLFreeStmt` avec la `SQL_CLOSE` option ; cela le comportement est défini uniquement par souci d’exhaustivité et les applications doivent appeler `SQLFreeStmt` ou `SQLCloseCursor` de fermeture des curseurs. Mais même si votre application [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit 3.5.x ou version ultérieure pour l'API ODBC, la fonction `SQLCancel` utilisera le comportement ODBC 2.x.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
