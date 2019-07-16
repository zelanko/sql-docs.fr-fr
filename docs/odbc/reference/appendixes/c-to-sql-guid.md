---
title: 'C en SQL : GUID | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5863935ddf595409d48be79dc646c0994ddeb0b8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019321"
---
# <a name="c-to-sql-guid"></a>C en SQL : GUID
L’identificateur pour le type de données GUID ODBC C est :  
  
 SQL_C_GUID  
  
 Le tableau suivant présente les types de données à laquelle les données de GUID C peuvent être converties à ODBC SQL. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificateur de type SQL|Tester|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Longueur d’octet de colonne > = 36|N/A|  
|SQL_VARCHAR|Colonne de longueur d’octet < 36|22001|  
|SQL_LONGVARCHAR|Valeur de données n’est pas un GUID valide|22018|  
|SQL_WCHAR|Longueur de colonne caractère > = 36|N/A|  
|SQL_WVARCHAR|Colonne de longueur < 36 caractères|22001|  
|SQL_WLONGVARCHAR|Valeur de données n’est pas un GUID valide|22018|  
|SQL_GUID|Aucun [a]|N/A|  
  
 [a] toutes les valeurs hexadécimales sont valides en tant que GUID.  
  
 Le pilote ignore la valeur de longueur/indicateur lors de la conversion des données à partir du type de données GUID C et suppose que la taille du tampon de données est la taille du type de données GUID C. La valeur de longueur / d’indicateur est passée dans le *StrLen_or_Ind* argument dans **SQLPutData** et dans la mémoire tampon spécifiée avec la *StrLen_or_IndPtr* argument dans **SQLBindParameter**. Le tampon de données est spécifié avec la *DataPtr* argument dans **SQLPutData** et *ParameterValuePtr* argument dans **SQLBindParameter**.
