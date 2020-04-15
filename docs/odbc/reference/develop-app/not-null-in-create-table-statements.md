---
title: NOT NULL dans LES déclarations DE TABLE CREATE (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- not null [ODBC]
- interoperability [ODBC], not null
ms.assetid: 3fb69943-f0c9-4ed2-aa42-20440e37e49d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 490f4a7e49acdad5f919ad21f93d479b03099eb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302387"
---
# <a name="not-null-in-create-table-statements"></a>NOT NULL dans les instructions CREATE TABLE
Certaines bases de données, et en particulier les bases de données de bureau, ne prennent pas en charge la contrainte de colonne **NOT NULL** dans les relevés CREATE **TABLE.** Pour plus d’informations, consultez l’option SQL_NON_NULLABLE_COLUMNS dans la description de la fonction [SQLGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md)
