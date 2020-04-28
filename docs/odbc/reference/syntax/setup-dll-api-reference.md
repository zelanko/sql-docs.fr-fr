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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25cff50b73868b5b3015dfc1a00c560c344a6d36
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298884"
---
# <a name="setup-dll-api-reference"></a>Informations de référence sur l’API de la DLL de configuration
Cette section décrit la syntaxe de l’API DLL d’installation du pilote, qui se compose de deux fonctions (**ConfigDriver** et **ConfigDSN**). **ConfigDriver** et **ConfigDSN** peuvent être dans la dll du pilote ou dans une DLL d’installation distincte.  
  
 En outre, cette section décrit la syntaxe de l’API DLL d’installation du traducteur, qui se compose d’une fonction unique (**ConfigTranslator**). **ConfigTranslator** peut être dans la dll du traducteur ou dans une DLL d’installation distincte.  
  
 Chaque fonction est étiquetée avec la version ODBC dans laquelle elle a été introduite.  
  
 Cette section contient les rubriques suivantes :  
  
-   [ConfigDriver, fonction](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN, fonction](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator, fonction](../../../odbc/reference/syntax/configtranslator-function.md)
