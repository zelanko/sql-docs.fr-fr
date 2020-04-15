---
title: Fonction SQLPutData (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPutData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPutData
helpviewer_keywords:
- SQLPutData function [ODBC]
ms.assetid: 9a60f004-1477-4c54-a20c-7378e1116713
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c4e704d96924942812904ea63d0e3d4fce8748e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300039"
---
# <a name="sqlputdata-function"></a>Fonction SQLPutData
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLPutData** permet à une application d’envoyer des données pour un paramètre ou une colonne au conducteur au moment de l’exécution de l’instruction. Cette fonction peut être utilisée pour envoyer des valeurs de caractère ou de données binaires en parties à une colonne avec un type de données spécifique à un personnage, binaire ou spécifique à la source de données (par exemple, les paramètres des types SQL_LONGVARBINARY ou SQL_LONGVARCHAR). **SQLPutData** prend en charge la liaison à un type de données Unicode C, même si le conducteur sous-jacent ne prend pas en charge les données Unicode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *DataPtr (en)*  
 [Entrée] Pointeur vers un tampon contenant les données réelles pour le paramètre ou la colonne. Les données doivent être du type de données C spécifiée dans *l’argument ValueType* de **SQLBindParameter** (pour les données de paramètres) ou de l’argument *TargetType* de **SQLBindCol** (pour les données de colonne).  
  
 *StrLen_or_Ind*  
 [Entrée] Longueur \*de *DataPtr*. Spécifie la quantité de données envoyées dans un appel à **SQLPutData**. La quantité de données peut varier avec chaque appel pour un paramètre ou une colonne donné. *StrLen_or_Ind* est ignorée à moins qu’elle ne réponde à l’une des conditions suivantes :  
  
-   *StrLen_or_Ind* est SQL_NTS, SQL_NULL_DATA ou SQL_DEFAULT_PARAM.  
  
-   Le type de données C spécifié dans **SQLBindParameter** ou **SQLBindCol** est SQL_C_CHAR ou SQL_C_BINARY.  
  
-   Le type de données C est SQL_C_DEFAULT, et le type de données C par défaut pour le type de données SQL spécifié est SQL_C_CHAR ou SQL_C_BINARY.  
  
 Pour tous les autres types de données C, si *StrLen_or_Ind* n’est pas SQL_NULL_DATA ou SQL_DEFAULT_PARAM, \*le conducteur suppose que la taille du tampon *DataPtr* est la taille du type de données C spécifié avec *ValueType* ou *TargetType* et envoie la valeur de données entière. Pour plus d’informations, voir [Convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) dans l’annexe D : Data Types.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLPutData** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLPutData** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données de chaîne ou binaires retournées pour un paramètre de sortie ont abouti à la troncation de caractères non-blank ou de données binaires non-NULL. Si c’était une valeur de chaîne, il était juste-tronqué. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|La valeur des données identifiée par *l’argument valueType* dans **SQLBindParameter** pour le paramètre lié n’a pas pu être convertie au type de données identifié par *l’argument de ParameterType* dans **SQLBindParameter**.|  
|07S01|Utilisation invalide du paramètre par défaut|Une valeur de paramètre, définie avec **SQLBindParameter**, a été SQL_DEFAULT_PARAM, et le paramètre correspondant n’avait pas de valeur par défaut.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22001|Données de chaîne, troncation droite|L’attribution d’un personnage ou d’une valeur binaire à une colonne a entraîné la troncation de caractères ou d’octets non-nulls (binaires).<br /><br /> Le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était « Y », et plus de données ont été envoyées pour un long paramètre (le type de données a été SQL_LONGVARCHAR, SQL_LONGVARBINARY, ou un type de données de données spécifiques à de longues sources de données) que ce qui a été spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**.<br /><br /> Le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était «Y», et plus de données ont été envoyées pour une longue colonne (le type de données a été SQL_LONGVARCHAR, SQL_LONGVARBINARY, ou un type de données spécifiques à la source de données longues) que ce qui a été spécifié dans le tampon de longueur correspondant à une colonne dans une rangée de données qui a été ajouté ou mis à jour avec **SQLBulkOperations** ou mis à jour avec **SQLSetPos**.|  
|22003|Valeur numérique hors de portée|Les données envoyées pour un paramètre ou une colonne numérique lié ont fait tronquer la partie entière (par opposition à fractionnelle) du nombre lorsqu’elle était affectée à la colonne de table associée.<br /><br /> Le retour d’une valeur numérique (en tant que numérique ou chaîne) pour un ou plusieurs paramètres d’entrée/sortie ou de sortie aurait fait tronquer l’ensemble (par opposition à la fractionnement) de la partie du nombre.|  
|22007|Format de date invalide|Les données envoyées pour un paramètre ou une colonne qui était lié à une date, l’heure ou une structure de timetamp était, respectivement, une date, une heure ou un fuseur horaires non valides.<br /><br /> Un paramètre d’entrée/sortie ou de sortie était lié à une structure de date, d’heure ou de timetamp C, et une valeur dans le paramètre retourné était, respectivement, une date, une heure ou un fuseur horaires non valides. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|22008|Débordement de champ datetime|Une expression de date calculée pour un paramètre d’entrée/sortie ou de sortie a donné lieu à une structure de date, d’heure ou de timetamp C qui était invalide.|  
|22012|Division par zéro|Une expression arithmétique calculée pour un paramètre d’entrée/sortie ou de sortie a entraîné une division par zéro.|  
|22015|Débordement de champ d’intervalle|Les données envoyées pour une colonne ou un paramètre numérique ou d’intervalle exact à un type de données SQL d’intervalle ont causé une perte de chiffres significatifs.<br /><br /> Les données ont été envoyées pour une colonne d’intervalle ou un paramètre avec plus d’un champ, ont été converties en type de données numériques et n’avaient aucune représentation dans le type de données numériques.<br /><br /> Les données envoyées pour les données de colonne ou de paramètre ont été attribuées à un type SQL d’intervalle, et il n’y avait aucune représentation de la valeur du type C dans le type SQL d’intervalle.<br /><br /> Les données envoyées pour une colonne numérique ou d’intervalle C exacte ou un paramètre à un type d’intervalle C ont causé une perte de chiffres significatifs.<br /><br /> Les données envoyées pour les données de colonne ou de paramètre ont été attribuées à une structure d’intervalle C, et il n’y avait aucune représentation des données dans la structure de données d’intervalle.|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|Le type C était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type SQL de la colonne était un type de données de caractère; et la valeur de la colonne ou du paramètre n’était pas un littéral valide du type C lié.<br /><br /> Le type SQL était un numérique exact ou approximatif, une date ou un type de données d’intervalle; le type C était SQL_C_CHAR; et la valeur de la colonne ou du paramètre n’était pas un littéral valide du type SQL lié.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|(DM) L’argument *DataPtr* était un pointeur nul, et *l’argument StrLen_or_Ind* n’était pas 0, SQL_DEFAULT_PARAM, ou SQL_NULL_DATA.|  
|HY010|Erreur de séquence de fonction|(DM) L’appel de fonction précédent n’était pas un appel à **SQLPutData** ou **SQLParamData**.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction SQLPutData a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY019|Données non-caractère et non binaires envoyées en morceaux|**SQLPutData** a été appelé plus d’une fois pour un paramètre ou une colonne, et il n’était pas utilisé pour envoyer des données de caractère C à une colonne avec un type de données de caractère, binaire, ou de source de données ou d’envoyer des données C binaires à une colonne avec un type de données de caractère, binaire, ou de source de données spécifique.|  
|HY020|Tentative de concatenate d’une valeur nulle|**SQLPutData** a été appelé plus d’une fois depuis l’appel qui est retourné SQL_NEED_DATA, et dans l’un de ces appels, *l’argument StrLen_or_Ind* contenait SQL_NULL_DATA ou SQL_DEFAULT_PARAM.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|L’argument *DataPtr* n’était pas un pointeur nul, et *l’argument StrLen_or_Ind* était inférieur à 0, mais pas égal à SQL_NTS ou SQL_NULL_DATA.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
 Si **SQLPutData** est appelé lors de l’envoi de données pour un paramètre dans une déclaration SQL, il peut retourner tout SQLSTATE qui peut être retourné par la fonction appelée pour exécuter la déclaration (**SQLExecute** ou **SQLExecDirect**). S’il s’agit d’envoyer des données pour une colonne mise à jour ou ajoutée avec **SQLBulkOperations** ou mise à jour avec **SQLSetPos**, il peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLBulkOperations** ou **SQLSetPos**.  
  
## <a name="comments"></a>Commentaires  
 **SQLPutData** peut être appelé à fournir des données de données à l’exécution pour deux utilisations: les données de paramètres à utiliser dans un appel à **SQLExecute** ou **SQLExecDirect**, ou les données de colonne à utiliser quand une ligne est mise à jour ou ajouté par un appel à **SQLBulkOperations** ou est mis à jour par un appel à **SQLSetPos**.  
  
 Lorsqu’une application appelle **SQLParamData** pour déterminer quelles données il doit envoyer, le conducteur renvoie un indicateur que l’application peut utiliser pour déterminer les données de paramètres à envoyer ou où les données de colonne peuvent être trouvées. Il renvoie également SQL_NEED_DATA, ce qui est un indicateur de l’application qu’il devrait appeler **SQLPutData** pour envoyer les données. Dans l’argument *DataPtr* à **SQLPutData**, l’application passe un pointeur vers le tampon contenant les données réelles pour le paramètre ou la colonne.  
  
 Lorsque le conducteur revient SQL_SUCCESS pour **SQLPutData**, l’application appelle **SQLParamData** à nouveau. **SQLParamData** retourne SQL_NEED_DATA si plus de données doivent être envoyées, auquel cas la demande appelle **SQLPutData** à nouveau. Il renvoie SQL_SUCCESS si toutes les données de données d’exécution ont été envoyées. L’application appelle ensuite **SQLParamData** à nouveau. Si le conducteur retourne SQL_NEED_DATA et un autre indicateur dans * \*ValuePtrPtr*, il nécessite des données pour un autre paramètre ou colonne et **SQLPutData** est appelé à nouveau. Si le conducteur retourne SQL_SUCCESS, toutes les données de données sur l’exécution ont été envoyées et la déclaration SQL peut être exécutée ou **l’appel SQLBulkOperations** ou **SQLSetPos** peut être traité.  
  
 Pour plus d’informations sur la façon dont les données de paramètres de données à l’exécution sont transmises au moment de l’exécution des relevés, voir « Valeurs de paramètres de passage » dans [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) et [envoyer de longues données.](../../../odbc/reference/develop-app/sending-long-data.md) Pour plus d’informations sur la façon dont les données de la colonne de données à l’exécution sont mises à jour ou ajoutées, voir la section "Using SQLSetPos" dans [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Performing Bulk Updates Using Bookmarks" dans [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), et [Long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
> [!NOTE]  
>  Une application peut utiliser **SQLPutData** pour envoyer des données en parties uniquement lors de l’envoi de données de caractère C à une colonne avec un type de données spécifique à un personnage, binaire ou spécifique à la source de données ou lors de l’envoi de données C binaires à une colonne avec un type de données de caractère, binaire ou spécifique à la source de données. Si **SQLPutData** est appelé plus d’une fois dans d’autres conditions, il retourne SQL_ERROR et SQLSTATE HY019 (données non-caractère et non binaires envoyées en morceaux).  
  
## <a name="example"></a>Exemple  
 L’échantillon suivant suppose un nom de source de données appelé Test. La base de données associée doit avoir une table que vous pouvez créer, comme suit :  
  
```sql  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```cpp  
// SQLPutData.cpp  
// compile with: odbc32.lib user32.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define TEXTSIZE  12000  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // SQLBindParameter variables.  
   SQLLEN cbTextSize, lbytes;  
  
   // SQLParamData variable.  
   PTR pParmID;  
  
   // SQLPutData variables.  
   UCHAR  Data[] =   
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyz";  
  
   SDWORD cbBatch = (SDWORD)sizeof(Data) - 1;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set parameters based on total data to send.  
   lbytes = (SDWORD)TEXTSIZE;  
   cbTextSize = SQL_LEN_DATA_AT_EXEC(lbytes);  
  
   // Bind the parameter marker.  
   retcode = SQLBindParameter (hstmt1,           // hstmt  
                               1,                // ipar  
                               SQL_PARAM_INPUT,  // fParamType  
                               SQL_C_CHAR,       // fCType  
                               SQL_LONGVARCHAR,  // FSqlType  
                               lbytes,           // cbColDef  
                               0,                // ibScale  
                               (VOID *)1,        // rgbValue  
                               0,                // cbValueMax  
                               &cbTextSize);     // pcbValue  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.  
   retcode =   
      SQLExecDirect(hstmt1, (UCHAR*)"INSERT INTO emp4 VALUES('Paul Borm', 46,'1950-11-12 00:00:00', ?)", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_NEED_DATA) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Check to see if NEED_DATA; if yes, use SQLPutData.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if (retcode == SQL_NEED_DATA) {  
      while (lbytes > cbBatch) {  
         SQLPutData(hstmt1, Data, cbBatch);  
         lbytes -= cbBatch;  
      }  
      // Put final batch.  
      retcode = SQLPutData(hstmt1, Data, lbytes);   
   }  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Make final SQLParamData call.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("Final SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clean up.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Retour du paramètre suivant pour envoyer des données pour|[SQLParamData, fonction](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
