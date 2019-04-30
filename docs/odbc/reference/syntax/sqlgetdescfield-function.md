---
title: SQLGetDescField, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6762eb4ea9b350a76fc794fa7074af2a107b511
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258925"
---
# <a name="sqlgetdescfield-function"></a>Fonction SQLGetDescField
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetDescField** renvoie le paramètre actuel ou la valeur d’un champ unique d’un enregistrement de descripteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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
 [Entrée] Handle du descripteur.  
  
 *RecNumber*  
 [Entrée] Indique que l’enregistrement de descripteur à partir de laquelle l’application cherche des informations. Enregistrements de descripteurs sont numérotés de 0, avec le numéro d’enregistrement 0 en cours de l’enregistrement de signet. Si le *FieldIdentifier* argument indique un champ d’en-tête, *RecNumber* est ignoré. Si *RecNumber* est inférieure ou égale à SQL_DESC_COUNT mais la ligne ne contient pas de données pour une colonne ou paramètre, un appel à **SQLGetDescField** retourne les valeurs par défaut des champs. (Pour plus d’informations, consultez « Initialisation de champs de descripteur » dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *FieldIdentifier*  
 [Entrée] Indique le champ du descripteur dont la valeur doit être retournée. Pour plus d’informations, consultez le «*FieldIdentifier* Argument « section [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 *ValuePtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner les informations du descripteur. Le type de données dépend de la valeur de *FieldIdentifier*.  
  
 Si *ValuePtr* est de type entier, les applications doivent utiliser une mémoire tampon de SQLULEN et initialiser la valeur 0 avant d’appeler cette fonction comme certains pilotes peut-être uniquement écrire la plus faible 32 ou 16 bits d’une mémoire tampon et laisser le bit d’ordre supérieur inchangé.  
  
 Si *ValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers laquelle pointée  *ValuePtr*.  
  
 *BufferLength*  
 [Entrée] Si *FieldIdentifier* est un champ défini par ODBC et *ValuePtr* pointe vers une chaîne de caractères ou une mémoire tampon binaire, cet argument doit être la longueur de \* *ValuePtr*. Si *FieldIdentifier* est un champ défini par ODBC et \* *ValuePtr* est un entier, *BufferLength* est ignoré. Si la valeur dans  *\*ValuePtr* est d’un type de données Unicode (lors de l’appel **SQLGetDescFieldW**), la *BufferLength* argument doit être un nombre pair.  
  
 Si *FieldIdentifier* est un champ défini par le pilote, l’application indique la nature du champ pour le Gestionnaire de pilotes en définissant le *BufferLength* argument. *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si  *\*ValuePtr* est un pointeur vers une chaîne de caractères, puis *BufferLength* est la longueur de la chaîne ou le SQL_NTS.  
  
-   Si  *\*ValuePtr* est un pointeur vers une mémoire tampon binaire, puis l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur*) macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si  *\*ValuePtr* est un pointeur vers une valeur autre qu’une chaîne de caractère ou binaire, puis *BufferLength* doit avoir la valeur SQL_IS_POINTER.  
  
-   Si  *\*ValuePtr* est contient un type de données de longueur fixe, puis *BufferLength* est SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_IS_USMALLINT, comme il convient.  
  
 *StringLengthPtr*  
 [Sortie] Pointeur vers la mémoire tampon dans lequel retourner le nombre total d’octets (à l’exclusion du nombre d’octets requis pour le caractère de fin de la valeur null) disponibles à renvoyer dans **ValuePtr*.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA ou SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA soit retourné si *RecNumber* est supérieur au nombre actuel d’enregistrements de descripteurs.  
  
 SQL_NO_DATA soit retourné si *DescriptorHandle* est un descripteur IRD et l’instruction est dans un état préparé ou exécuté, mais il n’a aucun curseur ouvert associé.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetDescField** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLGetDescField** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|La mémoire tampon \* *ValuePtr* n’était pas assez élevé pour renvoyer le champ de descripteur entière, donc le champ a été tronqué. La longueur du champ de descripteur non tronqué est retournée dans **StringLengthPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07009|Index de descripteur non valide|(DM) le *RecNumber* argument était égal à 0, l’attribut d’instruction SQL_ATTR_USE_BOOKMARK était SQL_UB_OFF et le *DescriptorHandle* argument était un descripteur IRD. (Cette erreur peut être retournée pour un descripteur alloué explicitement uniquement si le descripteur est associé à un descripteur d’instruction.)<br /><br /> Le *FieldIdentifier* argument était un champ d’enregistrement, le *RecNumber* argument était égale à 0 et le *DescriptorHandle* argument était un descripteur IPD.<br /><br /> Le *RecNumber* argument était inférieure à 0.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY007|L’instruction associée n’est pas préparée.|*DescriptorHandle* a été associé à un *au paramètre StatementHandle* comme un IRD et l’instruction associée handle n'avait pas été préparé ou exécuté.|  
|HY010|Erreur de séquence de fonction|(DM) *DescriptorHandle* a été associé à un *au paramètre StatementHandle* pour laquelle une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée et l’exécution quand cette fonction a été appelée.<br /><br /> (DM) *DescriptorHandle* a été associé à un *au paramètre StatementHandle* pour lequel **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, ou **SQLSetPos** a été appelée et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *DescriptorHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLGetDescField** fonction a été appelée.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY021|Informations de descripteur incohérentes|Les champs SQL_DESC_TYPE et SQL_DESC_DATETIME_INTERVAL_CODE ne forment pas un type ODBC SQL valide, un type valide de SQL spécifiques au pilote (pour IPD) ou un type ODBC C valide (pour ou à partir d’APD).|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM)  *\*ValuePtr* était une chaîne de caractères, et *BufferLength* était inférieur à zéro.|  
|HY091|Identificateur de champ de descripteur non valide|*FieldIdentifier* n’était pas un champ défini par ODBC et n’était pas une valeur définie par l’implémentation.<br /><br /> *FieldIdentifier* a été non définie pour le *DescriptorHandle*.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLGetDescField** pour retourner la valeur d’un champ unique d’un enregistrement de descripteur. Un appel à **SQLGetDescField** peut retourner la valeur de n’importe quel champ dans n’importe quel type de descripteur, y compris les champs d’en-tête, les champs d’enregistrement et les champs de signet. Une application peut obtenir les paramètres de plusieurs champs dans les descripteurs identiques ou différents, dans un ordre arbitraire, en effectuant des appels répétés à **SQLGetDescField**. **SQLGetDescField** peut également être appelée pour retourner les champs de descripteur définis par le pilote.  
  
 Pour des raisons de performances, une application ne doit pas appeler **SQLGetDescField** pour un IRD avant d’exécuter une instruction.  
  
 Les paramètres de plusieurs champs qui décrivent le nom, le type de données et le stockage des données de colonne ou paramètre peuvent également être récupérées dans un seul appel à **SQLGetDescRec**. **SQLGetStmtAttr** peut être appelée pour retourner la valeur d’un champ unique dans l’en-tête de descripteur qui est également un attribut d’instruction. **SQLColAttribute**, **SQLDescribeCol**, et **SQLDescribeParam** renvoie les champs d’enregistrement ou de signet.  
  
 Lorsqu’une application appelle **SQLGetDescField** pour récupérer la valeur d’un champ qui n’est pas défini pour un type particulier de descripteur, la fonction retourne SQL_SUCCESS, mais la valeur retournée pour le champ n’est pas définie. Par exemple, l’appel **SQLGetDescField** pour le champ SQL_DESC_NAME ou SQL_DESC_NULLABLE d’un APD ou d’ARD retourne SQL_SUCCESS, mais une valeur non définie pour le champ.  
  
 Lorsqu’une application appelle **SQLGetDescField** pour récupérer la valeur d’un champ qui est défini pour un type particulier de descripteur, mais qui n’a aucune valeur par défaut et n’a pas encore été définie, la fonction retourne SQL_SUCCESS, mais la valeur retournée pour le champ n’est pas défini. Pour plus d’informations sur l’initialisation de champs de descripteur et les descriptions des champs, consultez « Initialisation de champs de descripteur » dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Pour plus d’informations sur les descripteurs, consultez [descripteurs](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtention de plusieurs champs de descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Définition d’un champ de descripteur unique|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Définition de plusieurs champs de descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
