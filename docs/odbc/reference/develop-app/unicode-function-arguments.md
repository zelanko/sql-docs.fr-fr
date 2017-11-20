---
title: Arguments de la fonction Unicode | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff461881ea10c904ceefd1c51a364984ca10971b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="unicode-function-arguments"></a>Arguments de la fonction Unicode
Le Gestionnaire de pilotes ODBC 3.5 (ou version ultérieure) prend en charge les versions ANSI et Unicode de toutes les fonctions qui acceptent des pointeurs vers des chaînes de caractères ou SQLPOINTER dans leurs arguments. Les fonctions Unicode sont implémentées en tant que fonctions (avec un suffixe de nom *W*), et non comme macros. Les fonctions ANSI (qui peut être appelé avec ou sans le suffixe *A*) sont identiques aux fonctions API ODBC en cours.  
  
## <a name="remarks"></a>Notes  
 Fonctions Unicode toujours renvoyer ou prennent des chaînes ou des arguments de longueur sont passées en tant que nombre de caractères. Pour les fonctions qui retournent des informations de longueur pour les données de serveur, la taille d’affichage et la précision sont décrits dans le nombre de caractères. Lorsque les données de chaîne ou qui peut désigner une longueur (taille de transfert des données), la longueur est décrite dans la longueur d’octet. Par exemple, **SQLGetInfoW** continuent à occuper de la longueur en tant que nombre d’octets, mais **SQLExecDirectW** utilisera nombre de caractères.  
  
 -Nombre de caractères fait référence au nombre d’octets (octets) pour les fonctions ANSI et le nombre de WCHAR (mots 16 bits) pour les fonctions UNICODE. En particulier, une séquence de caractères à deux octets (DBCS) ou une séquence de caractères multioctets (MBCS) peut être composée de plusieurs octets. Une séquence de caractères Unicode UTF-16 peut être composée de plusieurs WCHAR.  
  
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
>  Fonctions déconseillées ont prise en charge du mappage Unicode en ANSI, car la version ODBC 3*.x* du Gestionnaire de pilotes prend en charge la recompilation ODBC 2. *x* applications avec UNICODE **#define**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Applications Unicode](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Pilotes d’Unicode](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [Mappage de fonction dans le Gestionnaire de pilotes](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)

