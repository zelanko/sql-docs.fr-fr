---
title: SQLSetDescRec, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a733c2b88954c9937e8a170b949535ffa118bad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039736"
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 Le **SQLSetDescRec** fonction définit plusieurs champs de descripteur qui affectent le type de données et la mémoire tampon à une colonne ou le paramètre des données liées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLSetDescRec(  
      SQLHDESC      DescriptorHandle,  
      SQLSMALLINT   RecNumber,  
      SQLSMALLINT   Type,  
      SQLSMALLINT   SubType,  
      SQLLEN        Length,  
      SQLSMALLINT   Precision,  
      SQLSMALLINT   Scale,  
      SQLPOINTER    DataPtr,  
      SQLLEN *      StringLengthPtr,  
      SQLLEN *      IndicatorPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *DescriptorHandle*  
 [Entrée] Handle du descripteur. Cela ne doit pas être un descripteur IRD.  
  
 *RecNumber*  
 [Entrée] Indique que l’enregistrement de descripteur qui contient les champs à définir. Enregistrements de descripteurs sont numérotés de 0, avec le numéro d’enregistrement 0 en cours de l’enregistrement de signet. Cet argument doit être égale ou supérieure à 0. Si *RecNumber* est supérieure à la valeur de SQL_DESC_COUNT, SQL_DESC_COUNTis modifié à la valeur de *RecNumber*.  
  
 *Type*  
 [Entrée] La valeur à laquelle définir le champ SQL_DESC_TYPE pour l’enregistrement de descripteur.  
  
 *SubType*  
 [Entrée] Pour les enregistrements dont le type est SQL_DATETIME ou SQL_INTERVAL, il s’agit de la valeur à laquelle définir le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *Longueur*  
 [Entrée] La valeur à laquelle définir le champ SQL_DESC_OCTET_LENGTH pour l’enregistrement de descripteur.  
  
 *Précision*  
 [Entrée] La valeur à laquelle définir le champ SQL_DESC_PRECISION pour l’enregistrement de descripteur.  
  
 *Échelle*  
 [Entrée] La valeur à laquelle définir le champ SQL_DESC_SCALE pour l’enregistrement de descripteur.  
  
 *DataPtr*  
 [Différée entrée ou sortie] La valeur à laquelle définir le champ SQL_DESC_DATA_PTR pour l’enregistrement de descripteur. *DataPtr* peut être définie sur un pointeur null.  
  
 Le *DataPtr* argument peut être défini à un pointeur null pour le champ SQL_DESC_DATA_PTR la valeur est un pointeur null. Si le handle dans le *DescriptorHandle* argument est associé à un ARD, cela annule la liaison de la colonne.  
  
 *StringLengthPtr*  
 [Différée entrée ou sortie] La valeur à laquelle définir le champ SQL_DESC_OCTET_LENGTH_PTR pour l’enregistrement de descripteur. *StringLengthPtr* peut être défini sur un pointeur null pour le champ SQL_DESC_OCTET_LENGTH_PTR la valeur est un pointeur null.  
  
 *IndicatorPtr*  
 [Différée entrée ou sortie] La valeur à laquelle définir le champ SQL_DESC_INDICATOR_PTR pour l’enregistrement de descripteur. *IndicatorPtr* peut être défini sur un pointeur null pour le champ SQL_DESC_INDICATOR_PTR la valeur est un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetDescRec** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_DESC et un *gérer* de *DescriptorHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLSetDescRec** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07009|Index de descripteur non valide|Le *RecNumber* argument a été défini sur 0 et le *DescriptorHandle* auquel un descripteur IPD.<br /><br /> Le *RecNumber* argument était inférieure à 0.<br /><br /> Le *RecNumber* argument était supérieur au nombre maximal de colonnes ou paramètres de la source de données peut prendre en charge, et le *DescriptorHandle* argument était un APD, IPD ou ARD.<br /><br /> Le *RecNumber* argument était égal à 0 et le *DescriptorHandle* argument auquel une APD alloué implicitement. (Cette erreur ne se produit pas avec un descripteur d’application alloués explicitement, car on ne sait pas si un descripteur d’application explicitement alloué soit un APD ARD jusqu'à ce que l’exécution.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) le *DescriptorHandle* a été associé à un *au paramètre StatementHandle* pour laquelle une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée et l’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* avec lequel le *DescriptorHandle* a été associé et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *DescriptorHandle*. Cette fonction aynchronous était en cours d’exécution lorsque le **SQLSetDescRec** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelée pour l’une des descripteurs d’instruction associés à la *DescriptorHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY016|Impossible de modifier un descripteur de ligne d’implémentation|Le *DescriptorHandle* argument a été associé à un IRD.|  
|HY021|Informations de descripteur incohérentes|Le *Type* champ, ou tout autre champ associé au champ SQL_DESC_TYPE dans le descripteur, n’était pas valide ou cohérente.<br /><br /> Informations de descripteur vérifiées pendant une vérification de cohérence n’étaient pas cohérentes. (Voir « Vérifications de cohérence, » plus loin dans cette section.)|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) le pilote a été une ODBC *2.x* pilote, le descripteur a été un ARD, le *ColumnNumber* argument a été défini sur 0 et la valeur spécifiée pour l’argument *BufferLength* a été non égal à 4.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLSetDescRec** pour définir les champs suivants pour une seule colonne ou un paramètre :  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (pour les enregistrements dont le type est SQL_DATETIME ou SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Si un appel à **SQLSetDescRec** échoue, le contenu de l’enregistrement de descripteur identifié par le *RecNumber* argument ne sont pas définis.  
  
 Lors de la liaison d’une colonne ou un paramètre **SQLSetDescRec** vous permet de modifier plusieurs champs qui affectent la liaison sans appeler **SQLBindCol** ou **SQLBindParameter** ou effectuer plusieurs appels à **SQLSetDescField**. **SQLSetDescRec** pouvez définir des champs sur un descripteur pas actuellement associé à une instruction. Notez que **SQLBindParameter** définit plus de champs que **SQLSetDescRec**, peut définir les champs sur un APD et une infrastructure ou IPD dans un seul appel et ne nécessite pas un handle de descripteur.  
  
> [!NOTE]  
>  L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS doit toujours être définie avant d’appeler **SQLSetDescRec** avec un *RecNumber* argument 0 pour définir des champs de signet. Bien que cela ne soit pas obligatoire, il est fortement recommandé.  
  
## <a name="consistency-checks"></a>Vérifications de cohérence  
 Une vérification de cohérence est effectuée par le pilote automatiquement chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR d’APD, ARD ou IPD. Si aucun champ n’est pas cohérente avec les autres champs, **SQLSetDescRec** retourne SQLSTATE HY021 (informations de descripteur incohérent).  
  
 Chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR d’APD, ARD ou IPD, le pilote vérifie que la valeur du champ SQL_DESC_TYPE et les valeurs applicables à ce champ SQL_DESC_TYPE sont valides et cohérentes. Cette vérification est toujours effectuée quand **SQLBindParameter** ou **SQLBindCol** est appelée ou quand **SQLSetDescRec** est appelée pour un APD, ARD ou IPD. Cette vérification de cohérence inclut les vérifications suivantes sur les champs de descripteur :  
  
-   Le champ SQL_DESC_TYPE doit être le C ODBC valide ou types SQL ou un type de pilote SQL. Le champ SQL_DESC_CONCISE_TYPE doit être un des types valides ODBC C ou SQL ou un type de C ou SQL spécifiques au pilote, y compris les types date/heure et intervalle concis.  
  
-   Si le champ d’enregistrement SQL_DESC_TYPE est SQL_DATETIME ou SQL_INTERVAL, le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE doit être un des codes intervalle datetime valide. (Consultez la description du champ valeur SQL_DESC_DATETIME_INTERVAL_CODE dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Si le champ SQL_DESC_TYPE indique un type numérique, les champs SQL_DESC_PRECISION et SQL_DESC_SCALE sont vérifiés pour être valide.  
  
-   Si le champ SQL_DESC_CONCISE_TYPE est un type de données heure ou d’horodatage, un intervalle type avec un composant « secondes », ou l’un des types de données d’intervalle avec un composant au moment, le champ SQL_DESC_PRECISION est vérifié à être une précision de secondes valide.  
  
-   Si le SQL_DESC_CONCISE_TYPE est un type de données d’intervalle, le champ SQL_DESC_DATETIME_INTERVAL_PRECISION est vérifié pour être une valeur de précision de début intervalle valide.  
  
 Le champ SQL_DESC_DATA_PTR d’une infrastructure ou IPD n’est pas normalement défini ; Toutefois, une application peut le faire pour forcer une vérification de cohérence de champs IPD. Impossible d’effectuer une vérification de cohérence sur un IRD. La valeur définie pour le champ SQL_DESC_DATA_PTR de l’IPD n’est pas réellement stockée et ne peut pas être récupérée par un appel à **SQLGetDescField** ou **SQLGetDescRec**; le paramètre est effectué uniquement pour forcer le vérification de cohérence.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une colonne|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Un paramètre de liaison|[SQLBindParameter, fonction](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Obtention d’un champ de descripteur unique|[SQLGetDescField, fonction](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtention de plusieurs champs de descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Définition des champs de descripteur unique|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
