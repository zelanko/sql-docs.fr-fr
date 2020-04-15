---
title: Fonction SQLDescribeParam (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be6d076ca121923a4b6769c7dad5269c3fd642ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301159"
---
# <a name="sqldescribeparam-function"></a>Fonction SQLDescribeParam
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLDescribeParam** renvoie la description d’un marqueur de paramètres associé à une déclaration SQL préparée. Ces informations sont également disponibles dans les domaines de l’IPD.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLDescribeParam(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT *   DataTypePtr,  
      SQLULEN *       ParameterSizePtr,  
      SQLSMALLINT *   DecimalDigitsPtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="argument"></a>Argument  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *ParameterNumber (en)*  
 [Entrée] Nombre de marqueur de paramètre commandé séquentiellement dans l’ordre de paramètres croissant, à partir de 1.  
  
 *DataTypePtr (en)*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le type de données SQL du paramètre. Cette valeur est lue à partir du champ d’enregistrement SQL_DESC_CONCISE_TYPE de l’IPD. Il s’agira de l’une des valeurs de la section types de [données SQL](../../../odbc/reference/appendixes/sql-data-types.md) de l’Annexe D : Data Types, ou d’un type de données SQL spécifique au conducteur.  
  
 À ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME ou SQL_TYPE_TIMESTAMP seront retournés dans * \*DataTypePtr* pour les données de date, d’heure ou de timetamp, respectivement; à ODBC 2. *x*, SQL_DATE, SQL_TIME ou SQL_TIMESTAMP seront retournés. Le gestionnaire de conducteur effectue les cartes requises lorsqu’un ODBC 2. *x* application fonctionne avec un ODBC 3. *x* conducteur ou lorsqu’un ODBC 3. *x* application fonctionne avec un ODBC 2. *x* conducteur.  
  
 Lorsque *ColumnNumber* est égal à 0 (pour une colonne de signets), SQL_BINARY est retourné dans * \*DataTypePtr* pour les signets à longueur variable. (SQL_INTEGER est retourné si les signets sont utilisés par un ODBC 3. *x* application fonctionnant avec un ODBC 2. *x* conducteur ou par un ODBC 2. *x* application fonctionnant avec un ODBC 3. *x* conducteur.)  
  
 Pour plus d’informations, consultez [SQL Data Types](../../../odbc/reference/appendixes/sql-data-types.md) in Annexe D: Data Types. Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur.  
  
 *ParamètresSizePtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la taille, en caractères, de la colonne ou l’expression du marqueur de paramètres correspondant tel que défini par la source de données. Pour plus d’informations sur la taille de la colonne, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert, et la taille d’affichage.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
 *DécimaleDigitsPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre de chiffres décimaux de la colonne ou l’expression du paramètre correspondant tel que défini par la source de données. Pour plus d’informations sur les chiffres décimaux, voir [La taille de colonne, les chiffres décimaux, la longueur d’octet de transfert, et la taille d’affichage.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
 *NullablePtr (nullablePtr)*  
 [Sortie] Pointeur vers un tampon dans lequel retourner une valeur qui indique si le paramètre permet des valeurs NULL. Cette valeur est lue à partir du champ SQL_DESC_NULLABLE de l’IPD. Celui-ci peut avoir l'une des valeurs suivantes :  
  
-   SQL_NO_NULLS : Le paramètre ne permet pas les valeurs NULL (c’est la valeur par défaut).  
  
-   SQL_NULLABLE : Le paramètre permet des valeurs NULL.  
  
-   SQL_NULLABLE_UNKNOWN : Le conducteur ne peut pas déterminer si le paramètre permet des valeurs NULL.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDescribeParam** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLDescribeParam** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07009|Indice descripteur invalide|(DM) La valeur spécifiée pour l’argument *ParameterNumber* est inférieure à 1.<br /><br /> La valeur spécifiée pour l’argument *ParameterNumber* était supérieure au nombre de paramètres dans la déclaration SQL associée.<br /><br /> Le marqueur de paramètres faisait partie d’une déclaration non-DML.<br /><br /> Le marqueur de paramètres faisait partie d’une liste **SELECT.**|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|21S01|La liste de valeur d’insertion ne correspond pas à la liste de colonnes|Le nombre de paramètres dans la déclaration **INSERT** ne correspondait pas au nombre de colonnes dans le tableau nommé dans la déclaration.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) La fonction a été appelée avant d’appeler **SQLPrepare** ou **SQLExecDirect** pour le *StatementHandle*.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLDescribeParam** a été appelée.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
## <a name="comments"></a>Commentaires  
 Les marqueurs de paramètres sont numérotés dans l’ordre de paramètres croissants, à commencer par 1, dans l’ordre qu’ils apparaissent dans la déclaration SQL.  
  
 **SQLDescribeParam** ne renvoie pas le type (entrée, entrée/sortie, ou sortie) d’un paramètre dans un communiqué SQL. Sauf dans les appels aux procédures, tous les paramètres dans les relevés SQL sont des paramètres d’entrée. Pour déterminer le type de chaque paramètre dans un appel à une procédure, une application appelle **SQLProcedureColumns**.  
  
 Pour plus d’informations, voir [Paramètres décrivants](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="code-example"></a>Exemple de code  
 L’exemple suivant invite l’utilisateur à une déclaration SQL et prépare ensuite cette déclaration. Ensuite, il appelle **SQLNumParams** pour déterminer si l’instruction contient des paramètres. Si l’énoncé contient des paramètres, il appelle **SQLDescribeParam** pour décrire ces paramètres et **SQLBindParameter** pour les lier. Enfin, il invite l’utilisateur pour les valeurs de tous les paramètres, puis exécute l’instruction.  
  
```cpp  
SQLCHAR       Statement[100];  
SQLSMALLINT   NumParams, i, DataType, DecimalDigits, Nullable;  
SQLUINTEGER   ParamSize;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement and prepare it.  
GetSQLStatement(Statement);  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Check to see if there are any parameters. If so, process them.  
SQLNumParams(hstmt, &NumParams);  
if (NumParams) {  
   // Allocate memory for three arrays. The first holds pointers to buffers in which  
   // each parameter value will be stored in character form. The second contains the  
   // length of each buffer. The third contains the length/indicator value for each  
   // parameter.  
   SQLPOINTER * PtrArray = (SQLPOINTER *) malloc(NumParams * sizeof(SQLPOINTER));  
   SQLINTEGER * BufferLenArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
   SQLINTEGER * LenOrIndArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
  
   for (i = 0; i < NumParams; i++) {  
   // Describe the parameter.  
   SQLDescribeParam(hstmt, i + 1, &DataType, &ParamSize, &DecimalDigits, &Nullable);  
  
   // Call a helper function to allocate a buffer in which to store the parameter  
   // value in character form. The function determines the size of the buffer from  
   // the SQL data type and parameter size returned by SQLDescribeParam and returns  
   // a pointer to the buffer and the length of the buffer.  
   AllocParamBuffer(DataType, ParamSize, &PtrArray[i], &BufferLenArray[i]);  
  
   // Bind the memory to the parameter. Assume that we only have input parameters.  
   SQLBindParameter(hstmt, i + 1, SQL_PARAM_INPUT, SQL_C_CHAR, DataType, ParamSize,  
         DecimalDigits, PtrArray[i], BufferLenArray[i],  
         &LenOrIndArray[i]);  
  
   // Prompt the user for the value of the parameter and store it in the memory  
   // allocated earlier. For simplicity, this function does not check the value  
   // against the information returned by SQLDescribeParam. Instead, the driver does  
   // this when the statement is executed.  
   GetParamValue(PtrArray[i], BufferLenArray[i], &LenOrIndArray[i]);  
   }  
}  
  
// Execute the statement.  
SQLExecute(hstmt);  
  
// Process the statement further, such as retrieving results (if any) and closing the  
// cursor (if any). Code not shown.  
  
// Free the memory allocated for each parameter and the memory allocated for the arrays  
// of pointers, buffer lengths, and length/indicator values.  
for (i = 0; i < NumParams; i++) free(PtrArray[i]);  
free(PtrArray);  
free(BufferLenArray);  
free(LenOrIndArray);  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Préparation d’une déclaration pour l’exécution|[Fonction SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
