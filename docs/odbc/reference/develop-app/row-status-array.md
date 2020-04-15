---
title: Tableau d’état de la rangée (en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: 60dead23fe0051c05698e094f37ddad96b2b337d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304290"
---
# <a name="row-status-array"></a>Tableau d’état des lignes
En plus des données, **SQLFetch** et **SQLFetchScroll** peuvent retourner un tableau qui donne l’état de chaque rangée dans le ramset. Ce tableau est spécifié par l’attribut SQL_ATTR_ROW_STATUS_PTR de l’instruction. Ce tableau est attribué par l’application et doit avoir autant d’éléments que spécifiés par l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration. Les valeurs du tableau sont définies par **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**et **SQLSetPos.** Les valeurs décrivent l’état de la ligne et si ce statut a changé depuis sa dernière récupération.  
  
|Valeur du tableau d’état de ligne|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|La rangée a été récupérée avec succès et n’a pas changé depuis sa dernière fois.|  
|SQL_ROW_SUCCESS_WITH_INFO|La rangée a été récupérée avec succès et n’a pas changé depuis sa dernière fois. Cependant, un avertissement a été retourné au sujet de la rangée.|  
|SQL_ROW_ERROR|Une erreur s’est produite en allant chercher la rangée.|  
|SQL_ROW_UPDATED|La rangée a été récupérée avec succès et a été mise à jour depuis sa dernière fois. Si la ligne est récupérée à nouveau ou rafraîchie par **SQLSetPos**, son statut est changé pour le nouveau statut.<br /><br /> Certains conducteurs ne peuvent pas détecter les modifications apportées aux données et ne peuvent donc pas retourner cette valeur. Pour déterminer si un conducteur peut détecter les mises à jour des lignes recadrées, une application appelle **SQLGetInfo** avec l’option SQL_ROW_UPDATES.|  
|SQL_ROW_DELETED|La ligne a été supprimée depuis sa dernière fois.|  
|SQL_ROW_ADDED|La rangée a été insérée par **SQLBulkOperations**. Si la ligne est récupérée à nouveau ou est rafraîchie par **SQLSetPos**, son statut est SQL_ROW_SUCCESS.<br /><br /> Cette valeur n’est pas fixée par **SQLFetch** ou **SQLFetchScroll**.|  
|SQL_ROW_NOROW|Le jeu de ligne chevauchait la fin de l’ensemble de résultats, et aucune ligne n’a été retournée qui correspondait à cet élément du tableau d’état de la ligne.|
