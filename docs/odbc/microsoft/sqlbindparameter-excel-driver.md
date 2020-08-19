---
description: SQLBindParameter (pilote Excel)
title: SQLBindParameter (pilote Excel) | Microsoft Docs
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
ms.openlocfilehash: 2f18d34bb17f6f6b039bac5f6842ff837c22f362
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483372"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Lorsque vous utilisez le pilote Microsoft Excel, l’exécution d’une instruction INSERT qui utilise un paramètre pour insérer une valeur NULL dans une colonne SQL_CHAR retourne SQL_SUCCESS_WITH_INFO avec SQLSTATE 01004, « données tronquées ».
