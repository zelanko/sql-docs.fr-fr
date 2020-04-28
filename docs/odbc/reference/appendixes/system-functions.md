---
title: Fonctions système | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- system functions [ODBC]
- functions [ODBC], system functions
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca71687887444cafc502c15683f3972cf6308e6b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302830"
---
# <a name="system-functions"></a>Fonctions système
Le tableau suivant répertorie les fonctions système incluses dans le jeu de fonctions scalaires ODBC. En appelant **SQLGetInfo** avec un *type d’informations* SQL_SYSTEM_FUNCTIONS, une application peut déterminer quelles fonctions système sont prises en charge par un pilote.  
  
 Les arguments dénotés comme *exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire ou un littéral, où le type de données sous-jacent peut être représenté sous la forme SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME ou SQL_TYPE_TIMESTAMP.  
  
 Les arguments dénotés comme *valeur* peuvent être une constante littérale, où le type de données sous-jacent peut être représenté sous la forme SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME ou SQL_TYPE_TIMESTAMP.  
  
 Les valeurs retournées sont représentées en tant que types de données ODBC.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**Base de données ()** (ODBC 1,0)|Retourne le nom de la base de données correspondant au handle de connexion. (Le nom de la base de données est également disponible en appelant **sqlgetconnectoption,** avec l’option de connexion SQL_CURRENT_QUALIFIER.)|  
|**IFNULL (** _exp_,_value_**)** (ODBC 1,0)|Si *exp* a la valeur null, la *valeur* est retournée. Si *exp* n’est pas null, *exp* est retourné. Le ou les types de données possibles *doivent être* compatibles avec le type de données *exp*.|  
|**Utilisateur ()** (ODBC 1,0)|Retourne le nom d’utilisateur dans le SGBD. (Le nom d’utilisateur est également disponible au moyen de **SQLGetInfo** en spécifiant le type d’informations : SQL_USER_NAME.) Il peut être différent du nom de connexion.|
