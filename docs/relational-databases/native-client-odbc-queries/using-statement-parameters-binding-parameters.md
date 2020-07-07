---
title: Liaison de paramètres | Microsoft Docs
description: Découvrez comment lier chaque marqueur de paramètre dans une instruction SQL à une variable dans l’application avant que l’instruction puisse s’exécuter.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab2bb533605c09a0a0d20e970eef58c1fbdd7ffd
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86002909"
---
# <a name="using-statement-parameters---binding-parameters"></a>Utilisation de paramètres d’instruction - Liaison de paramètres
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Chaque marqueur de paramètre dans une instruction SQL doit être associé, ou lié, à une variable dans l'application avant que l'instruction puisse être exécutée. Pour ce faire, appelez la fonction [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) . **SQLBindParameter** décrit la variable de programme (adresse, type de données C, etc.) au pilote. Cette fonction identifie également le marqueur de paramètre en indiquant sa valeur ordinale puis décrit les caractéristiques de l'objet SQL qu'il représente (type de données SQL, précision, etc.).  
  
 Les marqueurs de paramètre peuvent être liés ou liés une nouvelle fois à tout moment avant l'exécution d'une instruction. Une liaison de paramètre reste en vigueur jusqu'à ce que l'un des événements suivants se produise :  
  
-   Un appel à [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) avec le paramètre *Option* défini sur SQL_RESET_PARAMS libère tous les paramètres liés au descripteur d’instruction.  
  
-   Un appel à **SQLBindParameter** avec *ParameterNumber* défini sur l’ordinal d’un marqueur de paramètre lié libère automatiquement la liaison précédente.  
  
 Une application peut également lier des paramètres à des tableaux de variables de programme pour traiter une instruction SQL par lots. Il existe deux types de liaison de tableau :  
  
-   Une liaison selon les colonnes est effectuée lorsque chaque paramètre individuel est lié à son propre tableau de variables.  
  
     La liaison selon les colonnes est spécifiée en appelant [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) avec l' *attribut* défini sur SQL_ATTR_PARAM_BIND_TYPE et *ValuePtr* défini sur SQL_PARAM_BIND_BY_COLUMN.  
  
-   Une liaison selon les lignes est effectuée lorsque tous les paramètres dans l'instruction SQL sont liés en tant qu'unité à un tableau de structures qui contiennent les variables individuelles pour les paramètres.  
  
     La liaison selon les lignes est spécifiée en appelant **SQLSetStmtAttr** avec l' *attribut* défini sur SQL_ATTR_PARAM_BIND_TYPE et *ValuePtr* défini sur la taille de la structure contenant les variables de programme.  
  
 Lorsque le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client envoie des paramètres de chaîne de caractères ou binaires au serveur, il remplit les valeurs à la longueur spécifiée dans le paramètre **SQLBindParameter** *Columns* . Si une application ODBC 2. x spécifie 0 pour *Column*, le pilote remplit la valeur de paramètre avec la précision du type de données. La précision est 8000 lors d'une connexion à des serveurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 255 lors d'une connexion à des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La *colonne Columns* est en octets pour les colonnes de type Variant.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge la définition de noms pour les paramètres de procédure stockée. ODBC 3.5 a également introduit la prise en charge des paramètres nommés utilisés lors de l'appel de procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette prise en charge peut être utilisée pour :  
  
-   appeler une procédure stockée et fournir des valeurs pour un sous-ensemble des paramètres définis pour la procédure stockée ;  
  
-   spécifier les paramètres dans un ordre différent dans l'application de l'ordre spécifié quand la procédure stockée a été créée.  
  
 Les paramètres nommés sont pris en charge uniquement lors de l’utilisation de l' [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction **Execute** ou de la séquence d’échappement ODBC Call pour exécuter une procédure stockée.  
  
 Si **SQL_DESC_NAME** est définie pour un paramètre de procédure stockée, tous les paramètres de procédure stockée dans la requête doivent également définir **SQL_DESC_NAME**.  Si des littéraux sont utilisés dans les appels de procédure stockée, où les paramètres ont **SQL_DESC_NAME** défini, les littéraux doivent utiliser le format *'Name* = *value*', où *Name* est le nom du paramètre de procédure stockée (par exemple, @p1 ). Pour plus d’informations, consultez [liaison de paramètres par nom (paramètres nommés)](https://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de paramètres d'instruction](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
