---
title: Diagnostics pour les pilotes de base de données de bureau (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 99603c047e77d3cd3e077c1b07c2192eeb65f93c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303480"
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Diagnostics des pilotes pour les bases de données de poste de travail
Toutes les erreurs et avertissements non vérifiés ou partiellement vérifiés par le gestionnaire de conducteur sont gérés par le conducteur. Le conducteur cartographie également les erreurs indigènes, ou les erreurs retournées par la source de données, aux SQLSTATEs. Chaque fonction figurant dans la *référence du programmeur de l’ODBC* contient une section « Diagnostics » qui spécifie les conditions et les messages.  
  
 Les applications appellent **SQLGetDiagRec** pour récupérer SQLSTATE, code d’erreur natif et messages diagnostiques. Appeler **SQLGetDiagField** et spécifier le champ récupère les champs de diagnostic individuels. Le niveau de support des identificateurs diagnostiques est répertorié dans le tableau suivant.  
  
|DiagIdentificateurs|Niveau de support|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Non pris en charge|  
|SQL_DIAG_CLASS_ORIGIN|Pris en charge. Toujours "ODBC 3.0" pour les versions 3.0 et plus tard de ce pilote.|  
|SQL_DIAG_COLUMN_NUMBER|Prise en charge|  
|SQL_DIAG_CURSOR_ROW_COUNT|Non pris en charge|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Non pris en charge|  
|SQL_DIAG_MESSAGE_TEXT|Prise en charge|  
|SQL_DIAG_NATIVE|Prise en charge|  
|SQL_DIAG_NUMBER|Prise en charge|  
|SQL_DIAG_RETURNCODE|Soutenu mais mis en œuvre par le Driver Manager|  
|SQL_DIAG_ROW_COUNT|Prise en charge|  
|SQL_DIAG_ROW_NUMBER|Prise en charge|  
|SQL_DIAG_SERVER_NAME|Non pris en charge|  
|SQL_DIAG_SQLSTATE|Prise en charge|  
|SQL_DIAG_SUBCLASS_ORIGIN|Prise en charge|
