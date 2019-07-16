---
title: SQLSetScrollOptions (pilotes pour les postes de travail de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0adedfb69cd4a7b5cf195916747687826805e8bf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905392"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (pilotes pour les bases de données de poste de travail)
SQL_CONCUR_READ_ONLY prennent en charge les curseurs statiques et vers l’avant.  
  
 Uniquement les curseurs keyset sont pris en charge pour un *fConcurrency* argument de SQL_CONCUR_LOCK.  
  
 Un *fConcurrency* argument de SQL_CONCUR_ROWVER n’est pas pris en charge.  
  
 Les curseurs Dynamic et curseurs mixtes ne sont pas pris en charge.
