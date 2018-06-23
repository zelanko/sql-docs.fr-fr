---
title: SQLCancel | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6aff7aea0040e2fd7f86a3ad668b4e4438148497
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152813"
---
# <a name="sqlcancel"></a>SQLCancel
  Le [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) rubrique indique que dans ODBC 2.x, si une application appelle `SQLCancel` lorsque aucun traitement n’est effectuée sur l’instruction, `SQLCancel` a le même effet que `SQLFreeStmt` avec la `SQL_CLOSE` option ; cela le comportement est défini uniquement par souci d’exhaustivité et les applications doivent appeler `SQLFreeStmt` ou `SQLCloseCursor` de fermeture des curseurs. Mais même si votre application [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit 3.5.x ou version ultérieure pour l'API ODBC, la fonction `SQLCancel` utilisera le comportement ODBC 2.x.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  