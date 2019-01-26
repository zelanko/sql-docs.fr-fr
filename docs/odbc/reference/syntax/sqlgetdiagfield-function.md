---
title: SQLGetDiagField, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDiagField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagField
helpviewer_keywords:
- SQLGetDiagField function [ODBC]
ms.assetid: 1dbc4398-97a8-4585-bb77-1f7ea75e24c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13ab95c762573be002782c06615fc6f01317499f
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044296"
---
# <a name="sqlgetdiagfield-function"></a>Fonction SQLGetDiagField

**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLGetDiagField** retourne la valeur actuelle d’un champ d’un enregistrement de la structure de données de diagnostic (associé à un handle spécifié) qui contient des informations d’erreur, d’avertissement et d’état.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
SQLRETURN SQLGetDiagField(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     DiagIdentifier,  
     SQLPOINTER      DiagInfoPtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Un identificateur de type de handle qui décrit le type de handle pour lequel les tests de diagnostic sont requises. Doit prendre l'une des valeurs suivantes :  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 Handle SQL_HANDLE_DBC_INFO_TOKEN est utilisée uniquement par le Gestionnaire de pilotes et le pilote. Applications ne doivent pas utiliser ce type de handle. Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, consultez [développer la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Entrée] Un handle pour la structure de données de diagnostic, du type indiqué par *HandleType*. Si *HandleType* est SQL_HANDLE_ENV, *gérer* peut être partagé ou un handle d’environnement non partagé.  
  
 *RecNumber*  
 [Entrée] Indique que l’enregistrement de l’état à partir de laquelle l’application cherche des informations. Enregistrements d’état sont numérotées de 1. Si le *DiagIdentifier* argument indique n’importe quel champ de l’en-tête de diagnostics, *RecNumber* est ignoré. Si ce n’est pas le cas, il doit être supérieure à 0.  
  
 *DiagIdentifier*  
 [Entrée] Indique le champ du diagnostic dont la valeur doit être retournée. Pour plus d’informations, consultez le «*DiagIdentifier* Argument « section dans « Commentaires ».  
  
 *DiagInfoPtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner les informations de diagnostic. Le type de données dépend de la valeur de *DiagIdentifier*. Si *DiagInfoPtr* est de type entier, les applications doivent utiliser une mémoire tampon de SQLULEN et initialiser la valeur 0 avant d’appeler cette fonction, en tant que certains pilotes peut-être uniquement écrire la plus faible 32 ou 16 bits d’une mémoire tampon et laissez l’ordre le plus élevé- bit inchangé.  
  
 Si *DiagInfoPtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers laquelle pointée  *DiagInfoPtr*.  
  
 *BufferLength*  
 [Entrée] Si *DiagIdentifier* est un diagnostic définie par ODBC et *DiagInfoPtr* pointe vers une chaîne de caractères ou une mémoire tampon binaire, cet argument doit être la longueur de \* *DiagInfoPtr* . Si *DiagIdentifier* est un champ défini par ODBC et \* *DiagInfoPtr* est un entier, *BufferLength* est ignoré. Si la valeur dans  *\*DiagInfoPtr* est une chaîne Unicode (lors de l’appel **SQLGetDiagFieldW**), la *BufferLength* argument doit être un nombre pair.  
  
 Si *DiagIdentifier* est un champ défini par le pilote, l’application indique la nature du champ pour le Gestionnaire de pilotes en définissant le *BufferLength* argument. *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si *DiagInfoPtr* est un pointeur vers une chaîne de caractères, *BufferLength* est la longueur de la chaîne ou le SQL_NTS.  
  
-   Si *DiagInfoPtr* est un pointeur vers une mémoire tampon binaire, les emplacements de l’application le résultat de la SQL_LEN_BINARY_ATTR (*longueur*) macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si *DiagInfoPtr* est un pointeur vers une valeur autre qu’une chaîne de caractère ou binaire, *BufferLength* doit avoir la valeur SQL_IS_POINTER.  
  
-   Si  *\*DiagInfoPtr* contient un type de données de longueur fixe, *BufferLength* est SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_IS_USMALLINT, comme il convient.  
  
 *StringLengthPtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total d’octets (à l’exclusion du nombre d’octets requis pour le caractère de fin de la valeur null) disponibles à renvoyer dans \* *DiagInfoPtr*, pour les données caractères. Si le nombre d’octets à retourner est supérieur ou égal à *BufferLength*, le texte dans \* *DiagInfoPtr* est tronqué à *BufferLength* moins la longueur d’un caractère du caractère nul de terminaison.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_NO_DATA.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLGetDiagField** ne valide pas les enregistrements de diagnostic pour lui-même. Il utilise les valeurs de retournés suivantes pour signaler le résultat de sa propre exécution :  
  
-   SQL_SUCCESS : La fonction retournée avec succès les informations de diagnostic.  
  
-   SQL_SUCCESS_WITH_INFO : \**DiagInfoPtr* était trop petite pour contenir le champ de diagnostic demandé. Par conséquent, les données dans le champ de diagnostic a été tronquées. Pour déterminer qu’une troncation s’est produite, l’application doit comparer *BufferLength* au nombre réel d’octets disponibles, ce qui est écrite dans **StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE: Le handle a indiqué par *HandleType* et *gérer* n’était pas un handle valide.  
  
-   SQL_ERROR : Parmi les options suivantes s’est produite :  
  
    -   *Le DiagIdentifier* argument n’est pas une des valeurs valides.  
  
    -   *Le DiagIdentifier* argument a été SQL_DIAG_CURSOR_ROW_COUNT, SQL_DIAG_DYNAMIC_FUNCTION, SQL_DIAG_DYNAMIC_FUNCTION_CODE ou SQL_DIAG_ROW_COUNT, mais *gérer* n’était pas un descripteur d’instruction. (Le Gestionnaire de pilotes retourne ce diagnostic.)  
  
    -   *Le RecNumber* argument était négatif ou égal à 0 lorsque *DiagIdentifier* indiqué un champ à partir d’un enregistrement de diagnostic. *RecNumber* est ignoré pour les champs d’en-tête.  
  
    -   La valeur demandée était une chaîne de caractères et *BufferLength* était inférieur à zéro.  
  
    -   Lorsque vous utilisez la notification asynchrone, l’opération asynchrone sur le handle n’est pas complète.  
  
-   SQL_NO_DATA: *RecNumber* a été supérieur au nombre d’enregistrements de diagnostics qui existaient pour le handle spécifié dans *gérer.* La fonction retourne également SQL_NO_DATA pour n’importe quel résultat positif *RecNumber* si aucun enregistrement de diagnostic pour *gérer*.  
  
## <a name="comments"></a>Commentaires  
 Une application appelle généralement **SQLGetDiagField** pour accomplir une des trois objectifs :  
  
1.  Pour obtenir une erreur spécifique ou avertissement lorsqu’un appel de fonction a renvoyé SQL_ERROR ou SQL_SUCCESS_WITH_INFO (ou SQL_NEED_DATA pour le **SQLBrowseConnect** fonction).  
  
2.  Pour déterminer le nombre de lignes dans la source de données ont été affectées lorsque les opérations d’insertion, suppression ou mise à jour ont été effectuées par un appel à **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, ou **SQLSetPos** (à partir du champ d’en-tête SQL_DIAG_ROW_COUNT), ou pour déterminer le nombre de lignes qui existent dans le curseur ouvert actuel, si le pilote peut fournir ces informations (à partir de la Champ d’en-tête SQL_DIAG_CURSOR_ROW_COUNT).  
  
3.  Pour déterminer quelle fonction a été exécutée par un appel à **SQLExecDirect** ou **SQLExecute** (à partir des champs d’en-tête SQL_DIAG_DYNAMIC_FUNCTION et SQL_DIAG_DYNAMIC_FUNCTION_CODE).  
  
 Toute fonction ODBC peut valider zéro ou plusieurs enregistrements de diagnostic chaque fois qu’elle est appelée, donc une application peut appeler **SQLGetDiagField** après un appel de fonction ODBC. Il n’existe aucune limite au nombre d’enregistrements de diagnostic qui peuvent être stockés à tout moment. **SQLGetDiagField** récupère uniquement les informations de diagnostic plus récemment associées à la structure de données de diagnostic spécifiée dans le *gérer* argument. Si l’application appelle une fonction ODBC autre que **SQLGetDiagField** ou **SQLGetDiagRec**, des informations de diagnostic à partir d’un appel précédent avec le même handle sont perdues.  
  
 Une application peut analyser tous les enregistrements de diagnostics en incrémentant *RecNumber*, tant que **SQLGetDiagField** retourne SQL_SUCCESS. Le nombre d’enregistrements d’état est indiqué dans le champ d’en-tête SQL_DIAG_NUMBER. Les appels à **SQLGetDiagField** sont non destructives aux champs d’en-tête et un enregistrement. L’application peut appeler **SQLGetDiagField** ultérieurement pour récupérer un champ d’un enregistrement, tant qu’une fonction autres que les fonctions de Diagnostics n’a pas été appelée en attendant, ce qui serait de validation des enregistrements sur le même handle.  
  
 Une application peut appeler **SQLGetDiagField** pour retourner n’importe quel champ de diagnostic à tout moment, à l’exception SQL_DIAG_CURSOR_ROW_COUNT ou SQL_DIAG_ROW_COUNT, qui retourne SQL_ERROR si *gérer* n’est pas un descripteur d’instruction. Si tout autre champ de diagnostic n’est pas défini, l’appel à **SQLGetDiagField** retourne SQL_SUCCESS (fournie par aucun autre diagnostic n’est rencontrée) et une valeur non définie est retournée pour le champ.  
  
 Pour plus d’informations, consultez [à l’aide de SQLGetDiagRec et de SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) et [implémentation de SQLGetDiagRec et de SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Appel d’une API autre que celui qui est en cours d’exécution en mode asynchrone générera HY010 « Erreur de séquence de fonction ». Toutefois, l’enregistrement d’erreur ne peut pas être récupéré avant la fin de l’opération asynchrone.  
  
## <a name="handletype-argument"></a>Argument de HandleType  
 Chaque type de handle peut avoir des informations de diagnostic associées. Le *HandleType* argument indique le type de handle de *gérer*.  
  
 Certains champs d’en-tête et d’enregistrement ne peut pas être retournés pour environnement, connexion, instruction ou descripteur de handles. Ces handles pour lesquels un champ n’est pas applicable sont indiquées dans les sections « Champs d’en-tête » et « Champs de l’enregistrement » suivantes.  
  
 Si *HandleType* est SQL_HANDLE_ENV, *gérer* peut être soit un handle d’environnement partagé ou non partagé.  
  
 Aucun des champs de diagnostic spécifiques au pilote en-tête ne doivent être associés à un handle d’environnement.  
  
 Les champs d’en-tête uniquement de diagnostic qui sont définis pour un handle de descripteur sont SQL_DIAG_NUMBER et SQL_DIAG_RETURNCODE.  
  
## <a name="diagidentifier-argument"></a>Argument de DiagIdentifier  
 Cet argument indique l’identificateur de champ requis à partir de la structure de données de diagnostic. Si *RecNumber* est supérieur ou égal à 1, les données dans le champ décrivent les informations de diagnostic retournées par une fonction. Si *RecNumber* est 0, le champ est dans l’en-tête de la structure de données de diagnostic et par conséquent, contient les données se rapportant à l’appel de fonction qui a retourné les informations de diagnostic, pas à des informations spécifiques.  
  
 Pilotes peuvent définir en-tête spécifique au pilote et des champs d’enregistrement dans la structure de données de diagnostic.  
  
 Un ODBC 3 *.x* application fonctionne avec un ODBC 2 *.x* pilote sera en mesure d’appeler **SQLGetDiagField** uniquement avec un *DiagIdentifier* argument de SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME ou SQL_DIAG_SQLSTATE. Tous les autres champs de diagnostic retourne SQL_ERROR.  
  
## <a name="header-fields"></a>Champs d’en-tête  
 Les champs d’en-tête répertoriés dans le tableau suivant peuvent être inclus dans le *DiagIdentifier* argument.  
  
|DiagIdentifier|Type de retour|Valeur renvoyée|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN|Ce champ contient le nombre de lignes du curseur. Sa sémantique dépend de la **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES2 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 et SQL_STATIC_CURSOR_ATTRIBUTES2, qui indiquent les types d’informations nombre de lignes est disponibles pour chaque type de curseur (dans les bits SQL_CA2_CRC_EXACT et SQL_CA2_CRC_APPROXIMATE).<br /><br /> Le contenu de ce champ est défini uniquement pour les descripteurs d’instruction et uniquement après avoir **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelée. Appel **SQLGetDiagField** avec un *DiagIdentifier* de SQL_DIAG_CURSOR_ROW_COUNT sur autre qu’une instruction handle retourne SQL_ERROR.|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR *|Il s’agit d’une chaîne qui décrit l’instruction SQL qui a exécuté la fonction sous-jacente. (Consultez « Valeurs des champs de la fonction dynamique, », plus loin dans cette section, des valeurs spécifiques.) Le contenu de ce champ est défini uniquement pour les descripteurs d’instruction et uniquement après un appel à **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults**. Appel **SQLGetDiagField** avec un *DiagIdentifier* de SQL_DIAG_DYNAMIC_FUNCTION sur autre qu’une instruction handle retourne SQL_ERROR. La valeur de ce champ n’est pas définie avant un appel à **SQLExecute** ou **SQLExecDirect**.|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|Il s’agit d’un code numérique qui décrit l’instruction SQL qui a été exécutée par la fonction sous-jacente. (Consultez « Valeurs de la dynamique fonction champs, » plus loin dans cette section, pour une valeur spécifique.) Le contenu de ce champ est défini uniquement pour les descripteurs d’instruction et uniquement après un appel à **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults**. Appel **SQLGetDiagField** avec un *DiagIdentifier* de SQL_DIAG_DYNAMIC_FUNCTION_CODE sur autre qu’une instruction handle retourne SQL_ERROR. La valeur de ce champ n’est pas définie avant un appel à **SQLExecute** ou **SQLExecDirect**.|  
|SQL_DIAG_NUMBER|SQLINTEGER|Le nombre d’enregistrements d’état qui sont disponibles pour le handle spécifié.|  
|SQL_DIAG_RETURNCODE|SQLRETURN|Code de retour retournée par la fonction. Pour obtenir la liste des codes de retour, consultez [Codes de retour](../../../odbc/reference/develop-app/return-codes-odbc.md). Le pilote ne doit pas implémenter SQL_DIAG_RETURNCODE ; Il est toujours implémenté par le Gestionnaire de pilotes. Si aucune fonction n’a encore été appelée sur le *gérer*, SQL_SUCCESS est retournée pour SQL_DIAG_RETURNCODE.|  
|SQL_DIAG_ROW_COUNT|SQLLEN|Le nombre de lignes affectées par un insert, delete ou mise à jour effectuée par **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos**. Elle est définie par le pilote après un *spécification de curseur* a été exécutée. Le contenu de ce champ est défini uniquement pour les descripteurs d’instruction. Appel **SQLGetDiagField** avec un *DiagIdentifier* de SQL_DIAG_ROW_COUNT sur autre qu’une instruction handle retourne SQL_ERROR. Les données dans ce champ sont également renvoyées dans le *RowCountPtr* argument de **SQLRowCount**. Les données dans ce champ sont réinitialisées après chaque appel de fonction nondiagnostic, tandis que le nombre de lignes retournées par **SQLRowCount** reste la même jusqu'à ce que l’instruction est rétablie à l’état alloué ou préparé.|  
  
## <a name="record-fields"></a>Champs d’enregistrement  
 Les champs d’enregistrement répertoriés dans le tableau suivant peuvent être inclus dans le *DiagIdentifier* argument.  
  
|DiagIdentifier|Type de retour|Valeur renvoyée|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR *|Chaîne qui indique le document qui définit la partie de la classe de la valeur SQLSTATE dans cet enregistrement. Sa valeur est « ISO 9075 » pour tous les SQLSTATE définies par Open Group et l’interface de niveau d’appel ISO. Pour SQLSTATE de ODBC spécifiques (tous ceux dont la classe SQLSTATE est « Mi »), sa valeur est « ODBC 3.0 ».|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|Si le champ SQL_DIAG_ROW_NUMBER est un numéro de ligne valide dans un ensemble de lignes ou un ensemble de paramètres, ce champ contient la valeur qui représente le numéro de colonne du jeu de résultats ou le numéro de paramètre dans le jeu de paramètres. Jeu de résultats colonne numéros commencent toujours à 1 ; Si cet enregistrement d’état se rapporte à une colonne de signet, le champ peut être zéro. Numéros de paramètres commencent à 1. Il a la valeur SQL_NO_COLUMN_NUMBER si l’enregistrement de l’état n’est pas associé à un numéro de colonne ou paramètre. Si le pilote ne peut pas déterminer le numéro de colonne ou paramètre qui est associé à cet enregistrement, ce champ a la valeur SQL_COLUMN_NUMBER_UNKNOWN.<br /><br /> Le contenu de ce champ est défini uniquement pour les descripteurs d’instruction.|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR *|Chaîne qui indique le nom de la connexion concerne l’enregistrement de diagnostic. Ce champ est définie par le pilote. Pour les structures de données de diagnostic associés au handle d’environnement et pour les diagnostics ne sont pas liées à n’importe quelle connexion, ce champ est une chaîne de longueur nulle.|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR *|Un message d’information sur l’erreur ou l’avertissement. Ce champ est mis en forme comme décrit dans [Messages de Diagnostic](../../../odbc/reference/develop-app/diagnostic-messages.md). Il n’existe aucune longueur maximale pour le texte du message de diagnostic.|  
|SQL_DIAG_NATIVE|SQLINTEGER|Un code d’erreur natif spécifique à la source de données/pilote. S’il n’existe aucun code d’erreur natif, le pilote retourne 0.|  
|SQL_DIAG_ROW_NUMBER|SQLLEN|Ce champ contient le numéro de ligne dans l’ensemble de lignes, ou le numéro de paramètre dans le jeu de paramètres, à laquelle l’enregistrement de l’état est associé. Les numéros de ligne et de paramètre commencent à 1. Ce champ a la valeur SQL_NO_ROW_NUMBER si cet enregistrement de l’état n’est pas associé à un numéro de ligne ou un numéro de paramètre. Si le pilote ne peut pas déterminer le numéro de ligne ou le numéro de paramètre qui est associé à cet enregistrement, ce champ a la valeur SQL_ROW_NUMBER_UNKNOWN.<br /><br /> Le contenu de ce champ est défini uniquement pour les descripteurs d’instruction.|  
|SQL_DIAG_SERVER_NAME|SQLCHAR *|Chaîne qui indique le nom du serveur associé à l’enregistrement de diagnostic. Il est identique à la valeur retournée par un appel à **SQLGetInfo** avec l’option SQL_DATA_SOURCE_NAME. Pour les structures de données de diagnostic associés au handle d’environnement et pour les diagnostics ne sont pas liées à n’importe quel serveur, ce champ est une chaîne de longueur nulle.|  
|SQL_DIAG_SQLSTATE|SQLCHAR *|Un code de diagnostic SQLSTATE cinq caractères. Pour plus d’informations, consultez [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md).|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR *|Une chaîne avec le même format et les valeurs valides en tant que SQL_DIAG_CLASS_ORIGIN, qui identifie la partie de définition de la partie de la sous-classe du code SQLSTATE. Voici le SQLSTATE de ODBC spécifique pour lequel « ODBC 3.0 » est retournée :<br /><br /> 01 S 00, 01 S 01, 01 S 02, 01S06, 01 S 07, 07 S 01, 08 S 01, 21S01, 21S02, 25 S 01, 25S02, 25S03, 42S01, 42 S 02, 42S11, 42S12, 42S21, 42S22, HY095, HY097, HY098, HY099, HY100, HY101, HY105, HY107, HY109, HY110, HY111, HYT00, HYT01, IM001, IM002, IM003, IM004, IM005, IM006, IM007, IM008, IM010, IM011, IM012.|  
  
## <a name="values-of-the-dynamic-function-fields"></a>Valeurs des champs dynamiques (fonction)  
 Le tableau suivant décrit les valeurs de SQL_DIAG_DYNAMIC_FUNCTION et SQL_DIAG_DYNAMIC_FUNCTION_CODE qui s’appliquent à chaque type d’instruction SQL exécutée par un appel à **SQLExecute** ou **SQLExecDirect**. Le pilote peut ajouter des valeurs définies par le pilote à ceux répertoriés.  
  
|Instruction SQL<br /><br /> Exécutée|Valeur de<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION|Valeur de<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*alter-domain-statement*|« ALTER DOMAINE »|SQL_DIAG_ALTER_DOMAIN|  
|*alter-table-statement*|« ALTER TABLE »|SQL_DIAG_ALTER_TABLE|  
|*assertion-definition*|« CREATE ASSERTION »|SQL_DIAG_CREATE_ASSERTION|  
|*character-set-definition*|« CRÉER LE JEU DE CARACTÈRES »|SQL_DIAG_CREATE_CHARACTER_SET|  
|*collation-definition*|« CRÉER UN CLASSEMENT »|SQL_DIAG_CREATE_COLLATION|  
|*domainn-definition*|« CRÉER UN DOMAINE »|SQL_DIAG_CREATE_DOMAIN|
|*create-index-statement*|« CREATE INDEX »|SQL_DIAG_CREATE_INDEX|  
|*create-table-statement*|« CREATE TABLE »|SQL_DIAG_CREATE_TABLE|  
|*create-view-statement*|« CREATE VIEW »|SQL_DIAG_CREATE_VIEW|  
|*cursor-specification*|« SELECT CURSEUR »|SQL_DIAG_SELECT_CURSOR|  
|*delete-statement-positioned*|« CURSEUR DYNAMIQUE DE SUPPRESSION »|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*delete-statement-searched*|« DELETE WHERE »|SQL_DIAG_DELETE_WHERE|  
|*drop-assertion-statement*|« DROP ASSERTION »|SQL_DIAG_DROP_ASSERTION|  
|*drop-character-set-stmt*|« JEU DE CARACTÈRES DE DÉPÔT »|SQL_DIAG_DROP_CHARACTER_SET|  
|*drop-collation-statement*|« DROP CLASSEMENT »|SQL_DIAG_DROP_COLLATION|  
|*drop-domain-statement*|« DROP DOMAINE »|SQL_DIAG_DROP_DOMAIN|  
|*drop-index-statement*|« DROP INDEX »|SQL_DIAG_DROP_INDEX|  
|*drop-schema-statement*|« DROP SCHEMA »|SQL_DIAG_DROP_SCHEMA|  
|*drop-table-statement*|« DROP TABLE »|SQL_DIAG_DROP_TABLE|  
|*drop-translation-statement*|« DÉPÔT TRADUCTION »|SQL_DIAG_DROP_TRANSLATION|  
|*drop-view-statement*|« DROP VIEW »|SQL_DIAG_DROP_VIEW|  
|*grantstatement*|« GRANT »|SQL_DIAG_GRANT|
|*insert-statement*|« INSERT »|SQL_DIAG_INSERT|  
|*ODBC-procedure-extension*|« APPELER »|SQL_DIAG_ CALL|  
|*revoke-statement*|« REVOKE »|SQL_DIAG_REVOKE|  
|*schema-definition*|« CRÉER UN SCHÉMA »|SQL_DIAG_CREATE_SCHEMA|  
|*translation-definition*|« CRÉER LA TRADUCTION »|SQL_DIAG_CREATE_TRANSLATION|  
|*update-statement-positioned*|« MISE À JOUR DYNAMIQUE CURSOR »|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*update-statement-searched*|« UPDATE WHERE »|SQL_DIAG_UPDATE_WHERE|  
|Unknown|*chaîne vide*|SQL_DIAG_UNKNOWN_STATEMENT|  

<!--
These two malformed table rows were fixed by educated GUESS only.
Each pair starts with the original flawed row.
Flawed because treated as only two cells by HTML render,
and because missing info anyway.
Also, these flawed rows lacked '|' as their first nonWhitespace character (although markdown technically allows this omission, unfortunately).
Arguably the following SQL.H file shows the sequence of the flawed rows in the table was suboptimal also.

ftp://www.fpc.org/fpc32/VS6Disk1/VC98/INCLUDE/SQL.H

GeneMi , 2019/01/19
- - - - - - - - - - - - - -

n-definition*|"CREATE DOMAIN"|SQL_DIAG_CREATE_DOMAIN|  

|*domain-definition*|"CREATE DOMAIN"|SQL_DIAG_CREATE_DOMAIN|

-statement*|"GRANT"|SQL_DIAG_GRANT|  

|*grant-statement*|"GRANT"|SQL_DIAG_GRANT|

-->

## <a name="sequence-of-status-records"></a>Séquence d’enregistrements d’état

 Enregistrements d’état sont positionnés dans une séquence basée sur le numéro de ligne et le type du diagnostic. Le Gestionnaire de pilotes détermine l’ordre final dans lequel retourner les enregistrements d’état qu’il génère. Le pilote détermine l’ordre final dans lequel retourner les enregistrements d’état qu’il génère.  
  
 Si les enregistrements de diagnostic sont publiées par le Gestionnaire de pilotes et le pilote, le Gestionnaire de pilotes est responsable de leur classement.  
  
 S’il existe deux ou plusieurs enregistrements d’état, la séquence des enregistrements est déterminée par le numéro de ligne. Les règles suivantes s’appliquent à la détermination de la séquence des enregistrements de diagnostic en ligne :  
  
-   Les enregistrements qui ne correspondent pas à toutes les lignes apparaissent devant des enregistrements qui correspondent à une ligne particulière, étant donné que SQL_NO_ROW_NUMBER est défini comme étant -1.  
  
-   Les enregistrements pour lesquels le nombre de lignes est inconnu apparaissent devant tous les autres enregistrements, étant donné que SQL_ROW_NUMBER_UNKNOWN est défini comme étant -2.  
  
-   Pour tous les enregistrements qui se rapportent à des lignes spécifiques, les enregistrements sont triés par la valeur dans le champ SQL_DIAG_ROW_NUMBER. Toutes les erreurs et avertissements de la première ligne affectés sont répertoriés, et puis toutes les erreurs et avertissements de la prochaine ligne affectée et ainsi de suite.  
  
> [!NOTE]
>  Le 3 ODBC *.x* Gestionnaire de pilotes ne trie pas les enregistrements d’état dans la file d’attente diagnostic si 01 s 01 SQLSTATE (erreur de ligne) est retournée par un 2 ODBC *.x* pilote ou si 01 s 01 SQLSTATE (erreur de ligne) est retournée par une application ODBC 3 *.x* pilote lorsque **SQLExtendedFetch** est appelée ou **SQLSetPos** est appelée sur un curseur qui a été placé avec **SQLExtendedFetch** .  
  
 Dans chaque ligne, ou pour tous les enregistrements qui ne correspondent pas à une ligne ou pour lesquelles le nombre de lignes est inconnu, ou pour tous les enregistrements avec un nombre de lignes égal à SQL_NO_ROW_NUMBER, le premier enregistrement répertorié est déterminé à l’aide d’un ensemble de règles de tri. Après le premier enregistrement, l’ordre des enregistrements qui affectent une ligne n’est pas défini. Une application ne peut pas supposer que les erreurs précédent avertissements après le premier enregistrement. Applications doivent analyser la structure de données de diagnostic complet pour obtenir des informations complètes sur un appel à une fonction.  
  
 Les règles suivantes sont utilisées pour déterminer le premier enregistrement dans une ligne. L’enregistrement avec le rang le plus élevé est le premier enregistrement. La source d’un enregistrement (Gestionnaire de pilotes, pilotes, passerelle et ainsi de suite) constitue toutefois pas lorsque les enregistrements de classement.  
  
-   **Erreurs** enregistrements d’état qui décrivent les erreurs ont le rang le plus élevé. Les règles suivantes sont appliquées pour trier les erreurs :  
  
    -   Les enregistrements qui indiquent un échec de la transaction ou l’échec de la transaction possible outrank tous les autres enregistrements.  
  
    -   Si deux ou plusieurs enregistrements décrivent la condition d’erreur, SQLSTATE défini par la spécification Open groupe CLI (classes 03 via HZ) outrank SQLSTATE de ODBC et pilote définis.  
  
-   **Les valeurs de données non défini par l’implémentation** enregistrements d’état qui décrivent les valeurs des données de non définis par le pilote (classe 02) ont la deuxième rang le plus élevé.  
  
-   **Avertissements** enregistrements d’état qui décrivent les avertissements (classe 01) ont le rang le plus bas. Si deux ou plusieurs enregistrements décrivent la même condition d’avertissement, SQLSTATE défini par la spécification Open CLI de groupe, l’avertissement outrank SQLSTATE définies par ODBC et définis par le pilote.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtention de plusieurs champs d’une structure de données de diagnostic|[SQLGetDiagRec, fonction](sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
