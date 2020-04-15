---
title: Cartographie des fonctions de remplacement pour la compatibilité des applications - ODBC ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18669fe9b6edbd39859166e382ad18d1b04a99a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301089"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Mappage des fonctions de remplacement pour la compatibilité descendante des applications
Une application ODBC *3.x* travaillant par l’intermédiaire de l’ODBC *3.x* Driver Manager travaillera contre un pilote ODBC *2.x* tant qu’aucune nouvelle fonctionnalité n’est utilisée. Les deux fonctionnalités dupliquées et les changements de comportement affectent cependant la façon dont l’application ODBC *3.x* fonctionne sur un pilote ODBC *2.x.* Lorsque vous travaillez avec un pilote ODBC *2.x,* le Driver Manager cartographie les fonctions suivantes ODBC *3.x,* qui ont remplacé une ou plusieurs fonctions ODBC *2.x,* dans les fonctions ODBC *2.x* correspondantes.  
  
|Fonction ODBC *3.x*|Fonction ODBC *2.x*|  
|-------------------------|-------------------------|  
|**SQLAllocHandle**|**SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt**|  
|**SQLBulkOperations (SQLBulkOperations)**|**SQLSetPos**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransacte**|  
|**SQLFetch**|**SQLExtendedFetch**|  
|**SQLFetchScroll**|**SQLExtendedFetch**|  
|**SQLFreeHandle**|**SQLFreeEnv**, **SQLFreeConnect**, ou **SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption (SQLGetConnectOption)**|  
|**SQLGetDiagRec**|**Sqlerror**|  
|**SQLGetStmtAttr**|**SQLGetStmtOption**[1]|  
|**SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [1] D’autres mesures pourraient également être prises, selon l’attribut demandé.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 Le Driver Manager le cartographie à **SQLAllocEnv**, **SQLAllocConnect**, ou **SQLAllocStmt**, le cas échéant. L’appel suivant à **SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 entraînera la cartographie suivante (conceptuelle, aucune vérification des erreurs) :  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations (SQLBulkOperations)  
 Le Driver Manager en fait la carte à **SQLSetPos**. L’appel suivant à **SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 se traduira par la séquence suivante d’étapes :  
  
1.  Si l’argument de l’opération est SQL_ADD, le gestionnaire de conducteur appelle **SQLSetPos** comme suit :  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Si l’argument de l’opération n’est pas SQL_ADD, le conducteur retourne SQLSTATE HY092 (identification d’attribut/option invalide).  
  
3.  Si la demande tente de modifier la SQL_ATTR_ROW_STATUS_PTR entre les appels vers **SQLFetch** ou **SQLFetchScroll** et **SQLBulkOperations**, le gestionnaire de conducteur retournera SQLSTATE HY011 (Attribut ne peut pas être réglé dès maintenant).  
  
4.  Si l’argument de l’opération est SQL_ADD, l’application doit appeler **SQLBindCol** pour lier les données à insérer. Il ne peut pas appeler **SQLSetDescField** ou **SQLSetDescRec** pour lier les données à insérer.  
  
5.  Si l’argument de l’opération est SQL_ADD et que le nombre de lignes à insérer n’est pas le même que la taille actuelle du ramage, **SQLSetStmtAttr** doit être appelé à définir l’attribut de SQL_ATTR_ROW_ARRAY_SIZE déclaration au nombre de lignes à insérer avant d’appeler **SQLBulkOperations**. Pour revenir à la taille précédente de rowset, l’application doit définir l’attribut de SQL_ATTR_ROW_ARRAY_SIZE déclaration avant **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos** est appelé.  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Le Driver Manager le cartographie à **SQLColAttributes**. L’appel suivant à **SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 se traduira par la séquence suivante d’étapes :  
  
1.  Si *FieldIdentifier* est l’un des éléments suivants :  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX ou SQL_DESC_LOCAL_TYPE_NAME  
  
     le Driver Manager retourne SQL_ERROR avec SQLSTATE HY091 (identificateur de champ descripteur invalide). Aucune autre règle de cet article ne s’applique.  
  
2.  Le Driver Manager cartographie SQL_COLUMN_COUNT, SQL_COLUMN_NAME ou SQL_COLUMN_NULLABLE pour SQL_DESC_COUNT, SQL_DESC_NAME ou SQL_DESC_NULLABLE, respectivement. (Un conducteur ODBC *2.x* n’a besoin que d’SQL_COLUMN_COUNT de soutien, de SQL_COLUMN_NAME et de SQL_COLUMN_NULLABLE, et non de SQL_DESC_COUNT, de SQL_DESC_NAME et de SQL_DESC_NULLABLE.) L’appel à SQLColAttribute est cartographié pour :  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Toutes les autres valeurs *fieldIdentifier* sont transmises au conducteur, avec **SQLColAttribute** cartographié à **SQLColAttributes** comme indiqué précédemment.  
  
4.  Si *BufferLength* est inférieur à 0, le Driver Manager retourne SQL_ERROR avec SQLSTATE HY090 (longueur de chaîne ou tampon invalide). Aucune autre règle de cet article ne s’applique.  
  
5.  Si *FieldIdentifier* est SQL_DESC_CONCISE_TYPE et que le type retourné est un type de données de date concise, le Gestionnaire de pilote cartographie les valeurs de retour pour les codes de date, d’heure et d’heure.  
  
6.  Le gestionnaire de conducteur effectue les vérifications nécessaires pour voir si SQLSTATE HY010 (erreur de séquence de fonction) doit être soulevée. Si c’est le cas, le gestionnaire de conducteur retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction). Aucune autre règle de cet article ne s’applique.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Le Driver Manager le cartographie à **SQLTransact**. L’appel suivant à **SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 entraînera la cartographie suivante (conceptuelle, aucune vérification des erreurs) :  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Le gestionnaire de chauffeur en fait la carte à **SQLExtendedFetch** avec un argument *de fetchOrientation* de SQL_FETCH_NEXT. L’appel suivant à **SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 entraînera l’appel du gestionnaire de conducteur **SQLExtendedFetch**, comme suit :  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 Dans cet appel, l’argument *de pcRow* est réglé à la valeur que l’application définit l’attribut SQL_ATTR_ROWS_FETCHED_PTR déclaration à par un appel à **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Lorsque l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR pour indiquer un tableau d’état, le Gestionnaire de conducteur cache le pointeur. *RowStatusArray* peut être égal à un pointeur nul.  
  
 Si le conducteur n’appuie pas **SQLExtendedFetch** et que la bibliothèque de curseurs est chargée, le gestionnaire de conducteur utilise le **SQLExtendedFetch** de la bibliothèque de curseurs pour cartographier **SQLFetch** à **SQLExtendedFetch.** Si le conducteur n’appuie pas **SQLExtendedFetch** et que la bibliothèque de curseurs n’est pas chargée, le gestionnaire du conducteur passe **l’appel au SQLFetch** au conducteur. Si l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR, le gestionnaire de conducteur s’assure que le tableau est peuplé. Si l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROWS_FETCHED_PTR, le Driver Manager définit ce champ à 1.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Le Driver Manager en fait la carte à **SQLExtendedFetch**. L’appel suivant à **SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 se traduira par la séquence suivante d’étapes :  
  
1.  Lorsque l’application appelle **SQLSetStmtAttr** pour définir SQL_ATTR_ROW_STATUS_PTR (qui définit le champ SQL_DESC_ARRAY_STATUS_PTR dans l’IRD) pour indiquer un tableau de statut, le Driver Manager cache ce pointeur. Que ce pointeur soit *RowStatusArray*; sinon, que *RowStatusArray* soit égal à un pointeur nul. Si l’argument *RowStatusArray* est réglé sur un pointeur nul, le Gestionnaire de pilote génère un tableau de statut de ligne.  
  
2.  Si *FetchOrientation* n’est pas l’un des SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST ou SQL_FETCH_BOOKMARK, le Gestionnaire de conducteur revient avec SQL_ERROR et SQLSTATE HY106 (type Aller hors de portée). Aucune autre règle de cet article ne s’applique.  
  
3.  Casse :  
  
-   Si *FetchOrientation* est égal à SQL_FETCH_BOOKMARK, alors :  
  
    -   Si **SQLSetStmtAttr** a été appelé plus tôt pour définir la valeur de SQL_ATTR_FETCH_BOOKMARK_PTR, alors laissez *Bmk* être la valeur obtenue en reportant le pointeur SQL_DESC_FETCH_BOOKMARK_PTR.  
  
    -   Sinon, retour SQL_ERROR avec SQLSTATE HY111 (valeur de signet invalide). Aucune autre règle de cet article ne s’applique.  
  
     Le gestionnaire de chauffeur appelle maintenant **SQLExtendedFetch**, comme suit:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   Sinon, le gestionnaire de conducteur appelle **SQLExtendedFetch**, comme suit:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     Dans ces appels, l’argument *de pcRow* est réglé à la valeur que l’application définit l’attribut SQL_ATTR_ROWS_FETCHED_PTR déclaration à par un appel à **SQLSetStmtAttr**.  
  
-   SQL_ATTR_ROW_ARRAY_SIZE est cartographié pour SQL_ROWSET_SIZE.  
  
-   Si *rc* est égale à SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, et si *FetchOrientation* est égal à SQL_FETCH_BOOKMARK et *FetchOffset* n’est pas égal à 0, alors le gestionnaire de conducteur affiche un avertissement, SQLSTATE 01S10 (Tentative d’aller chercher par un décalage de signet, valeur offset ignorée), et retourne SQL_SUCCESS_WITH_INFO.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Le Driver Manager le cartographie à **SQLFreeEnv**, **SQLFreeConnect**, ou **SQLFreeStmt,** le cas échéant. L’appel suivant à **SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 entraînera la cartographie suivante (conceptuelle, aucune vérification des erreurs) :  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Le Driver Manager en fait la carte à **SQLGetConnectOption**. L’appel suivant à **SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 se traduira par la séquence suivante d’étapes :  
  
1.  Si *l’attribut n’est* pas un attribut de connexion ou de relevé défini par le conducteur et n’est pas un attribut défini dans ODBC *2.x*, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’attribut/option invalide). Aucune autre règle dans cette section ne s’applique.  
  
2.  Si *l’attribut* est égal à SQL_ATTR_AUTO_IPD ou SQL_ATTR_METADATA_ID, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE HY092 (identification d’attribut/option invalide).  
  
3.  Le gestionnaire de conducteur effectue les vérifications nécessaires pour voir si SQLSTATE 08003 (connexion non ouverte) ou SQLSTATE HY010 (erreur de séquence de fonction) doit être soulevée. Si c’est le cas, le gestionnaire de conducteur renvoie SQL_ERROR et affiche le message d’erreur approprié. Aucune autre règle de cet article ne s’applique.  
  
4.  Le gestionnaire de chauffeur appelle **SQLGetConnectOption** comme suit :  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Notez que les *BufferLength* et *StringLengthPtr* sont ignorés.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Lorsqu’une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* appelle **SQLGetData** avec *l’argument De ColumnNumber* égal à 0, l’ODBC *3.x* Driver Manager le fait un appel à **SQLGetStmtOption** avec *l’attribut Option* réglé pour SQL_GET_BOOKMARK.  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 Le Driver Manager le cartographie à **SQLGetStmtOption**. L’appel suivant à **SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 se traduira par la séquence suivante d’étapes :  
  
1.  Si *l’attribut n’est* pas un attribut de connexion ou de relevé défini par le conducteur et n’est pas un attribut défini dans ODBC *2.x*, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’attribut/option invalide). Aucune autre règle dans cette section ne s’applique.  
  
2.  Si *l’attribut* est l’un des éléments suivants :  
  
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
  
     le Driver Manager retourne SQL_ERROR avec SQLSTATE HY092 (identification d’attribut/option invalide). Aucune autre règle de cet article ne s’applique.  
  
3.  Le gestionnaire de conducteur effectue les vérifications nécessaires pour voir si SQLSTATE HY010 (erreur de séquence de fonction) doit être soulevée. Si c’est le cas, le gestionnaire de conducteur retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction). Aucune autre règle de cet article ne s’applique.  
  
4.  Si *l’attribut* est égal à SQL_ATTR_ROWS_FETCHED_PTR, le gestionnaire de conducteur retourne un pointeur à la *cRow*variable interne de gestionnaire de conducteur , qu’il a utilisée ou utilisera dans un appel à **SQLExtendedFetch**. Aucune autre règle de cet article ne s’applique.  
  
5.  Si *l’attribut* est égal à SQL_DESC_FETCH_BOOKMARK_PTR, le gestionnaire de conducteur retourne le pointeur approprié qu’il avait mis en cache lors d’un appel à **SQLSetStmtAttr**.  
  
6.  Si *l’attribut* est égal à SQL_ATTR_ROW_STATUS_PTR, le gestionnaire de conducteur retourne le pointeur approprié qu’il avait mis en cache lors d’un appel à **SQLSetStmtAttr**.  
  
7.  Le gestionnaire de conducteur appelle **SQLGetStmtOption** comme suit :  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     où *hstmt*, *fOption*, et *pvParam* seront réglés sur les valeurs de *StatementHandle*, *Attribut*, et *ValuePtr*, respectivement. Les *BufferLength* et *StringLengthPtr* sont ignorés.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Le Driver Manager en fait la carte à **SQLSetConnectOption**. L’appel suivant à **SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 se traduira par la séquence suivante d’étapes :  
  
1.  Si *l’attribut n’est* pas un attribut de connexion ou de relevé défini par le conducteur et n’est pas un attribut défini dans ODBC *2.x*, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’attribut/option invalide). Aucune autre règle dans cette section ne s’applique.  
  
2.  Si *l’attribut* est égal à SQL_ATTR_AUTO_IPD, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE HY092 (identification d’attribut/option invalide).  
  
3.  Le gestionnaire de conducteur effectue les vérifications nécessaires pour voir si SQLSTATE 08003 (connexion non ouverte) ou SQLSTATE HY010 (erreur de séquence de fonction) doivent être soulevées. Si l’une de ces erreurs doit être soulevée, le gestionnaire de pilote renvoie SQL_ERROR et affiche le message d’erreur approprié. Aucune autre règle de cet article ne s’applique.  
  
4.  Le gestionnaire de chauffeur appelle **SQLSetConnectOption** comme suit :  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     où *hdbc*, *fOption*, et *vParam* seront mis aux valeurs de *ConnectionHandle*, *Attribut*, et *ValuePtr*, respectivement. *StringLengthPtr* est ignoré.  
  
> [!NOTE]  
>  La capacité de définir les attributs des relevés sur le niveau de connexion a été amortie. Les attributs de déclaration ne doivent jamais être définis au niveau de connexion par une application ODBC *3.x.*  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Le Driver Manager le cartographie à **SQLSetStmtOption**. L’appel suivant à **SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 se traduira par la séquence suivante d’étapes :  
  
1.  Si *l’attribut n’est* pas un attribut de connexion ou de relevé défini par le conducteur et n’est pas un attribut défini dans ODBC *2.x*, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’attribut/option invalide). Aucune autre règle dans cette section ne s’applique.  
  
2.  Si *l’attribut* est l’un des éléments suivants :  
  
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
  
     le Driver Manager retourne SQL_ERROR avec SQLSTATE HY092 (identification d’attribut/option invalide). Aucune autre règle de cet article ne s’applique.  
  
3.  Le gestionnaire de conducteur effectue les vérifications nécessaires pour voir si SQLSTATE HY010 (erreur de séquence de fonction) doit être soulevée. Si c’est le cas, le gestionnaire de conducteur retourne SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction). Aucune autre règle de cet article ne s’applique.  
  
4.  Si *l’attribut* est égal à SQL_ATTR_PARAMSET_SIZE ou SQL_ATTR_PARAMS_PROCESSED_PTR, voir la section «Cartographies pour la manipulation des paramètres Arrays», plus tard dans ce sujet. Aucune autre règle de cet article ne s’applique.  
  
5.  Si *l’attribut* est égal à SQL_ATTR_ROWS_FETCHED_PTR, le Driver Manager cache la valeur de pointeur pour une utilisation ultérieure avec **SQLFetchScroll**.  
  
6.  Si *l’attribut* est égal à SQL_ATTR_ROW_STATUS_PTR, le Driver Manager cache la valeur de pointeur pour une utilisation ultérieure avec **SQLFetchScroll** ou **SQLSetPos**. Aucune autre règle de cet article ne s’applique.  
  
7.  Si *l’attribut* est égal à SQL_ATTR_FETCH_BOOKMARK_PTR, le gestionnaire de pilote cache *ValuePtr* et utilisera la valeur mise en cache plus tard dans un appel à **SQLFetchScroll**. Aucune autre règle de cet article ne s’applique.  
  
8.  Le gestionnaire de conducteur appelle **SQLSetStmtOption** comme suit :  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     où *hstmt*, *fOption*, et *vParam* seront mis aux valeurs de *StatementHandle*, *Attribut*, et *ValuePtr*, respectivement. *L’argument stringLength* est ignoré.  
  
     Si un pilote ODBC *2.x* prend en charge les options de relevés spécifiques à la chaîne de caractères, une application ODBC *3.x* devrait appeler **SQLSetStmtOption** pour définir ces options.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Cartographies pour la manipulation des paramètres  
 Lorsque l’application appelle :  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 le Driver Manager appelle :  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Le gestionnaire de conducteur renvoie plus tard un pointeur à cette variable lorsque l’application appelle **SQLGetStmtAttr** pour récupérer SQL_ATTR_PARAMS_PROCESSED_PTR. Le gestionnaire de conducteur ne peut pas modifier cette variable interne tant que la poignée de déclaration n’est pas retournée à l’état préparé ou attribué.  
  
 Une application ODBC *3.x* peut appeler **SQLGetStmtAttr** pour obtenir la valeur de SQL_ATTR_PARAMS_PROCESSED_PTR même si elle n’a pas explicitement mis le champ SQL_DESC_ARRAY_SIZE dans l’APD. Cette situation pourrait survenir, par exemple, si la demande a une routine générique qui vérifie la « rangée » actuelle des paramètres traités lorsque **SQLExecute** retourne SQL_NEED_DATA. Cette routine est invoquée, que le SQL_DESC_ARRAY_SIZE soit ou non supérieur à 1. Pour en tenir compte, le gestionnaire de conducteur devra définir cette variable interne, que l’application ait appelé **SQLSetStmtAttr** pour définir le champ SQL_DESC_ARRAY_SIZE dans APD. Si SQL_DESC_ARRAY_SIZE n’a pas été réglée, le gestionnaire de conducteur doit s’assurer que cette variable contient la valeur 1 avant de revenir de **SQLExecDirect** ou **SQLExecute**.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Dans ODBC *3.x*, appelant **SQLFetch** ou **SQLFetchScroll** peuple les SQL_DESC_ARRAY_STATUS_PTR de l’IRD, et le champ SQL_DIAG_ROW_NUMBER d’un dossier diagnostique donné contient le nombre de la rangée dans le ramage que ce dossier se rapporte. En utilisant cela, l’application peut corréler un message d’erreur avec une position de ligne donnée.  
  
 Un pilote ODBC *2.x* ne sera pas en mesure de fournir cette fonctionnalité. Toutefois, il fournira la démarcation d’erreur avec SQLSTATE 01S01 (Erreur de ligne). Une application ODBC *3.x* qui utilise **SQLFetch** ou **SQLFetchScroll** tout en allant à l’encontre d’un conducteur ODBC *2.x* doit être conscient de ce fait. Notez également qu’une telle application ne sera pas en mesure d’appeler **SQLGetDiagField** pour réellement obtenir le champ SQL_DIAG_ROW_NUMBER de toute façon. Une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* ne pourra appeler **SQLGetDiagField** qu’avec un argument *diagIdentificateur* de SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE ou SQL_DIAG_SQLSTATE. L’ODBC *3.x* Driver Manager maintient la structure de données diagnostiques lorsqu’il travaille avec un pilote ODBC *2.x,* mais le pilote ODBC *2.x* ne retourne que ces quatre champs.  
  
 Lorsqu’une application ODBC *2.x* fonctionne avec un pilote ODBC *2.x,* si une opération peut causer plusieurs erreurs pour être retournée par le gestionnaire de conducteur, différentes erreurs peuvent être retournées par le gestionnaire de conducteur ODBC *3.x* que par l’ODBC *2.x* Driver Manager.  
  
## <a name="mappings-for-bookmark-operations"></a>Cartographies pour les opérations de signets  
 L’ODBC *3.x* Driver Manager effectue les cartes suivantes lorsqu’une application ODBC *3.x* travaillant avec un pilote ODBC *2.x* effectue des opérations de signets.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Lorsqu’une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* appelle **SQLBindCol** pour se lier à la colonne 0 avec *fCType* égale à SQL_C_VARBOOKMARK, l’ODBC *3.x* Driver Manager vérifie si l’argument *De BufferLength* est inférieur à 4 ou plus de 4, et si oui, retourne SQLSTATE HY090 (longueur de chaîne ou tampon invalide). Si l’argument *de BufferLength* est égal à 4, le gestionnaire de conducteur appelle **SQLBindCol** dans le conducteur, après avoir remplacé *fCType* par SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Lorsqu’une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* appelle **SQLColAttribute** avec *l’argument De ColumnNumber* réglé à 0, le gestionnaire de conducteur renvoie les valeurs *FieldIdentifier* énumérées dans le tableau suivant.  
  
|*FieldIdentifier*|Value|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (chaîne vide)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|La même valeur retournée par **SQLNumResultCols**|  
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
|SQL_DESC_UNNAMED|SQL_UNNAMED|  
|SQL_DESC_UNSIGNED|SQL_FALSE|  
|SQL_DESC_UPDATEABLE|SQL_ATTR_READ_ONLY|  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 Lorsqu’une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* appelle **SQLDescribeCol** avec *l’argument De ColumnNumber* réglé à 0, le gestionnaire de conducteur retourne les valeurs énumérées dans le tableau suivant.  
  
|Buffer|Value|  
|------------|-----------|  
|ColumnName|"" (chaîne vide)|  
|NomLengthPtr|0|  
|DataTypePtr|SQL_BINARY|  
|-ColumnSizePtr|4|  
|-DécimadigitsPtr|0|  
|NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Lorsqu’une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* passe l’appel suivant à **SQLGetData** pour récupérer un signet :  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 l’appel est cartographié à **SQLGetStmtOption** avec une *fOption* de SQL_GET_BOOKMARK, comme suit:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 où *hstmt* et *pvParam* sont fixés aux valeurs dans *StatementHandle* et *TargetValuePtr*, respectivement. Le signet est retourné dans le tampon pointé vers l’argument *pvParam* (*TargetValuePtr*). La valeur dans le tampon indiqué par *l’argument StrLen_or_IndPtr* dans l’appel à **SQLGetData** est réglée 4.  
  
 Cette cartographie est nécessaire pour tenir compte du cas dans lequel **SQLFetch** a été appelé avant l’appel à **SQLGetData** et le conducteur ODBC *2.x* n’a pas pris en charge **SQLExtendedFetch**. Dans ce cas, **SQLFetch** serait transmis au conducteur ODBC *2.x,* auquel cas la récupération de signets n’est pas prise en charge.  
  
 **SQLGetData** ne peut pas être appelé plusieurs fois dans un pilote ODBC *2.x* pour récupérer un signet dans les pièces, donc appeler **SQLGetData** avec *l’argument BufferLength* réglé à une valeur inférieure à 4 et *l’argument ColumnNumber* réglé à 0 retournera SQLSTATE HY090 (durée de la chaîne invalide ou tampon). **SQLGetData** peut cependant être appelé plusieurs fois pour récupérer le même signet.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Lorsqu’une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* appelle **SQLSetStmtAttr** pour définir l’attribut SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE, le Gestionnaire de conducteur définit l’attribut à SQL_UB_ON dans le conducteur sous-jacent ODBC *2.x.*
