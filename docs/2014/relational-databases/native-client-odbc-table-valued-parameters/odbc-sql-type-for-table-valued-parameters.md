---
title: Type SQL ODBC pour les paramètres table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90857b24fb467df0292beeb88fb9751e68204d12
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63199987"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>type ODBC SQL pour les paramètres table
  La prise en charge des paramètres de table est fournie par un nouveau type SQL ODBC, SQL_SS_TABLE.  
  
## <a name="remarks"></a>Notes  
 SQL_SS_TABLE ne peut pas être converti en un autre type de données ODBC ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Si SQL_SS_TABLE est utilisé comme type de données C dans le paramètre *ValueType* de SQLBindParameter ou si une tentative est faite pour définir SQL_DESC_TYPE dans un enregistrement de descripteur de paramètre d’application (APD) à SQL_SS_TABLE, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE = HY003, « type de tampon d’application non valide ».  
  
 Si SQL_DESC_TYPE est défini avec la valeur SQL_SS_TABLE dans un enregistrement IPD et que l'enregistrement APD correspondant n'est pas SQL_C_DEFAULT, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE=HY003, « Type de tampon d'application non valide ». Cela peut se produire avec le *ParameterType* d’un SQLSetDescField, SQLSetDescRec ou SQLBindParameter.  
  
 Si le paramètre *TargetType* est SQL_SS_TABLE lors de l’appel de SQLGetData, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE = HY003, « type de tampon d’application non valide ».  
  
 Une colonne de paramètre table ne peut pas être liée comme type SQL_SS_TABLE. Si `SQLBindParameter` est appelé avec *ParameterType* défini sur SQL_SS_TABLE, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE = HY004, « type de données SQL non valide ». Cela peut également se produire avec SQLSetDescField et SQLSetDescRec.  
  
 Les valeurs des colonnes de paramètre table ont les mêmes options de conversion de données que les paramètres et les colonnes de résultat.  
  
 Un paramètre table ne peut être un paramètre d'entrée que dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure. Si une tentative est faite pour définir SQL_DESC_PARAMETER_TYPE sur une valeur autre que SQL_PARAM_INPUT via SQLBindParameter ou SQLSetDescField, SQL_ERROR est retourné et un enregistrement de diagnostic est ajouté à l’instruction avec SQLSTATE = HY105 et le message « type de paramètre non valide ».  
  
 Les colonnes de paramètre table ne peuvent pas utiliser SQL_DEFAULT_PARAM dans *StrLen_or_IndPtr*, parce que les valeurs par défaut par ligne ne sont pas prises en charge avec les paramètres table. À la place, une application peut définir l'attribut de colonne SQL_CA_SS_COL_HAS_DEFAULT_VALUE avec la valeur 1. Cela signifie que la colonne aura des valeurs par défaut pour toutes les lignes. Si *StrLen_or_IndPtr* a la valeur SQL_DEFAULT_PARAM, SQLExecute ou SQLExecDirect retourne SQL_ERROR et un enregistrement de diagnostic est ajouté à l’instruction avec SQLSTATE = HY090 et le message « longueur de chaîne ou de mémoire tampon non valide ».  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
