---
title: Mappage de SQLInstallTranslator | Documents Microsoft
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
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb17f3d77b39c43d1f20c4598ac0192332a9cf13
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlinstalltranslator-mapping"></a>Mappage de SQLInstallTranslator
Lorsqu’une application ODBC 2. *x* application appelle **SQLInstallTranslator** via un ODBC 3*.x* pilote, le Gestionnaire de pilotes est mappé à l’appel à **SQLInstallTranslatorEx**. Une application ne doit pas appeler **SQLInstallTranslator** dans ODBC 3*.x* du Gestionnaire de pilotes avec les *lpszInfFile* argument défini sur une valeur différente de NULL. ODBC. Fichier INF utilisé dans ODBC 2. *x* n’est plus pris en charge dans ODBC 3*.x*, même pour la compatibilité descendante.
