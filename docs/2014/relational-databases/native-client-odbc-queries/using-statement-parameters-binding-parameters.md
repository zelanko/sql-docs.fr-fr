---
title: Liaison de paramètres | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9dfe88f11cc26d4a9711b7f21caf4c4475ec954b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206737"
---
# <a name="binding-parameters"></a>Liaison de paramètres
  Chaque marqueur de paramètre dans une instruction SQL doit être associé, ou lié, à une variable dans l'application avant que l'instruction puisse être exécutée. Pour ce faire, appelez la fonction [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) . **SQLBindParameter** décrit la variable de programme (adresse, type de données C, etc.) au pilote. Cette fonction identifie également le marqueur de paramètre en indiquant sa valeur ordinale puis décrit les caractéristiques de l'objet SQL qu'il représente (type de données SQL, précision, etc.).  
  
 Les marqueurs de paramètre peuvent être liés ou liés une nouvelle fois à tout moment avant l'exécution d'une instruction. Une liaison de paramètre reste en vigueur jusqu'à ce que l'un des événements suivants se produise :  
  
-   Un appel à [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) avec le paramètre *Option* défini sur SQL_RESET_PARAMS libère tous les paramètres liés au descripteur d’instruction.  
  
-   Un appel à **SQLBindParameter** avec *ParameterNumber* défini sur l’ordinal d’un marqueur de paramètre lié libère automatiquement la liaison précédente.  
  
 Une application peut également lier des paramètres à des tableaux de variables de programme pour traiter une instruction SQL par lots. Il existe deux types de liaison de tableau :  
  
-   Une liaison selon les colonnes est effectuée lorsque chaque paramètre individuel est lié à son propre tableau de variables.  
  
     La liaison selon les colonnes est spécifiée en appelant [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) avec l' *attribut* défini sur SQL_ATTR_PARAM_BIND_TYPE et *ValuePtr* défini sur SQL_PARAM_BIND_BY_COLUMN.  
  
-   Une liaison selon les lignes est effectuée lorsque tous les paramètres dans l'instruction SQL sont liés en tant qu'unité à un tableau de structures qui contiennent les variables individuelles pour les paramètres.  
  
     La liaison selon les lignes est spécifiée en appelant **SQLSetStmtAttr** avec l' *attribut* défini sur SQL_ATTR_PARAM_BIND_TYPE et *ValuePtr* défini sur la taille de la structure contenant les variables de programme.  
  
 Lorsque le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client envoie des paramètres de chaîne de caractères ou binaires au serveur, il remplit les valeurs à la longueur spécifiée dans le paramètre **SQLBindParameter** *Columns* . Si une application ODBC 2. x spécifie 0 pour *Column*, le pilote remplit la valeur de paramètre avec la précision du type de données. La précision est 8000 lors d'une connexion à des serveurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 255 lors d'une connexion à des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La *colonne Columns* est en octets pour les colonnes de type Variant.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge la définition de noms pour les paramètres de procédure stockée. ODBC 3.5 a également introduit la prise en charge des paramètres nommés utilisés lors de l'appel de procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette prise en charge peut être utilisée pour :  
  
-   appeler une procédure stockée et fournir des valeurs pour un sous-ensemble des paramètres définis pour la procédure stockée ;  
  
-   spécifier les paramètres dans un ordre différent dans l'application de l'ordre spécifié quand la procédure stockée a été créée.  
  
 Les paramètres nommés sont pris en charge uniquement [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` lors de l’utilisation de l’instruction ou de la séquence d’échappement ODBC Call pour exécuter une procédure stockée.  
  
 Si `SQL_DESC_NAME` est défini pour un paramètre de procédure stockée, tous les paramètres de procédure stockée dans la requête doivent également définir `SQL_DESC_NAME`.  Si des littéraux sont utilisés dans les appels de procédure stockée `SQL_DESC_NAME` , où les paramètres ont défini, les littéraux doivent utiliser le format *'Name*=*value*', où *Name* est le nom du paramètre @p1de procédure stockée (par exemple,). Pour plus d’informations, consultez [liaison de paramètres par nom (paramètres nommés)](https://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de paramètres d'instruction](using-statement-parameters.md)  
  
  
