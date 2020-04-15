---
title: Fonction SQLGetDescRec (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescRec
helpviewer_keywords:
- SQLGetDescRec function [ODBC]
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 87d7b971b379f19f8451e924932a5e699e9b9983
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285484"
---
# <a name="sqlgetdescrec-function"></a>SQLGetDescRec, fonction
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetDescRec** retourne les paramètres ou les valeurs actuels de plusieurs champs d’un enregistrement descripteur. Les champs retournés décrivent le nom, le type de données et le stockage des données de colonne ou de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetDescRec(  
      SQLHDESC        DescriptorHandle,  
      SQLSMALLINT     RecNumber,  
      SQLCHAR *       Name,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLSMALLINT *   TypePtr,  
      SQLSMALLINT *   SubTypePtr,  
      SQLLEN *        LengthPtr,  
      SQLSMALLINT *   PrecisionPtr,  
      SQLSMALLINT *   ScalePtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *DescriptorHandle*  
 [Entrée] Poignée descripteur.  
  
 *RecNumber*  
 [Entrée] Indique le dossier descripteur à partir duquel la demande recherche des informations. Les enregistrements descripteur sont numérotés à partir de 1, avec le numéro 0 record étant le signet record. *L’argument du RecNumber* doit être inférieur ou égal à la valeur de SQL_DESC_COUNT. Si *RecNumber* est inférieur ou égal à SQL_DESC_COUNT mais que la ligne ne contient pas de données pour une colonne ou un paramètre, un appel à **SQLGetDescRec** retournera les valeurs par défaut des champs. (Pour plus d’informations, voir "Initialisation of Descriptor Fields" dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *Nom*  
 [Sortie] Un pointeur à un tampon dans lequel retourner le champ SQL_DESC_NAME pour le dossier descripteur.  
  
 Si *le nom* est NULL, *StringLengthPtr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *nom*.  
  
 *BufferLength*  
 [Entrée] Longueur du tampon*nom,* en caractères.  
  
 *StringLengthPtr*  
 [Sortie] Un pointeur vers un tampon dans lequel retourner le nombre \*de caractères de données disponibles pour revenir dans le tampon *Nom,* à l’exclusion du caractère de non-terminaison. Si le nombre de caractères était supérieur ou égal à *BufferLength*, les données dans \* *Le Nom* sont tronquées à *BufferLength* moins la longueur d’un caractère de non-termination, et est annulée par le conducteur.  
  
 *TypePtr (typePtr)*  
 [Sortie] Un pointeur à un tampon dans lequel retourner la valeur du champ SQL_DESC_TYPE pour l’enregistrement descripteur.  
  
 *SubTypePtr*  
 [Sortie] Pour les enregistrements dont le type est SQL_DATETIME ou SQL_INTERVAL, il s’agit d’un pointeur à un tampon dans lequel retourner la valeur du champ SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *LongueurPtr*  
 [Sortie] Un pointeur à un tampon dans lequel retourner la valeur du champ SQL_DESC_OCTET_LENGTH pour l’enregistrement descripteur.  
  
 *PrecisionPtr (en)*  
 [Sortie] Un pointeur à un tampon dans lequel retourner la valeur du champ SQL_DESC_PRECISION pour l’enregistrement descripteur.  
  
 *ScalePtr (en)*  
 [Sortie] Un pointeur à un tampon dans lequel retourner la valeur du champ SQL_DESC_SCALE pour l’enregistrement descripteur.  
  
 *NullablePtr (nullablePtr)*  
 [Sortie] Un pointeur à un tampon dans lequel retourner la valeur du champ SQL_DESC_NULLABLE pour l’enregistrement descripteur.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA ou SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA est retourné si *RecNumber* est supérieur au nombre actuel de dossiers descripteur.  
  
 SQL_NO_DATA est retourné si *DescriptorHandle* est une poignée IRD et la déclaration est dans l’état préparé ou exécuté, mais il n’y avait pas de curseur ouvert associé à elle.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetDescRec** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DESC et une *poignée* de *DescriptorHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLGetDescRec** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \* *nom* tampon n’était pas assez grand pour retourner l’ensemble du champ descripteur. Par conséquent, le champ a été tronqué. La longueur du champ descripteur non mensuré est retournée dans*le stringLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07009|Indice descripteur invalide|*L’argument de FieldIdentifier* était un champ record, *l’argument de RecNumber* a été fixé à 0, et *l’argument de DescriptorHandle* était une poignée d’IPD.<br /><br /> (DM) *L’argument de RecNumber* a été réglé à 0, et l’attribut de déclaration SQL_ATTR_USE_BOOKMARKS a été réglé pour SQL_UB_OFF, et *l’argument de DescriptorHandle* était une poignée de l’IRD.<br /><br /> *L’argument de RecNumber* était inférieur à 0.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire requise pour supporter l’exécution ou l’achèvement de la fonction.|  
|HY007|Déclaration associée n’est pas préparée|*DescriptorHandle* était associé à un IRD, et la poignée de déclaration associée n’était pas dans l’état préparé ou exécuté.|  
|HY010|Erreur de séquence de fonction|(DM) *DescriptorHandle* a été associé à un *StatementHandle* pour lequel une fonction d’exécution asynchrone (pas celle-ci) a été appelée et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) *DescriptorHandle* a été associé à une *déclaration* pour laquelle **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *DescriptorHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque **SQLGetDescRec** a été appelé.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé à *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLGetDescRec** pour récupérer les valeurs des champs descripteur suivants pour une seule colonne ou paramètre :  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (pour les dossiers dont le type est SQL_DATETIME ou SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec** ne récupère pas les valeurs pour les champs d’en-tête.  
  
 Une application peut empêcher le retour du réglage d’un champ en définissant l’argument qui correspond au champ à un pointeur nul.  
  
 Lorsqu’une application appelle **SQLGetDescRec** pour récupérer la valeur d’un champ qui n’est pas défini pour un type de descripteur particulier, la fonction renvoie SQL_SUCCESS mais la valeur retournée pour le champ n’est pas définie. Par exemple, appeler **SQLGetDescRec** pour le SQL_DESC_NAME ou SQL_DESC_NULLABLE champ d’une DPA ou d’un ARD retournera SQL_SUCCESS mais une valeur indéfinie pour le champ.  
  
 Lorsqu’une application appelle **SQLGetDescRec** pour récupérer la valeur d’un champ défini pour un type de descripteur particulier, mais qui n’a pas encore de valeur par défaut et qui n’a pas encore été définie, la fonction revient SQL_SUCCESS mais la valeur retournée pour le champ n’est pas définie. Pour plus d’informations, voir "Initialisation of Descriptor Fields" dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Les valeurs des champs peuvent également être récupérées individuellement par un appel à **SQLGetDescField**. Pour une description des champs dans un en-tête ou un enregistrement descripteur, voir [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Pour plus d’informations sur les descripteurs, voir [Descriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Reliser une colonne|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Lier un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Obtenir un champ descripteur|[Fonction SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Réglage de plusieurs champs descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
