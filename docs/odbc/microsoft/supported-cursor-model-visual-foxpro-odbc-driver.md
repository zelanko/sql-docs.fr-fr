---
title: Modèle cursor pris en charge (Visual FoxPro ODBC Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cf3400f24e20a8fa864404612bf07ea44efce49e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301125"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Modèle de curseur pris en charge (pilote ODBC Visual FoxPro)
Le visual FoxPro ODBC Driver prend en charge à la fois *le bloc* (*rowset*) et les curseurs *statiques.* Les curseurs statiques sont pris en charge pour tout pilote conforme à la conformité au niveau 1 ODBC. Le conducteur ne prend pas en charge les curseurs dynamiques, à clé ou mixtes (clés et dynamiques).  
  
 Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec une option SQL_CURSOR_TYPE de SQL_CURSOR_FORWARD_ONLY (curseur de bloc) ou SQL_CURSOR_STATIC (curseur statique).  
  
> [!NOTE]  
>  Si vous appelez **SQLSetStmtOption** avec une option SQL_CURSOR_TYPE autre que SQL_CURSOR_FORWARD_ONLY ou SQL_CURSOR_STATIC, la fonction renvoie SQL_SUCCESS_WITH_INFO avec un SQLSTATE de 01S02 (valeur d’option modifiée). Le conducteur définit tous les modes de curseur non pris en soutien pour SQL_CURSOR_STATIC.  
  
 Pour plus d’informations sur les types de curseurs et sur **SQLSetStmtOption**, voir la [référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>curseur de bloc  
 Un ensemble de résultats avant-scrolling et lu seulement est retourné au client, qui est responsable du stockage pour les données.  
  
## <a name="static-cursor"></a>curseur statique  
 Un instantané d’un ensemble de données défini par la requête. Les curseurs statiques ne reflètent pas les modifications en temps réel des données sous-jacentes par d’autres utilisateurs. Le tampon de mémoire du curseur est maintenu par la bibliothèque de curseurs ODBC, qui permet de défiler vers l’avant et vers l’arrière.  
  
## <a name="rowset"></a>ensemble de lignes  
 Blocs de données stockées dans un curseur, représentant les rangées récupérées à partir d’une source de données.
