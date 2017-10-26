---
title: "Pilotes de base de données de diagnostic pour Desktop | Documents Microsoft"
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
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 432d311b1f55ff636e8c0b6fedb28509e3d9e6ed
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="diagnostics-for-desktop-database-drivers"></a>Tests de diagnostic pour les pilotes de la base de données de bureau
Toutes les erreurs et avertissements pas vérifiées ou partiellement vérifiée par le Gestionnaire de pilotes sont gérés par le pilote. Le pilote mappe également natif erreurs ou les erreurs retournées par la source de données à SQLSTATE. Chaque fonction répertoriée dans le *de référence du programmeur ODBC* contient une section « Diagnostics » qui spécifie les conditions et les messages.  
  
 Appel d’applications **SQLGetDiagRec** pour récupérer le code SQLSTATE, code d’erreur natif et des messages de diagnostic. Appel de **SQLGetDiagField** et en spécifiant le champ récupère des champs de diagnostic. Le niveau de prise en charge des identificateurs de diagnostic est répertorié dans le tableau suivant.  
  
|DiagIdentifiers|Niveau de prise en charge|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Non pris en charge|  
|SQL_DIAG_CLASS_ORIGIN|Pris en charge. Toujours « ODBC 3.0 » pour les versions 3.0 et versions ultérieures de ce pilote.|  
|SQL_DIAG_COLUMN_NUMBER|Pris en charge|  
|SQL_DIAG_CURSOR_ROW_COUNT|Non pris en charge|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Non pris en charge|  
|SQL_DIAG_MESSAGE_TEXT|Pris en charge|  
|SQL_DIAG_NATIVE|Pris en charge|  
|SQL_DIAG_NUMBER|Pris en charge|  
|SQL_DIAG_RETURNCODE|Prise en charge mais implémenté par le Gestionnaire de pilotes|  
|SQL_DIAG_ROW_COUNT|Pris en charge|  
|SQL_DIAG_ROW_NUMBER|Pris en charge|  
|SQL_DIAG_SERVER_NAME|Non pris en charge|  
|SQL_DIAG_SQLSTATE|Pris en charge|  
|SQL_DIAG_SUBCLASS_ORIGIN|Pris en charge|

