---
title: Utilisation des types de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 170cbfffde1b28d60617f0e0166ca9f8e31f5fb6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63200183"
---
# <a name="data-type-usage"></a>Utilisation des types de données
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imposent l’utilisation suivante des types de données.  
  
|Type de données|Limitation|  
|---------------|----------------|  
|Littéraux de date|Les littéraux de date, lorsqu’ils sont stockés dans[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une colonne SQL_TYPE_TIMESTAMP (types de données **DateTime** ou **smalldatetime**), ont une valeur d’heure de 12:00:00.000 du matin|  
|**Money** et **smallmoney**|Seules les parties entières des types de données **Money** et **smallmoney** sont significatives. Si la partie décimale des données SQL **Money** est tronquée lors de la conversion du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données, le pilote ODBC Native Client retourne un avertissement, et non une erreur.|  
|SQL_BINARY (accepte les valeurs NULL)|En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 et versions antérieures, si une colonne SQL_BINARY accepte les valeurs NULL, les données stockées dans la source de données ne sont pas complétées avec des zéros. Lorsque les données d’une telle colonne sont récupérées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le pilote ODBC native client le remplit avec des zéros à droite. Toutefois, les données créées dans des opérations effectuées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles que la concaténation, ne font pas l'objet d'un tel remplissage.<br /><br /> Par ailleurs, lorsque des données sont placées dans une telle colonne dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 ou versions antérieures, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tronque les données à droite si elles sont trop longues pour tenir dans la colonne. **Remarque :**  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion à 6,5 et versions antérieures.|  
|SQL_CHAR (troncation)|En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 et versions antérieures, lorsque les données sont placées dans une colonne SQL_CHAR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les tronque à droite sans avertissement si les données sont trop longues pour tenir dans la colonne. **Remarque :**  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion à 6,5 et versions antérieures.|  
|SQL_CHAR (accepte les valeurs NULL)|En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 et versions antérieure, si une colonne SQL_CHAR accepte les valeurs NULL, les données stockées dans la source de données ne sont pas complétées avec des espaces. Lorsque les données d’une telle colonne sont récupérées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le pilote ODBC native client le remplit avec des espaces à droite. Toutefois, les données créées dans des opérations effectuées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], telles que la concaténation, ne font pas l'objet d'un tel remplissage. **Remarque :**  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion à 6,5 et versions antérieures.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|Les mises à jour de colonnes avec des types de données SQL_LONGVARBINARY, SQL_LONGVARCHAR ou SQL_WLONGVARCHAR (à l’aide d’une clause WHERE) qui affectent plusieurs lignes sont entièrement prises en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge lors de la connexion à une instance de 6. *x* et versions ultérieures. En cas de connexion à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de 4,2*x*, erreur S1000, «insertion/mise à jour partielle. L'insertion ou la mise à jour d'un texte ou de colonnes d'images n'a pas abouti. » est retournée si la mise à jour affecte plusieurs lignes. **Remarque :**  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion à 6,5 et versions antérieures.|  
|Paramètres de fonction de chaîne|*string_exp* paramètres des fonctions de chaîne doivent être de type SQL_CHAR ou SQL_VARCHAR. Les types de données SQL_LONG_VARCHAR ne sont pas pris en charge dans les fonctions de chaîne. Le paramètre *Count* doit être inférieur ou égal à 8 000, car les types de données SQL_CHAR et SQL_VARCHAR sont limités à une longueur maximale de 8 000 caractères.|  
|Littéraux d'heure|Les littéraux d’heure, lorsqu’ils sont stockés dans[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une colonne SQL_TIMESTAMP (types de données **DateTime** ou **smalldatetime**), ont une valeur date du 1er janvier 1900.|  
|**timestamp**|Seule une valeur NULL peut être insérée manuellement dans une colonne **timestamp** . Toutefois, étant donné que les colonnes **timestamp**sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]automatiquement mises à jour par, une valeur null est remplacée.|  
|**tinyint**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données **tinyint** n’est pas signé. Une colonne **tinyint** est liée à une variable de type de données SQL_C_UTINYINT par défaut.|  
|Types de données alias|En cas de connexion à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de 4,2*x*, le pilote ODBC ajoute null à une définition de colonne qui ne déclare pas explicitement la possibilité de valeur null d’une colonne. Par conséquent, la possibilité de valeur NULL stockée dans la définition d'un type de données alias est ignorée.<br /><br /> En cas de connexion à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de 4,2*x*, les colonnes avec un type de données alias dont le type de données de base est **char** ou **Binary** et pour lesquelles aucune possibilité de valeur NULL n’est déclarée sont créées en tant que type de données **varchar** ou **varbinary**. [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../native-client-odbc-api/sqlcolumns.md)et [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) retournent SQL_VARCHAR ou SQL_VARBINARY comme type de données pour ces colonnes. Les données qui sont récupérées de ces colonnes ne sont pas complétées. **Remarque :**  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion à 6,5 et versions antérieures.|  
|Types de données LONG|les paramètres de *données en* cours d’exécution sont restreints pour les types de données SQL_LONGVARBINARY et SQL_LONGVARCHAR.|  
|Types de valeur élevée|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client expose les types **varchar (max)**, **varbinary (max)** et **nvarchar (max)** comme SQL_VARCHAR, SQL_VARBINARY et SQL_WVARCHAR (respectivement) dans les API qui acceptent ou retournent des types de données SQL ODBC.|  
|Type défini par l'utilisateur (UDT)|Les colonnes UDT sont mappées en tant que SQL_SS_UDT. Si une colonne UDT est mappée explicitement à un autre type dans l'instruction SQL à l'aide des méthodes ToString() ou ToXMLString() du type UDT, ou via les fonctions CAST/CONVERT, le type de la colonne dans le jeu de résultats reflète le type réel vers lequel la colonne a été convertie.<br /><br /> Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client ne peut se lier qu’à une colonne UDT comme binaire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend uniquement en charge la conversion entre les types de données SQL_SS_UDT et SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertit automatiquement le code XML en texte Unicode. Le type XML est mappé en tant que SQL_SS_XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](processing-results-odbc.md)  
  
  
