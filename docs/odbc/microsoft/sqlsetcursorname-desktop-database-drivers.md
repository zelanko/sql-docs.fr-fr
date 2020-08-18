---
description: SQLSetCursorName (pilotes pour les bases de données de poste de travail)
title: SQLSetCursorName (pilotes de base de données de bureau) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 14fe15c6cdbdf50e6d28ca7e9a1168f54626e83b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411553"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (pilotes pour les bases de données de poste de travail)
Étant donné que le pilote ne prend pas en charge une mise à jour ou une suppression positionnée par la syntaxe WHERE CURRENT OF *CursorName* , **SQLSetCursorName** est pris en charge, mais ne peut pas être utilisé pour les mises à jour positionnées. Il ne peut être utilisé que lorsque la bibliothèque de curseurs est activée et que l’application utilise **SQLExtendedFetch**.
