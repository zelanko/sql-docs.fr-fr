---
title: NON NULL dans les instructions CREATE TABLE | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- not null [ODBC]
- interoperability [ODBC], not null
ms.assetid: 3fb69943-f0c9-4ed2-aa42-20440e37e49d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc96de9df9724e500709488054b3357b3c7e50aa
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="not-null-in-create-table-statements"></a>NOT NULL dans les instructions CREATE TABLE
Certaines bases de données et en particulier de bureau, ne prennent pas en charge la **non NULL** contrainte de colonne dans **CREATE TABLE** instructions. Pour plus d’informations, consultez l’option SQL_NON_NULLABLE_COLUMNS dans le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction.

