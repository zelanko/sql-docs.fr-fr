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
manager: craigg
ms.openlocfilehash: 8c2d78e26309d5ea7dc5e6eed5a04e84a1651b33
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63305736"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Partielle  
  
 Conformité d’API ODBC : Niveau 2  
  
 Définit les options qui contrôlent le comportement des curseurs associé à un descripteur d’instruction, *hstmt*.  
  
 Le pilote ODBC Visual FoxPro prend en charge uniquement la valeur SQL_CONCUR_READ_ONLY ; Il ne prend pas en charge la *fConcurrency* SQL_CONCUR_ROWVER de valeur. Le pilote convertit SQL_KEYSET_SIZE, type SQL_CURSOR_DYNAMIC et SQL_CURSOR_KEYSET_DRIVEN SQL_SCROLL_STATIC avec avertissement ODBC_01S02.  
  
 Pour plus d’informations, consultez [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) dans le *de référence du programmeur ODBC*.
