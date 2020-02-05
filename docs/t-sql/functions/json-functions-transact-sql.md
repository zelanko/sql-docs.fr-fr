---
title: Fonctions JSON (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: genemi
ms.technology: t-sql
ms.topic: language-reference
helpviewer_keywords:
- JSON functions
ms.assetid: ec97d451-06af-44a3-8304-305d410cfc8e
author: jovanpop-msft
ms.author: jovanpop
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: 5b83e6f6eefce1cf56b71e7d433dca19cb4575d1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68109419"
---
# <a name="json-functions-transact-sql"></a>Fonctions JSON (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Utilisez les fonctions décrites dans les pages de cette section pour valider ou modifier le texte JSON, ou pour extraire des valeurs simples ou complexes.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[ISJSON](../../t-sql/functions/isjson-transact-sql.md)|Teste si une chaîne contient des données JSON valides.|  
|[JSON_VALUE](../../t-sql/functions/json-value-transact-sql.md)|Extrait une valeur scalaire d’une chaîne JSON.|  
|[JSON_QUERY](../../t-sql/functions/json-query-transact-sql.md)|Extrait un objet ou un tableau à partir d’une chaîne JSON.|  
|[JSON_MODIFY](../../t-sql/functions/json-modify-transact-sql.md)|Met à jour la valeur d’une propriété dans une chaîne JSON et renvoie la chaîne JSON mise à jour.|

 Pour plus d’informations sur la prise en charge intégrée de JSON dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Données JSON &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md).  

## <a name="see-also"></a>Voir aussi

 - [Validate, Query, and Change JSON Data with Built-in Functions &#40;SQL Server&#41; [Valider, interroger et modifier les données JSON avec les fonctions intégrées &#40;SQL Server&#41;]](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)
 - [Expressions de chemin JSON &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)
 - [Données JSON &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
