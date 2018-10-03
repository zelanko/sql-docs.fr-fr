---
title: Améliorations date / heure (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56689bb045a6540bfdfbb9c7147dc34db110bde
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48123621"
---
# <a name="date-and-time-improvements-odbc"></a>Améliorations de la date et de l’heure (ODBC)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a introduit de nouveaux types de données de date et d'heure. Cette section décrit comment ces nouveaux types sont exposés en tant qu’extensions dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour une vue d’ensemble de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les nouveaux types date et heure données, consultez [améliorations Date / heure](../native-client/features/date-and-time-improvements.md). Pour un exemple illustrant la prise en charge de la date/heure ODBC, consultez [utilisez Types de Date et heure](../native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Pour obtenir des informations plus générales sur les types de données date et d’heure, consultez [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des types de données pour les améliorations date/heure (ODBC)](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Fournit des informations sur les types ODBC qui prennent en charge les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de date et d'heure.  
  
 [Métadonnées &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 Décrit les informations retournées dans le champ de descripteur de paramètre d'implémentation (IPD) et dans le champ de descripteur de ligne d'implémentation (IRD), ainsi que les métadonnées de colonne retournées par `SQLColumns` et `SQLProcedureColumns`. Elle décrit également les métadonnées de type de données retournées par `SQLGetTypeInfo`.  
  
 [Conversions de Type de données DateTime &#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 Décrit comment effectuer une conversion entre les valeurs datetime et datetimeoffset.  
  
 [Prise en charge sql_variant pour les types Date et Time](sql-variant-support-for-date-and-time-types.md)  
 Décrit la prise en charge de la fonction SQL_VARIANT pour les fonctionnalités de date et heure améliorées.  
  
 [En bloc de modifications de copie pour améliorée Types de Date et heure &#40;OLE DB et ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Décrit les améliorations des types date/time pour prendre en charge les opérations de copie en bloc.  
  
 [Comportement avec les Versions précédentes de SQL Server de Type améliorées de Date et d’heure &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Décrit le comportement attendu lorsqu’une application cliente à l’aide des fonctionnalités améliorées de date et heure communique avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et lorsqu’un client compilé avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client envoie des commandes à un serveur qui prend en charge les fonctionnalités de date et heure améliorées.  
  
 [Prise en charge des fonctionnalités de date et heure améliorées par l’API ODBC](odbc-api-support-for-enhanced-date-and-time-features.md)  
 Répertorie les fonctions ODBC qui prennent en charge les fonctionnalités de date et heure améliorées.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
