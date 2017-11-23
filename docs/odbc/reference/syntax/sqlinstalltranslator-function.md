---
title: Fonction de SQLInstallTranslator | Documents Microsoft
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
apiname: SQLInstallTranslator
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLInstallTranslator
helpviewer_keywords: SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef9452b9ff442ec5ed40b7eb38957936d31d16b5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator (fonction)
**Mise en conformité**  
 Version introduite : ODBC 2.5, déconseillée  
  
 **Résumé**  
 Dans la version 3.0 d’ODBC, **SQLInstallTranslator** a été remplacé par [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Les appels à **SQLInstallTranslator** sera mappé à **SQLInstallTranslatorEx**. Pour plus d’informations, consultez **SQLInstallTranslatorEx**.  
  
 **SQLInstallTranslator** retourne FALSE si une application appelle dans ODBC 3*.x* du Gestionnaire de pilotes avec les *lpszInfFile* argument défini sur une valeur différente de NULL. Le fichier Odbc.inf utilisé dans ODBC 2. *x* n’est plus pris en charge dans ODBC 3*.x*, même pour la compatibilité descendante.
