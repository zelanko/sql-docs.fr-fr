---
title: Fonction SQLGetDescField (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescField
helpviewer_keywords:
- SQLGetDescField function [ODBC]
ms.assetid: f09ff660-1e4a-4370-be85-90d4da0487d3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89972d7f36b436868cc8e243b03827f095b90492
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285474"
---
# <a name="sqlgetdescfield-function"></a>Fonction SQLGetDescField
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetDescField** retourne le réglage ou la valeur actuels d’un seul champ d’un enregistrement descripteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *DescriptorHandle*  
 [Entrée] Poignée descripteur.  
  
 *RecNumber*  
 [Entrée] Indique le dossier descripteur à partir duquel la demande recherche des informations. Les enregistrements descripteur sont numérotés à partir de 0, avec le numéro 0 record étant le signet record. Si l’argument *De FieldIdentifier* indique un champ d’en-tête, *RecNumber* est ignoré. Si *RecNumber* est inférieur ou égal à SQL_DESC_COUNT mais que la ligne ne contient pas de données pour une colonne ou un paramètre, un appel à **SQLGetDescField** retournera les valeurs par défaut des champs. (Pour plus d’informations, voir "Initialisation of Descriptor Fields" dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *FieldIdentifier*  
 [Entrée] Indique le champ du descripteur dont la valeur doit être retournée. Pour plus d’informations, voir la section «*FieldIdentifier* Argument » dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 *ValuePtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner les informations descripteur. Le type de données dépend de la valeur de *FieldIdentifier*.  
  
 Si *ValuePtr* est de type integer, les applications doivent utiliser un tampon de SQLULEN et initialiser la valeur à 0 avant d’appeler cette fonction que certains conducteurs ne peuvent écrire le plus bas 32 bits ou 16 bits d’un tampon et laisser le bit de l’ordre supérieur inchangé.  
  
 Si *ValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de résiliation nulle pour les données de caractère) disponible pour revenir dans le tampon indiqué par *ValuePtr*.  
  
 *BufferLength*  
 [Entrée] Si *FieldIdentifier* est un champ défini par ODBC et *que ValuePtr* pointe vers une \*chaîne de caractères ou un tampon binaire, cet argument doit être la longueur de *ValuePtr*. Si *FieldIdentifier* est un champ défini \*par L’ODBC et *que ValuePtr* est un intégrateur, *BufferLength* est ignoré. Si la valeur de * \*ValuePtr* est d’un type de données Unicode (lorsque vous appelez **SQLGetDescFieldW**), l’argument *BufferLength* doit être un nombre pair.  
  
 Si *FieldIdentifier* est un champ défini par le conducteur, l’application indique la nature du champ au gestionnaire de conducteur en définissant l’argument *De bufferLength.* *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si * \*ValuePtr* est un pointeur d’une chaîne de caractères, alors *BufferLength* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si * \*ValuePtr* est un pointeur à un tampon binaire, alors l’application place le résultat de la SQL_LEN_BINARY_ATTR(*longueur)* macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si * \*ValuePtr* est un pointeur à une valeur autre qu’une chaîne de caractère ou une chaîne binaire, alors *BufferLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si * \*ValuePtr* contient un type de données à durée fixe, *BufferLength* est soit SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_IS_USMALLINT, le cas échéant.  
  
 *StringLengthPtr*  
 [Sortie] Pointeur sur le tampon dans lequel retourner le nombre total d’octets (à l’exclusion du nombre d’octets requis pour le caractère de résiliation nulle) disponible pour revenir dans *'ValuePtr*.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA ou SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA est retourné si *RecNumber* est supérieur au nombre actuel de dossiers descripteur.  
  
 SQL_NO_DATA est retourné si *DescriptorHandle* est une poignée IRD et la déclaration est dans l’état préparé ou exécuté, mais il n’y avait pas de curseur ouvert associé à elle.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetDescField** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLGetDescField** et explique chacune dans le contexte de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *ValuePtr* n’était pas assez grand pour retourner l’ensemble du champ descripteur, de sorte que le champ a été tronqué. La longueur du champ descripteur non mensuré est retournée dans*le stringLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07009|Indice descripteur invalide|(DM) *L’argument de RecNumber* était égal à 0, l’attribut SQL_ATTR_USE_BOOKMARK déclaration était SQL_UB_OFF, et l’argument *de DescriptorHandle* était une poignée de l’IRD. (Cette erreur ne peut être retournée pour un descripteur explicitement attribué que si le descripteur est associé à une poignée de déclaration.)<br /><br /> *L’argument de FieldIdentifier* était un champ record, *l’argument de RecNumber* était 0, et *l’argument de DescriptorHandle* était une poignée d’IPD.<br /><br /> *L’argument de RecNumber* était inférieur à 0.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire requise pour supporter l’exécution ou l’achèvement de la fonction.|  
|HY007|Déclaration associée n’est pas préparée|*DescriptorHandle* a été associé à un *StatementHandle* en tant qu’IRD, et la poignée de déclaration associée n’avait pas été préparée ou exécutée.|  
|HY010|Erreur de séquence de fonction|(DM) *DescriptorHandle* a été associé à un *StatementHandle* pour lequel une fonction d’exécution asynchrone (pas celle-ci) a été appelée et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) *DescriptorHandle* a été associé à une *déclaration* pour laquelle **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *DescriptorHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLGetDescField** a été appelée.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY021|Informations descripteur incohérentes|Les champs de SQL_DESC_TYPE et de SQL_DESC_DATETIME_INTERVAL_CODE ne forment pas un type SQL ODBC valide, un type SQL valide spécifique au conducteur (pour les DPI) ou un type C ODBC valide (pour les APR ou les DR).|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) * \*ValuePtr* était une chaîne de caractères, et *BufferLength* était inférieur à zéro.|  
|HY091 HY091|Identifiant de champ descripteur invalide|*FieldIdentifier* n’était pas un champ défini par l’ODBC et n’était pas une valeur définie par la mise en œuvre.<br /><br /> *FieldIdentifier* n’était pas défini pour le *DescriptorHandle*.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLGetDescField** pour retourner la valeur d’un seul champ d’un enregistrement descripteur. Un appel à **SQLGetDescField** peut retourner le réglage de n’importe quel champ dans n’importe quel type de descripteur, y compris les champs d’en-tête, les champs d’enregistrement, et les champs de signets. Une application peut obtenir les paramètres de plusieurs champs dans les mêmes ou différents descripteurs, dans un ordre arbitraire, en faisant des appels répétés à **SQLGetDescField**. **SQLGetDescField** peut également être appelé à retourner les champs descripteur définis par le conducteur.  
  
 Pour des raisons de rendement, une demande ne doit pas appeler **SQLGetDescField** pour un IRD avant d’exécuter une déclaration.  
  
 Les paramètres de plusieurs champs qui décrivent le nom, le type de données et le stockage des données de colonne ou de paramètre peuvent également être récupérés en un seul appel à **SQLGetDescRec**. **SQLGetStmtAttr** peut être appelé à retourner le réglage d’un seul champ dans l’en-tête descripteur qui est également un attribut de déclaration. **SQLColAttribute**, **SQLDescribeCol**, et **SQLDescribeParam** retour record ou des champs de signets.  
  
 Lorsqu’une application appelle **SQLGetDescField** pour récupérer la valeur d’un champ qui n’est pas défini pour un type de descripteur particulier, la fonction renvoie SQL_SUCCESS mais la valeur retournée pour le champ n’est pas définie. Par exemple, appeler **SQLGetDescField** pour le SQL_DESC_NAME ou SQL_DESC_NULLABLE champ d’une DPA ou d’un ARD retournera SQL_SUCCESS mais une valeur indéfinie pour le champ.  
  
 Lorsqu’une application appelle **SQLGetDescField** pour récupérer la valeur d’un champ défini pour un type de descripteur particulier, mais qui n’a pas encore de valeur par défaut et qui n’a pas encore été défini, la fonction revient SQL_SUCCESS mais la valeur retournée pour le champ n’est pas définie. Pour plus d’informations sur l’initialisation des champs descripteur et les descriptions des champs, voir "Initialisation des champs descripteur" dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Pour plus d’informations sur les descripteurs, voir [Descriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtenir plusieurs champs descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Mise en place d’un champ descripteur unique|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Réglage de plusieurs champs descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
