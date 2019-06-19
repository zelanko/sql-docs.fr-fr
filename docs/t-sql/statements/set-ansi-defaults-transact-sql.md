---
title: SET ANSI_DEFAULTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET ANSI_DEFAULTS
- ANSI_DEFAULTS
- SET_ANSI_DEFAULTS_TSQL
- ANSI_DEFAULTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ANSI_DEFAULTS option
- SET ANSI_DEFAULTS statement
ms.assetid: bd721d97-6e23-488b-8c8c-c0453d5b3b86
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 871d79c805451e1710dbc400914d2dace01c7eea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62737074"
---
# <a name="set-ansidefaults-transact-sql"></a>SET ANSI_DEFAULTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contrôle un groupe de paramètres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui spécifie, de manière collective, certains comportements conformes à la norme ISO.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Syntaxe

```
-- Syntax for SQL Server

SET ANSI_DEFAULTS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_DEFAULTS ON
```

## <a name="remarks"></a>Notes  
ANSI_DEFAULTS est un paramètre côté serveur que le client ne modifie pas. Le client gère ses propres paramètres. Par défaut, ces paramètres sont l'inverse du paramètre serveur. Les utilisateurs ne doivent pas modifier le paramètre serveur. Pour modifier le comportement du client, les utilisateurs doivent recourir à SQL_COPT_SS_PRESERVE_CURSORS. Pour plus d’informations, consultez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
Lorsque cette option est activée (ON), elle active les paramètres ISO suivants :  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_NULL_DFLT_ON|SET IMPLICIT_TRANSACTIONS|  
|SET ANSI_PADDING|SET QUOTED_IDENTIFIER|  
|SET ANSI_WARNINGS||  
  
Ensemble, ces options SET ISO définissent l'environnement de traitement des requêtes pour la durée de la session de travail de l'utilisateur, de l'exécution d'un déclencheur ou d'une procédure stockée. Toutefois, ces options SET ne contiennent pas toutes les options requises pour se conformer à la norme ISO.  
  
Lorsque vous travaillez avec des index sur des colonnes calculées et des vues indexées, quatre options par défaut (ANSI_NULLS, ANSI_PADDING, ANSI_WARNINGS et QUOTED_IDENTIFIER) doivent être activées (valeur ON). Ces options par défaut font partie des sept options SET qui doivent avoir les valeurs requises lors de la création et de la modification des index sur des colonnes calculées et vues indexées. Les autres options SET sont ARITHABORT (ON), CONCAT_NULL_YIELDS_NULL (ON) et NUMERIC_ROUNDABORT (OFF). Pour plus d’informations sur les valeurs requises des options SET dans des vues indexées et des index de colonnes calculées, consultez [Remarques sur l’utilisation de l’instruction SET dans la rubrique](../../t-sql/statements/set-statements-transact-sql.md#considerations-when-you-use-the-set-statements).  
  
Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client et le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affectent automatiquement la valeur ON à ANSI_DEFAULTS lors de la connexion. Le pilote et le fournisseur désactivent ensuite CURSOR_CLOSE_ON_COMMIT et IMPLICIT_TRANSACTIONS. La désactivation de CURSOR_CLOSE_ON_COMMIT et IMPLICIT_TRANSACTIONS peut être configurée dans des sources de données ou des attributs de connexion ODBC, ou encore dans les propriétés de connexion OLE DB définies dans l’application avant la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans le cas d’applications DB-Library, ANSI_DEFAULTS prend par défaut la valeur OFF.  
  
Quand SET ANSI_DEFAULTS est émis, la valeur de QUOTED_IDENTIFIER est définie au moment de l’analyse, et les options suivantes sont définies au moment de l’exécution :  
  
|||  
|-|-|  
|SET ANSI_NULLS|SET ANSI_WARNINGS|  
|SET ANSI_NULL_DFLT_ON|SET CURSOR_CLOSE_ON_COMMIT|  
|SET ANSI_PADDING|SET IMPLICIT_TRANSACTIONS|  
  
## <a name="permissions"></a>Autorisations  
Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
L’exemple suivant définit ANSI_DEFAULTS avec la valeur ON et utilise l’instruction `DBCC USEROPTIONS` pour afficher les paramètres affectés.  
  
```sql  
-- SET ANSI_DEFAULTS ON.  
SET ANSI_DEFAULTS ON;  
GO  

-- Display the current settings.  
DBCC USEROPTIONS;  
GO 

-- SET ANSI_DEFAULTS OFF.  
SET ANSI_DEFAULTS OFF;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC USEROPTIONS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_NULL_DFLT_ON &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)   
 [SET CURSOR_CLOSE_ON_COMMIT &#40;Transact-SQL&#41;](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)   
 [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)  
  
  
