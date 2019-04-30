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
manager: craigg
ms.openlocfilehash: 03678023990fc15d03c73501f331ecc302f6b892
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208447"
---
# <a name="version-number"></a>Numéro de version
Il existe plusieurs versions d’ODBC, chacun avec différentes fonctionnalités. Une application détermine qui prennent en charge ODBC version du Gestionnaire de pilotes et un pilote spécifique en appelant **SQLGetInfo** avec les options SQL_ODBC_VER et SQL_DRIVER_ODBC_VER.
