---
title: Plusieurs instructions actives et les connexions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2a1edbf9947aff01ef6d4688959352986cf672d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63254222"
---
# <a name="multiple-active-statements-and-connections"></a>Instructions et connexions multiples actives simultanément
Certains pilotes et le SGBD limite le nombre d’instructions et connexions qui peuvent être actives en même temps. Ces numéros peuvent être aussi petit qu’un. Pour plus d’informations, consultez les options SQL_MAX_CONCURRENT_ACTIVITIES et SQL_MAX_DRIVER_CONNECTIONS dans le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description, de fonction et [instruction gère](../../../odbc/reference/develop-app/statement-handles.md) et [ Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md).
