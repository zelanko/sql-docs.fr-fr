---
title: Type SQL ODBC pour les paramètres de valeur de table (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6aae522544f4d9532dbc2d71db1b3d55ebee3da5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297839"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>type ODBC SQL pour les paramètres table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  La prise en charge des paramètres de table est fournie par un nouveau type SQL ODBC, SQL_SS_TABLE.  
  
## <a name="remarks"></a>Notes  
 SQL_SS_TABLE ne peut pas être converti en un autre type de données ODBC ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Si SQL_SS_TABLE est utilisé comme type de données C dans le paramètre *ValueType* de SQLBindParameter, ou si une tentative est faite pour établir SQL_DESC_TYPE dans un enregistrement descripteur de paramètre d’application (APD) pour SQL_SS_TABLE, SQL_ERROR est retourné et un dossier diagnostique est généré avec SQLSTATE-HY003, "Type tampon d’application invalide".  
  
 Si SQL_DESC_TYPE est défini avec la valeur SQL_SS_TABLE dans un enregistrement IPD et que l'enregistrement APD correspondant n'est pas SQL_C_DEFAULT, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE=HY003, « Type de tampon d'application non valide ». Cela peut se produire avec le *ParameterType* d’un SQLSetDescField, SQLSetDescRec ou SQLBindParameter.  
  
 Si le paramètre *TargetType* est SQL_SS_TABLE lorsqu’il appelle SQLGetData, SQL_ERROR est retourné et un dossier de diagnostic est généré avec SQLSTATE-HY003, «Type tampon d’application invalide».  
  
 Une colonne de paramètre table ne peut pas être liée comme type SQL_SS_TABLE. Si **SQLBindParameter** est appelé avec *ParameterType* défini avec la valeur SQL_SS_TABLE, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE=HY004, « Type de données SQL non valide ». Cela peut également se produire avec SQLSetDescField et SQLSetDescRec.  
  
 Les valeurs des colonnes de paramètre table ont les mêmes options de conversion de données que les paramètres et les colonnes de résultat.  
  
 Un paramètre table ne peut être un paramètre d'entrée que dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure. Si une tentative est faite pour établir SQL_DESC_PARAMETER_TYPE à une valeur autre que SQL_PARAM_INPUT via SQLBindParameter ou SQLSetDescField, SQL_ERROR est retourné et un dossier diagnostique est ajouté à la déclaration avec SQLSTATE-HY105 et le message "Type de paramètre invalide".  
  
 Les colonnes de paramètre table ne peuvent pas utiliser SQL_DEFAULT_PARAM dans *StrLen_or_IndPtr*, parce que les valeurs par défaut par ligne ne sont pas prises en charge avec les paramètres table. À la place, une application peut définir l'attribut de colonne SQL_CA_SS_COL_HAS_DEFAULT_VALUE avec la valeur 1. Cela signifie que la colonne aura des valeurs par défaut pour toutes les lignes. Si *StrLen_or_IndPtr* est réglée pour SQL_DEFAULT_PARAM, SQLExecute ou SQLExecDirect retourneront SQL_ERROR, et un dossier diagnostique sera ajouté à la déclaration avec SQLSTATE-HY090 et au message « Durée de la chaîne ou de la mémoire tampon invalide ».  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres évalués par la table &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
