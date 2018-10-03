---
title: Mappage des fonctions de remplacement pour la compatibilité des applications - ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping replacement functions [ODBC]
- upgrading applications [ODBC], mapping replacement functions
- compatibility [ODBC], mapping replacement functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], mapping replacement functions
- application upgrades [ODBC], mapping replacement functions
- backward compatibility [ODBC], mapping replacement functions
ms.assetid: f5e6d9da-76ef-42cb-b3f5-f640857df732
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cecc7fcd5ffa7234544dd0a9bc10407b1ea5cb1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626947"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Mappage des fonctions de remplacement pour la compatibilité descendante des applications
Un ODBC 3 *.x* application fonctionne via le ODBC 3 *.x* Gestionnaire de pilotes fonctionnera par rapport à une API ODBC 2. *x* pilote tant qu’aucune nouvelle fonctionnalité n’est utilisées. Les deux dupliquée des fonctionnalités et des changements de comportement, toutefois, affectent-elles la façon qui le ODBC 3. *x* application fonctionne sur un ODBC 2. *x* pilote. Lorsque vous travaillez avec un ODBC 2. *x* pilote, le Gestionnaire de pilotes mappe le suivantes ODBC 3. *x* fonctions qui ont remplacé un ou plusieurs ODBC 2. *x* les fonctions, en le correspondantes ODBC 2. *x* fonctions.  
  
|ODBC 3. *x* (fonction)|ODBC 2. *x* (fonction)|  
|-------------------------|-------------------------|  
|**SQLAllocHandle**|**SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt**|  
|**SQLBulkOperations**|**SQLSetPos**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransact**|  
|**SQLFetch**|**SQLExtendedFetch**|  
|**SQLFetchScroll**|**SQLExtendedFetch**|  
|**SQLFreeHandle**|**SQLFreeEnv**, **SQLFreeConnect**, ou **SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption**|  
|**SQLGetDiagRec**|**SQLError**|  
|**SQLGetStmtAttr**|**SQLGetStmtOption**[1]|  
|**SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [1] autres actions peuvent également être utilisées, en fonction de l’attribut demandé.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 Le Gestionnaire de pilotes le mappe à **SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt**, le cas échéant. L’appel suivant à **SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 entraîne dans le Gestionnaire de pilotes exécutant les opérations suivantes (conceptuel, aucune vérification des erreurs) mappage :  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 Le Gestionnaire de pilotes le mappe à **SQLSetPos**. L’appel suivant à **SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 entraîne la séquence d’étapes suivante :  
  
1.  Si l’argument de l’opération est SQL_ADD, le Gestionnaire de pilotes appelle **SQLSetPos** comme suit :  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Si l’argument de l’opération n’est pas SQL_ADD, le pilote retourne SQLSTATE HY092 (identificateur d’option/attribut non valide).  
  
3.  Si l’application tente de modifier le SQL_ATTR_ROW_STATUS_PTR entre les appels à **SQLFetch** ou **SQLFetchScroll** et **SQLBulkOperations**, sera le Gestionnaire de pilotes retourner SQLSTATE HY011 (attribut ne peut pas être défini maintenant).  
  
4.  Si l’argument de l’opération est SQL_ADD, l’application doit appeler **SQLBindCol** pour lier les données à insérer. Il ne peut pas appeler **SQLSetDescField** ou **SQLSetDescRec** pour lier les données à insérer.  
  
5.  Si l’argument de l’opération est SQL_ADD et le nombre de lignes à insérer n’est pas identique à la taille actuelle de l’ensemble de lignes, **SQLSetStmtAttr** doit être appelée pour définir l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE au nombre de lignes à être inséré avant d’appeler **SQLBulkOperations**. Pour revenir à la taille d’ensemble de lignes précédent, l’application doit définir l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE avant **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**est appelée.  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Le Gestionnaire de pilotes le mappe à **SQLColAttributes**. L’appel suivant à **SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 entraîne la séquence d’étapes suivante :  
  
1.  Si *FieldIdentifier* est une des opérations suivantes :  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX ou SQL_DESC_LOCAL_TYPE_NAME  
  
     le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE HY091 (identificateur de champ de descripteur non valide). Aucune autre règle de cette section s’appliquent.  
  
2.  Le Gestionnaire de pilotes mappe SQL_COLUMN_COUNT, SQL_COLUMN_NAME ou SQL_COLUMN_NULLABLE SQL_DESC_COUNT, SQL_DESC_NAME ou SQL_DESC_NULLABLE, respectivement. (Un ODBC 2 *.x* pilote devez prennent uniquement en charge SQL_COLUMN_COUNT SQL_COLUMN_NAME et SQL_COLUMN_NULLABLE, SQL_DESC_COUNT, SQL_DESC_NAME et non SQL_DESC_NULLABLE.) L’appel de SQLColAttribute est mappé à :  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Tous les autres *FieldIdentifier* valeurs sont transmises au pilote, avec **SQLColAttribute** mappé à **SQLColAttributes** comme indiqué précédemment.  
  
4.  Si *BufferLength* est inférieur à 0, le Gestionnaire de pilotes de retourne SQL_ERROR avec SQLSTATE HY090 (longueur de chaîne ou de mémoire tampon non valide). Aucune autre règle de cette section s’appliquent.  
  
5.  Si *FieldIdentifier* est SQL_DESC_CONCISE_TYPE et le type retourné est un type de données datetime concise, les mappages de gestionnaire de pilotes le retour des valeurs pour les codes de date, time et timestamp.  
  
6.  Le Gestionnaire de pilotes effectue les contrôles nécessaires pour voir si SQLSTATE HY010 (erreur de séquence de fonction) doit être déclenché. Si, par conséquent, le Gestionnaire de pilotes retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction). Aucune autre règle de cette section s’appliquent.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Le Gestionnaire de pilotes le mappe à **SQLTransact**. L’appel suivant à **SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 entraîne dans le Gestionnaire de pilotes exécutant les opérations suivantes (conceptuel, aucune vérification des erreurs) mappage :  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Le Gestionnaire de pilotes le mappe à **SQLExtendedFetch** avec un *FetchOrientation* argument de SQL_FETCH_NEXT. L’appel suivant à **SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 entraîne l’appel du Gestionnaire de pilotes **SQLExtendedFetch**, comme suit :  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 Dans cet appel, le *pcRow* argument est défini sur la valeur de l’application définit l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR à via un appel à **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Lorsque l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR pour pointer vers un tableau d’état, le Gestionnaire de pilotes met en cache le pointeur. *RowStatusArray* peut être égal à un pointeur null.  
  
 Si le pilote ne prend pas en charge **SQLExtendedFetch** et la bibliothèque de curseurs est chargée, le Gestionnaire de pilotes utilise la bibliothèque de curseurs **SQLExtendedFetch** pour mapper **SQLFetch** à **SQLExtendedFetch**. Si le pilote ne prend pas en charge **SQLExtendedFetch** et la bibliothèque de curseurs n’est pas chargée, le Gestionnaire de pilotes passe l’appel à **SQLFetch** par le biais du pilote. Si l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR, le Gestionnaire de pilotes permet de s’assurer que le tableau est rempli. Si l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROWS_FETCHED_PTR, le Gestionnaire de pilotes définit ce champ sur 1.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Le Gestionnaire de pilotes le mappe à **SQLExtendedFetch**. L’appel suivant à **SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 entraîne la séquence d’étapes suivante :  
  
1.  Lorsque l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR (qui définit le champ SQL_DESC_ARRAY_STATUS_PTR dans le descripteur IRD) pour pointer vers un tableau d’état, le Gestionnaire de pilotes met en cache ce pointeur. Soit ce pointeur *RowStatusArray*; sinon, laissez *RowStatusArray* égal à un pointeur null. Si le *RowStatusArray* argument est un pointeur null, le Gestionnaire de pilotes génère un tableau de l’état de ligne.  
  
2.  Si *FetchOrientation* ne fait pas partie de SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST ou SQL_FETCH_BOOKMARK, le Gestionnaire de pilotes retourne SQL_ERROR et SQLSTATE HY106 (type de récupération hors plage). Aucune autre règle de cette section s’appliquent.  
  
3.  Cas :  
  
-   Si *FetchOrientation* est égal à SQL_FETCH_BOOKMARK, puis :  
  
    -   Si **SQLSetStmtAttr** a été appelée précédemment pour définir la valeur de SQL_ATTR_FETCH_BOOKMARK_PTR, puis laissez *Bmk* la valeur obtenue par le pointeur SQL_DESC_FETCH_BOOKMARK_PTR.  
  
    -   Sinon, retourne SQL_ERROR avec SQLSTATE HY111 (valeur de signet non valide). Aucune autre règle de cette section s’appliquent.  
  
     Le Gestionnaire de pilotes appelle maintenant **SQLExtendedFetch**, comme suit :  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   Sinon, le Gestionnaire de pilotes appelle **SQLExtendedFetch**, comme suit :  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     Dans ces appels, la *pcRow* argument est défini sur la valeur de l’application définit l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR à via un appel à **SQLSetStmtAttr**.  
  
-   SQL_ATTR_ROW_ARRAY_SIZE est mappé à SQL_ROWSET_SIZE.  
  
-   Si *rc* est égale à SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO et si *FetchOrientation* est égal à SQL_FETCH_BOOKMARK et *FetchOffset* est différent de 0, puis le pilote Gestionnaire publie un avertissement, la valeur SQLSTATE 01S10 (tenter de récupérer par un offset du signet, valeur du décalage ignorée) et retourne SQL_SUCCESS_WITH_INFO.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Le Gestionnaire de pilotes le mappe à **SQLFreeEnv**, **SQLFreeConnect**, ou **SQLFreeStmt** selon le cas. L’appel suivant à **SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 entraîne dans le Gestionnaire de pilotes exécutant les opérations suivantes (conceptuel, aucune vérification des erreurs) mappage :  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Le Gestionnaire de pilotes le mappe à **SQLGetConnectOption**. L’appel suivant à **SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 entraîne la séquence d’étapes suivante :  
  
1.  Si *attribut* n’est pas un attribut de connexion ou d’instruction définis par le pilote et n’est pas un attribut défini dans ODBC 2. *x*, le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide). Aucune autre règle dans cette section s’appliquent.  
  
2.  Si *attribut* est égale à SQL_ATTR_AUTO_IPD ou SQL_ATTR_METADATA_ID, le Gestionnaire de pilotes de retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide).  
  
3.  Le Gestionnaire de pilotes effectue les contrôles nécessaires pour voir si SQLSTATE 08003 (connexion non ouverte) ou SQLSTATE HY010 (erreur de séquence de fonction) doit être déclenché. Dans ce cas, le Gestionnaire de pilotes retourne SQL_ERROR et publie le message d’erreur approprié. Aucune autre règle de cette section s’appliquent.  
  
4.  Les appels du Gestionnaire de pilotes **SQLGetConnectOption** comme suit :  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Notez que le *BufferLength* et *StringLengthPtr* sont ignorés.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Lorsqu’une application ODBC 3. *x* application fonctionne avec un ODBC 2 *.x* pilote appelle **SQLGetData** avec la *ColumnNumber* argument égal à 0, le Kit de développement ODBC 3 *.x* Gestionnaire de pilotes le mappe à un appel à **SQLGetStmtOption** avec la *Option* attribut la valeur SQL_GET_BOOKMARK.  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 Le Gestionnaire de pilotes le mappe à **SQLGetStmtOption**. L’appel suivant à **SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 entraîne la séquence d’étapes suivante :  
  
1.  Si *attribut* n’est pas un attribut de connexion ou d’instruction définis par le pilote et n’est pas un attribut défini dans ODBC 2. *x*, le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide). Aucune autre règle dans cette section s’appliquent.  
  
2.  Si *attribut* est une des opérations suivantes :  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide). Aucune autre règle de cette section s’appliquent.  
  
3.  Le Gestionnaire de pilotes effectue les contrôles nécessaires pour voir si SQLSTATE HY010 (erreur de séquence de fonction) doit être déclenché. Si, par conséquent, le Gestionnaire de pilotes retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction). Aucune autre règle de cette section s’appliquent.  
  
4.  Si *attribut* est égal à SQL_ATTR_ROWS_FETCHED_PTR, le Gestionnaire de pilotes retourne un pointeur à la variable de gestionnaire de pilotes interne *pattes*, qu’il a utilisé ou que vous utiliserez dans un appel à  **SQLExtendedFetch**. Aucune autre règle de cette section s’appliquent.  
  
5.  Si *attribut* est égal à SQL_DESC_FETCH_BOOKMARK_PTR, le Gestionnaire de pilotes retourne le pointeur approprié qui il avait mis en cache pendant un appel à **SQLSetStmtAttr**.  
  
6.  Si *attribut* est égal à SQL_ATTR_ROW_STATUS_PTR, le Gestionnaire de pilotes retourne le pointeur approprié qui il avait mis en cache pendant un appel à **SQLSetStmtAttr**.  
  
7.  Les appels du Gestionnaire de pilotes **SQLGetStmtOption** comme suit :  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     où *hstmt*, *fOption*, et *pvParam* sera défini sur les valeurs de *au paramètre StatementHandle*, *attribut*, et *ValuePtr*, respectivement. Le *BufferLength* et *StringLengthPtr* sont ignorés.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Le Gestionnaire de pilotes le mappe à **SQLSetConnectOption**. L’appel suivant à **SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 entraîne la séquence d’étapes suivante :  
  
1.  Si *attribut* n’est pas un attribut de connexion ou d’instruction définis par le pilote et n’est pas un attribut défini dans ODBC 2. *x*, le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide). Aucune autre règle dans cette section s’appliquent.  
  
2.  Si *attribut* est égal à SQL_ATTR_AUTO_IPD, le Gestionnaire de pilotes de retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide).  
  
3.  Le Gestionnaire de pilotes effectue les contrôles nécessaires pour voir si SQLSTATE 08003 (connexion non ouverte) ou SQLSTATE HY010 (erreur de séquence de fonction) devoir être déclenché. Si une de ces erreurs doit être déclenché, le Gestionnaire de pilotes retourne SQL_ERROR et publie le message d’erreur approprié. Aucune autre règle de cette section s’appliquent.  
  
4.  Les appels du Gestionnaire de pilotes **SQLSetConnectOption** comme suit :  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     où *pas*, *fOption*, et *vParam* sera défini sur les valeurs de *ConnectionHandle*, *attribut*, et *ValuePtr*, respectivement. *StringLengthPtr* est ignoré.  
  
> [!NOTE]  
>  Possibilité de définir des attributs d’instruction sur le niveau de la connexion a été déconseillée. Attributs d’instruction ne doivent jamais être définis sur le niveau de connexion par un ODBC 3. *x* application.  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Le Gestionnaire de pilotes le mappe à **SQLSetStmtOption**. L’appel suivant à **SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 entraîne la séquence d’étapes suivante :  
  
1.  Si *attribut* n’est pas un attribut de connexion ou d’instruction définis par le pilote et n’est pas un attribut défini dans ODBC 2. *x*, le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide). Aucune autre règle dans cette section s’appliquent.  
  
2.  Si *attribut* est une des opérations suivantes :  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide). Aucune autre règle de cette section s’appliquent.  
  
3.  Le Gestionnaire de pilotes effectue les vérifications nécessaires pour voir si SQLSTATE HY010 (erreur de séquence de fonction) devoir être déclenché. Si, par conséquent, le Gestionnaire de pilotes retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction). Aucune autre règle de cette section s’appliquent.  
  
4.  Si *attribut* est égal à SQL_ATTR_PARAMSET_SIZE ou SQL_ATTR_PARAMS_PROCESSED_PTR, consultez la section « Mappages pour gestion des tableaux de paramètres, » plus loin dans cette rubrique. Aucune autre règle de cette section s’appliquent.  
  
5.  Si *attribut* est égal à SQL_ATTR_ROWS_FETCHED_PTR, les caches de gestionnaire de pilotes que le pointeur de la valeur pour une utilisation ultérieure avec **SQLFetchScroll**.  
  
6.  Si *attribut* est égal à SQL_ATTR_ROW_STATUS_PTR, les caches de gestionnaire de pilotes que le pointeur de la valeur pour une utilisation ultérieure avec **SQLFetchScroll** ou **SQLSetPos**. Aucune autre règle de cette section s’appliquent.  
  
7.  Si *attribut* est égal à SQL_ATTR_FETCH_BOOKMARK_PTR, les caches de gestionnaire de pilotes *ValuePtr* et utilisera la valeur mise en cache plus loin dans un appel à **SQLFetchScroll**. Aucune autre règle de cette section s’appliquent.  
  
8.  Les appels du Gestionnaire de pilotes **SQLSetStmtOption** comme suit :  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     où *hstmt*, *fOption*, et *vParam* sera défini sur les valeurs de *au paramètre StatementHandle*, *attribut*, et *ValuePtr*, respectivement. Le *StringLength* argument est ignoré.  
  
     If un ODBC 2. *x* pilote prend en charge les options de l’instruction de chaîne de caractères, spécifiques au pilote, un ODBC 3. *x* application doit appeler **SQLSetStmtOption** pour définir ces options.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Mappages pour la gestion des tableaux de paramètres  
 Lorsque l’application appelle la méthode :  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 les appels du Gestionnaire de pilotes :  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Le Gestionnaire de pilotes une version ultérieure retourne un pointeur à cette variable lorsque l’application appelle **SQLGetStmtAttr** pour récupérer SQL_ATTR_PARAMS_PROCESSED_PTR. Le Gestionnaire de pilotes ne peut pas modifier cette variable interne jusqu'à ce que le descripteur d’instruction est retourné à l’état alloué ou préparé.  
  
 Une application ODBC 3. *x* application peut appeler **SQLGetStmtAttr** pour obtenir la valeur de SQL_ATTR_PARAMS_PROCESSED_PTR bien qu’il n’a pas explicitement défini le champ SQL_DESC_ARRAY_SIZE dans le descripteur APD. Cette situation peut se produire, par exemple, si l’application possède une routine générique qui vérifie la « ligne » de paramètres actuel en cours de traitement lorsque **SQLExecute** retourne SQL_NEED_DATA. Cette routine est appelée ou non le SQL_DESC_ARRAY_SIZE est 1 ou supérieur à 1. Pour éviter cela, le Gestionnaire de pilotes devez définir cette variable interne ou non l’application a appelé **SQLSetStmtAttr** pour définir le champ SQL_DESC_ARRAY_SIZE dans APD. Si SQL_DESC_ARRAY_SIZE n’a pas été définie, le Gestionnaire de pilotes doit s’assurer que cette variable contient la valeur 1 avant le retour à partir de **SQLExecDirect** ou **SQLExecute**.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Dans ODBC 3. *x*, l’appel **SQLFetch** ou **SQLFetchScroll** remplit le SQL_DESC_ARRAY_STATUS_PTR dans le descripteur IRD et le champ SQL_DIAG_ROW_NUMBER d’un enregistrement de diagnostic contient le numéro de la ligne dans l’ensemble de lignes appartenant à cet enregistrement. À l’aide de cela, l’application peut mettre en corrélation un message d’erreur avec une position de ligne donné.  
  
 Une application ODBC 2. *x* pilote sera incapable de fournir cette fonctionnalité. Toutefois, il fournira démarcation erreur avec 01 s 01 SQLSTATE (erreur de ligne). Une application ODBC 3. *x* application qui utilise **SQLFetch** ou **SQLFetchScroll** au cours par rapport à une API ODBC 2. *x* pilote doit être conscient de cette situation. Notez également que ce type d’application sera impossible d’appeler **SQLGetDiagField** afin d’obtenir réellement le champ SQL_DIAG_ROW_NUMBER quand même. Une application ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote sera en mesure d’appeler **SQLGetDiagField** uniquement avec un *DiagIdentifier* argument de SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE ou SQL_DIAG_ SQLSTATE. Le 3 ODBC *.x* Gestionnaire de pilotes conserve la structure de données de diagnostic lorsque vous travaillez avec un ODBC 2. *x* pilote, mais ODBC 2. *x* pilote retourne uniquement ces quatre champs.  
  
 Lorsqu’une application ODBC 2. *x* application fonctionne avec une API ODBC 2. *x* pilote, si une opération peut entraîner plusieurs erreurs renvoyées par le Gestionnaire de pilotes, différentes erreurs peuvent être renvoyés par la ODBC 3 *.x* Gestionnaire de pilotes que par ODBC 2. *x* Gestionnaire de pilotes.  
  
## <a name="mappings-for-bookmark-operations"></a>Mappages pour les opérations de signet  
 Le 3 ODBC *.x* Gestionnaire de pilotes effectue les mappages suivants lorsqu’un ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote effectue des opérations de signet.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Lorsqu’une application ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote appelle **SQLBindCol** pour lier à la colonne 0 avec *fCType* égal à SQL_C_VARBOOKMARK, les 3 ODBC *.x* vérifie Gestionnaire de pilotes Si le *BufferLength* argument est inférieur à 4 ou supérieure à 4 et si tel est le cas, retourne SQLSTATE HY090 (longueur de chaîne ou de mémoire tampon non valide). Si le *BufferLength* argument est égal à 4, le Gestionnaire de pilotes appelle **SQLBindCol** dans le pilote, après avoir remplacé *fCType* avec SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Lorsqu’une application ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote appelle **SQLColAttribute** avec la *ColumnNumber* argument la valeur 0, le Gestionnaire de pilote retourne la *FieldIdentifier* valeurs répertoriées dans le tableau suivant.  
  
|*FieldIdentifier*|Valeur|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (chaîne vide)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|La valeur retournée par **SQLNumResultCols**|  
|SQL_DESC_DATETIME_INTERVAL_CODE|0|  
|SQL_DESC_DISPLAY_SIZE|8|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|  
|SQL_DESC_LABEL|"" (chaîne vide)|  
|SQL_DESC_LENGTH|0|  
|SQL_DESC_LITERAL_PREFIX|"" (chaîne vide)|  
|SQL_DESC_LITERAL_SUFFIX|"" (chaîne vide)|  
|SQL_DESC_LOCAL_TYPE_NAME|"" (chaîne vide)|  
|SQL_DESC_NAME|"" (chaîne vide)|  
|SQL_DESC_NULLABLE|SQL_NO_NULLS|  
|SQL_DESC_OCTET_LENGTH|4|  
|SQL_DESC_PRECISION|4|  
|SQL_DESC_SCALE|0|  
|SQL_DESC_SCHEMA_NAME|"" (chaîne vide)|  
|SQL_DESC_SEARCHABLE|SQL_PRED_NONE|  
|SQL_DESC_TABLE_NAME|"" (chaîne vide)|  
|SQL_DESC_TYPE|SQL_BINARY|  
|SQL_DESC_TYPE_NAME|"" (chaîne vide)|  
|SQL_DESC_UNNAMED|VALEUR SQL_UNNAMED|  
|SQL_DESC_UNSIGNED|SQL_FALSE|  
|SQL_DESC_UPDATEABLE|SQL_ATTR_READ_ONLY|  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 Lorsqu’une application ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote appelle **SQLDescribeCol** avec la *ColumnNumber* argument la valeur 0, le Gestionnaire de pilotes retourne les valeurs répertoriées dans le tableau suivant.  
  
|Buffer|Valeur|  
|------------|-----------|  
|ColumnName|"" (chaîne vide)|  
|* NameLengthPtr|0|  
|* DataTypePtr|SQL_BINARY|  
|* ColumnSizePtr|4|  
|* DecimalDigitsPtr|0|  
|* NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Lorsqu’une application ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote effectue l’appel suivant à **SQLGetData** pour récupérer un signet :  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 l’appel est mappé à **SQLGetStmtOption** avec un *fOption* de SQL_GET_BOOKMARK, comme suit :  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 où *hstmt* et *pvParam* sont définies sur les valeurs dans *au paramètre StatementHandle* et *TargetValuePtr*, respectivement. Le signet est retourné dans la mémoire tampon vers laquelle pointée le *pvParam* (*TargetValuePtr*) argument. La valeur dans la mémoire tampon vers laquelle pointe le *StrLen_or_IndPtr* argument dans l’appel à **SQLGetData** est défini à 4.  
  
 Ce mappage est nécessaire pour prendre en compte le cas dans lequel **SQLFetch** a été appelé avant l’appel à **SQLGetData** et ODBC 2. *x* pilote ne prenait pas en charge **SQLExtendedFetch**. Dans ce cas, **SQLFetch** est repassée par ODBC 2. *x* pilote, dans lequel la récupération de signet cas n’est pas pris en charge.  
  
 **SQLGetData** ne peut pas être appelée plusieurs fois dans une API ODBC 2. *x* pilote de récupérer un signet en parties, ainsi, l’appel **SQLGetData** avec la *BufferLength* argument défini sur une valeur inférieure à 4 et le *ColumnNumber*argument la valeur 0 retourne SQLSTATE HY090 (longueur de chaîne ou de mémoire tampon non valide). **SQLGetData** peuvent, toutefois, être appelée plusieurs fois pour récupérer le même signet.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Lorsqu’une application ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote appelle **SQLSetStmtAttr** pour définir l’attribut SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE, le Gestionnaire de pilotes affecte l’attribut SQL_UB_ON dans sous-jacent ODBC 2. *x* pilote.
