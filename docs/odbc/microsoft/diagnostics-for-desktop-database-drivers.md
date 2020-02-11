---
title: Diagnostics pour les pilotes de base de données de bureau | Microsoft Docs
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
ms.openlocfilehash: d4e7c8ea96708886f9edf54047bd2a2104ba0ec8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68031223"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Diagnostics des pilotes pour les bases de données de poste de travail
Toutes les erreurs et tous les avertissements non vérifiés ou partiellement vérifiés par le gestionnaire de pilotes sont gérés par le pilote. Le pilote mappe également les erreurs natives, ou les erreurs retournées par la source de données, aux SQLSTATEs. Chaque fonction figurant dans le *Guide de référence du programmeur ODBC* contient une section « Diagnostics » qui spécifie des conditions et des messages.  
  
 Les applications appellent **SQLGetDiagRec** pour récupérer les messages SQLSTATE, le code d’erreur natif et les messages de diagnostic. L’appel de **SQLGetDiagField** et la spécification du champ récupèrent des champs de diagnostics individuels. Le niveau de prise en charge des identificateurs de diagnostic est indiqué dans le tableau suivant.  
  
|DiagIdentifiers|Niveau de support|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Non pris en charge|  
|SQL_DIAG_CLASS_ORIGIN| Pris en charge. Toujours « ODBC 3,0 » pour les versions 3,0 et ultérieures de ce pilote.|  
|SQL_DIAG_COLUMN_NUMBER|Prise en charge|  
|SQL_DIAG_CURSOR_ROW_COUNT|Non pris en charge|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Non pris en charge|  
|SQL_DIAG_MESSAGE_TEXT|Prise en charge|  
|SQL_DIAG_NATIVE|Prise en charge|  
|SQL_DIAG_NUMBER|Prise en charge|  
|SQL_DIAG_RETURNCODE|Pris en charge mais implémenté par le gestionnaire de pilotes|  
|SQL_DIAG_ROW_COUNT|Prise en charge|  
|SQL_DIAG_ROW_NUMBER|Prise en charge|  
|SQL_DIAG_SERVER_NAME|Non pris en charge|  
|SQL_DIAG_SQLSTATE|Prise en charge|  
|SQL_DIAG_SUBCLASS_ORIGIN|Prise en charge|
