---
title: Déclarations et connexions actives multiples ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8259967942f47b06c50a9043158f8b3b45c58d7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302428"
---
# <a name="multiple-active-statements-and-connections"></a>Instructions et connexions multiples actives simultanément
Certains conducteurs et DBMS limitent le nombre d’instructions et de connexions qui peuvent être actives en même temps. Ces chiffres peuvent être aussi petits qu’un. Pour plus d’informations, consultez les options de SQL_MAX_CONCURRENT_ACTIVITIES et de SQL_MAX_DRIVER_CONNECTIONS dans la description de la fonction [SQLGetInfo,](../../../odbc/reference/syntax/sqlgetinfo-function.md) ainsi que [les poignées](../../../odbc/reference/develop-app/statement-handles.md) de déclaration et les [poignées de connexion.](../../../odbc/reference/develop-app/connection-handles.md)
