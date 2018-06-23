---
title: Date et heure améliorations (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19c4e63fc9e101379af2ac7b6bc859daa783ae6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154145"
---
# <a name="date-and-time-improvements-odbc"></a>Date et heure améliorations (ODBC)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a introduit de nouveaux types de données de date et d'heure. Cette section décrit comment ces nouveaux types sont exposés en tant qu’extensions dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour une vue d’ensemble de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prise en charge Native Client pour la nouvelle date et les types de données, consultez [Date et heure améliorations](../native-client/features/date-and-time-improvements.md). Pour un exemple illustrant la prise en charge de la date et d’heure ODBC, consultez [utilisez Types de Date et heure](../native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Pour plus d’informations sur les types de données date et heure, consultez [datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des types de données pour les améliorations date/heure (ODBC)](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Fournit des informations sur les types ODBC qui prennent en charge les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de date et d'heure.  
  
 [Métadonnées &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 Décrit les informations retournées dans le champ de descripteur de paramètre d'implémentation (IPD) et dans le champ de descripteur de ligne d'implémentation (IRD), ainsi que les métadonnées de colonne retournées par `SQLColumns` et `SQLProcedureColumns`. Elle décrit également les métadonnées de type de données retournées par `SQLGetTypeInfo`.  
  
 [Conversions de types de données de DateTime &#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 Décrit comment effectuer une conversion entre les valeurs datetime et datetimeoffset.  
  
 [Prise en charge sql_variant pour les types Date et Time](sql-variant-support-for-date-and-time-types.md)  
 Décrit la prise en charge de la fonction SQL_VARIANT pour les fonctionnalités de date et heure améliorées.  
  
 [En bloc a été apportée pour une meilleure Types de Date et heure &#40;OLE DB et ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Décrit les améliorations des types date/time pour prendre en charge les opérations de copie en bloc.  
  
 [Comportement avec les Versions précédentes de SQL Server de Type améliorées de Date et d’heure &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Décrit le comportement attendu lorsqu’une application cliente à l’aide des fonctionnalités améliorées de date et heure communique avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et lorsqu’un client compilé avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client envoie des commandes à un serveur qui prend en charge améliorée des fonctionnalités de date et d’heure.  
  
 [Prise en charge des fonctionnalités de date et heure améliorées par l’API ODBC](odbc-api-support-for-enhanced-date-and-time-features.md)  
 Répertorie les fonctions ODBC qui prennent en charge les fonctionnalités de date et heure améliorées.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
