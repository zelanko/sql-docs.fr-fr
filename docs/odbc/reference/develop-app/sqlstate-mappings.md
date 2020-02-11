---
title: Mappages SQLSTATE | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3987085d7d04bf248bcc728c3bcd1ee5503d9af1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107361"
---
# <a name="sqlstate-mappings"></a>Mappages SQLSTATE
Cette rubrique décrit les valeurs SQLSTATE pour ODBC *2. x* et ODBC *3. x*. Pour plus d’informations sur les valeurs SQLSTATE ODBC *3. x* , consultez [annexe A : codes d’erreur ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 Dans ODBC *3. x*, les SQLSTATE HYxxx sont retournées à la place de S1xxx, et les SQLSTATE 42Sxx sont retournés au lieu de S00XX. Cela a été fait pour s’aligner sur les normes Open Group et ISO. Dans de nombreux cas, le mappage n’est pas un-à-un, car les normes ont redéfini l’interprétation de plusieurs SQLSTATEs.  
  
 Quand une application ODBC *2. x* est mise à niveau vers une application ODBC *3. x* , l’application doit être modifiée pour s’attendre à obtenir des SQLSTATE ODBC *3. x* au lieu des SQLSTATE ODBC *2. x* . Le tableau suivant répertorie les SQLSTATE ODBC *3. x* auxquelles chaque valeur SQLSTATE ODBC *2. x* est mappée.  
  
 Lorsque l’attribut d’environnement SQL_ATTR_ODBC_VERSION est défini sur SQL_OV_ODBC2, le pilote publie les SQLSTATE ODBC *2. x* au lieu des SQLSTATE ODBC *3. x* lors de l’appel de **SQLGetDiagField** ou **SQLGetDiagRec** . Un mappage spécifique peut être déterminé en notant la valeur SQLSTATE ODBC *2. x* dans la colonne 1 du tableau suivant qui correspond à ODBC *3. x* SQLSTATE dans la colonne 2.  
  
|ODBC *2. x* SQLSTATE|ODBC *3. x* SQLSTATE|Commentaires|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24 000|07005||  
|37000|42000||  
|70100|HY018||  
|S0001|42S01||  
|S0002|42S02||  
|S0011|42S11||  
|S0012|42S12||  
|S0021|42S21||  
|S0022|42S22||  
|S0023|42S23||  
|S1000|HY000||  
|S1001|HY001||  
|S1002|07009|ODBC *2. x* SQLSTATE S1002 est MAPPÉ à ODBC *3. x* SQLSTATE 07009 si la fonction sous-jacente **est SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch**, **SQLFetchScroll**ou **SQLGetData**.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Retourné pour une utilisation non valide d’un pointeur null.|  
|S1009|HY024|Retourné pour une valeur d’attribut non valide.|  
|S1009|HY092|Retourné pour la mise à jour ou la suppression de données par un appel à **SQLSetPos**, ou l’ajout, la mise à jour ou la suppression de données par un appel à **SQLBulkOperations**, lorsque la concurrence est en lecture seule.|  
|S1010|HY007 HY010|SQLSTATE S1010 est mappé à SQLSTATE HY007 lorsque **SQLDescribeCol** est appelé avant d’appeler **SQLPrepare**, **SQLExecDirect**ou une fonction de catalogue pour *StatementHandle*. Dans le cas contraire, SQLSTATE S1010 est mappé à SQLSTATE HY010.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC *3. x* SQLSTATE 07009 est MAPPÉ à ODBC *2. x* SQLSTATE S1093 si la fonction sous-jacente est **SQLBindParameter** ou **SQLDescribeParam**.|  
|S1096|HY096||  
|S1097|HY097||  
|S1098|HY098||  
|S1099|HY099||  
|S1100|HY100||  
|S1101|HY101||  
|S1103|HY103||  
|S1104|HY104||  
|S1105|HY105||  
|S1106|HY106||  
|S1107|HY107||  
|S1108|HY108||  
|S1109|HY109||  
|S1110|HY110||  
|S1111|HY111||  
|S1C00|HYC00||  
|S1T00|HYT00||  
  
> [!NOTE]  
>  ODBC *3. x* SQLSTATE 07008 est MAPPÉ à ODBC *2. x* SQLSTATE S1000.
