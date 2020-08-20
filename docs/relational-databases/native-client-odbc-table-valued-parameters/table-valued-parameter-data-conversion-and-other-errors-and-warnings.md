---
description: Conversion des données des paramètres table et autres erreurs et avertissements
title: Conversion de données de paramètre table
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b1ef0b488b8cd0e1ccd76142d78fe81a7bfbd88b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470381"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Conversion des données des paramètres table et autres erreurs et avertissements
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Les valeurs de colonne de paramètre table peuvent être converties du type de données client en type de données serveur de la même manière que toute autre valeur de colonne ou de paramètre. Toutefois, dans la mesure où un paramètre table peut contenir plusieurs colonnes et plusieurs lignes, il est important de pouvoir identifier la valeur réelle sur laquelle l'erreur s'est produite.  
  
 Lorsqu'une erreur ou un avertissement est détecté dans une colonne de paramètre table, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client génère un enregistrement de diagnostic. Le message d'erreur contient le numéro du paramètre table, accompagné de l'ordinal de colonne et du numéro de ligne. Une application peut également utiliser les champs de diagnostic SQL_DIAG_SS_TABLE_COLUMN_NUMBER et SQL_DIAG_SS_TABLE_ROW_NUMBER dans des enregistrements de diagnostic pour déterminer quelles valeurs sont associées à des erreurs et des avertissements. Ces champs de diagnostic sont disponibles dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures.  
  
 Les composants SQLSTATE et message des enregistrements de diagnostic sont conformes au comportement ODBC existant pour tous les autres aspects. Autrement dit, à l’exception des informations d’identification des paramètres, des lignes et des colonnes, les messages d’erreur ont les mêmes valeurs pour les paramètres table que pour les paramètres qui ne sont pas des tables.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
