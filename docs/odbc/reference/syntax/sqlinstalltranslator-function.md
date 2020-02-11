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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5b973332c2fe0fa541635d326a3a5adecf6ae91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076113"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator, fonction
**Conformité**  
 Version introduite : ODBC 2,5, déconseillé  
  
 **Résumé**  
 Dans ODBC 3,0, **sqlinstalltranslator,** a été remplacé par [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Les appels à **sqlinstalltranslator,** sont mappés à **SQLInstallTranslatorEx**. Pour plus d’informations, consultez **SQLInstallTranslatorEx**.  
  
 **Sqlinstalltranslator,** retourne la valeur false si une application l’appelle dans le gestionnaire de pilotes ODBC *3. x* avec l’argument *lpszInfFile* défini sur une valeur autre que NULL. Le fichier ODBC. inf utilisé dans ODBC *2. x* n’est plus pris en charge dans ODBC *3. x*, même pour la compatibilité descendante.
