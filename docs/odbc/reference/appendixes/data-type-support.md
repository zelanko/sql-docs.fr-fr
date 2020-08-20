---
description: Prise en charge du type de données
title: Prise en charge des types de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ab0fd163713a7f6657d8ce446336f5c35a3dd00
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456636"
---
# <a name="data-type-support"></a>Prise en charge du type de données
Les pilotes ODBC doivent prendre en charge au moins l’un des SQL_CHAR et SQL_VARCHAR. La prise en charge d’autres types de données est déterminée par le niveau de conformité de SQL-92 de la source de données ou du pilote. Une application doit appeler **SQLGetTypeInfo** pour déterminer les types de données pris en charge par le pilote.  
  
 Pour plus d’informations sur les types de données, consultez l' [annexe D : types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).
