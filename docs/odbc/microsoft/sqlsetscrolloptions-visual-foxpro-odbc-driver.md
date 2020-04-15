---
title: SQLSetScrollOptions (Visual FoxPro ODBC Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19051fc83466bc40d72c029089cfe6ec45c20a08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299419"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Partielle  
  
 Conformité API ODBC: Niveau 2  
  
 Définit les options qui contrôlent le comportement des curseurs associés à une poignée de déclaration, *hstmt*.  
  
 Le visual FoxPro ODBC Driver ne prend en charge que SQL_CONCUR_READ_ONLY; il ne prend pas en charge la valeur *fConcurrency* SQL_CONCUR_ROWVER. Le conducteur convertit SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC et SQL_CURSOR_KEYSET_DRIVEN pour SQL_SCROLL_STATIC avec des ODBC_01S02 d’avertissement.  
  
 Pour plus d’informations, voir [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) dans la *référence du programmeur ODBC*.
