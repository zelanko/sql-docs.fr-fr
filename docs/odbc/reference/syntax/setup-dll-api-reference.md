---
title: Informations de référence sur l’API DLL d’installation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26e5c36b41f68627a634714cfa06525c99451450
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947053"
---
# <a name="setup-dll-api-reference"></a>Informations de référence sur l’API de la DLL de configuration
Cette section décrit la syntaxe de l’API DLL d’installation du pilote, qui se compose de deux fonctions (**ConfigDriver** et **ConfigDSN**). **ConfigDriver** et **ConfigDSN** peuvent être dans la dll du pilote ou dans une DLL d’installation distincte.  
  
 En outre, cette section décrit la syntaxe de l’API DLL d’installation du traducteur, qui se compose d’une fonction unique (**ConfigTranslator**). **ConfigTranslator** peut être dans la dll du traducteur ou dans une DLL d’installation distincte.  
  
 Chaque fonction est étiquetée avec la version ODBC dans laquelle elle a été introduite.  
  
 Cette section contient les rubriques suivantes :  
  
-   [ConfigDriver, fonction](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN, fonction](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator, fonction](../../../odbc/reference/syntax/configtranslator-function.md)
