---
title: "Rôle du Gestionnaire de pilotes | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- diagnostic information [ODBC], driver manager error checking
- SQLGetDiagField function [ODBC], driver manager
- SQLGetDiagRec function [ODBC], driver manager
- ODBC driver manager [ODBC]
- diagnostic information [ODBC], SqlGetDiagRec
- driver manager [ODBC], error checking
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7718a3d514c6862807cc4b47ecca8729c4c3a162
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="role-of-the-driver-manager"></a>Rôle du Gestionnaire de pilotes
Le Gestionnaire de pilotes détermine l’ordre final dans lequel retourner les enregistrements d’état qu’elle génère. En particulier, il détermine quel enregistrement a le rang le plus élevé et doit être retournées en premier. Le pilote est chargé de classer des enregistrements d’état qu’elle génère. Si les enregistrements d’état sont publiées par le Gestionnaire de pilotes et le pilote, le Gestionnaire de pilotes est responsable de leur classement. Pour plus d’informations, consultez [séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Le Gestionnaire de pilote n’autant la vérification des erreurs que possible. Cela enregistre tous les pilotes à partir de la vérification pour les mêmes erreurs. Par exemple, si un argument de fonction accepte un nombre discret de valeurs, tel que *opération* dans **SQLSetPos**, le Gestionnaire de pilotes vérifie que la valeur spécifiée est autorisée.  
  
 Les sections suivantes décrivent les types de conditions vérifiées par le Gestionnaire de pilotes. Ils ne sont pas destinés à être exhaustive ; Pour obtenir une liste complète de la SQLSTATE retourne le Gestionnaire de pilotes, consultez la section « Diagnostics » de chaque fonction ; la description de chaque vérification est effectuée par le Gestionnaire de pilotes commence par les lettres « (DM) ». Consultez également les tables de transition d’état de [Tables de Transition d’état annexe b : ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); erreurs indiqués entre parenthèses sont détectées par le Gestionnaire de pilotes.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Vérifications de la valeur des arguments](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Vérifications des transitions d’état](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Vérifications des erreurs générales](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Vérifications des erreurs et avertissements du gestionnaire de pilotes](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
