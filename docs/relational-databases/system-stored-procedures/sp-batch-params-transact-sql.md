---
title: sp_batch_params (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_batch_params
- sp_batch_params_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_batch_params
ms.assetid: 7b92fe9e-e755-4b7a-8a15-822c58a813d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00efe39e8ab60df83ddd267269461f6a6ff61ee0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47594628"
---
# <a name="spbatchparams-transact-sql"></a>sp_batch_params (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne un ensemble de lignes qui contient des informations sur les paramètres inclus dans un [!INCLUDE[tsql](../../includes/tsql-md.md)] batch. **sp_batch_params** uniquement analyse le lot spécifié et retourne des informations sur les valeurs de paramètres incorporés. N'exécute pas le traitement et ne modifie pas l'environnement d'exécution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_batch_params [ [ @tsqlbatch = ] 'tsqlbatch' ]   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@tsqlbatch =**] **'***tsqlbatch***'**  
 Est une chaîne Unicode contenant un [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction ou un lot pour le paramètre informations sont que vous souhaitez. *tsqlbatch* est **nvarchar (max)** ou implicitement convertible en **nvarchar (max)**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**PARAMETER_NAME**|**sysname**|Nom du paramètre que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a trouvé dans le traitement.|  
|**COLUMN_TYPE**|**smallint**|Ce champ retourne l'une des valeurs suivantes :<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE<br /><br /> Cette colonne a toujours pour valeur 0.|  
|**DATA_TYPE**|**smallint**|Type de données du paramètre (code d'entier d'un type de données ODBC). Si ce type de données ne peut pas être mappé à un type ISO, la valeur est NULL. Le nom de type de données natif est retourné dans le **TYPE_NAME** colonne. Cette valeur est toujours NULL.|  
|**TYPE_NAME**|**sysname**|Représentation sous forme de chaîne du type de données tel qu'il est présenté par le SGBD sous-jacent. Cette valeur est NULL.|  
|**PRECISION**|**Int**|Nombre de chiffres significatifs. La valeur de retour pour la **précision** colonne est en base 10.|  
|**LENGTH**|**Int**|Taille de transfert des données. Cette valeur est NULL.|  
|**MISE À L’ÉCHELLE**|**smallint**|Nombre de chiffres situés à droite du séparateur décimal. Cette valeur est NULL.|  
|**RADIX**|**smallint**|Base des types numériques. Cette valeur est NULL.|  
|**NULLABLE**|**smallint**|Précise la possibilité de valeur nulle.<br /><br /> 1 = le type de données du paramètre peut être créé de manière à autoriser les valeurs NULL.<br /><br /> 0 = les valeurs NULL ne sont pas autorisées.<br /><br /> Cette valeur est NULL.|  
|**SQL_DATA_TYPE**|**smallint**|Valeur du type de données système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] telle qu'elle apparaît dans le champ TYPE du descripteur. Cette colonne est la même que la colonne **DATA_TYPE**, excepté pour les types de données **datetime** et **interval** ISO. Cette colonne renvoie toujours une valeur. Cette valeur est NULL.|  
|**SQL_DATETIME_SUB**|**smallint**|Le **datetime** ou ISO **intervalle** sous-code si la valeur de **SQL_DATA_TYPE** est SQL_DATETIME ou SQL_INTERVAL. Pour les données de types autres que **datetime** et ISO **intervalle**, cette colonne est NULL. Cette valeur est NULL.|  
|**CHAR_OCTET_LENGTH**|**Int**|Longueur maximale en octets d’un **caractère** ou **binaire** paramètre de type de données. Pour tous les autres types de données, cette colonne retourne une valeur NULL. Cette valeur est toujours NULL.|  
|**ORDINAL_POSITION**|**Int**|Numéro d'ordre du paramètre dans le traitement. Si le nom du paramètre est répété plusieurs fois, cette colonne indique la position de la première occurrence. Le premier paramètre occupe la position 1. Cette colonne renvoie toujours une valeur.|  
  
## <a name="permissions"></a>Permissions  
 Autorisation d’exécuter **sp_batch_params** est accordée aux **public**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre la transmission d'une requête à `sp_batch_params`. Le jeu de résultats énumère la liste des valeurs de paramètres incorporés.  
  
```  
DECLARE @SQLString nvarchar(500);  
/* Build the SQL string */  
SET @SQLString =  
     N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
     WHERE BusinessEntityID = @BusinessEntityID';  
EXECUTE sp_batch_params @SQLString;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de procédures stockées](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Les rubriques de procédures de procédures stockées en cours d’exécution &#40;ODBC&#41;](http://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)   
 [Exécution de procédures stockées &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)  
  
  
