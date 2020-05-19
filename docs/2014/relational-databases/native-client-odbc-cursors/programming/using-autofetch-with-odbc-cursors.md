---
title: Utilisation de l’auto-extraction avec les curseurs ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a15cc12787f5a7d05699737772e7478d57b6f6e8
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705598"
---
# <a name="using-autofetch-with-odbc-cursors"></a>Utilisation de l'auto-extraction avec les curseurs ODBC
  En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge une option d’auto-extraction lors de l’utilisation d’un type de curseur de serveur. Avec l’auto-extraction, la fonction **SQLExecute** ou **SQLExecDirect** qui ouvre le curseur a également une fonction [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) implicite. Les lignes qui comprennent le premier ensemble de lignes sont retournées aux variables d'application liée dans le cadre de l'exécution d'instruction, économisant un autre aller-retour sur le réseau jusqu'au serveur. [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) n’est pas pris en charge lorsque l’option d’auto-extraction est activée ; les colonnes du jeu de résultats doivent être liées à des variables de programme.  
  
 Les applications demandent l'auto-extraction en attribuant à l'attribut d'instruction SQL_SOPT_SS_CURSOR_OPTIONS spécifique au pilote la valeur SQL_CO_AF.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de programmation de curseur &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  
