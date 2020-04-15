---
title: SQLBindCol - France Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69457daccbc7868e58f91c71a48b4b25f15f5318
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302705"
---
# <a name="sqlbindcol"></a>SQLBindCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  En règle générale, tenez compte des implications de l’utilisation de **SQLBindCol** pour provoquer la conversion des données. Les conversions de liaison sont des processus clients. Ainsi, par exemple, l'extraction d'une valeur à virgule flottante liée à une colonne de type character conduit le pilote à effectuer localement la conversion du type de données float en character lorsqu'une ligne est extraite. La fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT peut être utilisée pour reporter le coût de la conversion des données sur le serveur.  
  
 Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner plusieurs jeux de lignes de résultats à l'issue de l'exécution d'une même instruction. Chaque jeu de résultats doit être lié séparément. Pour plus d’informations sur la liaison pour les ensembles de résultats multiples, voir [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Le développeur peut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]lier des colonnes à des types de données C spécifiques à l’aide de la valeur *TargetType* **SQL_C_BINARY**. Les colonnes liées à des types propres à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas portables. Les types de données ODBC C propres à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont définis correspondent aux définitions de types de DB-Library. Or les développeurs DB-Library portant des applications souhaiteront peut-être tirer parti de cette fonctionnalité.  
  
 La déclaration de la troncation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données est un processus coûteux pour le conducteur de native Client ODBC. Vous pouvez éviter la troncation en veillant à ce que toutes les mémoires tampons de données liées soient suffisamment grandes pour retourner des données. Pour les données de type character, la largeur doit inclure l'espace nécessaire pour un indicateur de fin de chaîne lorsque le comportement par défaut du pilote pour l'indicateur de fin de chaîne est utilisé. Par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la liaison d’une colonne **d’omble(5)** à un tableau de cinq caractères entraîne une troncation pour chaque valeur récupérée. La liaison de la même colonne à un tableau de six caractères évite la troncation en fournissant un élément de type character dans lequel stocker l'indicateur de fin null. [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) peut être utilisé pour récupérer efficacement les données à long caractère et binaires sans troncation.  
  
 Pour les types de données à grande valeur, si le tampon fourni par l’utilisateur n’est pas assez grand pour contenir la valeur totale de la colonne, **SQL_SUCCESS_WITH_INFO** est retournée et les " données de chaîne ; l’avertissement de troncation droite est émis. **L’argument StrLen_or_IndPtr** contiendra le nombre d’ombles/octets stockés dans le tampon.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLBindCol des fonctionnalités de date et heure améliorées  
 Les valeurs de la colonne de résultat des types de date/heure sont converties comme décrit [dans Conversions de SQL à C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Notez que pour récupérer les colonnes d’heure et de datetimeoffset comme leurs structures correspondantes **(SQL_SS_TIME2_STRUCT** et **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* doit être spécifié comme **SQL_C_DEFAULT** ou **SQL_C_BINARY**.  
  
 Pour plus d’informations, voir [Les améliorations de date et d’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Soutien SQLBindCol pour les grands UDT CLR  
 **SQLBindCol** prend en charge les grands types définis par les utilisateurs CLR (UDT). Pour plus d’informations, voir [Grands types définis par l’utilisateur CLR &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLBindCol](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
