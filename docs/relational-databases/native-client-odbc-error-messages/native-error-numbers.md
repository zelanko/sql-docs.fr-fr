---
title: Numéros d’erreur autochtones (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291603"
---
# <a name="native-error-numbers"></a>Numéros des erreurs natives
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pour les erreurs qui se produisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la source de données (retourné par ), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]le conducteur native de l’ODBC retourne le numéro d’erreur natif retourné à elle par . Pour les erreurs détectées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le conducteur, le conducteur de Native Client ODBC renvoie un nombre d’erreurs indigènes de 0. Pour plus d’informations sur une liste de numéros d’erreur natifs, voir la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]colonne d’erreur du tableau du système de **sysmessages** dans la base de données **principale** dans .  
  
 Pour plus d’informations sur les codes d’erreur de l’État, voir [SQLSTATE &#40;ODBC Error Codes&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). Pour les erreurs retournées par le Net-Library, le numéro d'erreur natif provient du logiciel réseau sous-jacent.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
