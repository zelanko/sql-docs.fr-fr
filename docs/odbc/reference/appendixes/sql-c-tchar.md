---
title: SQL_C_TCHAR | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 973d94b9b47371090a5f54fd3d259854ba78e9c2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304070"
---
# <a name="sql_c_tchar"></a>SQL_C_TCHAR
L’identificateur de type SQL_C_TCHAR n’identifie pas réellement un type de données ; Il s’agit d’une macro qui existe dans le fichier d’en-tête pour la conversion Unicode. Elle est remplacée par SQL_C_CHAR ou SQL_C_WCHAR en fonction du paramètre de l' **#define**Unicode. Elle est utile pour une application qui transfère des données de type caractère compilées en tant qu’application ANSI et Unicode.
