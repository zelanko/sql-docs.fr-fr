---
title: SQLSetScrollOptions (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b3746d9cea2ce5ffb7d03424d7cda4fa1889aabc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905384"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Partielle  
  
 Conformité d’API ODBC : Niveau 2  
  
 Définit les options qui contrôlent le comportement des curseurs associé à un descripteur d’instruction, *hstmt*.  
  
 Le pilote ODBC Visual FoxPro prend en charge uniquement la valeur SQL_CONCUR_READ_ONLY ; Il ne prend pas en charge la *fConcurrency* SQL_CONCUR_ROWVER de valeur. Le pilote convertit SQL_KEYSET_SIZE, type SQL_CURSOR_DYNAMIC et SQL_CURSOR_KEYSET_DRIVEN SQL_SCROLL_STATIC avec avertissement ODBC_01S02.  
  
 Pour plus d’informations, consultez [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) dans le *de référence du programmeur ODBC*.
