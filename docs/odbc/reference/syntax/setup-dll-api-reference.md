---
title: "Référence des API de DLL d’installation | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc1e600ad9b1a7c38150fdbc1ad346fde2b02b0f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="setup-dll-api-reference"></a>Référence des API de DLL d’installation
Cette section décrit la syntaxe de l’API de DLL, qui se compose de deux fonctions d’installation du pilote (**ConfigDriver** et **ConfigDSN**). **ConfigDriver** et **ConfigDSN** peut se trouver dans la DLL du pilote ou dans une fonction DLL d’installation.  
  
 En outre, cette section décrit la syntaxe de l’installation du traducteur API de DLL, qui se compose d’une seule fonction (**ConfigTranslator**). **ConfigTranslator** peut se trouver dans la DLL de traduction ou dans une fonction DLL d’installation.  
  
 Chaque fonction est étiquetée avec la version d’ODBC dans lequel elle a été introduite.  
  
 Cette section contient les rubriques suivantes.  
  
-   [ConfigDriver, fonction](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN, fonction](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator, fonction](../../../odbc/reference/syntax/configtranslator-function.md)
