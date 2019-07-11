---
title: Type de données C de signet | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76846a5027ff5229997151b36a93b1ea553ddbc8
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793222"
---
# <a name="bookmark-c-data-type"></a>Type de données C pour les signets
Le type de données C de signet permet à une application récupérer un signet. Les types de signet C sont utilisés seulement pour récupérer les valeurs de signet qui peuvent être variable en longueur ; ils ne doivent pas être convertis en autres types de données. Une application récupère un signet à partir de la colonne 0 du résultat défini avec **SQLBulkOperations** (avec une opération de SQL_ADD), **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData**. Pour plus d’informations, consultez [signets](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 Le tableau suivant répertorie la valeur de *CType* pour le type de données C de signet, le type de données ODBC C qui implémente le type de données C de signet et la définition de ces données de type à partir de SQL. H.  
  
> [!NOTE]
>  Le type de données SQL_C_BOOKMARK a été déconseillé. ODBC *3.x* applications ne doivent pas utiliser SQL_C_BOOKMARK. ODBC *3.x* pilotes doivent prendre en charge de SQL_C_BOOKMARK uniquement si ils veulent pouvoir travailler avec ODBC *2.x* applications qui l’utilisent. Le Gestionnaire de pilotes mappe SQL_C_VARBOOKMARK à SQL_C_BOOKMARK quand une application fonctionne avec une application ODBC *2.x* pilote.  
  
|Identificateur de type C|ODBC C typedef|Type C|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Déconseillé)|SIGNET|entier long non signé|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
