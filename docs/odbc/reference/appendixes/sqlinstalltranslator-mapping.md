---
title: SQLInstallTranslator, mappage | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 9760bfad769e9508d58d1cd00f98376dbd13d877
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298507"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator, mappage
Lorsqu’une application ODBC 2. *x* application appelle **SQLInstallTranslator** via un ODBC 3 *.x* pilote, le Gestionnaire de pilotes mappe l’appel à **SQLInstallTranslatorEx**. Une application ne doit pas appeler **SQLInstallTranslator** dans ODBC 3 *.x* Gestionnaire de pilotes avec les *lpszInfFile* argument défini sur une valeur autre que NULL. ODBC. Fichier INF utilisé dans ODBC 2. *x* n’est plus pris en charge dans ODBC 3 *.x*, même pour la compatibilité descendante.
