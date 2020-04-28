---
title: Sqlinstalltranslator, fonction) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b094aa730fff6db80b9addb63a92bee0f5f85b2a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300319"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator, fonction
**Conformité**  
 Version introduite : ODBC 2,5, déconseillé  
  
 **Résumé**  
 Dans ODBC 3,0, **sqlinstalltranslator,** a été remplacé par [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Les appels à **sqlinstalltranslator,** sont mappés à **SQLInstallTranslatorEx**. Pour plus d’informations, consultez **SQLInstallTranslatorEx**.  
  
 **Sqlinstalltranslator,** retourne la valeur false si une application l’appelle dans le gestionnaire de pilotes ODBC *3. x* avec l’argument *lpszInfFile* défini sur une valeur autre que NULL. Le fichier ODBC. inf utilisé dans ODBC *2. x* n’est plus pris en charge dans ODBC *3. x*, même pour la compatibilité descendante.
