---
description: Utilisation de l'auto-extraction avec les curseurs ODBC
title: Utilisation de l’auto-extraction avec les curseurs ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 60f044aa6568d73364e6adf56cff54354c5e82f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420713"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Utilisation de l'auto-extraction avec les curseurs ODBC
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge une option d’auto-extraction lors de l’utilisation d’un type de curseur de serveur. Avec l’auto-extraction, la fonction **SQLExecute** ou **SQLExecDirect** qui ouvre le curseur a également une fonction [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) implicite. Les lignes qui comprennent le premier ensemble de lignes sont retournées aux variables d'application liée dans le cadre de l'exécution d'instruction, économisant un autre aller-retour sur le réseau jusqu'au serveur. [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) n’est pas pris en charge lorsque l’option d’auto-extraction est activée ; les colonnes du jeu de résultats doivent être liées à des variables de programme.  
  
 Les applications demandent l'auto-extraction en attribuant à l'attribut d'instruction SQL_SOPT_SS_CURSOR_OPTIONS spécifique au pilote la valeur SQL_CO_AF.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseur &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
