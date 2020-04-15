---
title: Arguments de fonction Unicode (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284289"
---
# <a name="unicode-function-arguments"></a>Arguments des fonctions Unicode
L’ODBC 3.5 (ou plus) Driver Manager prend en charge les versions ANSI et Unicode de toutes les fonctions qui acceptent les indications aux chaînes de caractères ou SQLPOINTER dans leurs arguments. Les fonctions Unicode sont implémentées comme fonctions (avec un suffixe de *W),* et non comme macros. Les fonctions ANSI (qui peuvent être appelées avec ou sans suffixe de *A*) sont identiques aux fonctions actuelles de l’API ODBC.  
  
## <a name="remarks"></a>Notes  
 Les fonctions Unicode qui retournent ou prennent toujours des arguments de cordes ou de longueur sont passées comme des caractères de compte. Pour les fonctions qui renvoient les informations de longueur pour les données du serveur, la taille et la précision de l’affichage sont décrites en nombre de caractères. Lorsqu’une longueur (taille de transfert des données) peut se référer à des données de chaîne ou de non-corde, la longueur est décrite dans les longueurs des oscètes. Par exemple, **SQLGetInfoW** prendra toujours la longueur en tant que comte-d’octets, mais **SQLExecDirectW** utilisera le compte-de-caractères.  
  
 Le nombre de caractères se réfère au nombre d’octets (octets) pour les fonctions ANSI et au nombre de mots WCHAR (16 bits) pour les fonctions UNICODE. En particulier, une séquence de caractères à double octet (DBCS) ou une séquence de caractères multioctets (MBCS) peut être composée de plusieurs octets. Une séquence de caractères UTF-16 Unicode peut être composée de plusieurs WCHAR.  
  
 Voici une liste des fonctions API de l’ODBC qui prennent en charge les versions Unicode (W) et ANSI (A) :  
  
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
|**Sqlerror**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption (SQLGetConnectOption)**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 Voici une liste des fonctions ODBC Installer et ODBC Translator qui prennent en charge les versions Unicode (W) et ANSI (A) :  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource (en anglais)**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource (en anglais)**|**SQLReadFileDSN**|  
|**SQLGetAvailableProteurs**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator (SQLGetTranslator)**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  Les fonctions dépréciées ont un support cartographique Unicode-à-ANSI parce que l’ODBC *3.x* Driver Manager prend en charge la recomplation des applications ODBC *2.x* avec l’UNICODE **#define**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Applications Unicode](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Pilotes Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Mappage des fonctions dans le gestionnaire de pilotes](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
