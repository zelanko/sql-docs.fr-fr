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
ms.openlocfilehash: 50bfa00f482110d3d0695ef249e8758b5db02c80
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792812"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator, mappage
Lorsqu’une application ODBC *2.x* application appelle **SQLInstallTranslator** via une application ODBC *3.x* pilote, le Gestionnaire de pilotes mappe l’appel à  **SQLInstallTranslatorEx**. Une application ne doit pas appeler **SQLInstallTranslator** dans ODBC *3.x* Gestionnaire de pilotes avec les *lpszInfFile* argument défini sur une valeur autre que NULL. ODBC. Fichier INF utilisé dans ODBC *2.x* n’est plus pris en charge dans ODBC *3.x*, même pour la compatibilité descendante.
