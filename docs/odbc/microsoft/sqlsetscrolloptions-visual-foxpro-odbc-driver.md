---
description: SQLSetScrollOptions (pilote ODBC Visual FoxPro)
title: SQLSetScrollOptions (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.openlocfilehash: c0e7cecfb0ce7640575cb69f1e84e805a884b57b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421633"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : partielle  
  
 Conformité de l’API ODBC : niveau 2  
  
 Définit des options qui contrôlent le comportement des curseurs associés à un descripteur d’instruction, *HSTMT*.  
  
 Le pilote ODBC Visual FoxPro prend en charge uniquement SQL_CONCUR_READ_ONLY ; elle ne prend pas en charge la valeur *fConcurrency* SQL_CONCUR_ROWVER. Le pilote convertit SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC et SQL_CURSOR_KEYSET_DRIVEN en SQL_SCROLL_STATIC avec un avertissement ODBC_01S02.  
  
 Pour plus d’informations, consultez [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) dans le *Guide de référence du programmeur ODBC*.
