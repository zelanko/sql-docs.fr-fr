---
description: Tableau d’état des lignes
title: Tableau d’état de ligne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- cursors [ODBC], block
- result sets [ODBC], row status array
- block cursors [ODBC]
- result sets [ODBC], block cursors
- rowset status [ODBC]
ms.assetid: 4b69f189-2722-4314-8a02-f4ffecd6dabd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8067aaf8724a6634d165d53743cbd0ef2015f6bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465632"
---
# <a name="row-status-array"></a>Tableau d’état des lignes
En plus des données, **SQLFetch** et **SQLFetchScroll** peuvent retourner un tableau qui indique l’état de chaque ligne de l’ensemble de lignes. Ce tableau est spécifié à l’aide de l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR. Ce tableau est alloué par l’application et doit avoir autant d’éléments que spécifiés par l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE. Les valeurs du tableau sont définies par **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**et **SQLSetPos.** Les valeurs décrivent l’état de la ligne et indiquent si cet État a changé depuis sa dernière extraction.  
  
|Valeur du tableau d’état des lignes|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|La ligne a été récupérée avec succès et n’a pas été modifiée depuis sa dernière extraction.|  
|SQL_ROW_SUCCESS_WITH_INFO|La ligne a été récupérée avec succès et n’a pas été modifiée depuis sa dernière extraction. Toutefois, un avertissement a été renvoyé à propos de la ligne.|  
|SQL_ROW_ERROR|Une erreur s’est produite lors de l’extraction de la ligne.|  
|SQL_ROW_UPDATED|La ligne a été récupérée avec succès et a été mise à jour depuis sa dernière extraction. Si la ligne est à nouveau extraite ou actualisée par **SQLSetPos**, son état est remplacé par le nouvel État.<br /><br /> Certains pilotes ne peuvent pas détecter les modifications apportées aux données et ne peuvent donc pas retourner cette valeur. Pour déterminer si un pilote peut détecter des mises à jour à des lignes récupérées à nouveau, une application appelle **SQLGetInfo** avec l’option SQL_ROW_UPDATES.|  
|SQL_ROW_DELETED|La ligne a été supprimée depuis sa dernière extraction.|  
|SQL_ROW_ADDED|La ligne a été insérée par **SQLBulkOperations**. Si la ligne est à nouveau extraite ou qu’elle est actualisée par **SQLSetPos**, son état est SQL_ROW_SUCCESS.<br /><br /> Cette valeur n’est pas définie par **SQLFetch** ou **SQLFetchScroll**.|  
|SQL_ROW_NOROW|L’ensemble de lignes chevauche la fin du jeu de résultats et aucune ligne qui correspond à cet élément du tableau d’état de ligne n’a été retournée.|
