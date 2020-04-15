---
title: 'C à SQL: GUID Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b3b559499273e885e23da10d9093a0ce9ff92393
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306620"
---
# <a name="c-to-sql-guid"></a>C en SQL : GUID
L’identifiant pour le type de données GUID ODBC C est :  
  
 SQL_C_GUID  
  
 Le tableau suivant montre les types de données SQL ODBC auxquels les données GUID C peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Longueur d’ente de colonne >36|n/a|  
|SQL_VARCHAR|Longueur d’ente de colonne < 36|22001|  
|SQL_LONGVARCHAR|La valeur des données n’est pas une GUID valide|22018|  
|SQL_WCHAR|Longueur de caractère de colonne >36|n/a|  
|SQL_WVARCHAR|Longueur de caractère de colonne < 36|22001|  
|SQL_WLONGVARCHAR|La valeur des données n’est pas une GUID valide|22018|  
|SQL_GUID|Aucun[a]|n/a|  
  
 [a] Toutes les valeurs hexidecimales sont valables en tant que GUID.  
  
 Le conducteur ignore la valeur de longueur/indicateur lors de la conversion des données du type de données GUID C et suppose que la taille du tampon de données est la taille du type de données GUID C. La durée/valeur de l’indicateur est passée dans *l’argument StrLen_or_Ind* dans **SQLPutData** et dans le tampon spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**. Le tampon de données est spécifié avec l’argument *DataPtr* dans **SQLPutData** et *l’argument De ParameterValuePtr* dans **SQLBindParameter**.
