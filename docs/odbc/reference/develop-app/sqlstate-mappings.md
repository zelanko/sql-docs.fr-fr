---
title: Cartographie SQLSTATE Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec58c0e41869529bbba5fd31ad534976923a990d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299739"
---
# <a name="sqlstate-mappings"></a>Mappages SQLSTATE
Ce sujet traite des valeurs SQLSTATE pour ODBC *2.x* et ODBC *3.x*. Pour plus d’informations sur les valeurs ODBC *3.x* SQLSTATE, voir [Annexe A: ODBC Error Codes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 Dans ODBC *3.x*, HYxxx SQLSTATEs sont retournés au lieu de S1xxx, et 42Sxx SQLSTATEs sont retournés au lieu de S00XX. Cela a été fait pour s’aligner sur les normes Open Group et ISO. Dans de nombreux cas, la cartographie n’est pas en tête-à-tête parce que les normes ont redéfini l’interprétation de plusieurs SQLSTATEs.  
  
 Lorsqu’une application ODBC *2.x* est mise à niveau vers une application ODBC *3.x,* l’application doit être modifiée pour s’attendre à odBC *3.x* SQLSTATEs au lieu d’ODBC *2.x* SQLSTATEs. Le tableau suivant répertorie les SQLSTATEs ODBC *3.x* que chaque ODBC *2.x* SQLSTATE est cartographié.  
  
 Lorsque l’attribut de l’environnement SQL_ATTR_ODBC_VERSION est réglé pour SQL_OV_ODBC2, le conducteur affiche ODBC *2.x* SQLSTATEs au lieu d’ODBC *3.x* SQLSTATEs lorsque **SQLGetDiagField** ou **SQLGetDiagRec** est appelé. Une cartographie spécifique peut être déterminée en notant l’ODBC *2.x* SQLSTATE dans la colonne 1 du tableau suivant qui correspond à l’ODBC *3.x* SQLSTATE dans la colonne 2.  
  
|ODBC *2.x* SQLSTATE|ODBC *3.x* SQLSTATE|Commentaires|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24 000|07005||  
|37000|42000||  
|70100|HY018 HY018||  
|S0001 (en)|42S01||  
|S0002|42S02||  
|S0011 (en)|42S11||  
|S0012|42S12||  
|S0021|42S21||  
|S0022|42S22||  
|S0023|42S23||  
|S1000|HY000||  
|S1001|HY001 (hy001)||  
|S1002|07009|ODBC *2.x* SQLSTATE S1002 est cartographié à ODBC *3.x* SQLSTATE 07009 si la fonction sous-jacente est **SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData**.|  
|S1003|HY003 (HY003)||  
|S1004|HY004||  
|S1008|HY008 HY008||  
|S1009|HY009|Retourné pour une utilisation invalide d’un pointeur nul.|  
|S1009|HY024|Retourné pour une valeur d’attribut invalide.|  
|S1009|HY092 HY092|Retourné pour la mise à jour ou la suppression des données par un appel à **SQLSetPos**, ou l’ajout, la mise à jour ou la suppression des données par un appel à **SQLBulkOperations**, lorsque la concordance est lue uniquement.|  
|S1010|HY007 HY010|SQLSTATE S1010 est cartographié à SQLSTATE HY007 lorsque **SQLDescribeCol** est appelé avant d’appeler **SQLPrepare**, **SQLExecDirect**, ou une fonction de catalogue pour le *StatementHandle*. Sinon, SQLSTATE S1010 est cartographié à SQLSTATE HY010.|  
|S1011|HY011 HY011||  
|S1012|HY012||  
|S1090|HY090 HY090||  
|S1091|HY091 HY091||  
|S1092|HY092 HY092||  
|S1093|07009|ODBC *3.x* SQLSTATE 07009 est cartographié à ODBC *2.x* SQLSTATE S1093 si la fonction sous-jacente est **SQLBindParameter** ou **SQLDescribeParam**.|  
|S1096|HY096 HY096||  
|S1097|HY097 HY097||  
|S1098|HY098 HY098||  
|S1099|HY099 HY099||  
|S1100|Hy100||  
|S1101|Hy101||  
|S1103|HY103||  
|S1104|Hy104||  
|S1105|Hy105||  
|S1106|HY106||  
|S1107|HY107||  
|S1108|HY108||  
|S1109|HY109 HY109||  
|S1110|HY110||  
|S1111|HY111||  
|S1C00 (en)|HYC00||  
|S1T00|HYT00||  
  
> [!NOTE]  
>  ODBC *3.x* SQLSTATE 07008 est cartographié à ODBC *2.x* SQLSTATE S1000.
