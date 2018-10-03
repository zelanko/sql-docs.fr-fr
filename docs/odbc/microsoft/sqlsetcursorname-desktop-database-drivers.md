---
title: SQLSetCursorName (pilotes pour les postes de travail de base de données) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e433e6aee341085965f361992fc8ea9ac8744353
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786257"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (pilotes pour les bases de données de poste de travail)
Étant donné que le pilote ne pas prendre en charge une mise à jour positionnée ou supprimer par la WHERE CURRENT OF *cursorname* syntaxe, **SQLSetCursorName** est pris en charge, mais ne peut pas être utilisé pour les mises à jour positionnées. Elle peut être utilisée uniquement lorsque la bibliothèque de curseurs est activée et à l’aide de l’application **SQLExtendedFetch**.
