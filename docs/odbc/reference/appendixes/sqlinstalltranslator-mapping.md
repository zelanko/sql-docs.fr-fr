---
title: Mappage Sqlinstalltranslator, | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6433df796c88abd7873915266d1a2ca4041a5c62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125726"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator, mappage
Quand une application ODBC *2. x* appelle **sqlinstalltranslator,** via un pilote ODBC *3. x* , le gestionnaire de pilotes mappe l’appel à **SQLInstallTranslatorEx**. Une application ne doit pas appeler **sqlinstalltranslator,** dans le gestionnaire de pilotes ODBC *3. x* avec l’argument *lpszInfFile* défini sur une valeur autre que NULL. ODBC. Le fichier INF utilisé dans ODBC *2. x* n’est plus pris en charge dans ODBC *3. x*, même pour la compatibilité descendante.
