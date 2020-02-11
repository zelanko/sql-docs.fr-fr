---
title: Liaison et Transfert de données des paramètres table et des valeurs de colonne | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), binding and data transfer
ms.assetid: 0a2ea462-d613-42b6-870f-c7fa086a6b42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26bcf31c2d4e0d188e93587dd9bdec1a9ff382e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63199951"
---
# <a name="binding-and-data-transfer-of-table-valued-parameters-and-column-values"></a>Liaison et transfert de données de paramètres table et de valeurs de colonnes
  Les paramètres table, comme d'autres paramètres, doivent être liés avant d'être passés au serveur. L’application lie les paramètres table de la même façon qu’elle lie d’autres paramètres : en utilisant SQLBindParameter ou des appels équivalents à SQLSetDescField ou SQLSetDescRec. Le type de données serveur pour un paramètre table est SQL_SS_TABLE. Le type C peut être spécifié comme SQL_C_DEFAULT ou SQL_C_BINARY.  
  
 Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure, seuls les paramètres table d'entrée sont pris en charge. Par conséquent, toute tentative de définition de SQL_DESC_PARAMETER_TYPE à une valeur autre que SQL_PARAM_INPUT retourne SQL_ERROR avec SQLSTATE = HY105 et le message « type de paramètre non valide ».  
  
 Des valeurs par défaut peuvent être assignées à des colonnes de paramètres table entières à l'aide de l'attribut SQL_CA_SS_COL_HAS_DEFAULT_VALUE. Toutefois, il n’est pas possible d’assigner des valeurs par défaut à des valeurs de colonne de paramètre table individuelles à l’aide de SQL_DEFAULT_PARAM dans *StrLen_or_IndPtr* avec SQLBindParameter. Les paramètres table dans leur ensemble ne peuvent pas être définis sur une valeur par défaut à l’aide de SQL_DEFAULT_PARAM dans *StrLen_or_IndPtr* avec SQLBindParameter. Si ces règles ne sont pas suivies, SQLExecute ou SQLExecDirect retourne SQL_ERROR. Un enregistrement de diagnostic est généré avec SQLSTATE = 07S01 et le message « utilisation non valide du paramètre par défaut \<pour le paramètre p> \<», où p> est l’ordinal du TVP dans l’instruction de la requête.  
  
 Après avoir lié le paramètre table, l'application doit lier chaque colonne de paramètre table. Pour ce faire, l’application appelle d’abord SQLSetStmtAttr pour définir SQL_SOPT_SS_PARAM_FOCUS sur l’ordinal d’un paramètre table. Ensuite, l’application lie les colonnes du paramètre table en appelant les routines suivantes : SQLBindParameter, SQLSetDescRec et SQLSetDescField. L’affectation de la valeur 0 à SQL_SOPT_SS_PARAM_FOCUS restaure l’effet habituel de SQLBindParameter, SQLSetDescRec et SQLSetDescField en opérant sur des paramètres de niveau supérieur normaux.  
  
 Aucune donnée n'est réellement envoyée ou reçue pour le paramètre table lui-même, mais des données sont envoyées et reçues pour chacune de ses colonnes constituantes. Étant donné que le paramètre table est une pseudo-colonne, les paramètres de SQLBindParameter sont utilisés pour faire référence à des attributs différents de ceux des autres types de données, comme suit :  
  
|Paramètre|Attribut associé pour les types de paramètre non table, y compris les colonnes|Attribut associé pour les paramètres table|  
|---------------|--------------------------------------------------------------------------------|----------------------------------------------------|  
|*InputOutputType*|SQL_DESC_PARAMETER_TYPE dans IPD.<br /><br /> Pour les colonnes de paramètre table, ce doit être identique au paramètre du paramètre table lui-même.|SQL_DESC_PARAMETER_TYPE dans IPD.<br /><br /> Ce doit être SQL_PARAM_INPUT.|  
|*ValueType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans APD.|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans APD.<br /><br /> Ce doit être SQL_C_DEFAULT ou SQL_C_BINARY.|  
|*ParameterType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans IPD.|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE dans IPD.<br /><br /> Ce doit être SQL_SS_TABLE.|  
|*ColumnSize*|SQL_DESC_LENGTH ou SQL_DESC_PRECISION dans IPD.<br /><br /> Cela dépend de la valeur de *ParameterType*.|SQL_DESC_ARRAY_SIZE<br /><br /> Peut également être défini à l'aide de SQL_ATTR_PARAM_SET_SIZE lorsque le focus de paramètre est défini sur le paramètre table.<br /><br /> Pour un paramètre table, il s'agit du nombre de lignes dans les mémoires tampons de colonnes de paramètres table.|  
|*DecimalDigits*|SQL_DESC_PRECISION or SQL_DESC_SCALE dans IPD.|Non utilisé. Doit être 0.<br /><br /> Si ce paramètre n’est pas égal à 0, SQLBindParameter retourne SQL_ERROR et un enregistrement de diagnostic est généré avec SQLSTATE = HY104 et le message « précision ou échelle non valide ».|  
|*ParameterValuePtr*|SQL_DESC_DATA_PTR dans APD.|SQL_CA_SS_TYPE_NAME.<br /><br /> Ceci est facultatif pour les appels de procédure stockée et NULL peut être spécifié si ce n'est pas requis. Doit être spécifié pour les instructions SQL qui ne sont pas des appels de procédure.<br /><br /> Ce paramètre sert également de valeur unique que l'application peut utiliser pour identifier ce paramètre table lorsque la liaison de ligne variable est utilisée. Pour plus d'informations, consultez la section « Liaison de ligne de paramètre table variable » plus loin dans cette rubrique.<br /><br /> Lorsqu’un nom de type de paramètre table est spécifié sur un appel à SQLBindParameter, il doit être spécifié en tant que valeur Unicode, même dans les applications générées en tant qu’applications ANSI. La valeur utilisée pour le paramètre *StrLen_or_IndPtr* doit être SQL_NTS ou la longueur de chaîne du nom multipliée par sizeof (WCHAR).|  
|*BufferLength*|SQL_DESC_OCTET_LENGTH dans APD.|Longueur du nom de type de paramètre table en octets.<br /><br /> Cela peut être SQL_NTS si le nom de type se termine par une valeur Null ou 0 si le nom de type de paramètre table n'est pas requis.|  
|*StrLen_or_IndPtr*|SQL_DESC_OCTET_LENGTH_PTR dans APD.|SQL_DESC_OCTET_LENGTH_PTR dans APD.<br /><br /> Pour les paramètres table, il s'agit d'un nombre de lignes plutôt qu'une longueur de données.|  
  
 Deux modes de transfert de données sont pris en charge pour les paramètres table : la liaison de ligne fixe et la liaison de ligne variable.  
  
## <a name="fixed-table-valued-parameter-row-binding"></a>Liaison de ligne de paramètre table fixe  
 Pour la liaison de ligne fixe, une application alloue des mémoires tampon (ou tableaux de mémoires tampon) suffisamment grandes pour toutes les valeurs de colonne d'entrée possibles. L'application effectue les actions suivantes :  
  
1.  Lie tous les paramètres à l’aide des appels SQLBindParameter, SQLSetDescRec ou SQLSetDescField.  
  
    1.  Elle définit SQL_DESC_ARRAY_SIZE au nombre maximal de lignes qui peuvent être transférées pour chaque paramètre table. Cela peut être fait dans l’appel SQLBindParameter.  
  
2.  Appelle SQLSetStmtAttr pour définir SQL_SOPT_SS_PARAM_FOCUS à l’ordinal de chaque paramètre table.  
  
    1.  Pour chaque paramètre table, lie les colonnes de paramètre table à l’aide des appels SQLBindParameter, SQLSetDescRec ou SQLSetDescField.  
  
    2.  Pour chaque colonne de paramètre table qui doit avoir des valeurs par défaut, appelle SQLSetDescField pour affecter la valeur 1 à SQL_CA_SS_COL_HAS_DEFAULT_VALUE.  
  
3.  Appelle SQLSetStmtAttr pour affecter la valeur 0 à SQL_SOPT_SS_PARAM_FOCUS. Cela doit être fait avant l’appel de SQLExecute ou SQLExecDirect. Autrement, SQL_ERROR est retourné et un enregistrement de diagnostic est généré avec SQLSTATE=HY024 et le message « Valeur d'attribut non valide, SQL_SOPT_SS_PARAM_FOCUS (doit être égale à zéro au moment de l'exécution) ».  
  
4.  Définit *StrLen_or_IndPtr* ou SQL_DESC_OCTET_LENGTH_PTR à SQL_DEFAULT_PARAM pour un paramètre table sans ligne, ou le nombre de lignes à transférer lors de l’appel suivant de SQLExecute ou SQLExecDirect si le paramètre table a des lignes. *StrLen_or_IndPtr* ou SQL_DESC_OCTET_LENGTH_PTR ne peuvent pas être définis sur SQL_NULL_DATA pour un paramètre table, car les paramètres table ne sont pas nullables (bien que les colonnes constituantes des paramètres table puissent avoir la valeur null). Si cette valeur est définie sur une valeur non valide, SQLExecute ou SQLExecDirect retourne SQL_ERROR, et un enregistrement de diagnostic est généré avec SQLSTATE = HY090 et le message « longueur de chaîne ou \<de mémoire tampon non valide pour le paramètre p> », où p est le numéro du paramètre.  
  
5.  Appelle SQLExecute ou SQLExecDirect.  
  
 Les valeurs de colonne de paramètre table d’entrée peuvent être passées en parties si *StrLen_or_IndPtr* est défini sur SQL_LEN_DATA_AT_EXEC (*longueur*) ou SQL_DATA_AT_EXEC pour la colonne. Cela s'apparente au passage de valeurs en fragments lorsque des tableaux de paramètres sont utilisés. Comme avec tous les paramètres de données en cours d’exécution, SQLParamData n’indique pas la ligne du tableau pour lequel le pilote demande des données ; l’application doit s’en occuper. L'application ne peut pas faire d'hypothèses concernant l'ordre dans lequel le pilote demandera des valeurs.  
  
## <a name="variable-table-valued-parameter-row-binding"></a>Liaison de ligne de paramètre table variable  
 Pour la liaison de ligne variable, les lignes sont transférées par lots au moment de l'exécution et l'application passe des lignes au pilote sur demande. Cela s'apparente à la fonctionnalité « data-at-execution » pour les valeurs de paramètre individuelles. Pour la liaison de ligne variable, l'application effectue les opérations suivantes :  
  
1.  Elle lie les paramètres et les colonnes de paramètre table comme décrit aux étapes 1 à 3 de la section précédente, « Liaison de ligne de paramètre table fixe ».  
  
2.  Définit *StrLen_or_IndPtr* ou SQL_DESC_OCTET_LENGTH_PTR pour tous les paramètres table qui doivent être passés au moment de l’exécution pour SQL_DATA_AT_EXEC. Si ni l'un ni l'autre n'est défini, le paramètre est traité comme décrit dans la section précédente.  
  
3.  Appelle SQLExecute ou SQLExecDirect. Cela retourne SQL_NEED_DATA s'il y a des paramètres SQL_PARAM_INPUT ou SQL_PARAM_INPUT_OUTPUT à gérer comme paramètres « data-at-execution ». Dans ce cas, l'application effectue les opérations suivantes :  
  
    -   Appelle SQLParamData. Cela retourne la valeur *ParameterValuePtr* pour un paramètre de données en cours d’exécution et un code de retour de SQL_NEED_DATA. Lorsque toutes les données de paramètre ont été transmises au pilote, SQLParamData retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO ou SQL_ERROR. Pour les paramètres de données en cours d’exécution, *ParameterValuePtr*, qui est le même que le champ de descripteur SQL_DESC_DATA_PTR, peut être considéré comme un jeton pour identifier de manière unique un paramètre pour lequel une valeur est requise. Ce « jeton » est passé de l'application au pilote au moment de la liaison, puis repassé à l'application au moment de l'exécution.  
  
4.  Pour envoyer des données de ligne de paramètre table pour les paramètres table null, si le paramètre table n’a pas de ligne, une application appelle SQLPutData avec *StrLen_Or_Ind* défini sur SQL_DEFAULT_PARAM.  
  
     Pour les paramètres table non nuls, une application :  
  
    -   Définit *Str_Len_or_Ind* pour toutes les colonnes de paramètre table sur les valeurs appropriées, et remplit les tampons de données pour les colonnes de paramètre table qui ne sont pas des paramètres de données en cours d’exécution. Vous pouvez utiliser la fonctionnalité « data-at-execution » pour les colonnes de paramètres table d'une manière semblable à celle employée lorsque des paramètres ordinaires sont passés au pilote par fragments.  
  
    -   Appelle SQLPutData avec *Str_Len_or_Ind* défini sur le nombre de lignes à envoyer au serveur. Toute valeur en dehors de la plage 0 à SQL_DESC_ARRAY_SIZE ou SQL_DEFAULT_PARAM est une erreur et retourne SQLSTATE HY090 avec le message « Longueur de chaîne ou de mémoire tampon non valide ». 0 indique que toutes les lignes ont été envoyées et qu'il n'y a plus de données pour un paramètre table (comme noté dans le deuxième élément de puce dans cette liste). SQL_DEFAULT_PARAM peut être utilisé uniquement la première fois que le pilote demande des données pour un paramètre table (comme décrit dans le premier élément de puce dans cette liste).  
  
5.  Lorsque toutes les lignes ont été envoyées, appelle SQLPutData pour le paramètre table avec une valeur *Str_Len_or_Ind* égale à 0, puis passe à l’étape 3A ci-dessus.  
  
6.  Rappelle SQLParamData. S’il existe des paramètres de données en cours d’exécution parmi les colonnes de paramètre table, ceux-ci sont identifiés par la valeur *ValuePtrPtr* retournée par SQLParamData. Lorsque toutes les valeurs de colonne sont disponibles, SQLParamData retourne à nouveau la valeur *ParameterValuePtr* pour le paramètre table, et l’application recommence.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
