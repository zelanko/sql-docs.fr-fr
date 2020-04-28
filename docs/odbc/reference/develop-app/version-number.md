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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37b7924380b9e9beb60792b50436eaa13a503c76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306717"
---
# <a name="version-number"></a>Numéro de version
Il existe plusieurs versions d’ODBC, chacune avec des fonctionnalités différentes. Une application détermine la version ODBC prise en charge par le gestionnaire de pilotes et un pilote particulier en appelant **SQLGetInfo** avec les options SQL_ODBC_VER et SQL_DRIVER_ODBC_VER.
