---
title: Type de données bookmark C Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 566f1065d30a47b2db234ba1f11f877725189fb7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292289"
---
# <a name="bookmark-c-data-type"></a>Type de données C pour les signets
Le type de données du signet C permet à une application de récupérer un signet. Les types de signets C ne sont utilisés que pour récupérer des valeurs de signets qui peuvent être variables en longueur; ils ne devraient pas être convertis à d’autres types de données. Une application récupère un signet soit de la colonne 0 de l’ensemble de résultat avec **SQLBulkOperations** (avec une opération de SQL_ADD), **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData**. Pour plus d’informations, voir [Signmarks](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 Le tableau suivant énumère la valeur de *CType* pour le type de données du signet C, le type de données ODBC C qui implémente le type de données du signet C et la définition de ce type de données de SQL. H.  
  
> [!NOTE]
>  Le type de données SQL_C_BOOKMARK a été déprécié. Les applications ODBC *3.x* ne doivent pas utiliser SQL_C_BOOKMARK. Les conducteurs D’ODBC *3.x* n’ont besoin de prendre en charge SQL_C_BOOKMARK que s’ils veulent travailler avec les applications ODBC *2.x* qui l’utilisent. Le Driver Manager SQL_C_VARBOOKMARK à SQL_C_BOOKMARK lorsqu’une application fonctionne avec un pilote ODBC *2.x.*  
  
|Identifiant de type C|ODBC C typedef|Type C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Déconseillé)|Signet|unsigned long int|  
|SQL_C_VARBOOKMARK|SQLCHAR - France|unsigned char *|
