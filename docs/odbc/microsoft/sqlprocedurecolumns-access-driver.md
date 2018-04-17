---
title: SQLProcedureColumns (pilote Access) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 59cb68c06193d081bede5ff9ad33b08adb4c8235
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Access. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Les développeurs d’applications doivent rechercher les colonnes définies par le pilote en commençant à la fin du jeu de résultats et en procédant par ordre décroissant.  
  
|Colonne|Commentaires|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT ou SQL_RESULT_COL|  
|ORDINAL|Il s’agit d’une colonne spécifiques au pilote qui est retournée à la fin du jeu de résultats. Le type SQL de la colonne est un entier.|
