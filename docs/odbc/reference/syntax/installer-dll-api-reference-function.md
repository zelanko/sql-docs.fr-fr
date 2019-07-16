---
title: Fonction de référence de l’API de DLL de programme d’installation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installer DLL [ODBC]
ms.assetid: 47fcadc3-f102-4989-9ee7-a1c65233142a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4478595fe34e81919a67c37a7f0a714329a5ea44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906213"
---
# <a name="installer-dll-api-reference-function"></a>Informations de référence sur les fonctions de l’API de la DLL d’installation
Cette section décrit la syntaxe des fonctions dans le programme d’installation des API de DLL. Le programme d’installation que DLL API se compose de 20 fonctions. Trois de ces fonctions, **SQLGetTranslator**, **SQLRemoveDSNFromIni**, et **SQLWriteDSNToIni**, sont appelés uniquement par le programme d’installation DLL. Les autres fonctions sont appelées par les programmes d’installation et administration.  
  
 Chaque fonction est étiquetée avec la version d’ODBC dans lequel il a été introduit.  
  
 Cette section contient les rubriques suivantes.  
  
-   [SQLConfigDataSource, fonction](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)  
  
-   [SQLConfigDriver, fonction](../../../odbc/reference/syntax/sqlconfigdriver-function.md)  
  
-   [SQLCreateDataSource, fonction](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)  
  
-   [SQLGetConfigMode, fonction](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)  
  
-   [SQLGetInstalledDrivers, fonction](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)  
  
-   [SQLGetPrivateProfileString, fonction](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)  
  
-   [SQLGetTranslator, fonction](../../../odbc/reference/syntax/sqlgettranslator-function.md)  
  
-   [SQLInstallDriverEx, fonction](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)  
  
-   [SQLInstallDriverManager, fonction](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)  
  
-   [SQLInstallerError, fonction](../../../odbc/reference/syntax/sqlinstallererror-function.md)  
  
-   [SQLInstallTranslator, fonction](../../../odbc/reference/syntax/sqlinstalltranslator-function.md)  
  
-   [SQLInstallTranslatorEx, fonction](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)  
  
-   [SQLManageDataSources (fonction)](../../../odbc/reference/syntax/sqlmanagedatasources.md)  
  
-   [SQLPostInstallerError, fonction](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)  
  
-   [SQLReadFileDSN, fonction](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)  
  
-   [SQLRemoveDefaultDataSource, fonction](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)  
  
-   [SQLRemoveDriver, fonction](../../../odbc/reference/syntax/sqlremovedriver-function.md)  
  
-   [SQLRemoveDriverManager, fonction](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)  
  
-   [SQLRemoveDSNFromIni, fonction](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)  
  
-   [SQLRemoveTranslator, fonction](../../../odbc/reference/syntax/sqlremovetranslator-function.md)  
  
-   [SQLSetConfigMode, fonction](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)  
  
-   [SQLValidDSN, fonction](../../../odbc/reference/syntax/sqlvaliddsn-function.md)  
  
-   [SQLWriteDSNToIni, fonction](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)  
  
-   [SQLWriteFileDSN, fonction](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)  
  
-   [SQLWritePrivateProfileString, fonction](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)
