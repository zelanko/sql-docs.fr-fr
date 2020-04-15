---
title: Fonction SQLSetDescRec (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b29879ff7635d6eb7d5a0f7489ff3994758d4a35
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299529"
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec, fonction
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 La fonction **SQLSetDescRec** définit plusieurs champs descripteur qui affectent le type de données et la mémoire tampon liés à une colonne ou à des données de paramètres.  
  
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
 [Entrée] Poignée descripteur. Ce ne doit pas être une poignée IRD.  
  
 *RecNumber*  
 [Entrée] Indique l’enregistrement du descripteur qui contient les champs à définir. Les enregistrements descripteur sont numérotés à partir de 0, avec le numéro 0 record étant le signet record. Cet argument doit être égal ou supérieur à 0. Si *RecNumber* est supérieur à la valeur de SQL_DESC_COUNT, SQL_DESC_COUNTis changé à la valeur de *RecNumber*.  
  
 *Type*  
 [Entrée] La valeur à laquelle établir le champ SQL_DESC_TYPE pour le record descripteur.  
  
 *Sous-type*  
 [Entrée] Pour les enregistrements dont le type est SQL_DATETIME ou SQL_INTERVAL, c’est la valeur à laquelle définir le champ SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *Length*  
 [Entrée] La valeur à laquelle établir le champ SQL_DESC_OCTET_LENGTH pour le record descripteur.  
  
 *Précision*  
 [Entrée] La valeur à laquelle établir le champ SQL_DESC_PRECISION pour le record descripteur.  
  
 *Mettre à l'échelle*  
 [Entrée] La valeur à laquelle établir le champ SQL_DESC_SCALE pour le record descripteur.  
  
 *DataPtr (en)*  
 [Entrée différée ou sortie] La valeur à laquelle établir le champ SQL_DESC_DATA_PTR pour le record descripteur. *DataPtr* peut être réglé sur un pointeur nul.  
  
 *L’argument De DataPtr* peut être réglé à un pointeur nul pour définir le champ SQL_DESC_DATA_PTR à un pointeur nul. Si la poignée dans *l’argument DescriptorHandle* est associée à un ARD, cela découple la colonne.  
  
 *StringLengthPtr*  
 [Entrée différée ou sortie] La valeur à laquelle établir le champ SQL_DESC_OCTET_LENGTH_PTR pour le record descripteur. *StringLengthPtr* peut être réglé à un pointeur nul pour définir le champ SQL_DESC_OCTET_LENGTH_PTR à un pointeur nul.  
  
 *IndicateurPtr*  
 [Entrée différée ou sortie] La valeur à laquelle établir le champ SQL_DESC_INDICATOR_PTR pour le record descripteur. *IndicatorPtr* peut être réglé à un pointeur nul pour définir le champ SQL_DESC_INDICATOR_PTR à un pointeur nul.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetDescRec** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DESC et une *poignée* de *DescriptorHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLSetDescRec** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07009|Indice descripteur invalide|*L’argument du RecNumber* a été réglé à 0, et le *DescriptorHandle* a fait référence à une poignée IPD.<br /><br /> *L’argument de RecNumber* était inférieur à 0.<br /><br /> *L’argument de RecNumber* était supérieur au nombre maximal de colonnes ou de paramètres que la source de données peut prendre en charge, et *l’argument de DescriptorHandle* était un APD, IPD ou ARD.<br /><br /> *L’argument du RecNumber* était égal à 0, et *l’argument de DescriptorHandle* faisait référence à une DPA implicitement attribuée. (Cette erreur ne se produit pas avec un descripteur d’application explicitement attribué parce qu’on ne sait pas si un descripteur d’application explicitement attribué est un APD ou une ARD jusqu’au moment de l’exécution.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) Le *DescriptorHandle* a été associé à un *StatementHandle* pour lequel une fonction d’exécution asynchrone (pas celle-ci) a été appelée et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* avec lequel le *DescriptorHandle* a été associé et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *DescriptorHandle*. Cette fonction aynchrone était encore en cours d’exécution lorsque la fonction **SQLSetDescRec** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour l’une des poignées de déclaration associées au *DescriptorHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY016|Impossible de modifier un descripteur de ligne de mise en œuvre|*L’argument de DescriptorHandle* a été associé à un IRD.|  
|HY021|Informations descripteur incohérentes|Le champ *type,* ou tout autre champ associé au champ SQL_DESC_TYPE dans le descripteur, n’était pas valide ou cohérent.<br /><br /> Les renseignements descripteur vérifiés lors d’une vérification de cohérence n’étaient pas cohérents. (Voir « Vérifications de cohérence », plus tard dans cette section.)|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) Le conducteur était un conducteur ODBC *2.x,* le descripteur était un ARD, *l’argument de ColumnNumber* a été réglé à 0, et la valeur spécifiée pour l’argument *BufferLength* n’était pas égale à 4.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLSetDescRec** pour définir les champs suivants pour une seule colonne ou paramètre :  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (pour les dossiers dont le type est SQL_DATETIME ou SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Si un appel à **SQLSetDescRec** échoue, le contenu du dossier descripteur identifié par l’argument *du RecNumber* n’est pas défini.  
  
 Lors de la liaison d’une colonne ou d’un paramètre, **SQLSetDescRec** vous permet de modifier plusieurs champs affectant la liaison sans appeler **SQLBindCol** ou **SQLBindParameter** ou faire plusieurs appels à **SQLSetDescField**. **SQLSetDescRec** peut mettre des champs sur un descripteur qui n’est pas actuellement associé à une déclaration. Notez que **SQLBindParameter** définit plus de champs que **SQLSetDescRec**, peut mettre les champs sur une DPA et un IPD en un seul appel, et ne nécessite pas une poignée descripteur.  
  
> [!NOTE]  
>  L’attribut d’attribution de déclaration SQL_ATTR_USE_BOOKMARKS doit toujours être défini avant d’appeler **SQLSetDescRec** avec un argument *RecNumber* de 0 pour définir des champs de signets. Bien que ce ne soit pas obligatoire, il est fortement recommandé.  
  
## <a name="consistency-checks"></a>Vérifications de cohérence  
 Une vérification de cohérence est effectuée automatiquement par le conducteur chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR d’une DPA, d’une ARD ou d’une DPI. Si l’un des champs est incompatible avec d’autres champs, **SQLSetDescRec** retournera SQLSTATE HY021 (informations descripteur incohérentes).  
  
 Chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR d’une DPA, d’une ARD ou d’une DPI, le conducteur vérifie que la valeur du champ SQL_DESC_TYPE et les valeurs applicables à ce champ SQL_DESC_TYPE sont valides et cohérentes. Cette vérification est toujours effectuée lorsque **SQLBindParameter** ou **SQLBindCol** est appelé ou lorsque **SQLSetDescRec** est appelé pour un APD, ARD, ou IPD. Cette vérification de cohérence comprend les vérifications suivantes sur les champs descripteur :  
  
-   Le champ SQL_DESC_TYPE doit être l’un des types C ou SQL valides de l’ODBC ou d’un type SQL spécifique au conducteur. Le champ SQL_DESC_CONCISE_TYPE doit être l’un des types C ou SQL valides de l’ODBC ou d’un type C ou SQL spécifique au conducteur, y compris les types de date et d’intervalle concis.  
  
-   Si le champ d’enregistrement SQL_DESC_TYPE est SQL_DATETIME ou SQL_INTERVAL, le champ SQL_DESC_DATETIME_INTERVAL_CODE doit être l’un des codes de date ou d’intervalle valides. (Voir la description du champ SQL_DESC_DATETIME_INTERVAL_CODE dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Si le champ SQL_DESC_TYPE indique un type numérique, les champs SQL_DESC_PRECISION et SQL_DESC_SCALE sont vérifiés pour être valides.  
  
-   Si le champ SQL_DESC_CONCISE_TYPE est un type de données temporelle ou temporelle, un type d’intervalle avec un composant de secondes, ou l’un des types de données d’intervalle avec un composant de temps, le champ SQL_DESC_PRECISION est vérifié pour être une précision valide secondes.  
  
-   Si le SQL_DESC_CONCISE_TYPE est un type de données d’intervalle, le champ SQL_DESC_DATETIME_INTERVAL_PRECISION est vérifié comme une valeur de précision de précision d’intervalle valide.  
  
 Le champ SQL_DESC_DATA_PTR d’un IPD n’est normalement pas défini; cependant, une application peut le faire pour forcer une vérification de cohérence des champs IPD. Une vérification de cohérence ne peut pas être effectuée sur un IRD. La valeur à laquelle le champ SQL_DESC_DATA_PTR de l’IPD est configuré n’est pas réellement stockée et ne peut pas être récupérée par un appel à **SQLGetDescField** ou **SQLGetDescRec;** le réglage est fait uniquement pour forcer le contrôle de cohérence.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Reliser une colonne|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Lier un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Obtenir un champ descripteur unique|[Fonction SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtenir plusieurs champs descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Réglage des champs descripteur unique|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
