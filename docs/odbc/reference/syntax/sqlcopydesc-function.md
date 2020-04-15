---
title: Fonction SQLCopyDesc (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef1fa5b319e8d72d5b70e6f2010e493eec6f844a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301226"
---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc, fonction
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLCopyDesc** copie les informations descripteur d’une poignée descripteur à une autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *SourceDescHandle*  
 [Entrée] Poignée source descripteur.  
  
 *TargetDescHandle (en)*  
 [Entrée] Poignée descripteur cible. *L’argument De TargetDescHandle* peut être une poignée à un descripteur d’application ou un IPD. *TargetDescHandle* ne peut pas être réglé à une poignée à un IRD, ou **SQLCopyDesc** retournera SQLSTATE HY016 (Ne peut pas modifier un descripteur de ligne d’implémentation).  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLCopyDesc** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DESC et une *poignée* de *TargetDescHandle*. Si une *SourceDescHandle* invalide a été adoptée dans l’appel, SQL_INVALID_HANDLE sera retourné, mais aucun SQLSTATE ne sera retourné. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLCopyDesc** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
 Lorsqu’une erreur est retournée, l’appel à **SQLCopyDesc** est immédiatement avorté, et le contenu des champs du descripteur *TargetDescHandle* n’est pas défini.  
  
 Étant donné que **SQLCopyDesc** peut être mis en œuvre en appelant **SQLGetDescField** et **SQLSetDescField**, **SQLCopyDesc** peut retourner SQLSTATEs retournés par **SQLGetDescField** ou **SQLSetDescField**.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire requise pour supporter l’exécution ou l’achèvement de la fonction.|  
|HY007|Déclaration associée n’est pas préparée|*SourceDescHandle* était associé à un IRD, et la poignée de déclaration associée n’était pas dans l’état préparé ou exécuté.|  
|HY010|Erreur de séquence de fonction|(DM) La poignée descripteur dans *SourceDescHandle* ou *TargetDescHandle* a été associée à un *StatementHandle* pour lequel une fonction d’exécution asynchrone (pas celle-ci) a été appelée et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) La poignée descripteur dans *SourceDescHandle* ou *TargetDescHandle* a été associée à un *StatementHandle* pour lequel **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *SourceDescHandle* ou *TargetDescHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLCopyDesc** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour l’une des poignées de déclaration associées à la *SourceDescHandle* ou *TargetDescHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY016|Impossible de modifier un descripteur de ligne de mise en œuvre|*TargetDescHandle* était associé à un IRD.|  
|HY021|Informations descripteur incohérentes|Les renseignements descripteur vérifiés lors d’une vérification de cohérence n’étaient pas cohérents. Pour plus d’informations, voir "Vérifications de cohérence" dans **SQLSetDescField**.|  
|HY092 HY092|Identification d’attribut/option invalide|L’appel à **SQLCopyDesc** a suscité un appel à **SQLSetDescField**, mais * \*ValuePtr* n’était pas valide pour *l’argument FieldIdentifier* sur *TargetDescHandle*.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé à la *SourceDescHandle* ou *TargetDescHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Un appel à **SQLCopyDesc** copie les champs de la poignée source descripteur à la poignée du descripteur cible. Les champs ne peuvent être copiés qu’à un descripteur d’application ou à un IPD, mais pas à un IRD. Les champs peuvent être copiés à partir d’une application ou d’un descripteur de mise en œuvre.  
  
 Les champs ne peuvent être copiés à partir d’un IRD que si la poignée de déclaration se trouve dans l’état préparé ou exécuté; autrement, la fonction renvoie SQLSTATE HY007 (Déclaration associée n’est pas préparée).  
  
 Les champs peuvent être copiés à partir d’une DPI si oui ou non une déclaration a été préparée. Si une déclaration SQL avec des paramètres dynamiques a été préparée et que la population automatique de l’IPD est prise en charge et activée, alors la DPI est peuplée par le conducteur. Lorsque **SQLCopyDesc** est appelé avec l’IPD comme *sourceDescHandle*, les champs peuplés sont copiés. Si l’IPD n’est pas peuplé par le conducteur, le contenu des champs à l’origine dans l’IPD sont copiés.  
  
 Tous les champs du descripteur, à l’exception de SQL_DESC_ALLOC_TYPE (qui précise si la poignée du descripteur a été automatiquement ou explicitement allouée), sont copiées, que le champ soit défini ou non pour le descripteur de destination. Les champs copiés surmorment les champs existants.  
  
 Le conducteur copie tous les champs descripteur si les arguments *SourceDescHandle* et *TargetDescHandle* sont associés au même conducteur, même si les pilotes sont sur deux connexions ou environnements différents. Si les arguments *SourceDescHandle* et *TargetDescHandle* sont associés à différents conducteurs, le gestionnaire de conducteur copie les champs définis par ODBC, mais ne copie pas les champs ou les champs définis par le conducteur qui ne sont pas définis par ODBC pour le type de descripteur.  
  
 L’appel à **SQLCopyDesc** est avorté immédiatement en cas d’erreur.  
  
 Lorsque le champ SQL_DESC_DATA_PTR est copié, une vérification de cohérence est effectuée sur le descripteur cible. En cas d’échec de la vérification de cohérence, SQLSTATE HY021 (informations descripteur incohérentes) est retourné et l’appel à **SQLCopyDesc** est immédiatement avorté. Pour plus d’informations sur les contrôles de cohérence, voir "Vérifications de cohérence" dans [LA fonction SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Les poignées descripteur peuvent être copiées entre les connexions même si les connexions sont sous différents environnements. Si le gestionnaire de conducteur détecte que la source et les poignées descripteur de destination n’appartiennent pas à la même connexion et que les deux connexions appartiennent à des pilotes distincts, il implémente **SQLCopyDesc** en effectuant une copie champ par champ à l’aide **de SQLGetDescField** et **SQLSetDescField**.  
  
 Lorsque **SQLCopyDesc** est appelé avec un *SourceDescHandle* sur un conducteur et un *TargetDescHandle* sur un autre conducteur, la file d’attente d’erreur de la *SourceDescHandle* est effacée. Cela se produit parce que **SQLCopyDesc** dans ce cas est mis en œuvre par des appels à **SQLGetDescField** et **SQLSetDescField**.  
  
> [!NOTE]  
>  Une application pourrait être en mesure d’associer une poignée descripteur explicitement allouée à un *StatementHandle*, plutôt que d’appeler **SQLCopyDesc** pour copier les champs d’un descripteur à un autre. Un descripteur explicitement attribué peut être associé à un autre *StatementHandle* sur le même *ConnectionHandle* en définissant l’attribut SQL_ATTR_APP_ROW_DESC ou SQL_ATTR_APP_PARAM_DESC déclaration à la poignée du descripteur explicitement attribué. Lorsque cela est fait, **SQLCopyDesc** n’a pas besoin d’être appelé à copier les valeurs de champ descripteur d’un descripteur à l’autre. Une poignée descripteur ne peut pas être associée à un *StatementHandle* sur un autre *ConnectionHandle*, cependant; pour utiliser les mêmes valeurs de champ descripteur sur *StatementHandles* sur différents *ConnectionHandles*, **SQLCopyDesc** doit être appelé.  
  
 Pour une description des champs dans un en-tête ou un enregistrement descripteur, voir [SQLSetDescField Fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Pour plus d’informations sur les descripteurs, voir [Descriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="copying-rows-between-tables"></a>Copier les rangées entre les tables  
 Une application peut copier des données d’une table à l’autre sans copier les données au niveau de l’application. Pour ce faire, l’application lie les mêmes tampons de données et les mêmes informations descripteur à une déclaration qui récupère les données et l’instruction qui insère les données dans une copie. Cela peut être fait soit en partageant un descripteur d’application (contraignant un descripteur explicitement attribué à la fois comme l’ARD à une déclaration et l’APD dans un autre) ou en utilisant **SQLCopyDesc** pour copier les liaisons entre l’ARD et l’APD des deux déclarations. Si les déclarations sont sur différentes connexions, **SQLCopyDesc** doit être utilisé. De plus, **SQLCopyDesc** doit être appelé à copier les liaisons entre l’IRD et l’IPD des deux déclarations. Lors de la copie à travers les déclarations sur la même connexion, le type d’information SQL_ACTIVE_STATEMENTS retourné par le conducteur pour un appel à **SQLGetInfo** doit être supérieur à 1 pour que cette opération réussisse. (Ce n’est pas le cas lors de la copie entre les connexions.)  
  
### <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, les opérations descripteur sont utilisées pour copier les champs de la table PartsSource dans la table PartsCopy. Le contenu de la table PartsSource est récupéré dans des tampons en rangée dans *hstmt0*. Ces valeurs sont utilisées comme paramètres d’une déclaration INSERT sur *hstmt1* pour remplir les colonnes de la table PartsCopy. Pour ce faire, les champs de l’IRD de *hstmt0* sont copiés sur les champs de l’IPD de *hstmt1*, et les champs de l’ARD de *hstmt0* sont copiés sur les champs de l’APD de *hstmt1*. Utilisez **SQLSetDescField** pour définir l’attribut SQL_DESC_PARAMETER_TYPE de l’IPD à SQL_PARAM_INPUT lorsque vous copiez les champs IRD à partir d’une déclaration avec des paramètres de sortie aux champs IPD qui doivent être des paramètres d’entrée.  
  
```cpp  
#define ROWS 100  
#define DESC_LEN 50  
#define SQL_SUCCEEDED(rc) (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)  
  
// Template for a row  
typedef struct {  
   SQLINTEGER   sPartID;  
   SQLINTEGER   cbPartID;  
   SQLUCHAR     szDescription[DESC_LENGTH];  
   SQLINTEGER   cbDescription;  
   REAL         sPrice;  
   SQLINTEGER   cbPrice;  
} PartsSource;  
  
PartsSource    rget[ROWS];          // rowset buffer  
SQLUSMALLINT   sts_ptr[ROWS];       // status pointer  
SQLHSTMT       hstmt0, hstmt1;  
SQLHDESC       hArd0, hIrd0, hApd1, hIpd1;  
  
// ARD and IRD of hstmt0  
SQLGetStmtAttr(hstmt0, SQL_ATTR_APP_ROW_DESC, &hArd0, 0, NULL);  
SQLGetStmtAttr(hstmt0, SQL_ATTR_IMP_ROW_DESC, &hIrd0, 0, NULL);  
  
// APD and IPD of hstmt1  
SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_PARAM_DESC, &hApd1, 0, NULL);  
SQLGetStmtAttr(hstmt1, SQL_ATTR_IMP_PARAM_DESC, &hIpd1, 0, NULL);  
  
// Use row-wise binding on hstmt0 to fetch rows  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER) sizeof(PartsSource), 0);  
  
// Set rowset size for hstmt0  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
  
// Execute a select statement  
SQLExecDirect(hstmt0, "SELECT PARTID, DESCRIPTION, PRICE FROM PARTS ORDER BY 3, 1, 2"",  
               SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt0, 1, SQL_C_SLONG, rget[0].sPartID, 0,   
   &rget[0].cbPartID);  
SQLBindCol(hstmt0, 2, SQL_C_CHAR, &rget[0].szDescription, DESC_LEN,   
   &rget[0].cbDescription);  
SQLBindCol(hstmt0, 3, SQL_C_FLOAT, rget[0].sPrice,   
   0, &rget[0].cbPrice);  
  
// Perform parameter bindings on hstmt1.   
SQLCopyDesc(hArd0, hApd1);  
SQLCopyDesc(hIrd0, hIpd1);  
  
// Set the array status pointer of IRD  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_STATUS_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the ARRAY_STATUS_PTR field of APD to be the same  
// as that in IRD.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_PARAM_OPERATION_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the hIpd1 records as input parameters  
rc = SQLSetDescField(hIpd1, 1, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 2, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 3, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
  
// Prepare an insert statement on hstmt1. PartsCopy is a copy of  
// PartsSource  
SQLPrepare(hstmt1, "INSERT INTO PARTS_COPY VALUES (?, ?, ?)", SQL_NTS);  
  
// In a loop, fetch a rowset, and copy the fetched rowset to PARTS_COPY  
  
rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
while (SQL_SUCCEEDED(rc)) {  
  
   // After the call to SQLFetchScroll, the status array has row   
   // statuses. This array is used as input status in the APD  
   // and hence determines which elements of the rowset buffer  
   // are inserted.  
   SQLExecute(hstmt1);  
  
   rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
} // while  
```  
  
### <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtenir plusieurs champs descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Mise en place d’un champ descripteur unique|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Réglage de plusieurs champs descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
