---
title: Référence des API de DLL d’installation | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0c8ef5d12cbe85bf4a575fe0b7d8d2687e12b1b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="setup-dll-api-reference"></a>Référence des API de DLL d’installation
Cette section décrit la syntaxe de l’API de DLL, qui se compose de deux fonctions d’installation du pilote (**ConfigDriver** et **ConfigDSN**). **ConfigDriver** et **ConfigDSN** peut se trouver dans la DLL du pilote ou dans une fonction DLL d’installation.  
  
 En outre, cette section décrit la syntaxe de l’installation du traducteur API de DLL, qui se compose d’une seule fonction (**ConfigTranslator**). **ConfigTranslator** peut se trouver dans la DLL de traduction ou dans une fonction DLL d’installation.  
  
 Chaque fonction est étiquetée avec la version d’ODBC dans lequel elle a été introduite.  
  
 Cette section contient les rubriques suivantes.  
  
-   [ConfigDriver, fonction](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN, fonction](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator, fonction](../../../odbc/reference/syntax/configtranslator-function.md)
