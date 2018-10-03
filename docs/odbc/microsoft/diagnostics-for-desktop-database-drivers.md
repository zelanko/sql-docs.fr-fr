---
title: Pilotes de base de données de diagnostic pour Desktop | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6c21af2ef3f47c05aacf4b47673ab42a170f506
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709627"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Diagnostics des pilotes pour les bases de données de poste de travail
Toutes les erreurs et avertissements pas activé ou partiellement activé par le Gestionnaire de pilotes sont gérées par le pilote. Le pilote mappe également natif d’erreurs ou les erreurs retournées par la source de données à SQLSTATE. Chaque fonction répertoriée dans le *de référence du programmeur ODBC* contient une section « Diagnostics » qui spécifie les conditions et les messages.  
  
 Applications appellent **SQLGetDiagRec** pour récupérer SQLSTATE, code d’erreur natif et messages de diagnostic. Appel **SQLGetDiagField** et en spécifiant le champ extrait les champs de diagnostics individuels. Le niveau de prise en charge des identificateurs de diagnostics est répertorié dans le tableau suivant.  
  
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
|SQL_DIAG_RETURNCODE|Prise en charge, mais elle est implémentée par le Gestionnaire de pilotes|  
|SQL_DIAG_ROW_COUNT|Pris en charge|  
|SQL_DIAG_ROW_NUMBER|Pris en charge|  
|SQL_DIAG_SERVER_NAME|Non pris en charge|  
|SQL_DIAG_SQLSTATE|Pris en charge|  
|SQL_DIAG_SUBCLASS_ORIGIN|Pris en charge|
