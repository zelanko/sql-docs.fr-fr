---
title: sp_special_columns_100 (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.subservice: design
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5774fadc-77cc-46f8-8f9f-a0f9efe95e21
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1be02aa5a19e49788aafdfdb9b6f818a66968283
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68054843"
---
# <a name="sp_special_columns_100-sql-data-warehouse"></a>sp_special_columns_100 (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne le jeu optimal de colonnes qui identifie de façon unique une ligne d'une table. Retourne également les colonnes automatiquement mises à jour lorsqu'une transaction met à jour une valeur dans la ligne.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_special_columns_100 [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @qualifier = ] 'qualifier' ]   
     [ , [ @col_type = ] 'col_type' ]   
     [ , [ @scope = ] 'scope' ]  
     [ , [ @nullable = ] 'nullable' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @table_name=] '*table_name*'  
 Nom de la table utilisée pour renvoyer des informations de catalogue. *Name* est de **type sysname**, sans valeur par défaut. La recherche de correspondance avec des caractères génériques n'est pas prise en charge.  
  
 [ @table_owner=] '*TABLE_OWNER*'  
 Propriétaire de la table utilisée pour retourner les informations de catalogue. *owner* est de **type sysname**, avec NULL comme valeur par défaut. La recherche de correspondance avec des caractères génériques n'est pas prise en charge. Si *owner* n’est pas spécifié, les règles de visibilité de table par défaut du SGBD sous-jacent s’appliquent.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si l'utilisateur actuel est propriétaire d'une table portant le nom spécifié, les colonnes de cette table sont renvoyées. Si *owner* n’est pas spécifié et que l’utilisateur actuel ne possède pas de table portant le *nom*spécifié, cette procédure recherche une table portant le *nom* spécifié, détenue par le propriétaire de la base de données. Si la table existe, ses colonnes sont retournées.  
  
 [ @qualifier=] '*qualificateur*'  
 Nom du qualificateur de la table. *qualifier* est de **type sysname**, avec NULL comme valeur par défaut. Divers produits SGBD prennent en charge les noms de table en trois parties (*qualifier.Owner.Name*). Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette colonne représente le nom de la base de données. Dans certains produits, elle représente le nom du serveur de l'environnement de base de données de la table.  
  
 [ @col_type=] '*col_type*'  
 Type de colonne. *col_type* est de type **char (** 1 **)**, avec r comme valeur par défaut. type r retourne la colonne ou le jeu de colonnes optimal qui, en extrayant des valeurs de la ou des colonnes, permet d’identifier de manière unique toutes les lignes de la table spécifiée. Une colonne peut être soit une colonne virtuelle spécifiquement créée à cet effet, soit la ou les colonnes d'un index unique de la table. Le type V fournit la ou les colonnes de la table spécifiée qui, le cas échéant, sont automatiquement mises à jour par la source de données lorsqu'une valeur dans la ligne est mise à jour par une transaction.  
  
 [ @scope=] '*scope*'  
 Étendue minimale requise de l'identificateur de ligne ROWID. *scope* est de **type char (** 1 **)**, avec T comme valeur par défaut. l’étendue C spécifie que ROWID n’est valide que lorsqu’il est positionné sur cette ligne. L'étendue T indique que le ROWID est valide pour l'ensemble de la transaction.  
  
 [ @nullable=] '*Nullable*'  
 Permet de savoir si les colonnes spéciales peuvent accepter ou non une valeur NULL. *Nullable* est de **type char (** 1 **)**, avec U. O comme valeur par défaut. spécifie des colonnes spéciales qui n’autorisent pas les valeurs NULL. U identifie les colonnes qui acceptent partiellement des valeurs NULL.  
  
 [ @ODBCVer=] «*ODBCVer*»  
 Version ODBC utilisée. *ODBCVer* est de **type int (** 4 **)**, avec 2 comme valeur par défaut. Cela indique ODBC version 2.0. Pour plus d'informations sur les différences existant entre la version 2.0 et la version 3.0 d'ODBC, consultez la spécification ODBC SQLSpecialColumns pour ODBC version 3.0.  
  
## <a name="return-code-values"></a>Codet de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|SCOPE|**smallint**|Étendue réelle de l'identificateur de ligne. Peut prendre les valeurs 0, 1 ou 2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]retourne toujours 0. Ce champ retourne toujours une valeur.<br /><br /> 0 = SQL_SCOPE_CURROW. La validité du numéro d'identification de ligne est garantie uniquement pendant qu'il est positionné sur cette ligne. Il se peut qu'une sélection ultérieure qui utiliserait le numéro d'identification de la ligne ne retourne pas de ligne si celle-ci a été mise à jour ou supprimée au cours d'une autre transaction.<br /><br /> 1 = SQL_SCOPE_TRANSACTION. La validité du numéro d'identification de ligne est garantie pour la durée de la transaction en cours.<br /><br /> 2 = SQL_SCOPE_SESSION. L'identificateur de ligne est valide pour la durée de la session (parmi les limites de transaction).|  
|COLUMN_NAME|**sysname**|Nom de colonne de chaque colonne de la *table*retournée. Ce champ retourne toujours une valeur.|  
|DATA_TYPE|**smallint**|Type de données ODBC SQL.|  
|TYPE_NAME|**sysname**|Nom du type de données dépendant de la source de données ; par exemple, **char**, **varchar**, **Money**ou **Text**.|  
|PRECISION|**Int**|Précision de la colonne dans la source de données. Ce champ retourne toujours une valeur.|  
|LENGTH|**Int**|Longueur, en octets, requise pour le type de données sous sa forme binaire dans la source de données, par exemple 10 pour **char (** 10 **)**, 4 pour **Integer**et 2 pour **smallint**.|  
|SCALE|**smallint**|Échelle de la colonne dans la source de données. La valeur NULL est retournée pour les types de données pour lesquels l'échelle n'est pas applicable.|  
|PSEUDO_COLUMN|**smallint**|Indique si la colonne est un pseudocolonne. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne toujours 1 :<br /><br /> 0 = SQL_PC_UNKNOWN<br /><br /> 1 = SQL_PC_NOT_PSEUDO<br /><br /> 2 = SQL_PC_PSEUDO|  
  
## <a name="remarks"></a>Notes  
 La procédure stockée sp_special_columns est équivalente à SQLSpecialColumns dans ODBC. Les résultats obtenus sont triés par SCOPE.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation SELECT sur le schéma.  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Cet exemple retourne des informations sur la colonne qui identifie les lignes de manière unique dans la table `FactFinance`.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_special_columns_100 @table_name = 'FactFinance';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées SQL Data Warehouse](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)  
  
  

