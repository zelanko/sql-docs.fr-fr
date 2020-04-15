---
title: Transfert de données des paramètres évalués par la table
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), binding and data transfer
ms.assetid: 0a2ea462-d613-42b6-870f-c7fa086a6b42
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3b7eecfdac3d42b7a3d8d66ffe1f8ac68652230f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304494"
---
# <a name="binding-and-data-transfer-of-table-valued-parameters-and-column-values"></a>Liaison et transfert de données de paramètres table et de valeurs de colonnes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les paramètres table, comme d'autres paramètres, doivent être liés avant d'être passés au serveur. L’application lie les paramètres de valeur de table de la même façon qu’il lie d’autres paramètres : en utilisant SQLBindParameter ou des appels équivalents à SQLSetDescField ou SQLSetDescRec. Le type de données serveur pour un paramètre table est SQL_SS_TABLE. Le type C peut être spécifié comme SQL_C_DEFAULT ou SQL_C_BINARY.  
  
 Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure, seuls les paramètres table d'entrée sont pris en charge. Par conséquent, toute tentative de définition de SQL_DESC_PARAMETER_TYPE à une valeur autre que SQL_PARAM_INPUT retourne SQL_ERROR avec SQLSTATE = HY105 et le message « type de paramètre non valide ».  
  
 Des valeurs par défaut peuvent être assignées à des colonnes de paramètres table entières à l'aide de l'attribut SQL_CA_SS_COL_HAS_DEFAULT_VALUE. Toutefois, les valeurs de colonnes de paramètres individuelles évaluées par table ne peuvent pas être attribuées à des valeurs par défaut en utilisant SQL_DEFAULT_PARAM dans *StrLen_or_IndPtr* avec SQLBindParameter. Les paramètres évalués par table dans leur ensemble ne peuvent pas être définis à une valeur par défaut en utilisant SQL_DEFAULT_PARAM dans *StrLen_or_IndPtr* avec SQLBindParameter. Si ces règles ne sont pas respectées, SQLExecute ou SQLExecDirect retourneront SQL_ERROR. Un dossier diagnostique sera généré avec SQLSTATE-07S01 et le message \<"Utilisation invalide \<du paramètre par défaut pour le paramètre p>", où p> est l’ordinaire du TVP dans l’énoncé de requête.  
  
 Après avoir lié le paramètre table, l'application doit lier chaque colonne de paramètre table. Pour ce faire, l’application appelle d’abord SQLSetStmtAttr pour régler SQL_SOPT_SS_PARAM_FOCUS à l’ordinaire d’un paramètre de valeur de table. Ensuite, l’application lie les colonnes du paramètre de valeur de table par des appels aux routines suivantes : SQLBindParameter, SQLSetDescRec et SQLSetDescField. Réglage SQL_SOPT_SS_PARAM_FOCUS à 0 restaure l’effet habituel de SQLBindParameter, SQLSetDescRec et SQLSetDescField en fonction des paramètres réguliers de haut niveau.
 
 Note: pour les pilotes Linux et Mac ODBC avec unixODBC 2.3.1 à 2.3.4, lors de la mise en place du nom TVP par SQLSetDescField avec le champ descripteur SQL_CA_SS_TYPE_NAME, unixODBC ne se convertit pas automatiquement entre les chaînes ANSI et Unicode en fonction de la fonction exacte appelée (SQLSetDescFieldA / SQLDesSetcFieldW). Il est nécessaire soit d’utiliser toujours SQLBindParameter ou SQLSetDescFieldW avec une chaîne Unicode (UTF-16) pour définir le nom TVP.
  
 Aucune donnée n'est réellement envoyée ou reçue pour le paramètre table lui-même, mais des données sont envoyées et reçues pour chacune de ses colonnes constituantes. Étant donné que le paramètre évalué à la table est une pseudo colonne, les paramètres de SQLBindParameter sont utilisés pour désigner des attributs différents de ceux des autres types de données, comme suit :  
  
|Paramètre|Attribut connexe pour les types de paramètres non évalués par table, y compris les colonnes|Attribut associé pour les paramètres table|  
|---------------|--------------------------------------------------------------------------------|----------------------------------------------------|  
|*InputOutputType*|SQL_DESC_PARAMETER_TYPE dans IPD.<br /><br /> Pour les colonnes de paramètre table, ce doit être identique au paramètre du paramètre table lui-même.|SQL_DESC_PARAMETER_TYPE dans IPD.<br /><br /> Ce doit être SQL_PARAM_INPUT.|  
|*Valuetype*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans APD.|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans APD.<br /><br /> Ce doit être SQL_C_DEFAULT ou SQL_C_BINARY.|  
|*ParamètreType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans IPD.|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans IPD.<br /><br /> Ce doit être SQL_SS_TABLE.|  
|*ColumnSize*|SQL_DESC_LENGTH ou SQL_DESC_PRECISION dans IPD.<br /><br /> Cela dépend de la valeur de *ParameterType*.|SQL_DESC_ARRAY_SIZE<br /><br /> Peut également être défini à l'aide de SQL_ATTR_PARAM_SET_SIZE lorsque le focus de paramètre est défini sur le paramètre table.<br /><br /> Pour un paramètre table, il s'agit du nombre de lignes dans les mémoires tampons de colonnes de paramètres table.|  
|*DecimalDigits*|SQL_DESC_PRECISION or SQL_DESC_SCALE dans IPD.|Inutilisé. Doit être 0.<br /><br /> Si ce paramètre n’est pas 0, SQLBindParameter reviendra SQL_ERROR, et un dossier diagnostique sera généré avec SQLSTATE HY104 et le message "Précision ou échelle invalide".|  
|*ParameterValuePtr*|SQL_DESC_DATA_PTR dans APD.|SQL_CA_SS_TYPE_NAME.<br /><br /> Ceci est facultatif pour les appels de procédure stockée et NULL peut être spécifié si ce n'est pas requis. Doit être spécifié pour les instructions SQL qui ne sont pas des appels de procédure.<br /><br /> Ce paramètre sert également de valeur unique que l'application peut utiliser pour identifier ce paramètre table lorsque la liaison de ligne variable est utilisée. Pour plus d'informations, consultez la section « Liaison de ligne de paramètre table variable » plus loin dans cette rubrique.<br /><br /> Lorsqu’un nom de type paramètre de valeur de table est spécifié lors d’un appel à SQLBindParameter, il doit être spécifié comme valeur Unicode, même dans les applications qui sont construites sous forme d’applications ANSI. La valeur utilisée pour le paramètre *StrLen_or_IndPtr* doit être soit SQL_NTS ou la longueur de la chaîne du nom multiplié par sizeof (WCHAR).|  
|*BufferLength*|SQL_DESC_OCTET_LENGTH dans APD.|Longueur du nom de type de paramètre table en octets.<br /><br /> Cela peut être SQL_NTS si le nom de type se termine par une valeur Null ou 0 si le nom de type de paramètre table n'est pas requis.|  
|*StrLen_or_IndPtr*|SQL_DESC_OCTET_LENGTH_PTR dans APD.|SQL_DESC_OCTET_LENGTH_PTR dans APD.<br /><br /> Pour les paramètres table, il s'agit d'un nombre de lignes plutôt qu'une longueur de données.|  
||||

 Deux modes de transfert de données sont pris en charge pour les paramètres table : la liaison de ligne fixe et la liaison de ligne variable.  
  
## <a name="fixed-table-valued-parameter-row-binding"></a>Liaison de ligne de paramètre table fixe  
 Pour la liaison de ligne fixe, une application alloue des mémoires tampon (ou tableaux de mémoires tampon) suffisamment grandes pour toutes les valeurs de colonne d'entrée possibles. L'application effectue les actions suivantes :  
  
1.  Lie tous les paramètres en utilisant les appels SQLBindParameter, SQLSetDescRec ou SQLSetDescField.  
  
    1.  Elle définit SQL_DESC_ARRAY_SIZE au nombre maximal de lignes qui peuvent être transférées pour chaque paramètre table. Cela peut être fait dans l’appel SQLBindParameter.  
  
2.  Appelle SQLSetStmtAttr pour régler SQL_SOPT_SS_PARAM_FOCUS à l’ordinaire de chaque paramètre de table.  
  
    1.  Pour chaque paramètre de valeur de table, lie les colonnes de paramètres de valeur de table en utilisant des appels SQLBindParameter, SQLSetDescRec ou SQLSetDescField.  
  
    2.  Pour chaque colonne de paramètres évaluée en table qui doit avoir des valeurs par défaut, appelle SQLSetDescField pour définir SQL_CA_SS_COL_HAS_DEFAULT_VALUE à 1.  
  
3.  Appelle SQLSetStmtAttr pour régler SQL_SOPT_SS_PARAM_FOCUS 0. Cela doit être fait avant SQLExecute ou SQLExecDirect est appelé. Autrement, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE=HY024 et le message « Valeur d'attribut non valide, SQL_SOPT_SS_PARAM_FOCUS (doit être égale à zéro au moment de l'exécution) ».  
  
4.  Définit *StrLen_or_IndPtr* ou SQL_DESC_OCTET_LENGTH_PTR à SQL_DEFAULT_PARAM pour un paramètre de valeur de table sans lignes, ou le nombre de lignes à transférer sur le prochain appel de SQLExecute ou SQLExecDirect si le paramètre de table de valeur a des lignes. *StrLen_or_IndPtr* ou SQL_DESC_OCTET_LENGTH_PTR ne peuvent pas être SQL_NULL_DATA pour un paramètre évalué à la table, car les paramètres évalués à la table ne sont pas in nullables (bien que les colonnes constituantes de paramètres évaluées en table puissent être annulées). Si cela est réglé à une valeur invalide, SQLExecute ou SQLExecDirect retourne SQL_ERROR, et un dossier de diagnostic est généré avec \<SQLSTATE-HY090 et le message "Chaîne invalide ou longueur tampon pour le paramètre p>", où p est le numéro de paramètre.  
  
5.  Appels SQLExecute ou SQLExecDirect.  
  
 Les valeurs de colonne de paramètres évaluées en table d’entrée peuvent être transmises en morceaux si *StrLen_or_IndPtr* est réglée sur SQL_LEN_DATA_AT_EXEC(*longueur)* ou SQL_DATA_AT_EXEC pour la colonne. Cela s'apparente au passage de valeurs en fragments lorsque des tableaux de paramètres sont utilisés. Comme pour tous les paramètres de données d’exécution, SQLParamData n’indique pas la ligne du tableau pour laquelle le conducteur demande des données; l’application doit s’en occuper. L'application ne peut pas faire d'hypothèses concernant l'ordre dans lequel le pilote demandera des valeurs.  
  
## <a name="variable-table-valued-parameter-row-binding"></a>Liaison de ligne de paramètre table variable  
 Pour la liaison de ligne variable, les lignes sont transférées par lots au moment de l'exécution et l'application passe des lignes au pilote sur demande. Cela s'apparente à la fonctionnalité « data-at-execution » pour les valeurs de paramètre individuelles. Pour la liaison de ligne variable, l'application effectue les opérations suivantes :  
  
1.  Elle lie les paramètres et les colonnes de paramètre table comme décrit aux étapes 1 à 3 de la section précédente, « Liaison de ligne de paramètre table fixe ».  
  
2.  Définit *StrLen_or_IndPtr* ou SQL_DESC_OCTET_LENGTH_PTR pour tous les paramètres de valeur de table qui doivent être transmis au moment de l’exécution pour SQL_DATA_AT_EXEC. Si ni l'un ni l'autre n'est défini, le paramètre est traité comme décrit dans la section précédente.  
  
3.  Appels SQLExecute ou SQLExecDirect. Cela retourne SQL_NEED_DATA s'il y a des paramètres SQL_PARAM_INPUT ou SQL_PARAM_INPUT_OUTPUT à gérer comme paramètres « data-at-execution ». Dans ce cas, l'application effectue les opérations suivantes :  
  
    -   Appelle SQLParamData. Cela renvoie la valeur *ParameterValuePtr* pour un paramètre de données à l’exécution et un code de retour de SQL_NEED_DATA. Lorsque toutes les données de paramètres ont été transmises au conducteur, SQLParamData retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO ou SQL_ERROR. Pour les paramètres de données à l’exécution, *ParameterValuePtr*, qui est le même que le champ descripteur SQL_DESC_DATA_PTR, peut être considéré comme un jeton pour identifier de façon unique un paramètre pour lequel une valeur est nécessaire. Ce « jeton » est passé de l'application au pilote au moment de la liaison, puis repassé à l'application au moment de l'exécution.  
  
4.  Pour envoyer des données de la ligne de paramètres de valeur de table pour les paramètres de valeur de table nulles, si le paramètre de valeur de table n’a pas de lignes, une application appelle SQLPutData avec *StrLen_or_Ind* réglé pour SQL_DEFAULT_PARAM.  
  
     Pour les paramètres table non nuls, une application :  
  
    -   Définit *Str_Len_or_Ind* pour toutes les colonnes de paramètres évaluées en table à des valeurs appropriées, et remplit les tampons de données pour les colonnes de paramètres de valeur de table qui ne doivent pas être des paramètres de données à l’exécution. Vous pouvez utiliser la fonctionnalité « data-at-execution » pour les colonnes de paramètres table d'une manière semblable à celle employée lorsque des paramètres ordinaires sont passés au pilote par fragments.  
  
    -   Appelle SQLPutData avec *Str_Len_or_Ind* réglés sur le nombre de lignes à envoyer au serveur. Toute valeur en dehors de la plage 0 à SQL_DESC_ARRAY_SIZE ou SQL_DEFAULT_PARAM est une erreur et retourne SQLSTATE HY090 avec le message « Longueur de chaîne ou de mémoire tampon non valide ». 0 indique que toutes les lignes ont été envoyées et qu'il n'y a plus de données pour un paramètre table (comme noté dans le deuxième élément de puce dans cette liste). SQL_DEFAULT_PARAM peut être utilisé uniquement la première fois que le pilote demande des données pour un paramètre table (comme décrit dans le premier élément de puce dans cette liste).  
  
5.  Lorsque toutes les lignes ont été envoyées, appelle SQLPutData pour le paramètre de valeur de table avec une valeur *Str_Len_or_Ind* de 0, puis procède à l’étape 3a ci-dessus.  
  
6.  Appels SQLParamData nouveau. S’il y a des paramètres de données à l’exécution parmi les colonnes de paramètres de valeur de table, ceux-ci seront identifiés par la valeur *ValuePtrPtr* retournée par SQLParamData. Lorsque toutes les valeurs de colonne sont disponibles, SQLParamData retournera à nouveau la valeur *ParameterValuePtr* pour le paramètre de valeur de table, et l’application recommence.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres évalués par la table &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
