---
title: Fonction SQLBindParameter (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBindParameter
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBindParameter
helpviewer_keywords:
- SQLBindParameter function [ODBC]
ms.assetid: 38349d4b-be03-46f9-9d6a-e50dd144e225
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02f50862bcfb0295c7f098afc6856c91e0249f66
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301359"
---
# <a name="sqlbindparameter-function"></a>Fonction SQLBindParameter

**Conformité**  
 Version introduite : ODBC 2.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLBindParameter** lie un tampon à un marqueur de paramètres dans un communiqué SQLL. **SQLBindParameter** prend en charge la liaison vers un type de données Unicode C, même si le conducteur sous-jacent ne prend pas en charge les données Unicode.  
  
> [!NOTE]  
>  Cette fonction remplace la fonction ODBC 1.0 **SQLSetParam**. Pour plus d’informations, voir "Commentaires".  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN SQLBindParameter(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT     InputOutputType,  
      SQLSMALLINT     ValueType,  
      SQLSMALLINT     ParameterType,  
      SQLULEN         ColumnSize,  
      SQLSMALLINT     DecimalDigits,  
      SQLPOINTER      ParameterValuePtr,  
      SQLLEN          BufferLength,  
      SQLLEN *        StrLen_or_IndPtr);  
```
  
## <a name="arguments"></a>Arguments

 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *ParameterNumber (en)*  
 [Entrée] Nombre de paramètres, commandé séquentiellement dans l’ordre de paramètres croissant, à partir de 1.  
  
 *InputOutputType*  
 [Entrée] Le type de paramètre. Pour plus d’informations, voir «*InputOutputType* Argument » dans « Commentaires ».  
  
 *Valuetype*  
 [Entrée] Le type de données C du paramètre. Pour plus d’informations, voir "*ValueType* Argument " dans "Commentaires".  
  
 *ParamètreType*  
 [Entrée] Le type de données SQL du paramètre. Pour plus d’informations, voir "*ParameterType* Argument " dans "Commentaires".  
  
 *ColumnSize*  
 [Entrée] La taille de la colonne ou l’expression du marqueur de paramètres correspondant. Pour plus d’informations, voir " Argument de la taille des*colonnes* » dans " Commentaires ".  
  
 Si votre application s’exécute sur un système d’exploitation Windows 64 bits, consultez [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md).  
  
 *DecimalDigits*  
 [Entrée] Les chiffres décimaux de la colonne ou l’expression du marqueur de paramètres correspondant. Pour plus d’informations sur la taille de la colonne, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert, et la taille d’affichage.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
 *ParameterValuePtr*  
 [Entrée différée] Un pointeur vers un tampon pour les données du paramètre. Pour plus d’informations, voir "*ParameterValuePtr* Argument " dans "Commentaires".  
  
 *BufferLength*  
 [Entrée/sortie] Longueur du tampon *ParameterValuePtr* dans les octets. Pour plus d’informations, voir "*BufferLength* Argument " dans "Commentaires".  
  
 Consultez [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécute sur un système d’exploitation 64 bits.  
  
 *StrLen_or_IndPtr*  
 [Entrée différée] Un pointeur vers un tampon pour la longueur du paramètre. Pour plus d’informations, voir "*StrLen_or_IndPtr* Argument " dans "Commentaires".  
  
## <a name="returns"></a>Retours

 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics

 Lorsque **SQLBindParameter** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLBindParameter** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  

|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|Le type de données identifié par l’argument *ValueType* ne peut pas être converti au type de données identifié par l’argument *de ParameterType.* Notez que cette erreur peut être retournée par **SQLExecDirect**, **SQLExecute**, ou **SQLPutData** au moment de l’exécution, au lieu de par **SQLBindParameter**.|  
|07009|Indice descripteur invalide|(DM) La valeur spécifiée pour l’argument *Paramètre était* inférieure à 1.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le tampon*MessageText* décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY003 (HY003)|Type tampon d’application invalide|La valeur spécifiée par l’argument *ValueType* n’était pas un type de données C valide ou SQL_C_DEFAULT.|  
|HY004|Type de données SQL invalide|La valeur spécifiée pour l’argument *ParameterType* n’était ni un identifiant de type de données ODBC SQL valide, ni un identifiant de type de données SQL spécifique au conducteur, pris en charge par le conducteur.|  
|HY009|Valeur d’argument invalide|(DM) L’argument *ParameterValuePtr* était un pointeur nul, *l’argument StrLen_or_IndPtr* était un pointeur nul, et l’argument *InputOutputType* n’était pas SQL_PARAM_OUTPUT.<br /><br /> (DM) SQL_PARAM_OUTPUT, où l’argument *ParameterValuePtr* était un pointeur nul, le type C était char ou binaire, et le BufferLength (*cbValueMax*) était supérieur à 0.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque **SQLBindParameter** a été appelé.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY021|Informations descripteur incohérentes|Les renseignements descripteur vérifiés lors d’une vérification de cohérence n’étaient pas cohérents. (Voir la section « Vérifications de cohérence » dans **SQLSetDescField**.)<br /><br /> La valeur spécifiée pour l’argument *DecimalDigits* était en dehors de la gamme de valeurs étayées par la source de données pour une colonne du type de données SQL spécifiée par l’argument *de ParameterType.*|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur de *BufferLength* était inférieure à 0. (Voir la description du champ SQL_DESC_DATA_PTR dans **SQLSetDescField**.)|  
|Hy104|Précision invalide ou valeur à l’échelle|La valeur spécifiée pour l’argument *ColumnSize* ou *DecimalDigits* était en dehors de la gamme de valeurs supportées par la source de données pour une colonne du type de données SQL spécifiée par l’argument *de ParameterType.*|  
|Hy105|Type de paramètre invalide|(DM) La valeur spécifiée pour l’argument *InputOutputType* était invalide. (Voir "Commentaires.")|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ou la source de données ne prend pas en charge la conversion spécifiée par la combinaison de la valeur spécifiée pour l’argument *ValueType* et la valeur spécifique au conducteur spécifiée pour l’argument *ParameterType*.<br /><br /> La valeur spécifiée pour l’argument *Paramètre* était un identifiant de type de données ODBC SQL valide pour la version d’ODBC prise en charge par le conducteur, mais n’était pas pris en charge par le conducteur ou la source de données.<br /><br /> Le conducteur ne prend en charge que L’ODBC 2. *x* et l’argument *ValueType* était l’un des éléments suivants :<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> et tous les types de données d’intervalle C répertoriés dans [les types de données C](../../../odbc/reference/appendixes/c-data-types.md) à l’annexe D : Types de données.<br /><br /> Le conducteur ne prend en charge les versions ODBC avant 3.50, et l’argument *ValueType* a été SQL_C_GUID.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires

 Une application appelle **SQLBindParameter** pour lier chaque marqueur de paramètres dans une déclaration SQLL. Les liaisons restent en vigueur jusqu’à ce que l’application appelle **SQLBindParameter** à nouveau, appelle **SQLFreeStmt** avec l’option SQL_RESET_PARAMS, ou appelle **SQLSetDescField** pour définir le champ d’en-tête SQL_DESC_COUNT de l’APD à 0.  
  
 Pour plus d’informations sur les paramètres, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md). Pour plus d’informations sur les types de données de paramètres et les marqueurs de paramètres, voir [types de données paramétriques](../../../odbc/reference/appendixes/parameter-data-types.md) et [marqueurs de paramètres](../../../odbc/reference/appendixes/parameter-markers.md) à l’annexe C : SQL Grammar.  
  
## <a name="parameternumber-argument"></a>ParameterNumber Argument  
 Si *ParameterNumber* dans l’appel à **SQLBindParameter** est supérieur à la valeur de SQL_DESC_COUNT, **SQLSetDescField** est appelé à augmenter la valeur de SQL_DESC_COUNT à *ParameterNumber*.  
  
## <a name="inputoutputtype-argument"></a>InputOutputType Argument  
 *L’argument d’InputOutputType* spécifie le type de paramètre. Cet argument définit le champ SQL_DESC_PARAMETER_TYPE de l’IPD. Tous les paramètres dans les instructions SQL qui n’appellent pas les procédures, telles que les relevés **INSERT,** sont *des paramètres d’entrée*. Les paramètres dans les appels de procédure peuvent être des paramètres d’entrée, d’entrée/sortie ou de sortie. (Une application appelle **SQLProcedureColumns** pour déterminer le type de paramètre dans un appel de procédure; les paramètres dont le type ne peut être déterminé sont supposés être des paramètres d’entrée.)  
  
 L’argument *InputOutputType* est l’une des valeurs suivantes :  
  
-   SQL_PARAM_INPUT. Le paramètre indique un paramètre dans une déclaration SQL qui n’appelle pas une procédure, comme une déclaration **INSERT,** ou il marque un paramètre d’entrée dans une procédure. Par exemple, les paramètres **d’INSERT INTO Employee VALUES (?, ?, ?)** sont des paramètres d’entrée, tandis que les paramètres de « Call **AddEmp (?, ?, ?)** peuvent être, mais ne sont pas nécessairement, des paramètres d’entrée.  
  
     Lorsque la déclaration est exécutée, le conducteur envoie des données pour le paramètre à la source de données; le \*tampon *ParamètreValuePtr* doit contenir une valeur d’entrée valide, ou le tampon*de StrLen_or_IndPtr* doit contenir SQL_NULL_DATA, SQL_DATA_AT_EXEC, ou le résultat de la macro SQL_LEN_DATA_AT_EXEC.  
  
     Si une demande ne peut pas déterminer le type de paramètre dans un appel de procédure, elle définit *InputOutputType* à SQL_PARAM_INPUT; si la source de données retourne une valeur pour le paramètre, le conducteur le rejette.  
  
-   SQL_PARAM_INPUT_OUTPUT. Le paramètre indique un paramètre d’entrée/sortie dans une procédure. Par exemple, le paramètre **« appelez GetEmpDept (?)** est un paramètre d’entrée/sortie qui accepte le nom d’un employé et qui renvoie le nom du service de l’employé.  
  
     Lorsque la déclaration est exécutée, le conducteur envoie des données pour le paramètre à la source de données; le \*tampon *ParameterValuePtr* doit contenir une \*valeur d’entrée valide, ou le tampon *StrLen_or_IndPtr* doit contenir SQL_NULL_DATA, SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC. Une fois la déclaration exécutée, le conducteur renvoie les données pour le paramètre à l’application; si la source de données ne retourne pas une valeur pour un paramètre d’entrée/sortie, le pilote définit le tampon*StrLen_or_IndPtr* pour SQL_NULL_DATA.  
  
    > [!NOTE]  
    >  Lorsqu’une demande ODBC 1.0 appelle **SQLSetParam** dans un conducteur ODBC 2.0, le gestionnaire de conducteur convertit cela en un appel à **SQLBindParameter** dans lequel l’argument *d’InputOutputType* est prêt à SQL_PARAM_INPUT_OUTPUT.  
  
-   SQL_PARAM_OUTPUT. Le paramètre marque la valeur de rendement d’une procédure ou d’un paramètre de sortie dans une procédure; dans les deux cas, ceux-ci sont connus sous le nom *de paramètres de sortie*. Par exemple, le paramètre dans **getNextEmpID est** un paramètre de sortie qui renvoie la prochaine pièce d’identité de l’employé.  
  
     Une fois la déclaration exécutée, le conducteur renvoie les données pour le paramètre à l’application, à moins que les arguments *Paramétacte Et* *StrLen_or_IndPtr* soient tous deux des pointeurs nuls, auquel cas le conducteur écarte la valeur de sortie. Si la source de données ne retourne pas une valeur pour un paramètre de sortie, le pilote définit le tampon*de StrLen_or_IndPtr* pour SQL_NULL_DATA.  
  
-   SQL_PARAM_INPUT_OUTPUT_STREAM. Indique qu’un paramètre d’entrée/sortie doit être diffusé. **SQLGetData** peut lire les valeurs de paramètres en parties. *BufferLength* est ignoré parce que la longueur du tampon sera déterminée à l’appel de **SQLGetData**. La valeur du tampon *StrLen_or_IndPtr* doit contenir SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_DATA_AT_EXEC, ou le résultat de la macro SQL_LEN_DATA_AT_EXEC. Un paramètre doit être lié comme paramètre de données à l’exécution (DAE) à l’entrée s’il est diffusé à la sortie. *ParaValuePtr* peut être n’importe quelle valeur de pointeur non nulle qui sera retournée par **SQLParamData** comme le jeton défini par l’utilisateur dont la valeur a été adoptée avec *ParameterValuePtr* pour l’entrée et la sortie. Pour plus d’informations, voir [Paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
-   SQL_PARAM_OUTPUT_STREAM. Identique à SQL_PARAM_INPUT_OUTPUT_STREAM, pour un paramètre de sortie. **StrLen_or_IndPtr* est ignoré à l’entrée.  
  
 Le tableau suivant répertorie différentes combinaisons *d’InputOutputType* et*de StrLen_or_IndPtr*:  
  
|*InputOutputType*|**StrLen_or_IndPtr*|Résultat|Remarque sur ParameterValuePtr|  
|-----------------------|----------------------------|-------------|---------------------------------|  
|SQL_PARAM_INPUT|SQL_LEN_DATA_AT_EXEC (*len*) ou SQL_DATA_AT_EXEC|Entrée dans les pièces|*ParaValuePtr* peut être n’importe quelle valeur pointeur qui sera retournée par **SQLParamData** comme le jeton défini par l’utilisateur dont la valeur a été adoptée avec *ParameterValuePtr*.|  
|SQL_PARAM_INPUT|Pas SQL_LEN_DATA_AT_EXEC (*len*) ou SQL_DATA_AT_EXEC|Mémoire tampon liée à l’entrée|*ParameterValuePtr* est l’adresse du tampon d’entrée.|  
|SQL_PARAM_OUTPUT|Ignoré à l’entrée.|Tampon lié à la sortie|*ParameterValuePtr* est l’adresse du tampon de sortie.|  
|SQL_PARAM_OUTPUT_STREAM|Ignoré à l’entrée.|Sortie en streaming|*ParaValuePtr* peut être n’importe quelle valeur pointeur, qui sera retournée par **SQLParamData** comme le jeton défini par l’utilisateur dont la valeur a été adoptée avec *ParameterValuePtr*.|  
|SQL_PARAM_INPUT_OUTPUT|SQL_LEN_DATA_AT_EXEC (*len*) ou SQL_DATA_AT_EXEC|Entrée dans les pièces et tampon lié à la sortie|*ParaValuePtr* est l’adresse du tampon de sortie, qui sera également retourné par **SQLParamData** comme le jeton défini par l’utilisateur dont la valeur a été adoptée avec *ParameterValuePtr*.|  
|SQL_PARAM_INPUT_OUTPUT|Pas SQL_LEN_DATA_AT_EXEC (*len*) ou SQL_DATA_AT_EXEC|Tampon lié à l’entrée et tampon lié à la sortie|*ParameterValuePtr* est l’adresse du tampon d’entrée/sortie partagé.|
|SQL_PARAM_INPUT_OUTPUT_STREAM|SQL_LEN_DATA_AT_EXEC (*len*) ou SQL_DATA_AT_EXEC|Entrée dans les pièces et la sortie en continu|*ParaValuePtr* peut être n’importe quelle valeur de pointeur non nulle, qui sera retournée par **SQLParamData** comme le jeton défini par l’utilisateur dont la valeur a été adoptée avec *ParameterValuePtr* pour l’entrée et la sortie.|  
  
> [!NOTE]  
>  Le conducteur doit décider quels types SQL sont autorisés lorsqu’une application lie un paramètre de sortie ou d’entrée-sortie tel qu’il est diffusé. Le gestionnaire du conducteur ne générera pas d’erreur pour un type SQL invalide.  
  
## <a name="valuetype-argument"></a>ValueType Argument

 *L’argument ValueType* spécifie le type de données C du paramètre. Cet argument définit les champs SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE et SQL_DESC_DATETIME_INTERVAL_CODE de la DPA. Cela doit être l’une des valeurs de la section [C Data Types](../../../odbc/reference/appendixes/c-data-types.md) de l’Annexe D : Data Types.  
  
 Si l’argument *valueType* est l’un des types de données d’intervalle, le champ SQL_DESC_TYPE de *l’enregistrement De l’APD* est réglé pour SQL_INTERVAL, le champ SQL_DESC_CONCISE_TYPE de l’APD est réglé sur le type de données d’intervalle concis, et le champ SQL_DESC_DATETIME_INTERVAL_CODE de *l’enregistrement ParameterNumber* est réglé sur un sous-code pour le type de données d’intervalle spécifique. (Voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).) L’intervalle par défaut menant la précision (2) et les secondes d’intervalle par défaut (6), tels qu’établis dans les champs SQL_DESC_DATETIME_INTERVAL_PRECISION et SQL_DESC_PRECISION de l’APD, respectivement, sont utilisés pour les données. Si l’une ou l’autre précision par défaut n’est pas appropriée, l’application doit définir explicitement le champ descripteur par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Si l’argument *de ValueType* est l’un des types de données de date, le champ SQL_DESC_TYPE de *l’enregistrement De l’APD* est réglé pour SQL_DATETIME, le champ SQL_DESC_CONCISE_TYPE de *l’enregistrement De ParameterNumber* de la DPA est réglé sur le type de données de date concise C, et le champ SQL_DESC_DATETIME_INTERVAL_CODE de *l’enregistrement De ParameterNumber* est fixé à un sous-code pour le type spécifique de données de date. (Voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Si l’argument *ValueType* est un type de données SQL_C_NUMERIC, la précision par défaut (qui est définie par le conducteur) et l’échelle par défaut (0), telle qu’elle est définie dans les champs SQL_DESC_PRECISION et SQL_DESC_SCALE de la DPA, sont utilisées pour les données. Si la précision ou l’échelle par défaut n’est pas appropriée, l’application doit définir explicitement le champ descripteur par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
 SQL_C_DEFAULT précise que la valeur du paramètre doit être transférée à partir du type de données C par défaut pour le type de données SQL spécifié avec *ParameterType*.  
  
 Vous pouvez également spécifier un type de données C étendu. Pour plus d’informations, voir [C Data Types in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
 Pour plus d’informations, consultez les types de [données par défaut C](../../../odbc/reference/appendixes/default-c-data-types.md), la conversion des données de C à [SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md), et la conversion des données de [SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) dans l’annexe D: Data Types.  
  
## <a name="parametertype-argument"></a>ParameterType Argument

 Cela doit être l’une des valeurs énumérées dans la section types de [données SQL](../../../odbc/reference/appendixes/sql-data-types.md) de l’Annexe D : Types de données, ou il doit s’agir d’une valeur spécifique au conducteur. Cet argument définit les champs SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE et SQL_DESC_DATETIME_INTERVAL_CODE de l’IPD.  
  
 Si l’argument *de ParameterType* est l’un des identificateurs de date, le champ SQL_DESC_TYPE de l’IPD est réglé pour SQL_DATETIME, le champ SQL_DESC_CONCISE_TYPE de l’IPD est réglé au type de données SQL de date concise, et le champ SQL_DESC_DATETIME_INTERVAL_CODE est réglé à la valeur de sous-code de date appropriée.  
  
 Si *Paramètre* est l’un des identificateurs d’intervalle, le champ SQL_DESC_TYPE de l’IPD est réglé pour SQL_INTERVAL, le champ SQL_DESC_CONCISE_TYPE de l’IPD est réglé sur le type concis de données d’intervalle SQL, et le champ SQL_DESC_DATETIME_INTERVAL_CODE de l’IPD est réglé sur le sous-code d’intervalle approprié. Le champ SQL_DESC_DATETIME_INTERVAL_PRECISION de l’IPD est réglé à la précision de tête d’intervalle, et le champ SQL_DESC_PRECISION est réglé à la précision des secondes d’intervalle, le cas échéant. Si la valeur par défaut de SQL_DESC_DATETIME_INTERVAL_PRECISION ou SQL_DESC_PRECISION n’est pas appropriée, l’application doit la définir explicitement en appelant **SQLSetDescField**. Pour plus d’informations sur l’un de ces domaines, voir [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Si l’argument *ValueType* est un type de données SQL_NUMERIC, la précision par défaut (qui est définie par le conducteur) et l’échelle par défaut (0), telle qu’elle est définie dans les domaines SQL_DESC_PRECISION et SQL_DESC_SCALE de l’IPD, sont utilisées pour les données. Si la précision ou l’échelle par défaut n’est pas appropriée, l’application doit définir explicitement le champ descripteur par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Pour plus d’informations sur la façon dont les données sont converties, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) et convertir les données de [SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) dans l’annexe D : Data Types.  
  
## <a name="columnsize-argument"></a>ColumnSize Argument

 *L’argument De ColumnSize* spécifie la taille de la colonne ou de l’expression qui correspond au marqueur de paramètres, à la longueur de ces données, ou les deux. Cet argument définit différents domaines de l’IPD, selon le type de données SQL (l’argument *de ParameterType).* Les règles suivantes s’appliquent à cette cartographie :  
  
-   Si *ParameterType* est SQL_CHAR, SQL_VARCHAR, SQL_LONGVARCHAR, SQL_BINARY, SQL_VARBINARY, SQL_LONGVARBINARY, ou l’un des types concis de date SQL ou de données d’intervalle, le champ SQL_DESC_LENGTH de l’IPD est réglé à la valeur de *ColumnSize*. (Pour plus d’informations, voir la [taille de la colonne, les chiffres décimaux, la longueur d’octet de transfert et la section taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe D : types de données.)  
  
-   Si *ParameterType* est SQL_DECIMAL, SQL_NUMERIC, SQL_FLOAT, SQL_REAL ou SQL_DOUBLE, le champ SQL_DESC_PRECISION de l’IPD est réglé à la valeur de *ColumnSize*.  
  
-   Pour d’autres types de données, l’argument *De ColumnSize* est ignoré.  
  
 Pour plus d’informations, voir « Valeurs paramètres de passage » et SQL_DATA_AT_EXEC dans «*StrLen_or_IndPtr* Argument ».  
  
## <a name="decimaldigits-argument"></a>Argument DécmalDigits

 Si *ParameterType* est SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, SQL_INTERVAL_SECOND, SQL_INTERVAL_DAY_TO_SECOND, SQL_INTERVAL_HOUR_TO_SECOND ou SQL_INTERVAL_MINUTE_TO_SECOND, le champ SQL_DESC_PRECISION de l’IPD est fixé à *DecimalDigits*. Si *ParameterType* est SQL_NUMERIC ou SQL_DECIMAL, le champ SQL_DESC_SCALE de l’IPD est réglé sur *DecimalDigits*. Pour tous les autres types de données, l’argument *DecimalDigits* est ignoré.  
  
## <a name="parametervalueptr-argument"></a>Argument ParamètreValuePtr

 *L’argument de ParameterValuePtr* indique un tampon qui, **lorsqu’on appelle SQLExecute** ou **SQLExecDirect,** contient les données réelles du paramètre. Les données doivent être dans la forme spécifiée par l’argument *ValueType.* Cet argument définit le champ SQL_DESC_DATA_PTR de l’APD. Une application peut définir l’argument *de ParameterValuePtr* à un pointeur nul, tant * \** que StrLen_or_IndPtr est SQL_NULL_DATA ou SQL_DATA_AT_EXEC. (Cela ne s’applique qu’aux paramètres d’entrée ou d’entrée/sortie.)  
  
 Si \* *StrLen_or_IndPtr* est le résultat de la SQL_LEN_DATA_AT_EXEC (*longueur)* macro ou SQL_DATA_AT_EXEC, alors *ParameterValuePtr* est une valeur de pointeur définie par l’application qui est associée au paramètre. Il est retourné à l’application par **SQLParamData**. Par exemple, *ParavaluePtr* peut être un jeton non zéro tel qu’un numéro de paramètre, un pointeur vers les données, ou un pointeur à une structure que l’application utilisait pour lier les paramètres d’entrée. Toutefois, notez que si le paramètre est un paramètre d’entrée/sortie, *ParameterValuePtr* doit être un pointeur vers un tampon où la valeur de sortie sera stockée. Si la valeur de l’attribut de l’SQL_ATTR_PARAMSET_SIZE’énoncé est supérieure à 1, l’application peut utiliser la valeur indiquée par l’attribut SQL_ATTR_PARAMS_PROCESSED_PTR déclaration ainsi que l’argument *de ParameterValuePtr.* Par exemple, *ParameterValuePtr* peut indiquer un éventail de valeurs et l’application peut utiliser la valeur pointée par SQL_ATTR_PARAMS_PROCESSED_PTR pour récupérer la valeur correcte de la gamme. Pour plus d’informations, voir « Valeurs paramètres de passage » plus tard dans cette section.  
  
 Si l’argument *d’InputOutputType* est SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT, *ParameterValuePtr* indique un tampon dans lequel le conducteur retourne la valeur de sortie. Si la procédure renvoie un \*ou plusieurs ensembles de résultats, le tampon *ParavaluePtr* n’est pas garanti pour être défini jusqu’à ce que tous les ensembles de résultats/nombres de lignes aient été traités. Si le tampon n’est pas défini tant que le traitement n’est pas terminé, les paramètres de sortie et les valeurs de retour ne sont pas disponibles jusqu’à ce que **SQLMoreResults** revienne SQL_NO_DATA. Appeler **SQLCloseCursor** ou **SQLFreeStmt** avec une option de SQL_CLOSE entraînera l’abandon de ces valeurs.  
  
 Si la valeur de l’attribut de l’SQL_ATTR_PARAMSET_SIZE est supérieure à 1, *ParameterValuePtr* indique un tableau. Un seul relevé SQL traite la gamme complète de valeurs d’entrée pour un paramètre d’entrée ou d’entrée/sortie et renvoie un éventail de valeurs de sortie pour un paramètre d’entrée/sortie ou de sortie.  
  
## <a name="bufferlength-argument"></a>BufferLength Argument

 Pour \*les données de caractère et de C binaires, l’argument *BufferLength* spécifie la longueur du tampon \* *ParameterValuePtr* (s’il s’agit d’un seul élément) ou la longueur d’un élément dans le tableau *ParaValuePtr* (si la valeur de l’attribut SQL_ATTR_PARAMSET_SIZE déclaration est supérieure à 1). Cet argument établit le SQL_DESC_OCTET_LENGTH champ record de l’APD. Si l’application spécifie plusieurs valeurs, *BufferLength* est utilisé pour déterminer l’emplacement des valeurs dans le tableau*De ParamètresValuePtr,* tant sur l’entrée que sur la sortie. Pour les paramètres d’entrée/sortie et de sortie, il est utilisé pour déterminer s’il convient de tronquer les données de caractère et de C binaires sur la sortie :  
  
-   Pour les données de caractère C, si le nombre d’octets disponibles pour \*revenir est supérieur ou égal à *BufferLength*, les données dans *ParameterValuePtr* est tronquée à *BufferLength* moins la longueur d’un caractère de non-termination et est annulée par le conducteur.  
  
-   Pour les données C binaires, si le nombre d’octets disponibles pour revenir est supérieur à *BufferLength*, les données dans \* *ParameterValuePtr* sont tronquées sur les octets *BufferLength.*  
  
 Pour tous les autres types de données C, l’argument *de BufferLength* est ignoré. La longueur \*du tampon *ParaValuePtr* (s’il s’agit d’un \*seul élément) ou la longueur d’un élément du tableau *ParaValuePtr* (si l’application appelle **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_PARAMSET_SIZE de spécifier des valeurs multiples pour chaque paramètre) est supposé être la longueur du type de données C.  
  
 Pour la sortie en continu ou les paramètres d’entrée/sortie en streaming, l’argument *de BufferLength* est ignoré parce que la longueur du tampon est spécifiée dans **SQLGetData**.  
  
> [!NOTE]  
>  Lorsqu’une application ODBC 1.0 appelle **SQLSetParam** dans un ODBC 3. *x* conducteur, le Driver Manager convertit cela en un appel à **SQLBindParameter** dans lequel *l’argument BufferLength* est toujours SQL_SETPARAM_VALUE_MAX. Parce que le gestionnaire de conducteur renvoie une erreur si un ODBC 3. *x* application définit *BufferLength* à SQL_SETPARAM_VALUE_MAX, un ODBC 3. *x* le conducteur peut l’utiliser pour déterminer quand il est appelé par une application ODBC 1.0.  
  
> [!NOTE]  
>  Dans **SQLSetParam**, la façon dont une application spécifie la longueur du tampon*De ParameterValuePtr* afin que le conducteur puisse retourner des données de caractère ou binaires, et la façon dont une application envoie un tableau de caractères ou des valeurs de paramètres binaires au pilote, sont définies par le conducteur.  
  
## <a name="strlen_or_indptr-argument"></a>StrLen_or_IndPtr Argument

 *L’argument StrLen_or_IndPtr* indique un tampon qui, lorsque **SQLExecute** ou **SQLExecDirect** est appelé, contient l’un des éléments suivants. (Cet argument définit les SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_INDICATOR_PTR les champs d’enregistrement des pointeurs de paramètres d’application.)  
  
-   La longueur de la valeur du paramètre stockée dans*le paramètreValuePtr*. Ceci est ignoré sauf pour les données de caractère ou de C binaire.  
  
-   SQL_NTS. La valeur du paramètre est une chaîne non terminée.  
  
-   SQL_NULL_DATA. La valeur du paramètre est NULL.  
  
-   SQL_DEFAULT_PARAM. Une procédure consiste à utiliser la valeur par défaut d’un paramètre, au lieu d’une valeur récupérée à partir de l’application. Cette valeur n’est valable que dans une procédure appelée syntaxe canonique ODBC, et seulement si *l’argument d’InputOutputType* est SQL_PARAM_INPUT, SQL_PARAM_INPUT_OUTPUT, ou SQL_PARAM_INPUT_OUTPUT_STREAM. Lorsque \* *StrLen_or_IndPtr* est SQL_DEFAULT_PARAM, le *ValueType*, *ParameterType*, *ColumnSize*, *DecimalDigits*, *BufferLength*, et *ParameterValuePtr* arguments sont ignorés pour les paramètres d’entrée et ne sont utilisés que pour définir la valeur de paramètre de sortie pour les paramètres d’entrée / sortie.  
  
-   Le résultat de la SQL_LEN_DATA_AT_EXEC(*longueur)* macro. Les données du paramètre seront envoyées avec **SQLPutData**. Si l’argument *de ParameterType* est SQL_LONGVARBINARY, SQL_LONGVARCHAR, ou un type de données longue et spécifique à la source de données, et que le conducteur renvoie « Y » pour le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo**, la *longueur* est le nombre d’octets de données à envoyer pour le paramètre; autrement, *la longueur* doit être une valeur non native et est ignorée. Pour plus d’informations, voir « Valeurs paramètres de passage », plus tard dans cette section.  
  
     Par exemple, pour spécifier que 10 000 octets de données seront envoyés avec **SQLPutData** dans un ou plusieurs appels, pour un paramètre SQL_LONGVARCHAR, un ensemble d’applications*StrLen_or_IndPtr* à SQL_LEN_DATA_AT_EXEC(10000).  
  
-   SQL_DATA_AT_EXEC. Les données du paramètre seront envoyées avec **SQLPutData**. Cette valeur est utilisée par les applications ODBC 1.0 lorsqu’elles appellent ODBC 3. *x* conducteurs. Pour plus d’informations, voir « Valeurs paramètres de passage », plus tard dans cette section.  
  
 Si *StrLen_or_IndPtr* est un pointeur nul, le pilote suppose que toutes les valeurs de paramètres d’entrée ne sont pas-NULL et que le caractère et les données binaires sont annulés. Si *InputOutputType* est SQL_PARAM_OUTPUT ou SQL_PARAM_OUTPUT_STREAM et *paramévaluePtr* et *StrLen_or_IndPtr* sont tous deux des pointeurs nuls, le conducteur écarte la valeur de sortie.  
  
> [!NOTE]  
>  Les développeurs d’applications sont fortement déconseillés de spécifier un pointeur nul pour *StrLen_or_IndPtr* lorsque le type de données du paramètre est SQL_C_BINARY. Pour s’assurer qu’un pilote ne tronque pas de façon inattendue SQL_C_BINARY données, *StrLen_or_IndPtr* doit contenir un pointeur à une valeur de longueur valide.  
  
 Si *l’argument d’InputOutputType* est SQL_PARAM_INPUT_OUTPUT, SQL_PARAM_OUTPUT, SQL_PARAM_INPUT_OUTPUT_STREAM ou SQL_PARAM_OUTPUT_STREAM, *StrLen_or_IndPtr* indique un tampon dans lequel le conducteur retourne SQL_NULL_DATA, le nombre d’octets disponibles pour revenir dans \* *ParameterValuePtr* (à l’exclusion du byte de terminaison nulle des données de caractère), ou SQL_NO_TOTAL (si le nombre de octets disponibles pour revenir ne peut pas être déterminé). Si la procédure renvoie un ou plusieurs ensembles de résultats, le tampon*de StrLen_or_IndPtr* n’est pas garanti d’être défini jusqu’à ce que tous les résultats aient été récupérés.  
  
 Si la valeur de l’attribut de l’SQL_ATTR_PARAMSET_SIZE est supérieure à 1, *StrLen_or_IndPtr* indique un éventail de valeurs SQLLEN. Il peut s’agir de l’une ou l’autre des valeurs énumérées plus tôt dans cette section et traitées avec une seule déclaration SQL.  
  
## <a name="passing-parameter-values"></a>Valeurs de paramètres de passage

 Une application peut passer la valeur d’un paramètre soit dans le \*tampon *ParameterValuePtr* ou avec un ou plusieurs appels à **SQLPutData**. Les paramètres dont les données sont transmises avec **SQLPutData** sont connus sous le nom de paramètres *de données à l’exécution.* Ceux-ci sont généralement utilisés pour envoyer des données pour SQL_LONGVARBINARY et SQL_LONGVARCHAR paramètres, et peuvent être mélangés avec d’autres paramètres.  
  
 Pour passer les valeurs de paramètres, une application effectue la séquence suivante d’étapes :  
  
1.  Appelle **SQLBindParameter** pour chaque paramètre pour lier les tampons pour la valeur du paramètre (argument*ParamètreValuePtr)* et la longueur / indicateur *(StrLen_or_IndPtr* argument). Pour les paramètres de données à l’exécution, *ParavaluePtr* est une valeur de pointeur définie par l’application, comme un numéro de paramètre ou un pointeur pour les données. La valeur sera retournée plus tard et peut être utilisée pour identifier le paramètre.  
  
2.  Place les valeurs pour les paramètres \*d’entrée et d’entrée/sortie dans le *ParamètreValuePtr* et les tampons*StrLen_or_IndPtr* :  
  
    -   Pour les paramètres normaux, l’application \*place la valeur paramètre dans le tampon *ParameterValuePtr* et la longueur de cette valeur dans le tampon*StrLen_or_IndPtr.* Pour plus d’informations, voir [Définir les valeurs paramètres](../../../odbc/reference/develop-app/setting-parameter-values.md).  
  
    -   Pour les paramètres de données à l’exécution, l’application met le résultat de la SQL_LEN_DATA_AT_EXEC(*longueur)* macro (lors de l’appel d’un pilote ODBC 2.0) dans le tampon*de StrLen_or_IndPtr.*  
  
3.  Appelle **SQLExecute** ou **SQLExecDirect** pour exécuter la déclaration SQL.  
  
    -   S’il n’y a pas de paramètres de données à l’exécution, le processus est terminé.  
  
    -   S’il existe des paramètres de données à l’exécution, la fonction renvoie SQL_NEED_DATA.  
  
4.  Appelle **SQLParamData** pour récupérer la valeur définie par l’application spécifiée dans l’argument *de ParameterValuePtr* de **SQLBindParameter** pour le premier paramètre de données à exécuter à traiter. **SQLParamData** revient SQL_NEED_DATA.  
  
    > [!NOTE]  
    >  Bien que les paramètres de données à l’exécution ressemblent à des colonnes de données à l’exécution, la valeur retournée par **SQLParamData** est différente pour chacun. Les paramètres de données à l’exécution sont des paramètres dans une déclaration SQL pour laquelle les données seront envoyées avec **SQLPutData** lorsque la déclaration sera exécutée avec **SQLExecDirect** ou **SQLExecute**. Ils sont liés avec **SQLBindParameter**. La valeur retournée par **SQLParamData** est une valeur pointeur passée à **SQLBindParameter** dans l’argument *De ParameterValuePtr.* Les colonnes de données d’exécution sont des colonnes dans un ensemble de rangées pour lesquelles les données seront envoyées avec **SQLPutData** lorsqu’une ligne est mise à jour ou ajoutée avec **SQLBulkOperations** ou mise à jour avec **SQLSetPos**. Ils sont liés avec **SQLBindCol**. La valeur retournée par **SQLParamData** est l’adresse de la rangée dans le tampon*TargetValuePtr* (fixé par un appel à **SQLBindCol**) qui est en cours de traitement.  
  
5.  Appelle **SQLPutData** une ou plusieurs fois pour envoyer des données pour le paramètre. Plus d’un appel est nécessaire si \*la valeur des données est plus grande que le tampon *ParameterValuePtr* spécifié dans **SQLPutData**; plusieurs appels vers **SQLPutData** pour le même paramètre ne sont autorisés que lors de l’envoi de données de caractère C à une colonne avec un type de données spécifique à un personnage, binaire ou spécifique à la source de données ou lors de l’envoi de données C binaires à une colonne avec un type de données de caractère, binaire ou spécifique à la source de données.  
  
6.  Appelle **SQLParamData** à nouveau pour signaler que toutes les données ont été envoyées pour le paramètre.  
  
    -   S’il y a plus de paramètres de données à l’exécution, **SQLParamData** renvoie SQL_NEED_DATA et la valeur définie par l’application pour le prochain paramètre de données à exécution à traiter. L’application reprend les étapes 4 et 5.  
  
    -   S’il n’y a plus de paramètres de données à l’exécution, le processus est terminé. Si la déclaration a été exécutée avec succès, **SQLParamData** renvoie SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO; si l’exécution a échoué, elle renvoie SQL_ERROR. À ce stade, **SQLParamData** peut retourner n’importe quel SQLSTATE qui peut être retourné par la fonction qui est utilisée pour exécuter la déclaration (**SQLExecDirect** ou **SQLExecute**).  
  
         Les valeurs de sortie pour les paramètres d’entrée/sortie ou de sortie sont disponibles dans le \* *ParamètreValuePtr* et*StrLen_or_IndPtr* tampons après que l’application récupère tous les ensembles de résultats générés par l’instruction.  
  
 Appeler **SQLExecute** ou **SQLExecDirect** met la déclaration dans un état SQL_NEED_DATA. À ce stade, l’application ne peut appeler que **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **SQLParamData**, ou **SQLPutData** avec la déclaration ou la *poignée de connexion* associée à la déclaration. S’il appelle toute autre fonction avec l’instruction ou la connexion associée à l’instruction, la fonction renvoie SQLSTATE HY010 (erreur de séquence de fonction). La déclaration laisse l’état SQL_NEED_DATA lorsque **SQLParamData** ou **SQLPutData** renvoie une erreur, **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, ou la déclaration est annulée.  
  
 Si l’application appelle **SQLCancel** alors que le conducteur a encore besoin de données pour les paramètres de données à l’exécution, le conducteur annule l’exécution de la déclaration; l’application peut alors appeler **SQLExecute** ou **SQLExecDirect** à nouveau.  
  
## <a name="retrieving-streamed-output-parameters"></a>Récupération des paramètres de sortie en continu

 Lorsqu’une application définit *InputOutputType* à SQL_PARAM_INPUT_OUTPUT_STREAM ou SQL_PARAM_OUTPUT_STREAM, la valeur du paramètre de sortie doit être récupérée par un ou plusieurs appels à **SQLGetData**. Lorsque le conducteur a une valeur de paramètre de sortie en streaming pour revenir à l’application, il retournera SQL_PARAM_DATA_AVAILABLE en réponse à un appel aux fonctions suivantes: **SQLMoreResults**, **SQLExecute**, et **SQLExecDirect**. Une application appelle **SQLParamData** pour déterminer quelle valeur de paramètre est disponible.  
  
 Pour plus d’informations sur SQL_PARAM_DATA_AVAILABLE et les paramètres de sortie en streaming, voir [Les paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="using-arrays-of-parameters"></a>Utilisation de tableaux de paramètres

 Lorsqu’une application prépare une déclaration avec des marqueurs de paramètres et passe dans un tableau de paramètres, il existe deux façons différentes d’exécuter cela. Une façon est pour le conducteur de s’appuyer sur les capacités de traitement de la gamme de l’extrémité arrière, auquel cas l’ensemble de la déclaration avec la gamme de paramètres est traitée comme une unité atomique. Oracle est un exemple d’une source de données qui prend en charge les capacités de traitement des réseaux. Une autre façon de mettre en œuvre cette fonctionnalité est pour le conducteur de générer un lot de déclarations SQL, une déclaration SQL pour chaque ensemble de paramètres dans le tableau de paramètres, et d’exécuter le lot. Les ensembles de paramètres ne peuvent pas être utilisés avec une **mise À JOUR Où CURRENT OF** déclaration.  
  
 Lorsqu’un éventail de paramètres est traité, des ensembles de résultats individuels/des comptes de ligne (un pour chaque paramètre) peuvent être disponibles ou les ensembles/lignes de résultat peuvent être enroulés en un seul. L’option SQL_PARAM_ARRAY_ROW_COUNTS dans **SQLGetInfo** indique si le nombre de rangées est disponible pour chaque ensemble de paramètres (SQL_PARC_BATCH) ou si un seul nombre de lignes est disponible (SQL_PARC_NO_BATCH).  
  
 L’option SQL_PARAM_ARRAY_SELECTS dans **SQLGetInfo** indique si un ensemble de résultats est disponible pour chaque ensemble de paramètres (SQL_PAS_BATCH) ou un seul ensemble de résultats est disponible (SQL_PAS_NO_BATCH). Si le pilote ne permet pas l’exécution d’une déclaration génératrice de paramètres avec un éventail de paramètres, SQL_PARAM_ARRAY_SELECTS renvoie SQL_PAS_NO_SELECT.  
  
 Pour plus d’informations, consultez [LA fonction SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 Pour prendre en charge les ensembles de paramètres, l’attribut SQL_ATTR_PARAMSET_SIZE’énoncé est défini pour spécifier le nombre de valeurs pour chaque paramètre. Si le champ est supérieur à 1, les champs SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR de la DPA doivent indiquer les tableaux. La cardinalité de chaque tableau est égale à la valeur de SQL_ATTR_PARAMSET_SIZE.  
  
 Le champ SQL_DESC_ROWS_PROCESSED_PTR de la DPA indique un tampon qui contient le nombre d’ensembles de paramètres qui ont été traités, y compris les ensembles d’erreurs. Au fur et à mesure que chaque ensemble de paramètres est traité, le conducteur stocke une nouvelle valeur dans le tampon. Aucun numéro ne sera retourné s’il s’agit d’un pointeur nul. Lorsque des tableaux de paramètres sont utilisés, la valeur indiquée par le champ SQL_DESC_ROWS_PROCESSED_PTR de l’APD est peuplée même si SQL_ERROR est retournée par la fonction de réglage. Si SQL_NEED_DATA est retournée, la valeur soulignée par le champ SQL_DESC_ROWS_PROCESSED_PTR de la DPA est définie à l’ensemble des paramètres en cours de traitement.  
  
 Ce qui se passe lorsqu’un tableau de paramètres est lié et qu’une **mise à JOUR Où LA** déclaration DE l’ACTUAL EST exécutée est définie par le conducteur.  
  
## <a name="column-wise-parameter-binding"></a>Liaison de paramètres de colonne-sage

 Dans la liaison de colonne-sage, l’application lie paramètres séparés et la longueur / panneaux d’indicateur à chaque paramètre.  
  
 Pour utiliser la liaison de colonne-sage, l’application définit d’abord l’attribut SQL_ATTR_PARAM_BIND_TYPE énoncé à SQL_PARAM_BIND_BY_COLUMN. (C’est la valeur par défaut.) Pour que chaque colonne soit liée, l’application effectue les étapes suivantes :  
  
1.  Alloue un tableau tampon de paramètres.  
  
2.  Alloue une gamme de tampons de longueur/indicateur.  
  
    > [!NOTE]  
    >  Si l’application écrit directement aux descripteurs lorsque la liaison de la colonne est utilisée, des tableaux distincts peuvent être utilisés pour la longueur et les données d’indicateur.  
  
3.  Appelle **SQLBindParameter** avec les arguments suivants:  
  
    -   *ValueType* est le type C d’un seul élément dans le tableau de mémoire tampon de paramètre.  
  
    -   *ParamètreType* est le type SQL du paramètre.  
  
    -   *ParameterValuePtr* est l’adresse du tableau tampon paramètre.  
  
    -   *BufferLength* est la taille d’un seul élément dans le tableau de mémoire tampon de paramètre. *L’argument de BufferLength* est ignoré lorsque les données sont des données à durée fixe.  
  
    -   *StrLen_or_IndPtr* est l’adresse du tableau de longueur/indicateur.  
  
 Pour plus d’informations sur la façon dont ces informations sont utilisées, voir "ParameterValuePtr Argument" dans "Commentaires", plus tard dans cette section. Pour plus d’informations sur la liaison des paramètres par colonnes, voir [Binding Arrays of Parameters](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="row-wise-parameter-binding"></a>Liaison de paramètres de ligne-sage

 Dans la fixation en ligne, l’application définit une structure qui contient des paramètres et des tampons de longueur/indicateur pour chaque paramètre à lier.  
  
 Pour utiliser la fixation en ligne, l’application effectue les étapes suivantes :  
  
1.  Définit une structure pour contenir un ensemble unique de paramètres (y compris les paramètres et la longueur/indicateurs) et alloue un tableau de ces structures.  
  
    > [!NOTE]  
    >  Si l’application écrit directement aux descripteurs lorsque la liaison en ligne est utilisée, des champs distincts peuvent être utilisés pour la longueur et les données d’indicateurs.  
  
2.  Définit l’attribut SQL_ATTR_PARAM_BIND_TYPE énoncé à la taille de la structure qui contient un seul ensemble de paramètres ou à la taille d’une instance d’un tampon dans lequel les paramètres seront liés. La longueur doit inclure de l’espace pour tous les paramètres liés, et tout rembourrage de la structure ou du tampon, pour s’assurer que lorsque l’adresse d’un paramètre lié est incrémentée avec la longueur spécifiée, le résultat indiquera le début du même paramètre dans la rangée suivante. Lorsque vous utilisez la *taille de l’opérateur* dans ANSI C, ce comportement est garanti.  
  
3.  Appelle **SQLBindParameter** avec les arguments suivants pour que chaque paramètre soit lié :  
  
    -   *ValueType* est le type de membre de mémoire tampon paramètre à lié à la colonne.  
  
    -   *ParamètreType* est le type SQL du paramètre.  
  
    -   *ParameterValuePtr* est l’adresse du membre tampon paramètre dans le premier élément de tableau.  
  
    -   *BufferLength* est la taille du membre de mémoire tampon paramètre.  
  
    -   *StrLen_or_IndPtr* est l’adresse du membre de la longueur/indicateur à lier.  
  
 Pour plus d’informations sur la façon dont ces informations sont utilisées, voir «*ParameterValuePtr* Argument », plus tard dans cette section. Pour plus d’informations sur la fixation des paramètres en ligne, voir les [tableaux contraignants des paramètres](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md).  
  
## <a name="error-information"></a>Informations sur l'erreur

 Si un pilote n’implémente pas les tableaux de paramètres en lots (l’option SQL_PARAM_ARRAY_ROW_COUNTS est égale à SQL_PARC_NO_BATCH), les situations d’erreur sont traitées comme si une instruction avait été exécutée. Si le conducteur implémente les tableaux de paramètres en lots, une application peut utiliser le champ d’en-tête SQL_DESC_ARRAY_STATUS_PTR de l’IPD pour déterminer quel paramètre d’une déclaration SQL ou quel paramètre dans un tableau de paramètres a amené **SQLExecDirect** ou **SQLExecute** à renvoyer une erreur. Ce champ contient des informations d’état pour chaque rangée de valeurs de paramètres. Si le champ indique qu’une erreur s’est produite, les champs de la structure de données diagnostiques indiqueront le nombre de lignes et de paramètres du paramètre qui a échoué. Le nombre d’éléments dans le tableau sera défini par le champ d’en-tête SQL_DESC_ARRAY_SIZE dans la DPA, qui peut être défini par l’attribut de l’SQL_ATTR_PARAMSET_SIZE déclaration.  
  
> [!NOTE]  
>  Le champ d’en-tête SQL_DESC_ARRAY_STATUS_PTR dans l’APD est utilisé pour ignorer les paramètres. Pour plus d’informations sur l’ignorance des paramètres, voir la section suivante, "Ignorer un ensemble de paramètres."  
  
 Lorsque **SQLExecute** ou **SQLExecDirect** revient SQL_ERROR, les éléments du tableau pointés par le champ SQL_DESC_ARRAY_STATUS_PTR dans la DPI contiendront SQL_PARAM_ERROR, SQL_PARAM_SUCCESS, SQL_PARAM_SUCCESS_WITH_INFO, SQL_PARAM_UNUSED ou SQL_PARAM_DIAG_UNAVAILABLE.  
  
 Pour chaque élément de ce tableau, la structure de données diagnostiques contient un ou plusieurs enregistrements d’état. Le champ SQL_DIAG_ROW_NUMBER de la structure indique le nombre de lignes des valeurs de paramètres qui ont causé l’erreur. S’il est possible de déterminer le paramètre particulier dans une rangée de paramètres qui ont causé l’erreur, le numéro de paramètre sera entré dans le champ SQL_DIAG_COLUMN_NUMBER.  
  
 SQL_PARAM_UNUSED est saisie lorsqu’un paramètre n’a pas été utilisé parce qu’une erreur s’est produite dans un paramètre antérieur qui a forcé **SQLExecute** ou **SQLExecDirect** à avorter. Par exemple, s’il y a 50 paramètres et qu’une erreur s’est produite lors de l’exécution de l’ensemble de paramètres qui a causé l’interruption de **SQLExecute** ou **SQLExecDirect,** alors SQL_PARAM_UNUSED est inscrit dans le tableau d’état pour les paramètres 41 à 50.  
  
 SQL_PARAM_DIAG_UNAVAILABLE est entré lorsque le conducteur traite des tableaux de paramètres comme une unité monolithique, de sorte qu’il ne génère pas ce niveau de paramètre individuel d’informations d’erreur.  
  
 Certaines erreurs dans le traitement d’un seul ensemble de paramètres provoquent le traitement des ensembles ultérieurs de paramètres dans le tableau de s’arrêter. D’autres erreurs n’affectent pas le traitement des paramètres ultérieurs. Les erreurs qui arrêteront le traitement sont définies par le conducteur. Si le traitement n’est pas arrêté, tous les paramètres du tableau sont traités, SQL_SUCCESS_WITH_INFO est retourné à la suite de l’erreur, et le tampon défini par SQL_ATTR_PARAMS_PROCESSED_PTR est réglé sur le nombre total d’ensembles de paramètres traités (tel que défini par l’attribut SQL_ATTR_PARAMSET_SIZE déclaration), qui comprend des ensembles d’erreurs.  
  
> [!CAUTION]  
>  Le comportement d’ODBC lorsqu’une erreur se produit dans le traitement d’un tableau de paramètres est différent dans ODBC 3. *x* qu’il ne l’était dans ODBC 2. *x*. À ODBC 2. *x*, la fonction est retournée SQL_ERROR et le traitement a cessé. Le tampon pointé *pirow* par l’argument de la moelle de **SQLParamOptions** contenait le nombre de la rangée d’erreurs. À ODBC 3. *x*, la fonction retourne SQL_SUCCESS_WITH_INFO et le traitement peut s’arrêter ou continuer. S’il se poursuit, le tampon spécifié par SQL_ATTR_PARAMS_PROCESSED_PTR sera réglé sur la valeur de tous les paramètres traités, y compris ceux qui ont entraîné une erreur. Ce changement de comportement peut causer des problèmes pour les applications existantes.  
  
 Lorsque **SQLExecute** ou **SQLExecDirect** revient avant de terminer le traitement de tous les ensembles de paramètres dans un tableau de paramètres, comme lorsque SQL_ERROR ou SQL_NEED_DATA est retourné, le tableau d’état contient des statuts pour les paramètres qui ont déjà été traités. L’emplacement indiqué par le champ SQL_DESC_ROWS_PROCESSED_PTR dans l’IPD contient le numéro de ligne dans le tableau de paramètres qui a causé le code d’erreur SQL_ERROR ou SQL_NEED_DATA. Lorsqu’un éventail de paramètres est envoyé à une instruction SELECT, la disponibilité des valeurs du tableau d’état est définie par le conducteur; ils peuvent être disponibles après l’exécution de la déclaration ou, par conséquent, les ensembles sont récupérés.  
  
## <a name="ignoring-a-set-of-parameters"></a>Ignorer un ensemble de paramètres

 Le champ SQL_DESC_ARRAY_STATUS_PTR de l’APD (tel qu’établi par l’attribut de l’SQL_ATTR_PARAM_STATUS_PTR) peut être utilisé pour indiquer qu’un ensemble de paramètres liés dans une déclaration SQL doit être ignoré. Pour ordonner au conducteur d’ignorer un ou plusieurs ensembles de paramètres pendant l’exécution, une application doit suivre ces étapes :  
  
1.  Appelez **SQLSetDescField** pour définir le champ d’en-tête SQL_DESC_ARRAY_STATUS_PTR de l’APD pour indiquer un éventail de valeurs SQLUSMALLINT pour contenir les informations sur l’état. Ce champ peut également être défini en appelant **SQLSetStmtAttr** avec un *attribut* de SQL_ATTR_PARAM_OPERATION_PTR, ce qui permet à une application de définir le champ sans obtenir une poignée descripteur.  
  
2.  Définissez chaque élément du tableau défini par le champ SQL_DESC_ARRAY_STATUS_PTR de l’APD à l’une des deux valeurs :  
  
    -   SQL_PARAM_IGNORE, pour indiquer que la rangée est exclue de l’exécution de déclaration.  
  
    -   SQL_PARAM_PROCEED, pour indiquer que la rangée est incluse dans l’exécution de la déclaration.  
  
3.  Appelez **SQLExecDirect** ou **SQLExecute** pour exécuter la déclaration préparée.  
  
 Les règles suivantes s’appliquent au tableau défini par le champ SQL_DESC_ARRAY_STATUS_PTR de l’APD :  
  
-   Le pointeur est configuré à null par défaut.  
  
-   Si le pointeur est nul, tous les ensembles de paramètres sont utilisés, comme si tous les éléments étaient réglés pour SQL_ROW_PROCEED.  
  
-   La définition d’un élément à SQL_PARAM_PROCEED ne garantit pas que l’opération utilisera cet ensemble particulier de paramètres.  
  
-   SQL_PARAM_PROCEED est défini comme 0 dans le fichier d’en-tête.  
  
 Une application peut définir le champ SQL_DESC_ARRAY_STATUS_PTR dans l’APD pour indiquer le même tableau que celui indiqué par le champ SQL_DESC_ARRAY_STATUS_PTR dans l’IRD. Ceci est utile lors de la liaison des paramètres à la ligne des données. Les paramètres peuvent alors être ignorés en fonction de l’état des données de la ligne. En plus de SQL_PARAM_IGNORE, les codes suivants font ignorer un paramètre dans une déclaration SQL : SQL_ROW_DELETED, SQL_ROW_UPDATED et SQL_ROW_ERROR. En plus de SQL_PARAM_PROCEED, les codes suivants font qu’une déclaration de SQL est en cours : SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO et SQL_ROW_ADDED.  
  
## <a name="rebinding-parameters"></a>Paramètres de rebinding

 Une application peut effectuer l’une ou l’autre des deux opérations pour modifier une liaison :  
  
-   Appelez **SQLBindParameter** pour spécifier une nouvelle liaison pour une colonne déjà liée. Le conducteur surmene l’ancienne fixation avec la nouvelle.  
  
-   Spécifier une compensation à ajouter à l’adresse tampon qui a été spécifiée par l’appel de liaison à **SQLBindParameter**. Pour plus d’informations, voir la section suivante, "Rebinding with Offsets."  
  
## <a name="rebinding-with-offsets"></a>Rebinding avec Offsets

 La rebindation des paramètres est particulièrement utile lorsqu’une application dispose d’une configuration de zone tampon qui peut contenir de nombreux paramètres, mais un appel à **SQLExecDirect** ou **SQLExecute** utilise seulement quelques-uns des paramètres. L’espace restant dans la zone tampon peut être utilisé pour la prochaine série de paramètres en modifiant la liaison existante par un décalage.  
  
 Le champ de SQL_DESC_BIND_OFFSET_PTR de la tête dans l’APD pointe vers le décalage de liaison. Si le champ n’est pas nul, le conducteur déreférence le pointeur et, si aucune des valeurs dans les SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR champs est un pointeur nul, ajoute la valeur déreférée à ces champs dans les dossiers descripteur au moment de l’exécution. Les nouvelles valeurs de pointeur sont utilisées lorsque les relevés SQL sont exécutés. Le décalage reste valide après la rebindation. Étant donné que SQL_DESC_BIND_OFFSET_PTR est un pointeur sur le décalage plutôt que le décalage lui-même, une application peut modifier le décalage directement, sans avoir à appeler [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) ou [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md) pour changer le champ descripteur. Le pointeur est configuré à null par défaut. Le champ SQL_DESC_BIND_OFFSET_PTR de l’ARD peut être réglé par un appel à [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) ou par un appel à [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)avec un *fAttribute* de SQL_ATTR_PARAM_BIND_OFFSET_PTR.  
  
 Le décalage contraignant est toujours ajouté directement aux valeurs dans les domaines de la SQL_DESC_DATA_PTR, de la SQL_DESC_INDICATOR_PTR et de la SQL_DESC_OCTET_LENGTH_PTR. Si le décalage est modifié à une valeur différente, la nouvelle valeur est toujours ajoutée directement à la valeur dans chaque champ descripteur. Le nouveau décalage n’est pas ajouté à la somme de la valeur du champ et à toute compensation antérieure.  
  
## <a name="descriptors"></a>Descripteurs

 La façon dont un paramètre est lié est déterminée par les champs des AD APD et des DPI. Les arguments de **SQLBindParameter** sont utilisés pour définir ces champs descripteur. Les champs peuvent également être définis par les fonctions **SQLSetDescField,** bien que **SQLBindParameter** soit plus efficace à utiliser parce que l’application n’a pas besoin d’obtenir une poignée descripteur pour appeler **SQLBindParameter**.  
  
> [!CAUTION]  
>  Appeler **SQLBindParameter** pour une déclaration peut affecter d’autres déclarations. Cela se produit lorsque l’ARD associé à l’instruction est explicitement attribué et est également associé à d’autres énoncés. Étant donné que **SQLBindParameter** modifie les champs de l’APD, les modifications s’appliquent à toutes les déclarations auxquelles ce descripteur est associé. Si ce n’est pas le comportement requis, l’application doit dissocier ce descripteur des autres déclarations avant d’appeler **SQLBindParameter**.  
  
 Conceptuellement, **SQLBindParameter** effectue les étapes suivantes dans l’ordre :  
  
1.  Appelle [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) pour obtenir la poignée APD.  
  
2.  Appelle [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) pour obtenir le champ SQL_DESC_COUNT de l’APD, et si la valeur de *l’argument De La fiche* dépasse la valeur de SQL_DESC_COUNT, appelle **SQLSetDescField** pour augmenter la valeur de SQL_DESC_COUNT à *ColumnNumber*.  
  
3.  Appelle [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) plusieurs fois pour attribuer des valeurs aux champs suivants de l’APD :  
  
    -   Définit SQL_DESC_TYPE et SQL_DESC_CONCISE_TYPE à la valeur de *ValueType*, sauf que si *ValueType* est l’un des identificateurs concis d’un sous-type de date ou d’intervalle, il définit SQL_DESC_TYPE à SQL_DATETIME ou SQL_INTERVAL, respectivement, définit SQL_DESC_CONCISE_TYPE à l’identifiant concis, et définit SQL_DESC_DATETIME_INTERVAL_CODE à la date correspondante ou sous-code d’intervalle.  
  
    -   Définit le champ SQL_DESC_OCTET_LENGTH à la valeur de *BufferLength*.  
  
    -   Définit le champ SQL_DESC_DATA_PTR à la valeur de *ParameterValue*.  
  
    -   Définit le champ SQL_DESC_OCTET_LENGTH_PTR à la valeur de *StrLen_or_Ind*.  
  
    -   Définit le champ SQL_DESC_INDICATOR_PTR aussi à la valeur de *StrLen_or_Ind*.  
  
     Le *paramètre StrLen_or_Ind* spécifie à la fois l’information sur l’indicateur et la longueur de la valeur du paramètre.  
  
4.  Appelle [SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md) pour obtenir la poignée IPD.  
  
5.  Appelle [SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) pour obtenir le champ SQL_DESC_COUNT de l’IPD, et si la valeur de *l’argument De La fiche* dépasse la valeur de SQL_DESC_COUNT, appelle **SQLSetDescField** pour augmenter la valeur de SQL_DESC_COUNT à *ColumnNumber*.  
  
6.  Appelle [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) plusieurs fois pour attribuer des valeurs aux champs suivants de l’IPD :  
  
    -   Définit SQL_DESC_TYPE et SQL_DESC_CONCISE_TYPE à la valeur de *ParameterType*, sauf que si *ParameterType* est l’un des identificateurs concis d’un sous-type de date ou d’intervalle, il définit SQL_DESC_TYPE à SQL_DATETIME ou SQL_INTERVAL, respectivement, définit SQL_DESC_CONCISE_TYPE à l’identifiant concis, et définit SQL_DESC_DATETIME_INTERVAL_CODE à la date correspondante ou sous-code d’intervalle.  
  
    -   Définit une ou plusieurs SQL_DESC_LENGTH, SQL_DESC_PRECISION et SQL_DESC_DATETIME_INTERVAL_PRECISION, le cas échéant pour *ParameterType*.  
  
    -   Définit SQL_DESC_SCALE à la valeur de *DecimalDigits*.  
  
 Si l’appel à **SQLBindParameter** échoue, le contenu des champs descripteur qu’il aurait mis dans la DPA n’est pas défini, et le champ SQL_DESC_COUNT de l’APD est inchangé. En outre, les SQL_DESC_LENGTH, les SQL_DESC_PRECISION, les SQL_DESC_SCALE et les SQL_DESC_TYPE domaines du dossier approprié dans la DPI sont indéfinis et le champ SQL_DESC_COUNT de la DPI est inchangé.  
  
## <a name="conversion-of-calls-to-and-from-sqlsetparam"></a>Conversion d’appels à et en provenance de SQLSetParam

 Lorsqu’une application ODBC 1.0 appelle **SQLSetParam** dans un ODBC 3. *x* pilote, l’ODBC 3. *x* Driver Manager cartographie l’appel tel qu’il est indiqué dans le tableau suivant.  
  
|Appel par ODBC 1.0 application|Appelez à ODBC 3. *x* conducteur|  
|----------------------------------|-------------------------------|  
|SQLSetParam( StatementHandle, ParameterNumber, ValueType, ParameterType, LengthPrecision, ParameterScale, ParameterValuePtr, StrLen_or_IndPtr);|SQLBindParameter ( StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, *ColumnSize*, *DecimalDigits*, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr);|  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application prépare une déclaration SQL pour insérer des données dans le tableau ORDERS. Pour chaque paramètre de l’instruction, l’application appelle **SQLBindParameter** pour spécifier le type de données ODBC C et le type de données SQL du paramètre, et pour lier un tampon à chaque paramètre. Pour chaque ligne de données, l’application attribue des valeurs de données à chaque paramètre et appelle **SQLExecute** pour exécuter l’instruction.  
  
 L’échantillon suivant suppose que vous avez une source de données ODBC sur votre ordinateur appelé Northwind qui est associée à la base de données Northwind.  
  
 Pour plus d’exemples de code, voir [SQLBulkOperations Function](../../../odbc/reference/syntax/sqlbulkoperations-function.md), [SQLProcedures Function](../../../odbc/reference/syntax/sqlprocedures-function.md), [SQLPutData Function](../../../odbc/reference/syntax/sqlputdata-function.md), et [SQLSetPos Function](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp
// SQLBindParameter_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define EMPLOYEE_ID_LEN 10  
  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLSMALLINT sCustID;  
  
SQLCHAR szEmployeeID[EMPLOYEE_ID_LEN];  
SQL_DATE_STRUCT dsOrderDate;  
SQLINTEGER cbCustID = 0, cbOrderDate = 0, cbEmployeeID = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, EMPLOYEE_ID_LEN, 0, szEmployeeID, 0, &cbEmployeeID);  
   retcode = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sCustID, 0, &cbCustID);  
   retcode = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TIMESTAMP, sizeof(dsOrderDate), 0, &dsOrderDate, 0, &cbOrderDate);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"INSERT INTO Orders(CustomerID, EmployeeID, OrderDate) VALUES (?, ?, ?)", SQL_NTS);  
  
   strcpy_s((char*)szEmployeeID, _countof(szEmployeeID), "BERGS");  
   sCustID = 5;  
   dsOrderDate.year = 2006;  
   dsOrderDate.month = 3;  
   dsOrderDate.day = 17;  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="code-example"></a>Exemple de code

 Dans l’exemple suivant, une application exécute une procédure stockée SQL Server à l’aide d’un paramètre nommé.  
  
```cpp
// SQLBindParameter_Function_2.cpp  
// compile with: ODBC32.lib  
// sample assumes the following stored procedure:  
// use northwind  
// DROP PROCEDURE SQLBindParameter  
// GO  
//   
// CREATE PROCEDURE SQLBindParameter @quote int  
// AS  
// delete from orders where OrderID >= @quote  
// GO  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
SQLHDESC hIpd = NULL;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLRETURN retcode;  
SQLHSTMT hstmt = NULL;  
SQLCHAR szQuote[50] = "100084";  
SQLINTEGER cbValue = SQL_NTS;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retcode = SQLPrepare(hstmt, (SQLCHAR*)"{call SQLBindParameter(?)}", SQL_NTS);  
   retcode = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 50, 0, szQuote, 0, &cbValue);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
   retcode = SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
   retcode = SQLExecute(hstmt);  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retour d’informations sur un paramètre dans une déclaration|[Fonction SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Libérer les tampons de paramètres sur la déclaration|[Fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|Retour du nombre de paramètres d’instruction|[Fonction SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|Retour du paramètre suivant pour envoyer des données pour|[SQLParamData, fonction](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|Spécifier plusieurs valeurs de paramètres|[SQLParamOptions, fonction](../../../odbc/reference/syntax/sqlparamoptions-function.md)|  
|Envoi de données de paramètres au moment de l’exécution|[Fonction SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Voir aussi

 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
