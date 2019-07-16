---
title: Numéro de version | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 331b60b31c49a203da5f25c4481a604132fbb0e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079553"
---
# <a name="version-number"></a>Numéro de version
Il existe plusieurs versions d’ODBC, chacun avec différentes fonctionnalités. Une application détermine qui prennent en charge ODBC version du Gestionnaire de pilotes et un pilote spécifique en appelant **SQLGetInfo** avec les options SQL_ODBC_VER et SQL_DRIVER_ODBC_VER.
