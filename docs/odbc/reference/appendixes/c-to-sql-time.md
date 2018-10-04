---
title: 'C en SQL : heure | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ea11803847505698ea42d13727b6177f3a24bda
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606177"
---
# <a name="c-to-sql-time"></a>C en SQL : heure
L’identificateur pour le type de données ODBC C temps est :  
  
 SQL_C_TYPE_TIME  
  
 Le tableau suivant présente les types de données à laquelle les données de C de temps peuvent être converties à ODBC SQL. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificateur de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’octet de colonne > = 8<br /><br /> Colonne de longueur d’octet < 8<br /><br /> Valeur de données n’est pas une heure valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur de colonne caractère > = 8<br /><br /> Colonne de longueur < 8 caractères<br /><br /> Valeur de données n’est pas une heure valide|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Valeur de données est une heure valide<br /><br /> Valeur de données n’est pas une heure valide|n/a<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Valeur de données est une heure valide [a]<br /><br /> Valeur de données n’est pas une heure valide|n/a<br /><br /> 22007|  
  
 [a] la date de partie de l’horodatage est définie sur la date actuelle et la fraction de seconde partie de l’horodatage est défini à zéro.  
  
 Pour plus d’informations sur les valeurs qui sont valides dans une structure SQL_C_TYPE_TIME, consultez [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md), plus haut dans cette annexe.  
  
 Lorsque les données de temps C sont converties en données de caractères SQL, les données de caractères résultant sont dans la «*hh*:*mm*:*ss*« format.  
  
 Le pilote ignore la valeur de longueur/indicateur lors de la conversion des données à partir de l’heure de type de données de C et suppose que la taille du tampon de données est la taille du type de données C de temps. La valeur de longueur / d’indicateur est passée dans le *StrLen_or_Ind* argument dans **SQLPutData** et dans la mémoire tampon spécifiée avec la *StrLen_or_IndPtr* argument dans **SQLBindParameter**. Le tampon de données est spécifié avec la *DataPtr* argument dans **SQLPutData** et *ParameterValuePtr* argument dans **SQLBindParameter**.
