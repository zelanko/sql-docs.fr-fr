---
title: "Numéro de version | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e017577bdf84115ff5fc9936024031e9f4f2f71f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="version-number"></a>Numéro de version
Il existe plusieurs versions d’ODBC, chacun avec différentes fonctionnalités. Une application détermine qui prennent en charge ODBC version du Gestionnaire de pilotes et un pilote spécifique en appelant **SQLGetInfo** avec les options SQL_ODBC_VER et SQL_DRIVER_ODBC_VER.
