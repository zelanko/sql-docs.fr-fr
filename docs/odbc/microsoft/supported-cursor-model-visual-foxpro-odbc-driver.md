---
description: Modèle de curseur pris en charge (pilote ODBC Visual FoxPro)
title: Modèle de curseur pris en charge (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.openlocfilehash: 789d55a894e66c87fc5773856375757947835b35
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471531"
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Modèle de curseur pris en charge (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro prend en charge les curseurs de *bloc* (*rowset*) et *statiques* . Les curseurs statiques sont pris en charge pour tous les pilotes conformes à la compatibilité ODBC de niveau 1. Le pilote ne prend pas en charge les curseurs dynamiques, pilotés par jeu de clés ou mixtes (keyset et Dynamic).  
  
 Votre application peut appeler [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) avec une option SQL_CURSOR_TYPE de SQL_CURSOR_FORWARD_ONLY (curseur de bloc) ou SQL_CURSOR_STATIC (curseur statique).  
  
> [!NOTE]  
>  Si vous appelez **SQLSetStmtOption** avec une option SQL_CURSOR_TYPE autre que SQL_CURSOR_FORWARD_ONLY ou SQL_CURSOR_STATIC, la fonction retourne SQL_SUCCESS_WITH_INFO avec un SQLSTATE de 01s02 ne (valeur d’option modifiée). Le pilote définit tous les modes de curseur non pris en charge pour SQL_CURSOR_STATIC.  
  
 Pour plus d’informations sur les types de curseurs et sur **SQLSetStmtOption**, consultez [Guide de référence du programmeur ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>curseur de bloc  
 Un jeu de résultats en lecture seule de défilement avant est retourné au client, qui est responsable de la maintenance du stockage pour les données.  
  
## <a name="static-cursor"></a>curseur statique  
 Instantané d’un jeu de données défini par la requête. Les curseurs statiques ne reflètent pas les modifications en temps réel des données sous-jacentes par d’autres utilisateurs. La mémoire tampon du curseur est conservée par la bibliothèque de curseurs ODBC, ce qui permet de faire défiler vers l’avant et vers l’arrière.  
  
## <a name="rowset"></a>ensemble de lignes  
 Blocs de données stockés dans un curseur, représentant les lignes extraites d’une source de données.
