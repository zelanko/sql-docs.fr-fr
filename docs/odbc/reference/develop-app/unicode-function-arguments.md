---
title: Arguments de fonction Unicode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a25dd6fe0a77aad5c5ec9ba15eaf12bd2ec3fc18
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284289"
---
# <a name="unicode-function-arguments"></a>Arguments des fonctions Unicode
Le gestionnaire de pilotes ODBC 3,5 (ou version ultérieure) prend en charge les versions ANSI et Unicode de toutes les fonctions qui acceptent des pointeurs vers des chaînes de caractères ou des SQLPOINTER dans leurs arguments. Les fonctions Unicode sont implémentées en tant que fonctions (avec un suffixe *W*), et non pas en tant que macros. Les fonctions ANSI (qui peuvent être appelées avec ou sans suffixe *) sont*identiques aux fonctions de l’API ODBC en cours.  
  
## <a name="remarks"></a>Notes  
 Les fonctions Unicode qui renvoient ou prennent toujours des chaînes ou des arguments de longueur sont passées en tant que nombre de caractères. Pour les fonctions qui retournent des informations de longueur pour les données du serveur, la taille et la précision d’affichage sont décrites en nombre de caractères. Quand une longueur (taille de transfert des données) peut faire référence à des données de type chaîne ou non, la longueur est décrite en octets. Par exemple, **SQLGetInfoW** prend toujours la longueur comme nombre d’octets, mais **SQLExecDirectW** utilise le nombre de caractères.  
  
 Nombre de caractères fait référence au nombre d’octets (octets) pour les fonctions ANSI et au nombre de WCHAR (mots 16 bits) pour les fonctions UNICODE. En particulier, une séquence de caractères codés sur deux octets (DBCS) ou une séquence de caractères multioctets (MBCS) peut être composée de plusieurs octets. Une séquence de caractères Unicode UTF-16 peut être composée de plusieurs WCHARs.  
  
 La liste suivante répertorie les fonctions d’API ODBC qui prennent en charge à la fois les versions Unicode (W) et ANSI (A) :  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagRec**|  
|**SQLColAttribute**|**SQLGetInfo**|  
|**SQLColAttributes**|**SQLGetStmtAttr**|  
|**SQLColumnPrivileges**|**SQLGetTypeInfo**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**Sqlgetconnectoption,**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 La liste suivante répertorie les fonctions ODBC installer et convertisseur ODBC qui prennent en charge les versions Unicode (W) et ANSI (A) :  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  Les fonctions déconseillées ont une prise en charge du mappage Unicode-à-ANSI, car le gestionnaire de pilotes ODBC *3. x* prend en charge la recompilation des applications ODBC *2. x* avec les **#define**Unicode.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Applications Unicode](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Pilotes Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Mappage des fonctions dans le gestionnaire de pilotes](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
