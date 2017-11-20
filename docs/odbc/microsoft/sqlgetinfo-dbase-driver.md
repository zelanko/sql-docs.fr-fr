---
title: SQLGetInfo (pilote dBASE) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetInfo
ms.assetid: 42ffdc9c-281b-4df5-ac6d-7b34f15ecd4c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d79bc7a4f83c3c5eccc69bebc1e8f5c29ffe6ac3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetinfo-dbase-driver"></a>SQLGetInfo (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** prend en charge le type d’informations SQL_FILE_USAGE. La valeur retournée est un entier 16 bits qui indique comment le pilote traite directement les fichiers dans une source de données :  
  
-   SQL_FILE_NOT_SUPPORTED : Le pilote n’est pas un pilote de niveau unique.  
  
-   SQL_FILE_TABLE : Un pilote de niveau unique traite les fichiers dans une source de données en tant que tables.  
  
-   SQL_FILE_QUALIFIER : Un pilote de niveau unique traite les fichiers dans une source de données en tant que qualificateur.  
  
 Le pilote ODBC retourne SQL_FILE_TABLE, car chaque fichier est une table.  
  
## <a name="sqlaltertable"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN &#124; SQL_AT_DROP_COLUMN  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Version|Format des numéros de version|  
|----------|-------------|-------------------------------|  
|DBASE|3.0|03.00.0000|  
||4.0|04.00.0000|  
||5.0|05.00.0000|  
  
## <a name="sqlddlindex"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION &#124; SQL_QU_INDEX_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_DAYOFMONTH &#124;  SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124;  SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124;  SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR

