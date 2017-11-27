---
title: SQL_C_TCHAR | Documents Microsoft
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
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 411e6fb221544b2146ecb4d141195b172c6430e5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
L’identificateur de type SQL_C_TCHAR n’identifie pas réellement d’un type de données ; Il s’agit d’une macro qui existe dans le fichier d’en-tête pour la conversion d’Unicode. Il est remplacé par SQL_C_CHAR ou SQL_C_WCHAR selon le paramètre de l’UNICODE **#define**. Il est utile pour une application de transfert de données de caractères qui sont compilées en tant que ANSI et une application Unicode.
