---
title: SQLGetDescRec, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f8c585bc758b74c666c8da625c1e57af7af2582
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258799"
---
# <a name="sqlgetdescrec-function"></a>SQLGetDescRec, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetDescRec** retourne les paramètres actuels ou les valeurs de plusieurs champs d’un enregistrement de descripteur. Les champs retournés décrivent le nom, le type de données et le stockage des données de colonne ou du paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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
 [Entrée] Handle du descripteur.  
  
 *RecNumber*  
 [Entrée] Indique que l’enregistrement de descripteur à partir de laquelle l’application cherche des informations. Enregistrements de descripteurs sont numérotées de 1, avec le numéro d’enregistrement 0 en cours de l’enregistrement de signet. Le *RecNumber* argument doit être inférieur ou égal à la valeur de SQL_DESC_COUNT. Si *RecNumber* est inférieure ou égale à SQL_DESC_COUNT mais la ligne ne contient pas de données pour une colonne ou paramètre, un appel à **SQLGetDescRec** retourne les valeurs par défaut des champs. (Pour plus d’informations, consultez « Initialisation de champs de descripteur » dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *Nom*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner le champ SQL_DESC_NAME pour l’enregistrement de descripteur.  
  
 Si *nom* est NULL, *StringLengthPtr* retournera toujours le nombre total de caractères (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers laquelle pointée  *Nom*.  
  
 *BufferLength*  
 [Entrée] Longueur de la **nom* mémoire tampon, en caractères.  
  
 *StringLengthPtr*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner le nombre de caractères de données available retourner dans le \* *nom* mémoire tampon, à l’exclusion du caractère de caractère nul de terminaison. Si le nombre de caractères est supérieur ou égal à *BufferLength*, les données dans \* *nom* est tronqué à *BufferLength* moins la longueur d’un caractère du caractère nul de terminaison et se terminant par null par le pilote.  
  
 *TypePtr*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner la valeur du champ SQL_DESC_TYPE pour l’enregistrement de descripteur.  
  
 *SubTypePtr*  
 [Sortie] Pour les enregistrements dont le type est SQL_DATETIME ou SQL_INTERVAL, il s’agit d’un pointeur vers une mémoire tampon dans lequel retourner la valeur du champ valeur SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *LengthPtr*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner la valeur du champ SQL_DESC_OCTET_LENGTH pour l’enregistrement de descripteur.  
  
 *PrecisionPtr*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner la valeur du champ SQL_DESC_PRECISION pour l’enregistrement de descripteur.  
  
 *ScalePtr*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner la valeur du champ SQL_DESC_SCALE pour l’enregistrement de descripteur.  
  
 *NullablePtr*  
 [Sortie] Un pointeur vers une mémoire tampon dans lequel retourner la valeur du champ SQL_DESC_NULLABLE pour l’enregistrement de descripteur.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA ou SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA soit retourné si *RecNumber* est supérieur au nombre actuel d’enregistrements de descripteurs.  
  
 SQL_NO_DATA soit retourné si *DescriptorHandle* est un descripteur IRD et l’instruction est dans un état préparé ou exécuté, mais il n’a aucun curseur ouvert associé.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetDescRec** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_DESC et un *gérer* de *DescriptorHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetDescRec** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|La mémoire tampon \* *nom* n’était pas assez élevé pour renvoyer le champ de descripteur entière. Par conséquent, le champ a été tronqué. La longueur du champ de descripteur non tronqué est retournée dans **StringLengthPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07009|Index de descripteur non valide|Le *FieldIdentifier* argument était un champ d’enregistrement, le *RecNumber* argument a été défini sur 0 et le *DescriptorHandle* argument était un descripteur IPD.<br /><br /> (DM) le *RecNumber* argument a été défini sur 0, et l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a été défini à SQL_UB_OFF et le *DescriptorHandle* argument était un descripteur IRD.<br /><br /> Le *RecNumber* argument était inférieure à 0.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY007|L’instruction associée n’est pas préparée.|*DescriptorHandle* a été associé à un IRD et le descripteur d’instruction associée n’était pas dans un état préparé ou exécuté.|  
|HY010|Erreur de séquence de fonction|(DM) *DescriptorHandle* a été associé à un *au paramètre StatementHandle* pour laquelle une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée et l’exécution quand cette fonction a été appelée.<br /><br /> (DM) *DescriptorHandle* a été associé à un *au paramètre StatementHandle* pour lequel **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, ou **SQLSetPos** a été appelée et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *DescriptorHandle*. Cette fonction asynchrone était en cours d’exécution lorsque **SQLGetDescRec** a été appelée.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLGetDescRec** pour récupérer les valeurs des champs de descripteur suivants pour une seule colonne ou un paramètre :  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (pour les enregistrements dont le type est SQL_DATETIME ou SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec** ne récupère pas les valeurs des champs d’en-tête.  
  
 Une application peut empêcher le retour d’un paramètre en définissant l’argument qui correspond au champ à un pointeur null.  
  
 Lorsqu’une application appelle **SQLGetDescRec** pour récupérer la valeur d’un champ qui n’est pas défini pour un type particulier de descripteur, la fonction retourne SQL_SUCCESS, mais la valeur retournée pour le champ n’est pas définie. Par exemple, l’appel **SQLGetDescRec** pour le champ SQL_DESC_NAME ou SQL_DESC_NULLABLE d’un APD ou d’ARD retourne SQL_SUCCESS, mais une valeur non définie pour le champ.  
  
 Lorsqu’une application appelle **SQLGetDescRec** pour récupérer la valeur d’un champ qui est défini pour un type particulier de descripteur, mais qui n’a aucune valeur par défaut et n’a pas encore été définie, la fonction retourne SQL_SUCCESS, mais la valeur retournée pour le champ n’est pas défini. Pour plus d’informations, consultez « Initialisation de champs de descripteur » dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Les valeurs des champs peuvent également être récupérées individuellement par un appel à **SQLGetDescField**. Pour obtenir une description des champs dans un en-tête de descripteur ou un enregistrement, consultez [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Pour plus d’informations sur les descripteurs, consultez [descripteurs](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une colonne|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Un paramètre de liaison|[SQLBindParameter, fonction](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Obtention d’un champ de descripteur|[SQLGetDescField, fonction](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Définition de plusieurs champs de descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
