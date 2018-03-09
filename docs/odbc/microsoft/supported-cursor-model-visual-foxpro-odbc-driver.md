---
title: "Prise en charge du modèle de curseur (le pilote ODBC Visual FoxPro) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 097e8a5a4156ea9a107fc7393a7b9d76bdb1a70a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Modèle de curseur prises en charge (le pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro prend en charge les deux *bloc* (*ensemble de lignes*) et *statique* les curseurs. Les curseurs statiques sont prises en charge pour un pilote qui est conforme à la conformité de niveau 1 ODBC. Le pilote ne prend pas en charge dynamique, commandé par keyset ou mixte (keyset et dynamic) les curseurs.  
  
 Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec une option de SQL_CURSOR_TYPE de SQL_CURSOR_FORWARD_ONLY (curseur de bloc) ou SQL_CURSOR_STATIC (curseur statique).  
  
> [!NOTE]  
>  Si vous appelez **SQLSetStmtOption** avec une option SQL_CURSOR_TYPE autre que SQL_CURSOR_FORWARD_ONLY ou SQL_CURSOR_STATIC, la fonction retourne SQL_SUCCESS_WITH_INFO avec une valeur SQLSTATE 01 s 02 (Option la valeur modifiée). Le pilote affecte tous les modes de curseur non pris en charge SQL_CURSOR_STATIC.  
  
 Pour plus d’informations sur les types de curseurs et sur **SQLSetStmtOption**, consultez la [de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>curseur de bloc  
 Un jeu de résultats de défilement avant, en lecture seule retourné au client, qui est chargé de gérer le stockage des données.  
  
## <a name="static-cursor"></a>curseur statique  
 Un instantané d’un jeu de données défini par la requête. Les curseurs statiques ne reflètent pas les modifications en temps réel des données sous-jacentes par d’autres utilisateurs. Mémoire tampon de mémoire du curseur est conservée par la bibliothèque de curseurs ODBC, qui permet le défilement vers l’avant et vers l’arrière.  
  
## <a name="rowset"></a>ensemble de lignes  
 Blocs de données stockées dans un curseur, représentant les lignes récupérées à partir d’une source de données.
