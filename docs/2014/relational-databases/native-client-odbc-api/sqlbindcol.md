---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ede93e1552451f7db8e286ac28284fed79ddef0c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067855"
---
# <a name="sqlbindcol"></a>SQLBindCol
  En règle générale, prenez en compte les implications de l’utilisation de **SQLBindCol** pour la conversion de données. Les conversions de liaison sont des processus clients. Ainsi, par exemple, l'extraction d'une valeur à virgule flottante liée à une colonne de type character conduit le pilote à effectuer localement la conversion du type de données float en character lorsqu'une ligne est extraite. La fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT peut être utilisée pour reporter le coût de la conversion des données sur le serveur.  
  
 Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner plusieurs jeux de lignes de résultats à l'issue de l'exécution d'une même instruction. Chaque jeu de résultats doit être lié séparément. Pour plus d’informations sur la liaison de plusieurs jeux de résultats, consultez [SQLMoreResults](sqlmoreresults.md).  
  
 Le développeur peut lier des colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à des types de données C spécifiques à à `SQL_C_BINARY`l’aide de la valeur *TargetType* . Les colonnes liées à des types propres à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas portables. Les types de données ODBC C propres à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont définis correspondent aux définitions de types de DB-Library. Or les développeurs DB-Library portant des applications souhaiteront peut-être tirer parti de cette fonctionnalité.  
  
 La création de rapports de troncation des données est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un processus coûteux pour le pilote ODBC Native Client. Vous pouvez éviter la troncation en veillant à ce que toutes les mémoires tampons de données liées soient suffisamment grandes pour retourner des données. Pour les données de type character, la largeur doit inclure l'espace nécessaire pour un indicateur de fin de chaîne lorsque le comportement par défaut du pilote pour l'indicateur de fin de chaîne est utilisé. Par exemple, la liaison [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’une colonne de **type char (5)** à un tableau de cinq caractères entraîne une troncation pour chaque valeur extraite. La liaison de la même colonne à un tableau de six caractères évite la troncation en fournissant un élément de type character dans lequel stocker l'indicateur de fin null. [SQLGetData](sqlgetdata.md) peut être utilisé pour récupérer efficacement des données binaires et de caractères longs sans troncation.  
  
 Pour les types de données de valeur élevée, si la mémoire tampon fournie par l’utilisateur n’est pas suffisamment grande pour `SQL_SUCCESS_WITH_INFO` contenir la valeur entière de la colonne, est retournée et les données de chaîne ; la troncation à droite» est émise. L'argument `StrLen_or_IndPtr` contient le nombre de chars/octets stockés dans la mémoire tampon.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLBindCol des fonctionnalités de date et heure améliorées  
 Les valeurs de colonne de résultats de types date/heure sont converties comme décrit dans [conversions de SQL en C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Notez que pour récupérer des colonnes time et DateTimeOffset en tant que structures`SQL_SS_TIME2_STRUCT` correspondantes (et **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* doit `SQL_C_DEFAULT` être `SQL_C_BINARY`spécifié en tant que ou.  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Prise en charge de SQLBindCol pour les UDT volumineux CLR  
 **SQLBindCol** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLBindCol, fonction](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
