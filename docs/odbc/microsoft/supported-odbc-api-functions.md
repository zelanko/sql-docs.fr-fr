---
title: Fonctions D’API D’ODBC soutenues ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC, API functions
- ODBC SQL grammar, API functions mapped to driver (table) [ODBC]
ms.assetid: b28a8ed6-09b1-4acf-bf3e-f90bb32422de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec6ceaf57d8fe3c5325f85a9644cf4c8016663e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304100"
---
# <a name="supported-odbc-api-functions"></a>Fonctions de l’API ODBC prises en charge
Le but du nivellement est d’informer l’application des caractéristiques qui lui sont disponibles auprès du conducteur. Les pilotes microsoft ODBC Desktop Database prennent en charge toutes les fonctions Core et Level 1.  
  
 Pour plus d’informations sur les niveaux de conformité pour les fonctions et la grammaire, voir [Niveaux de conformité](../../odbc/reference/develop-app/conformance-levels.md) dans la référence du *programmeur ODBC*.  
  
 Le soutien des fonctions API D’ODBC peut dépendre du conducteur utilisé. Le tableau suivant résume le support des fonctions. La colonne la plus à gauche fournit un lien vers la page de référence générale pour chaque fonction. Ces pages de référence sont répertoriées par ordre alphabétique dans la section [de référence de l’ODBC API,](../../odbc/reference/syntax/odbc-api-reference.md) dans le cadre [de la référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md). Les colonnes à droite fournissent des liens vers des notes spécifiques au conducteur sur chaque fonction supportée. Ces sujets spécifiques au conducteur sont énumérés dans la section « Autres détails de programmation » pour chaque pilote. Alternativement, si les mêmes remarques au sujet d’une fonction s’appliquent à tous les pilotes de base de données de bureau ODBC, la colonne la plus juste fournit un lien vers un sujet qui résume le soutien des pilotes de base de données de bureau pour cette fonction. Ces sujets sont énumérés à la fin de la section actuelle (« Fonctions D’API de l’ODBC]).  
  
|Fonction ODBC|Accédez à des notes spécifiques au conducteur|dBASE Notes spécifiques au conducteur|Notes spécifiques à Paradox Driver|Text File Notes spécifiques au conducteur|Notes spécifiques au conducteur Excel|Notes pertinentes à tous les conducteurs|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)|[y accéder](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[y accéder](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[y accéder](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[Dbase](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[y accéder](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[Dbase](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[y accéder](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)|
|[SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)|  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[y accéder](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[y accéder](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)||||||  
|[SQLProcedures](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[y accéder](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[Dbase](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[SQLSetPos](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[Tous les pilotes](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|[SQLStatistics](../../odbc/reference/syntax/sqlstatistics-function.md)|[y accéder](../../odbc/microsoft/sqlstatistics-access-driver.md)|[Dbase](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[y accéder](../../odbc/microsoft/sqltables-access-driver.md)|[Dbase](../../odbc/microsoft/sqltables-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqltables-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)|  
|[SQLTransacte](../../odbc/reference/syntax/sqltransact-function.md)|[y accéder](../../odbc/microsoft/sqltransact-access-driver.md)|[Dbase](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Paradoxe](../../odbc/microsoft/sqltransact-paradox-driver.md)|[Fichier texte](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 Les sujets suivants fournissent des remarques sur les fonctions de l’ODBC. Ces remarques s’appliquent à tous les pilotes de base de données de bureau ODBC.  
  
-   [SQLGetData (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [SQLGetStmtOption (Desktop Database Drivers)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (pilotes pour les bases de données de poste de travail)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
