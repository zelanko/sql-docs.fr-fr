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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 68a03de54a8a5f63a994578d64c6bce5a1279138
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057038"
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
L’identificateur de type SQL_C_TCHAR n’identifie pas réellement un type de données ; Il est une macro qui existe dans le fichier d’en-tête pour la conversion d’Unicode. Il est remplacé par SQL_C_CHAR ou SQL_C_WCHAR selon le paramètre de l’UNICODE **#define**. Il est utile pour une application de transfert de données de caractère qui sont compilées en tant que ANSI et une application Unicode.
