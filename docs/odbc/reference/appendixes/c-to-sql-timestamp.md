---
title: 'C à SQL: Timestamp Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3102e5043527a1aa9463980c9dd546839cb92f37
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283749"
---
# <a name="c-to-sql-timestamp"></a>C en SQL : Timestamp
L’identifiant pour le type de données ODBC C est :  
  
 SQL_C_TYPE_TIMESTAMP  
  
 Le tableau suivant montre les types de données SQL ODBC auxquels les données de l’humidité du temps C peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’ente de colonne >- Longueur d’ente de caractère<br /><br /> 19 <- Longueur d’ente de colonne < Longueur de caractère<br /><br /> Longueur d’ente de colonne < 19<br /><br /> La valeur des données n’est pas un 2e temps valide|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur de caractère de colonne >- Longueur de caractère des données<br /><br /> 19 <- Longueur de caractère de colonne < longueur de caractère des données<br /><br /> Longueur de caractère de colonne < 19<br /><br /> La valeur des données n’est pas un 2e temps valide|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Les champs de temps sont nuls<br /><br /> Les champs de temps sont nonzero<br /><br /> La valeur des données ne contient pas de date valide|n/a<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Les champs de secondes fractionnées sont nuls[a]<br /><br /> Les champs de secondes fractionnées sont nonzero[a]<br /><br /> La valeur des données ne contient pas de temps valide|n/a<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Les champs fractionnaires de secondes ne sont pas tronqués<br /><br /> Les champs fractionnels de secondes sont tronqués<br /><br /> La valeur des données n’est pas un 2e temps valide|n/a<br /><br /> 22008<br /><br /> 22007|  
  
 [a] Les champs de date de la structure de timestamp sont ignorés.  
  
 Pour plus d’informations sur les valeurs qui sont valables dans une structure SQL_C_TIMESTAMP, voir [C Data Types](../../../odbc/reference/appendixes/c-data-types.md), plus tôt dans cette annexe.  
  
 Lorsque les données de timestamp C sont converties en données SQL de caractère, les données de caractère qui en résultent se situent dans le «*yyyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.* f...*]" Format.  
  
 Le conducteur ignore la valeur de longueur/indicateur lors de la conversion des données du type de données de l’humidité du temps C et suppose que la taille du tampon de données est la taille du type de données de l’humidité du temps C. La durée/valeur de l’indicateur est passée dans *l’argument StrLen_or_Ind* dans **SQLPutData** et dans le tampon spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**. Le tampon de données est spécifié avec l’argument *DataPtr* dans **SQLPutData** et *l’argument De ParameterValuePtr* dans **SQLBindParameter**.
