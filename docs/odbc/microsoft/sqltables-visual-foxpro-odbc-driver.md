---
title: SQLTables (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5467fc8c1717d5ceb548b3950a0894fd2a1b4499
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299281"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 1  
  
 Retourne la liste des noms de table spécifiés par le paramètre dans l’énoncé **SQLTables.** Si aucun paramètre n’est spécifié, renvoie les noms de table stockés dans la source de données actuelle. Le conducteur renvoie l’information à la suite de l’ensemble.  
  
 Les appels de type recensement ne recevront pas d’entrée définie de résultat pour les vues à distance ou les vues paramétrisées locales. Cependant, un appel à **SQLTables** avec un spécificateur de nom de table unique trouvera une correspondance pour une telle vue si présent avec ce nom; cela permet à l’API d’être utilisée pour vérifier les conflits de nom avant la création d’une nouvelle table.  
  
> [!NOTE]  
>  Le pilote Visual FoxPro ODBC fait la distinction entre [les tables de base de données](../../odbc/microsoft/visual-foxpro-terminology.md) et les tables [gratuites,](../../odbc/microsoft/visual-foxpro-terminology.md)même lorsque les deux types de tables sont stockés dans le même répertoire sur votre système. Si votre source de données est un répertoire de tables gratuites, le visual FoxPro ODBC Driver ne catalogue pas ou ne renvoie pas les noms des tables associées à une base de données.  
  
 Pour plus d’informations, voir [SQLTables](../../odbc/reference/syntax/sqltables-function.md) dans la *référence du programmeur ODBC*.
