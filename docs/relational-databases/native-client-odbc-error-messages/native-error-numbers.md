---
title: Numéros des erreurs natives | Microsoft Docs
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
ms.openlocfilehash: 0b5572ee784f47b0444e1d825de1b6dd53db8066
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81291603"
---
# <a name="native-error-numbers"></a>Numéros des erreurs natives
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pour les erreurs qui se produisent dans la source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](retournée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par), le pilote ODBC Native Client retourne le numéro d’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]natif retourné par. Pour les erreurs détectées par le pilote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le pilote ODBC Native Client retourne le numéro d’erreur natif 0. Pour plus d’informations sur la liste des numéros d’erreur natifs, consultez la colonne erreur de la table système **sysmessages** dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]base de données **Master** dans.  
  
 Pour plus d’informations sur les codes d’erreur d’État, consultez [SQLSTATE &#40;codes d’erreur ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). Pour les erreurs retournées par le Net-Library, le numéro d'erreur natif provient du logiciel réseau sous-jacent.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
