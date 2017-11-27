---
title: "Implémentation de SQLGetDiagRec et SQLGetDiagField | Documents Microsoft"
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d757e4addf483690e491a71d2f7094aa3d9ad116
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implémentation de SQLGetDiagRec et SQLGetDiagField
**SQLGetDiagRec** et **SQLGetDiagField** sont implémentées par le Gestionnaire de pilotes et chaque pilote. Le Gestionnaire de pilotes et chaque pilote de mettre à jour les enregistrements de diagnostic pour chaque environnement, connexion, l’instruction et handle de descripteur et libèrent ces enregistrements uniquement quand une autre fonction est appelée avec que handle ou le handle est libéré.  
  
 Bien que le Gestionnaire de pilotes et chaque pilote doivent déterminer le premier enregistrement de l’état selon les classements dans [séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md), le Gestionnaire de pilotes détermine la séquence finale d’enregistrements.  
  
 **SQLGetDiagRec** et **SQLGetDiagField** ne validez pas les enregistrements de diagnostic sur eux-mêmes.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Règles de gestion des diagnostics](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Rôle du gestionnaire de pilotes](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Rôle du pilote](../../../odbc/reference/develop-app/role-of-the-driver.md)
