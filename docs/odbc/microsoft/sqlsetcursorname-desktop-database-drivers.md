---
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
ms.openlocfilehash: 5d618a7f845a87394c2fc3c7978a7aef5716e21f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301480"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (pilotes pour les bases de données de poste de travail)
Étant donné que le pilote ne prend pas en charge une mise à jour ou une suppression positionnée par la syntaxe WHERE CURRENT OF *CursorName* , **SQLSetCursorName** est pris en charge, mais ne peut pas être utilisé pour les mises à jour positionnées. Il ne peut être utilisé que lorsque la bibliothèque de curseurs est activée et que l’application utilise **SQLExtendedFetch**.
