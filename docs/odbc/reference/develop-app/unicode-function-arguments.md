---
title: Arguments des fonctions Unicode | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0e67f437cd629411230daed17f6a39f24b7103d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669457"
---
# <a name="unicode-function-arguments"></a>Arguments des fonctions Unicode
Le Gestionnaire de pilotes ODBC 3.5 (ou version ultérieure) prend en charge les versions ANSI et Unicode de toutes les fonctions qui acceptent des pointeurs vers des chaînes de caractères ou SQLPOINTER dans leurs arguments. Les fonctions Unicode sont implémentées en tant que fonctions (avec le suffixe de *W*), et non comme macros. Les fonctions ANSI (qui peut être appelé avec ou sans le suffixe *A*) sont identiques aux fonctions API ODBC en cours.  
  
## <a name="remarks"></a>Notes  
 Unicode des fonctions qui retournent toujours ou de prennent des chaînes ou des arguments de longueur sont passées en tant que nombre de caractères. Pour les fonctions qui retournent des informations de longueur pour les données de serveur, la taille d’affichage et la précision sont décrits dans le nombre de caractères. Lorsque les données de chaîne ou sans chaînes peut désigner une longueur (taille de transfert des données), la longueur est décrite dans la longueur d’octet. Par exemple, **SQLGetInfoW** prendra toujours la longueur que le nombre d’octets, mais **SQLExecDirectW** utilisera le nombre de caractères.  
  
 Nombre de caractères fait référence au nombre d’octets (octets) pour les fonctions ANSI et le nombre de WCHAR (mots de 16 bits) pour les fonctions UNICODE. En particulier, une séquence de caractères de deux octets (DBCS) ou une séquence de caractères multioctets (MBCS) peut être composée de plusieurs octets. Une séquence de caractères Unicode UTF-16 peut être composée de plusieurs WCHAR.  
  
 Voici une liste des fonctions API ODBC qui prennent en charge les versions Unicode (W) et ANSI (A) :  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagField**|  
|**SQLColAttribute**|**SQLGetDiagRec**|  
|**SQLColAttributes**|**SQLGetInfo**|  
|**SQLColumnPrivileges**|**SQLGetStmtAttr**|  
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
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
  
 Voici une liste des fonctions de programme d’installation ODBC et convertisseur ODBC qui prennent en charge les versions Unicode (W) et ANSI (A) :  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC n'**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]  
>  Fonctions déconseillées ont prise en charge du mappage Unicode en ANSI, car le ODBC 3 *.x* Gestionnaire de pilotes prend en charge la recompilation d’ODBC 2. *x* des applications avec le UNICODE **#define**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Applications Unicode](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Pilotes Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Mappage des fonctions dans le gestionnaire de pilotes](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
