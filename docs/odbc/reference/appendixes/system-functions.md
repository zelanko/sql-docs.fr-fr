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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5870cb445d7afd098aba32ffd9be7a88c048bae5
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591513"
---
# <a name="system-functions"></a>Fonctions système
Le tableau suivant répertorie les fonctions système qui sont incluses dans le jeu de fonction scalaire ODBC. En appelant **SQLGetInfo** avec un *d’informations, tapez* de SQL_SYSTEM_FUNCTIONS, une application peut déterminer les fonctions système sont prises en charge par un pilote.  
  
 Arguments indiqués par *exp* peut être pas le nom d’une colonne, le résultat d’une autre fonction scalaire ou un littéral, où le type de données sous-jacent peut être représenté en tant que SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL _BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP.  
  
 Arguments indiqués par *valeur* peut être une constante littérale, où le type de données sous-jacent peut être représenté comme les SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_ TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP.  
  
 Valeurs retournées sont représentés en tant que types de données ODBC.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**(DE BASE DE DONNÉES)** (ODBC 1.0)|Retourne le nom de la base de données correspondant au descripteur de connexion. (Le nom de la base de données est également disponible en appelant **SQLGetConnectOption** avec l’option de connexion SQL_CURRENT_QUALIFIER.)|  
|**IFNULL (** _exp_,_valeur_**)** (ODBC version 1.0)|Si *exp* a la valeur null, *valeur* est retourné. Si *exp* n’est pas null, *exp* est retourné. L’ou les types de données possibles *valeur* doit être compatible avec le type de données *exp*.|  
|**UTILISATEUR ()** (ODBC 1.0)|Retourne le nom d’utilisateur dans le SGBD. (Le nom d’utilisateur est également disponible par le biais de **SQLGetInfo** en spécifiant le type d’informations : SQL_USER_NAME.) Cela peut être différent du nom de connexion.|
