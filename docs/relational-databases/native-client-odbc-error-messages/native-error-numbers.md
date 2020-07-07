---
title: Numéros des erreurs natives | Microsoft Docs
description: Pour les erreurs, le pilote ODBC SQL Server Native Client retourne le numéro d’erreur natif de SQL Server ou, pour les erreurs détectées par le pilote, 0.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b8b9c46efdd901d8645f5c044105311041e7fa35
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009178"
---
# <a name="native-error-numbers"></a>Numéros des erreurs natives
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Pour les erreurs qui se produisent dans la source de données (retournée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ), le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne le numéro d’erreur natif retourné par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour les erreurs détectées par le pilote, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne le numéro d’erreur natif 0. Pour plus d’informations sur la liste des numéros d’erreur natifs, consultez la colonne erreur de la table système **sysmessages** dans la base de données **Master** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour plus d’informations sur les codes d’erreur d’État, consultez [SQLSTATE &#40;codes d’erreur ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). Pour les erreurs retournées par le Net-Library, le numéro d'erreur natif provient du logiciel réseau sous-jacent.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
