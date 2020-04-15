---
title: Fonctions du système Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302830"
---
# <a name="system-functions"></a>Fonctions système
Le tableau suivant répertorie les fonctions du système qui sont incluses dans l’ensemble de fonctions scalar ODBC. En appelant **SQLGetInfo** avec un *type d’information* de SQL_SYSTEM_FUNCTIONS, une application peut déterminer quelles fonctions système sont prises en charge par un conducteur.  
  
 Les arguments dénotés comme *exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un littéral, où le type de données sous-jacentes pourrait être représenté comme SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME, ou SQL_TYPE_TIMESTAMP.  
  
 Les arguments désignés comme *la valeur* peuvent être une constante littérale, où le type de données sous-jacent peut être représenté comme SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME ou SQL_TYPE_TIMESTAMP.  
  
 Les valeurs retournées sont représentées comme types de données ODBC.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**BASE DE DONNÉES) )** (ODBC 1.0)|Retourne le nom de la base de données correspondant à la poignée de connexion. (Le nom de la base de données est également disponible en appelant **SQLGetConnectOption** avec l’option de connexion SQL_CURRENT_QUALIFIER.)|  
|**IFNULL (** _exp_,_valeur_**)** (ODBC 1.0)|Si *l’exp* est nul, *la valeur* est retournée. Si *l’exp n’est* pas nul, *exp* est retourné. Le type de données possible ou les types de *valeur* doivent être compatibles avec le type de données *d’exp*.|  
|**UTILISATEUR) )** (ODBC 1.0)|Retourne le nom d’utilisateur dans le DBMS. (Le nom d’utilisateur est également disponible par le chemin de **SQLGetInfo** en spécifiant le type d’information: SQL_USER_NAME.) Cela peut être différent de celui de la connexion.|
