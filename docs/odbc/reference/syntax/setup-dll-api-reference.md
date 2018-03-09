---
title: "Référence des API de DLL d’installation | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
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
ms.openlocfilehash: 953fbdf89defc5b17e3899cad3ec2077c693df9d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="setup-dll-api-reference"></a>Référence des API de DLL d’installation
Cette section décrit la syntaxe de l’API de DLL, qui se compose de deux fonctions d’installation du pilote (**ConfigDriver** et **ConfigDSN**). **ConfigDriver** et **ConfigDSN** peut se trouver dans la DLL du pilote ou dans une fonction DLL d’installation.  
  
 En outre, cette section décrit la syntaxe de l’installation du traducteur API de DLL, qui se compose d’une seule fonction (**ConfigTranslator**). **ConfigTranslator** peut se trouver dans la DLL de traduction ou dans une fonction DLL d’installation.  
  
 Chaque fonction est étiquetée avec la version d’ODBC dans lequel elle a été introduite.  
  
 Cette section contient les rubriques suivantes.  
  
-   [ConfigDriver, fonction](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN, fonction](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator, fonction](../../../odbc/reference/syntax/configtranslator-function.md)
