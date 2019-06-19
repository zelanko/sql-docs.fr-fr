---
title: Prise en charge le modèle de curseur (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 875348a501c292e55b267ece769f16dd6bc9dbdd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270934"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Modèle de curseur pris en charge (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro prend en charge les deux *bloc* (*ensemble de lignes*) et *statique* les curseurs. Les curseurs statiques sont prises en charge pour n’importe quel pilote est conforme à la conformité de niveau 1 ODBC. Le pilote ne prend pas en charge dynamiques, pilotés par jeu de clés ou mixte (keyset et dynamic) les curseurs.  
  
 Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec une option SQL_CURSOR_TYPE de SQL_CURSOR_FORWARD_ONLY (curseur de bloc) ou SQL_CURSOR_STATIC (curseur statique).  
  
> [!NOTE]  
>  Si vous appelez **SQLSetStmtOption** avec une option SQL_CURSOR_TYPE autre que SQL_CURSOR_FORWARD_ONLY ou SQL_CURSOR_STATIC, la fonction retourne SQL_SUCCESS_WITH_INFO avec une valeur SQLSTATE de 01 s 02 (valeur d’Option modifiée). Le pilote affecte tous les modes de curseur non pris en charge SQL_CURSOR_STATIC.  
  
 Pour plus d’informations sur les types de curseur et environ **SQLSetStmtOption**, consultez le [de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>curseur de bloc  
 Un jeu de résultats de défilement avant, en lecture seule retourné au client, qui est responsable de la maintenance du stockage pour les données.  
  
## <a name="static-cursor"></a>curseur statique  
 Une capture instantanée d’un jeu de données défini par la requête. Les curseurs statiques ne reflètent pas les modifications en temps réel des données sous-jacentes par d’autres utilisateurs. Mémoire tampon de mémoire du curseur est maintenu par la bibliothèque de curseurs ODBC, ce qui permet le défilement vers l’avant et vers l’arrière.  
  
## <a name="rowset"></a>ensemble de lignes  
 Blocs de données stockées dans un curseur, représentant les lignes récupérées à partir d’une source de données.
