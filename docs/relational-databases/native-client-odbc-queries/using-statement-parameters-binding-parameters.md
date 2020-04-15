---
title: Paramètres contraignants (en anglais) Microsoft Docs
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
ms.openlocfilehash: 01e179d2abc6ef786f94b6d7938f0e21938c5a59
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304625"
---
# <a name="using-statement-parameters---binding-parameters"></a>Utilisation de paramètres d’instruction - Liaison de paramètres
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Chaque marqueur de paramètre dans une instruction SQL doit être associé, ou lié, à une variable dans l'application avant que l'instruction puisse être exécutée. Cela se fait en appelant la fonction [SQLBindParameter.](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) **SQLBindParameter** décrit la variable du programme (adresse, type de données C, etc.) au conducteur. Cette fonction identifie également le marqueur de paramètre en indiquant sa valeur ordinale puis décrit les caractéristiques de l'objet SQL qu'il représente (type de données SQL, précision, etc.).  
  
 Les marqueurs de paramètre peuvent être liés ou liés une nouvelle fois à tout moment avant l'exécution d'une instruction. Une liaison de paramètre reste en vigueur jusqu'à ce que l'un des événements suivants se produise :  
  
-   Un appel à [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) avec le paramètre *Option* réglé pour SQL_RESET_PARAMS libère tous les paramètres liés à la poignée de déclaration.  
  
-   Un appel à **SQLBindParameter** avec *ParameterNumber* réglé à l’ordinaire d’un marqueur de paramètres lié libère automatiquement la liaison précédente.  
  
 Une application peut également lier des paramètres à des tableaux de variables de programme pour traiter une instruction SQL par lots. Il existe deux types de liaison de tableau :  
  
-   Une liaison selon les colonnes est effectuée lorsque chaque paramètre individuel est lié à son propre tableau de variables.  
  
     La liaison de colonne-sage est spécifiée en appelant [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) avec *attribut* réglé à SQL_ATTR_PARAM_BIND_TYPE et *ValuePtr* réglé à SQL_PARAM_BIND_BY_COLUMN.  
  
-   Une liaison selon les lignes est effectuée lorsque tous les paramètres dans l'instruction SQL sont liés en tant qu'unité à un tableau de structures qui contiennent les variables individuelles pour les paramètres.  
  
     La liaison de ligne-sage est spécifiée en appelant **SQLSetStmtAttr** avec *attribut* réglé à SQL_ATTR_PARAM_BIND_TYPE et *ValuePtr* réglé à la taille de la structure tenant les variables du programme.  
  
 Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote Native Client ODBC envoie des paramètres de caractère ou de chaîne binaire au serveur, il tamponne les valeurs à la longueur spécifiée dans le paramètre **SQLBindParameter** *ColumnSize.* Si une application ODBC 2.x spécifie 0 pour *ColumnSize,* le pilote tamponne la valeur de paramètres à la précision du type de données. La précision est 8000 lors d'une connexion à des serveurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 255 lors d'une connexion à des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *ColumnSize* est dans les octets pour les colonnes variante.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge la définition de noms pour les paramètres de procédure stockée. ODBC 3.5 a également introduit la prise en charge des paramètres nommés utilisés lors de l'appel de procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette prise en charge peut être utilisée pour :  
  
-   appeler une procédure stockée et fournir des valeurs pour un sous-ensemble des paramètres définis pour la procédure stockée ;  
  
-   spécifier les paramètres dans un ordre différent dans l'application de l'ordre spécifié quand la procédure stockée a été créée.  
  
 Les paramètres nommés ne [!INCLUDE[tsql](../../includes/tsql-md.md)] sont pris en charge que lors de l’utilisation de l’instruction **EXECUTE** ou de la séquence d’évacuation ODBC CALL pour exécuter une procédure stockée.  
  
 Si **SQL_DESC_NAME** est définie pour un paramètre de procédure stocké, tous les paramètres de procédure stockés dans la requête doivent également définir **SQL_DESC_NAME**.  Si les littérals sont utilisés dans les appels de procédure stockés, où les paramètres ont **SQL_DESC_NAME** défini, les littérals doivent utiliser le format *«valeur* *du nom»,*=où le *nom* est le nom de paramètre de procédure stockée (par exemple, @p1). Pour plus d’informations, voir [Paramètres contraignants par nom (Paramètres nommés)](https://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de paramètres d'instruction](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
