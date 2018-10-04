---
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7959068d5e24aa38157525ec133ab071611b5e85
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845307"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Utilisation de l'auto-extraction avec les curseurs ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Lors de la connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge une option d’auto-extraction lors de l’utilisation de n’importe quel type de curseur de serveur. Avec l’auto-extraction, la **SQLExecute** ou **SQLExecDirect** fonction qui ouvre le curseur a également implicite [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)(fonction) (SQL_FIRST). Les lignes qui comprennent le premier ensemble de lignes sont retournées aux variables d'application liée dans le cadre de l'exécution d'instruction, économisant un autre aller-retour sur le réseau jusqu'au serveur. [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) n’est pas pris en charge lorsque l’option d’auto-extraction est activée ; les colonnes du jeu de résultats doivent être liés à des variables de programme.  
  
 Les applications demandent l'auto-extraction en attribuant à l'attribut d'instruction SQL_SOPT_SS_CURSOR_OPTIONS spécifique au pilote la valeur SQL_CO_AF.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseurs &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
