---
title: SQLInstallTranslator, fonction | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 08a9e3a1afef8b9ea3bf1f4266196341e0edeb76
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792864"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator, fonction
**Conformité**  
 Version introduite : ODBC 2.5, déconseillée  
  
 **Résumé**  
 Dans ODBC 3.0, **SQLInstallTranslator** a été remplacé par [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md). Les appels à **SQLInstallTranslator** sera mappé à **SQLInstallTranslatorEx**. Pour plus d’informations, consultez **SQLInstallTranslatorEx**.  
  
 **SQLInstallTranslator** renvoie la valeur FALSE si une application l’appelle dans le système ODBC *3.x* Gestionnaire de pilotes avec les *lpszInfFile* argument défini sur une valeur autre que NULL. Le fichier Odbc.inf utilisé dans ODBC *2.x* n’est plus pris en charge dans ODBC *3.x*, même pour la compatibilité descendante.
