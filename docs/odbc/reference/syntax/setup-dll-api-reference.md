---
title: Référence des API de DLL d’installation | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: d81bb9f5ec54f3d66089205f5b5941119d365501
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62652897"
---
# <a name="setup-dll-api-reference"></a>Informations de référence sur l’API de la DLL de configuration
Cette section décrit la syntaxe de l’installation du pilote API de DLL, qui se compose de deux fonctions (**ConfigDriver** et **ConfigDSN**). **ConfigDriver** et **ConfigDSN** peut se trouver dans la DLL du pilote ou dans une fonction DLL d’installation.  
  
 En outre, cette section décrit la syntaxe traducteur du paramétrage de l’API de DLL, qui se compose d’une seule fonction (**ConfigTranslator**). **ConfigTranslator** peut se trouver dans la DLL de traduction ou dans une fonction DLL d’installation.  
  
 Chaque fonction est étiquetée avec la version d’ODBC dans lequel il a été introduit.  
  
 Cette section contient les rubriques suivantes.  
  
-   [ConfigDriver, fonction](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN, fonction](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator, fonction](../../../odbc/reference/syntax/configtranslator-function.md)
