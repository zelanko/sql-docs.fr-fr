---
title: Utilisation de type de données (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data types
- ODBC data types, about ODBC data types
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC]
- SQL Server Native Client ODBC driver, data types
- data types [ODBC], about data types
ms.assetid: 4f19b0d6-94ac-4a98-a121-57d38787864c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0384857c53e898af9fca89bb2ee2351f0b65f986
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297854"
---
# <a name="data-type-usage"></a>Utilisation des types de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC et impose l’utilisation suivante des types de données.  
  
|Type de données|Limitation|  
|---------------|----------------|  
|Littéraux de date|Les littérals de date, lorsqu’ils[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont stockés dans une colonne de SQL_TYPE_TIMESTAMP (types de données de **date ou** **de smalldatetime**), ont une valeur temporelle de 12:00:00.000 A.M.|  
|**argent** et **smallmoney**|Seules les parties integer de **l’argent** et les types de données **smallmoney** sont importants. Si la partie décimale des données **monétaires** SQL est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tronquée lors de la conversion de type de données, le conducteur de Native Client ODBC renvoie un avertissement, et non une erreur.|  
|SQL_BINARY (accepte les valeurs NULL)|En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 et versions antérieures, si une colonne SQL_BINARY accepte les valeurs NULL, les données stockées dans la source de données ne sont pas complétées avec des zéros. Lorsque les données d’une telle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne sont récupérées, le conducteur de Native Client ODBC les tamponne avec des zéros sur la droite. Toutefois, les données créées dans des opérations effectuées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles que la concaténation, ne font pas l'objet d'un tel remplissage.<br /><br /> Par ailleurs, lorsque des données sont placées dans une telle colonne dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 ou versions antérieures, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tronque les données à droite si elles sont trop longues pour tenir dans la colonne.<br /><br /> Remarque : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le conducteur d’ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du client autochtone prend en charge la connexion à 6,5 et plus tôt.|  
|SQL_CHAR (troncation)|En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 et versions antérieures, lorsque les données sont placées dans une colonne SQL_CHAR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les tronque à droite sans avertissement si les données sont trop longues pour tenir dans la colonne.<br /><br /> Remarque : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le conducteur d’ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du client autochtone prend en charge la connexion à 6,5 et plus tôt.|  
|SQL_CHAR (accepte les valeurs NULL)|En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 et versions antérieure, si une colonne SQL_CHAR accepte les valeurs NULL, les données stockées dans la source de données ne sont pas complétées avec des espaces. Lorsque les données d’une telle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne sont récupérées, le conducteur de Native Client ODBC les tamponne avec des blancs sur la droite. Toutefois, les données créées dans des opérations effectuées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles que la concaténation, ne font pas l'objet d'un tel remplissage.<br /><br /> Remarque : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le conducteur d’ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du client autochtone prend en charge la connexion à 6,5 et plus tôt.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|Les mises à jour des colonnes avec SQL_LONGVARBINARY, SQL_LONGVARCHAR ou SQL_WLONGVARCHAR types de données (à l’aide d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clause WHERE) qui affectent plusieurs lignes sont entièrement prises en charge lorsqu’elles sont connectées à une instance de 6. *x* et plus tard. Lorsqu’il est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connecté à une instance de 4,2*x*, une erreur S1000, "Insert partiel / mise à jour. L'insertion ou la mise à jour d'un texte ou de colonnes d'images n'a pas abouti. » est retournée si la mise à jour affecte plusieurs lignes.<br /><br /> Remarque : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le conducteur d’ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du client autochtone prend en charge la connexion à 6,5 et plus tôt.|  
|Paramètres de fonction de chaîne|*string_exp* paramètres des fonctions de chaîne doivent être de type de données SQL_CHAR ou SQL_VARCHAR. Les types de données SQL_LONG_VARCHAR ne sont pas pris en charge dans les fonctions de chaîne. Le *paramètre de comptage* doit être inférieur ou égal à 8 000 parce que les types de données SQL_CHAR et SQL_VARCHAR sont limités à une longueur maximale de 8 000 caractères.|  
|Littéraux d'heure|Les littérals de temps, lorsqu’ils[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont stockés dans une colonne de SQL_TIMESTAMP (types de données de **date** ou **de smalldatetime**), ont une valeur de date du 1er janvier 1900.|  
|**timestamp**|Seule une valeur NULL peut être insérée manuellement dans une colonne **de timestamp.** Cependant, parce que les colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **de timestamp**sont automatiquement mises à jour par , une valeur NULL est écrasée.|  
|**TINYINT**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données **tinyint** n’est pas signé. Une colonne **tinyint** est liée à une variable de type de données SQL_C_UTINYINT par défaut.|  
|Types de données alias|Lorsqu’il est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connecté à une instance de 4,2*x,* le pilote ODBC ajoute NULL à une définition de colonne qui ne déclare pas explicitement l’annulation d’une colonne. Par conséquent, la possibilité de valeur NULL stockée dans la définition d'un type de données alias est ignorée.<br /><br /> Lorsqu’il est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connecté à une instance de 4,2*x*, colonnes avec un type de données alias qui a un type de données de base de **l’omble chevalier** ou **binaire** et pour lequel aucune nullité est déclarée sont créés comme **varchar** de type de données ou **varbinaire**. [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md), et [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) retournent SQL_VARCHAR ou SQL_VARBINARY comme type de données pour ces colonnes. Les données qui sont récupérées de ces colonnes ne sont pas complétées.<br /><br /> Remarque : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le conducteur d’ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du client autochtone prend en charge la connexion à 6,5 et plus tôt.|  
|Types de données LONG|les paramètres *de données d’exécution* sont limités tant pour les SQL_LONGVARBINARY que pour les types de données SQL_LONGVARCHAR.|  
|Types de valeur élevée|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC exposera **le varchar(max)**, les types **de varbinaires (max)** et **de nvarchar(max)** comme SQL_VARCHAR, SQL_VARBINARY et SQL_WVARCHAR (respectivement) dans les API qui acceptent ou retournent les types de données SQL d’ODBC.|  
|Type défini par l'utilisateur (UDT)|Les colonnes UDT sont mappées en tant que SQL_SS_UDT. Si une colonne UDT est mappée explicitement à un autre type dans l'instruction SQL à l'aide des méthodes ToString() ou ToXMLString() du type UDT, ou via les fonctions CAST/CONVERT, le type de la colonne dans le jeu de résultats reflète le type réel vers lequel la colonne a été convertie.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote Native Client ODBC ne peut se lier qu’à une colonne UDT comme binaire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend uniquement en charge la conversion entre les types de données SQL_SS_UDT et SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit automatiquement le code XML en texte Unicode. Le type XML est mappé en tant que SQL_SS_XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Résultats de traitement &#40;&#41;ODBC](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
