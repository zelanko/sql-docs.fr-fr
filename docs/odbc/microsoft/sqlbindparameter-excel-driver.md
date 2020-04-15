---
title: SQLBindParameter (Excel Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3a2d0a03bded3ec909cd158b36f52ee9007647e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300629"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (pilote Excel)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Excel Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Lorsque le pilote Microsoft Excel est utilisé, l’exécution d’une déclaration INSERT qui utilise un paramètre pour insérer un NULL dans une colonne SQL_CHAR reviendra SQL_SUCCESS_WITH_INFO avec SQLSTATE 01004, "Data Truncated."
