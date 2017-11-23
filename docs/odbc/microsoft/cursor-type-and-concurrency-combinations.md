---
title: "Type de curseur et d’accès concurrentiel combinaisons | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d9798b819b702b4e984872a19b0c761a8621de2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="cursor-type-and-concurrency-combinations"></a>Type de curseur et les combinaisons d’accès concurrentiel
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Types de curseurs contrôlent les fonctionnalités du curseur à l’utilisateur. Options d’accès concurrentiel contrôlent la mise à jour et le comportement de verrouillage d’un jeu de résultats.  
  
|Type de curseur|Accès concurrentiel (les valeurs autorisées)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1] </sup> Consultez [Limitations d’utilisation de curseurs](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2] </sup> SQL_CONCUR_LOCK est pris en charge uniquement lorsque l’option de connexion SQL_AUTOCOMMIT a la valeur SQL_AUTOCOMMIT_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de connexion](../../odbc/microsoft/connect-options.md)
