---
title: Fonction SQLGetDiagField (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a26319868a4b94b895da73d39b284f612fe35889
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285429"
---
# <a name="sqlgetdiagfield-function"></a>Fonction SQLGetDiagField

**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetDiagField** retourne la valeur actuelle d’un champ d’un enregistrement de la structure de données diagnostiques (associée à une poignée spécifiée) qui contient des informations d’erreur, d’avertissement et d’état.  
  
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
 [Entrée] Un identifiant de type manche qui décrit le type de poignée pour laquelle des diagnostics sont nécessaires. Doit prendre l'une des valeurs suivantes :  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN poignée n’est utilisée que par le Gestionnaire du conducteur et le conducteur. Les applications ne doivent pas utiliser ce type de poignée. Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, voir [Developing Connection-Pool Awareness in an ODBC Driver](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Entrée] Une poignée pour la structure de données diagnostiques, du type indiqué par *HandleType*. Si *HandleType* est SQL_HANDLE_ENV, *Handle* peut être soit une poignée d’environnement partagée ou non partagée.  
  
 *RecNumber*  
 [Entrée] Indique le dossier d’état à partir duquel la demande recherche des informations. Les dossiers d’état sont numérotés à partir de 1. Si l’argument *diagIdentificateur* indique n’importe quel champ de l’en-tête de diagnostic, *RecNumber* est ignoré. Si ce n’est pas le cas, il devrait être plus de 0.  
  
 *DiagIdentificateur*  
 [Entrée] Indique le domaine du diagnostic dont la valeur doit être retournée. Pour plus d’informations, consultez la section «*DiagIdentifier* Argument » dans « Commentaires ».  
  
 *DiagInfoPtr (en anglais)*  
 [Sortie] Pointeur vers un tampon dans lequel retourner les informations diagnostiques. Le type de données dépend de la valeur de *DiagIdentifier*. Si *DiagInfoPtr* est un type d’intégrateur, les applications doivent utiliser un tampon de SQLULEN et initialiser la valeur à 0 avant d’appeler cette fonction, car certains conducteurs ne peuvent écrire que le plus bas 32 bits ou 16 bits d’un tampon et laisser le bit de l’ordre supérieur inchangé.  
  
 Si *DiagInfoPtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de désinsation pour les données de caractère) disponible pour revenir dans le tampon indiqué par *DiagInfoPtr*.  
  
 *BufferLength*  
 [Entrée] Si *DiagIdentifier* est un diagnostic défini par ODBC et *DiagInfoPtr* pointe vers une chaîne \*de caractères ou un tampon binaire, cet argument devrait être la longueur de *DiagInfoPtr*. Si *DiagIdentifier* est un champ défini \*par ODBC et *que DiagInfoPtr* est un intégrateur, *BufferLength* est ignoré. Si la valeur de * \*DiagInfoPtr* est une chaîne Unicode (lorsqu’elle appelle **SQLGetDiagFieldW**), l’argument *BufferLength* doit être un nombre pair.  
  
 Si *DiagIdentifier* est un champ défini par le conducteur, l’application indique la nature du champ au gestionnaire de conducteur en définissant l’argument *BufferLength.* *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si *DiagInfoPtr* est un pointeur d’une chaîne de caractères, *BufferLength* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si *DiagInfoPtr* est un pointeur vers un tampon binaire, l’application place le résultat de la SQL_LEN_BINARY_ATTR(*longueur)* macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si *DiagInfoPtr* est un pointeur à une valeur autre qu’une chaîne de caractères ou une chaîne binaire, *BufferLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si * \*DiagInfoPtr* contient un type de données à durée fixe, *BufferLength* est SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_IS_USMALLINT, le cas échéant.  
  
 *StringLengthPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total d’octets (à l’exclusion \*du nombre d’octets requis pour le caractère de résiliation nulle) disponible pour revenir dans *DiagInfoPtr*, pour les données de caractère. Si le nombre d’octets disponibles pour revenir est supérieur ou \*égal à *BufferLength*, le texte dans *DiagInfoPtr* est tronqué à *BufferLength* moins la longueur d’un caractère de non-terminaison.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_NO_DATA.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLGetDiagField** ne poste pas de dossiers diagnostiques pour lui-même. Il utilise les valeurs de retour suivantes pour signaler le résultat de sa propre exécution :  
  
-   SQL_SUCCESS : La fonction a retourné avec succès l’information diagnostique.  
  
-   SQL_SUCCESS_WITH_INFO: \* *DiagInfoPtr* était trop petit pour tenir le domaine de diagnostic demandé. Par conséquent, les données dans le domaine du diagnostic ont été tronquées. Pour déterminer qu’une troncation s’est produite, l’application doit comparer *BufferLength* au nombre réel d’octets disponibles, qui est écrit à*StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE : La poignée indiquée par *HandleType* et *Handle* n’était pas une poignée valide.  
  
-   SQL_ERROR : L’un des éléments suivants s’est produit :  
  
    -   *L’argument de DiagIdentifier* n’était pas l’une des valeurs valides.  
  
    -   *L’argument de DiagIdentifier* était SQL_DIAG_CURSOR_ROW_COUNT, SQL_DIAG_DYNAMIC_FUNCTION, SQL_DIAG_DYNAMIC_FUNCTION_CODE, ou SQL_DIAG_ROW_COUNT, mais *Handle* n’était pas une poignée de déclaration. (Le Driver Manager retourne ce diagnostic.)  
  
    -   *L’argument de RecNumber* était négatif ou 0 quand *DiagIdentifier* a indiqué un domaine d’un dossier diagnostique. *RecNumber* est ignoré pour les champs d’en-tête.  
  
    -   La valeur demandée était une chaîne de caractères et *BufferLength* était inférieure à zéro.  
  
    -   Lors de l’utilisation de la notification asynchrone, l’opération asynchrone sur la poignée n’était pas terminée.  
  
-   SQL_NO_DATA : *RecNumber* était supérieur au nombre de dossiers diagnostiques qui existaient pour la poignée spécifiée dans *Handle.* La fonction renvoie également SQL_NO_DATA pour tout *RecNumber* positif s’il n’y a pas de dossiers diagnostiques pour *handle*.  
  
## <a name="comments"></a>Commentaires  
 Une application appelle généralement **SQLGetDiagField** pour atteindre l’un des trois objectifs :  
  
1.  Pour obtenir des informations spécifiques d’erreur ou d’avertissement lorsqu’un appel de fonction est retourné SQL_ERROR ou SQL_SUCCESS_WITH_INFO (ou SQL_NEED_DATA pour la fonction **SQLBrowseConnect).**  
  
2.  Pour déterminer le nombre de lignes dans la source de données qui ont été affectées lors de l’insertion, de la suppression ou de la mise à jour des opérations ont été effectuées avec un appel à **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** (du champ d’en-tête SQL_DIAG_ROW_COUNT), ou pour déterminer le nombre de lignes qui existent dans le curseur ouvert actuel, si le conducteur peut fournir cette information (à partir du champ d’en-tête SQL_DIAG_CURSOR_ROW_COUNT).  
  
3.  Déterminer quelle fonction a été exécutée par un appel à **SQLExecDirect** ou **SQLExecute** (à partir des champs d’en-tête SQL_DIAG_DYNAMIC_FUNCTION et SQL_DIAG_DYNAMIC_FUNCTION_CODE).  
  
 Toute fonction ODBC peut publier des enregistrements diagnostiques nuls ou plus chaque fois qu’elle est appelée, de sorte qu’une application peut appeler **SQLGetDiagField** après tout appel de fonction ODBC. Il n’y a pas de limite au nombre de dossiers diagnostiques qui peuvent être stockés à tout moment. **SQLGetDiagField** ne récupère que les informations diagnostiques les plus récentes associées à la structure de données diagnostiques spécifiées dans l’argument *de handle.* Si l’application appelle une fonction ODBC autre que **SQLGetDiagField** ou **SQLGetDiagRec**, toute information diagnostique d’un appel précédent avec la même poignée est perdue.  
  
 Une application peut numériser tous les dossiers diagnostiques en incrémentant *RecNumber*, tant que **SQLGetDiagField** retourne SQL_SUCCESS. Le nombre de dossiers d’état est indiqué dans le champ d’en-tête SQL_DIAG_NUMBER. Les appels à **SQLGetDiagField** ne sont pastructifs pour les champs d’en-tête et d’enregistrement. L’application peut appeler **SQLGetDiagField** à nouveau plus tard pour récupérer un champ d’un enregistrement, tant qu’une fonction autre que les fonctions diagnostiques n’a pas été appelé dans l’intervalle, qui afficherait des enregistrements sur la même poignée.  
  
 Une application peut appeler **SQLGetDiagField** pour retourner n’importe quel champ de diagnostic à tout moment, sauf pour SQL_DIAG_CURSOR_ROW_COUNT ou SQL_DIAG_ROW_COUNT, qui retournera SQL_ERROR si *handle* n’est pas une poignée de déclaration. Si un autre domaine de diagnostic n’est pas défini, l’appel à **SQLGetDiagField** retournera SQL_SUCCESS (à condition qu’aucun autre diagnostic ne soit rencontré) et une valeur indéfinie est retournée pour le champ.  
  
 Pour plus d’informations, voir [à l’aide de SQLGetDiagRec et SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) et [mise en œuvre SQLGetDiagRec et SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Appeler une API autre que celle qui est exécuté asynchrone générera HY010 "Erreur de séquence de fonction". Toutefois, l’enregistrement d’erreur ne peut pas être récupéré avant la fin de l’opération asynchrone.  
  
## <a name="handletype-argument"></a>HandleType Argument  
 Chaque type de poignée peut avoir des informations diagnostiques qui lui sont associées. *L’argument HandleType* indique le type de poignée de *poignée*.  
  
 Certains champs d’en-tête et d’enregistrement ne peuvent pas être retournés pour l’environnement, la connexion, l’instruction et les poignées descripteur. Les poignées pour lesquelles un champ n’est pas applicable sont indiquées dans les sections « Champs d’en-tête » et « Champs d’enregistrement » suivantes.  
  
 Si *HandleType* est SQL_HANDLE_ENV, *Handle* peut être une poignée d’environnement partagée ou non partagée.  
  
 Aucun champ de diagnostic d’en-tête spécifique au conducteur ne doit être associé à une poignée d’environnement.  
  
 Les seuls champs d’en-tête diagnostiques qui sont définis pour une poignée descripteur sont SQL_DIAG_NUMBER et SQL_DIAG_RETURNCODE.  
  
## <a name="diagidentifier-argument"></a>Argument de diagIdentificateur  
 Cet argument indique l’identifiant du champ requis à partir de la structure de données diagnostiques. Si *RecNumber* est supérieur ou égal à 1, les données sur le terrain décrivent l’information diagnostique retournée par une fonction. Si *RecNumber* est 0, le champ est dans l’en-tête de la structure de données diagnostiques et contient donc des données relatives à l’appel de fonction qui a retourné l’information diagnostique, pas à l’information spécifique.  
  
 Les conducteurs peuvent définir les champs d’en-tête et d’enregistrement spécifiques au conducteur dans la structure de données diagnostiques.  
  
 Une application ODBC 3 *.x* travaillant avec un pilote ODBC 2 *.x* ne pourra appeler **SQLGetDiagField** qu’avec un argument *diagIdentificateur* de SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME ou SQL_DIAG_SQLSTATE. Tous les autres domaines diagnostiques seront de retour SQL_ERROR.  
  
## <a name="header-fields"></a>Champs d’en-têtes  
 Les champs d’en-tête énumérés dans le tableau suivant peuvent être inclus dans l’argument *DiagIdentifier.*  
  
|DiagIdentificateur|Type de retour|Retours|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN (SQLLEN)|Ce champ contient le nombre de rangées dans le curseur. Sa sémantique dépend des types d’information **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 et SQL_STATIC_CURSOR_ATTRIBUTES2, qui indiquent quels comptes de rangée sont disponibles pour chaque type de curseur (dans les bits SQL_CA2_CRC_EXACT et SQL_CA2_CRC_APPROXIMATE).<br /><br /> Le contenu de ce champ est défini uniquement pour les poignées de déclaration et seulement après **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé. Appeler **SQLGetDiagField** avec un *DiagIdentificateur* de SQL_DIAG_CURSOR_ROW_COUNT sur autre qu’une poignée de déclaration sera de retour SQL_ERROR.|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR - France|Il s’agit d’une chaîne qui décrit la déclaration SQL que la fonction sous-jacente exécutée. (Voir « Valeurs des champs de fonction dynamique », plus tard dans cette section, pour des valeurs spécifiques.) Le contenu de ce champ est défini uniquement pour les poignées de déclaration et seulement après un appel à **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults**. Appeler **SQLGetDiagField** avec un *DiagIdentificateur* de SQL_DIAG_DYNAMIC_FUNCTION sur autre qu’une poignée de déclaration sera de retour SQL_ERROR. La valeur de ce domaine n’est pas définie avant un appel à **SQLExecute** ou **SQLExecDirect**.|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|Il s’agit d’un code numérique qui décrit la déclaration SQL qui a été exécutée par la fonction sous-jacente. (Voir « Valeurs des champs de fonction dynamiques », plus tard dans cette section, pour une valeur spécifique.) Le contenu de ce champ est défini uniquement pour les poignées de déclaration et seulement après un appel à **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults**. Appeler **SQLGetDiagField** avec un *DiagIdentificateur* de SQL_DIAG_DYNAMIC_FUNCTION_CODE sur autre qu’une poignée de déclaration sera de retour SQL_ERROR. La valeur de ce domaine n’est pas définie avant un appel à **SQLExecute** ou **SQLExecDirect**.|  
|SQL_DIAG_NUMBER|SQLINTEGER|Nombre d’enregistrements d’état disponibles pour la poignée spécifiée.|  
|SQL_DIAG_RETURNCODE|SQLRETURN|Code de retour retourné par la fonction. Pour une liste de codes de retour, voir [codes de retour](../../../odbc/reference/develop-app/return-codes-odbc.md). Le conducteur n’a pas à mettre en œuvre SQL_DIAG_RETURNCODE; il est toujours mis en œuvre par le Driver Manager. Si aucune fonction n’a encore été appelée sur la *poignée,* SQL_SUCCESS sera retourné pour SQL_DIAG_RETURNCODE.|  
|SQL_DIAG_ROW_COUNT|SQLLEN (SQLLEN)|Le nombre de lignes touchées par un encart, supprimer ou mettre à jour effectué par **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos**. Il est défini par le conducteur après *l’exécution d’une spécification curseur.* Le contenu de ce champ n’est défini que pour les poignées de relevés. Appeler **SQLGetDiagField** avec un *DiagIdentificateur* de SQL_DIAG_ROW_COUNT sur autre qu’une poignée de déclaration sera de retour SQL_ERROR. Les données dans ce domaine sont également retournées dans l’argument *RowCountPtr* de **SQLRowCount**. Les données dans ce domaine sont réinitialisées après chaque appel de fonction non diagnostiquée, tandis que le nombre de rangées retournés par **SQLRowCount** reste le même jusqu’à ce que la déclaration soit remise à l’état préparé ou attribué.|  
  
## <a name="record-fields"></a>Champs d’enregistrement  
 Les champs d’enregistrement énumérés dans le tableau suivant peuvent être inclus dans l’argument *DiagIdentifier.*  
  
|DiagIdentificateur|Type de retour|Retours|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR - France|Une chaîne qui indique le document qui définit la partie de classe de la valeur SQLSTATE dans cet enregistrement. Sa valeur est "ISO 9075" pour toutes les SQLSTATEs définies par Open Group et ISO interface de niveau d’appel. Pour les SQLSTATES spécifiques à L’ODBC (tous ceux dont la classe SQLSTATE est « IM »), sa valeur est « ODBC 3.0 ».|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|Si le champ SQL_DIAG_ROW_NUMBER est un numéro de ligne valide dans un ensemble de lignes ou un ensemble de paramètres, ce champ contient la valeur qui représente le numéro de colonne dans l’ensemble de résultat ou le nombre de paramètres dans l’ensemble des paramètres. Les numéros de colonne de jeu de résultat commencent toujours à 1 ; si cet enregistrement d’état se rapporte à une colonne de signets, le champ peut être nul. Les nombres de paramètres commencent à 1. Il a la valeur SQL_NO_COLUMN_NUMBER si l’enregistrement d’état n’est pas associé à un numéro de colonne ou un numéro de paramètre. Si le conducteur ne peut pas déterminer le numéro de colonne ou le numéro de paramètre associé à cet enregistrement, ce champ a la valeur SQL_COLUMN_NUMBER_UNKNOWN.<br /><br /> Le contenu de ce champ n’est défini que pour les poignées de relevés.|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR - France|Une chaîne qui indique le nom de la connexion à laquelle le dossier diagnostique se rapporte. Ce champ est défini par le conducteur. Pour les structures de données diagnostiques associées à la poignée de l’environnement et pour les diagnostics qui ne se rapportent à aucune connexion, ce champ est une chaîne de zéro longueur.|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR - France|Un message d’information sur l’erreur ou l’avertissement. Ce domaine est formaté comme décrit dans [Diagnostic Messages](../../../odbc/reference/develop-app/diagnostic-messages.md). Il n’y a pas de longueur maximale au texte du message diagnostique.|  
|SQL_DIAG_NATIVE|SQLINTEGER|Un code d’erreur natif spécifique à la source de conducteur/données. S’il n’y a pas de code d’erreur natif, le conducteur renvoie 0.|  
|SQL_DIAG_ROW_NUMBER|SQLLEN (SQLLEN)|Ce champ contient le numéro de ligne dans le jeu de ligne, ou le nombre de paramètres dans l’ensemble des paramètres, avec lequel l’enregistrement d’état est associé. Les numéros de ligne et les nombres de paramètres commencent par 1. Ce champ a la valeur SQL_NO_ROW_NUMBER si ce dossier d’état n’est pas associé à un numéro de ligne ou un numéro de paramètre. Si le conducteur ne peut pas déterminer le numéro de ligne ou le numéro de paramètre associé à cet enregistrement, ce champ a la valeur SQL_ROW_NUMBER_UNKNOWN.<br /><br /> Le contenu de ce champ n’est défini que pour les poignées de relevés.|  
|SQL_DIAG_SERVER_NAME|SQLCHAR - France|Une chaîne qui indique le nom du serveur à lequel le dossier diagnostique se rapporte. C’est la même chose que la valeur retournée pour un appel à **SQLGetInfo** avec l’option SQL_DATA_SOURCE_NAME. Pour les structures de données diagnostiques associées à la poignée de l’environnement et pour les diagnostics qui ne se rapportent à aucun serveur, ce champ est une chaîne de zéro longueur.|  
|SQL_DIAG_SQLSTATE|SQLCHAR - France|Un code de diagnostic SQLSTATE à cinq caractères. Pour plus d’informations, voir [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md).|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR - France|Une chaîne avec le même format et les valeurs valides que SQL_DIAG_CLASS_ORIGIN, qui identifie la partie déterminante de la partie sous-classe du code SQLSTATE. Les SQLSTATES spécifiques à l’ODBC pour lesquels « ODBC 3.0 » est retourné sont les suivants :<br /><br /> 01S00, 01S01, 01S02, 01S06, 01S07, 07S01, 08S01, 21S01, 21S02, 25S01, 25S02, 25S03, 42S01, 42S02, 42S11, 42S12, 42S21, 42S22, HY095, HY097, HY098, HY099, HY099, HY099, HY099, HY099, HY099, HY099, HY099, HY099, HY099, HY099, HY099 HY100, HY101, HY105, HY107, HY109, HY110, HY111, HYT00, HYT01, IM001, IM002, IM003, IM004, IM005, IM006, IM007, IM008, IM010, IM011, IM012.|  
  
## <a name="values-of-the-dynamic-function-fields"></a>Valeurs des champs de fonction dynamique  
 Le tableau suivant décrit les valeurs de SQL_DIAG_DYNAMIC_FUNCTION et de SQL_DIAG_DYNAMIC_FUNCTION_CODE qui s’appliquent à chaque type de déclaration SQL exécutée par un appel à **SQLExecute** ou **SQLExecDirect**. Le conducteur peut ajouter des valeurs définies par le conducteur à celles énumérées.  
  
|Instruction SQL<br /><br /> Exécuté|Valeur de <br /><br /> SQL_DIAG_DYNAMIC_FUNCTION|Valeur de <br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*alter-domaine-déclaration*|"DOMAINE ALTERNATIF"|SQL_DIAG_ALTER_DOMAIN|  
|*alter-table-déclaration*|"ALTER TABLE"|SQL_DIAG_ALTER_TABLE|  
|*affirmation-définition*|"CRÉER L’AFFIRMATION"|SQL_DIAG_CREATE_ASSERTION|  
|*définition des caractères*|"CRÉER UN ENSEMBLE DE CARACTÈRES"|SQL_DIAG_CREATE_CHARACTER_SET|  
|*collation-définition*|"CRÉER LA COLLATION"|SQL_DIAG_CREATE_COLLATION|  
|*domainn-définition*|"CRÉER LE DOMAINE"|SQL_DIAG_CREATE_DOMAIN|
|*créer-index-déclaration*|"CRÉER L’INDICE"|SQL_DIAG_CREATE_INDEX|  
|*créer-table-déclaration*|"CRÉER TABLE"|SQL_DIAG_CREATE_TABLE|  
|*créer-view-statement*|"CRÉER UNE VUE"|SQL_DIAG_CREATE_VIEW|  
|*spécification curseur-spécifique*|"SÉLECTIONNEZ CURSEUR"|SQL_DIAG_SELECT_CURSOR|  
|*supprimer-déclaration-positionné*|"DYNAMIC SUPPRIMER CURSEUR"|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*supprimer-déclaration-recherché*|"SUPPRIMER OÙ"|SQL_DIAG_DELETE_WHERE|  
|*drop-assertion-déclaration*|"AFFIRMATION DE CHUTE"|SQL_DIAG_DROP_ASSERTION|  
|*drop-character-set-stmt*|"DROP CHARACTER SET"|SQL_DIAG_DROP_CHARACTER_SET|  
|*drop-collation-déclaration*|"DROP COLLATION"|SQL_DIAG_DROP_COLLATION|  
|*drop-domain-déclaration*|"DOMAINE DE CHUTE"|SQL_DIAG_DROP_DOMAIN|  
|*drop-index-déclaration*|"INDICE DE CHUTE"|SQL_DIAG_DROP_INDEX|  
|*drop-schema-statement*|"DROP SCHEMA"|SQL_DIAG_DROP_SCHEMA|  
|*drop-table-déclaration*|"TABLE DE CHUTE"|SQL_DIAG_DROP_TABLE|  
|*drop-traduction-déclaration*|"DROP TRANSLATION"|SQL_DIAG_DROP_TRANSLATION|  
|*drop-view-statement*|"DROP VIEW"|SQL_DIAG_DROP_VIEW|  
|*octroi*|"SUBVENTION"|SQL_DIAG_GRANT|
|*insertion-déclaration*|"INSÉRER"|SQL_DIAG_INSERT|  
|*ODBC-procédure-extension*|"APPEL"|SQL_DIAG_ CALL|  
|*révocation-déclaration*|"RÉVOQUER"|SQL_DIAG_REVOKE|  
|*schéma-définition*|"CRÉER DES SCHÉMAS"|SQL_DIAG_CREATE_SCHEMA|  
|*traduction-définition*|"CRÉER LA TRADUCTION"|SQL_DIAG_CREATE_TRANSLATION|  
|*mise à jour-déclaration positionnée*|"CURSOR DE MISE À JOUR DYNAMIQUE"|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*mise à jour-déclaration-recherché*|"MISE À JOUR OÙ"|SQL_DIAG_UPDATE_WHERE|  
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

 Les enregistrements d’état sont positionnés dans une séquence basée sur le numéro de ligne et le type de diagnostic. Le gestionnaire de pilote détermine l’ordre final dans lequel retourner les enregistrements d’état qu’il génère. Le conducteur détermine l’ordre final dans lequel retourner les enregistrements d’état qu’il génère.  
  
 Si les dossiers diagnostiques sont affichés par le gestionnaire de conducteur et le conducteur, le gestionnaire de conducteur est responsable de leur commande.  
  
 S’il y a deux enregistrements ou plus, la séquence des enregistrements est déterminée en premier par numéro de rangée. Les règles suivantes s’appliquent à la détermination de la séquence des enregistrements diagnostiques par rangée :  
  
-   Les enregistrements qui ne correspondent à aucune rangée apparaissent devant des enregistrements qui correspondent à une rangée particulière, parce que SQL_NO_ROW_NUMBER est définie comme étant de -1.  
  
-   Les enregistrements pour lesquels le numéro de ligne est inconnu apparaissent devant tous les autres enregistrements, parce que SQL_ROW_NUMBER_UNKNOWN est défini comme étant de -2.  
  
-   Pour tous les enregistrements qui se rapportent à des lignes spécifiques, les enregistrements sont triés par la valeur dans le domaine SQL_DIAG_ROW_NUMBER. Toutes les erreurs et avertissements de la première rangée affectée sont énumérés, puis toutes les erreurs et avertissements de la rangée suivante affectée, et ainsi de suite.  
  
> [!NOTE]
>  L’ODBC 3 *.x* Driver Manager ne commande pas d’enregistrements d’état dans la file d’attente diagnostique si SQLSTATE 01S01 (Erreur de ligne) est retourné par un conducteur ODBC 2 *.x* ou si SQLSTATE 01S (Erreur de ligne) est retourné par un conducteur ODBC 3 *.x* lorsque **SQLExtendedFetch** est appelé ou **SQLSetPos** est appelé sur un curseur qui a été positionné avec **SQLExtendedFetch**.  
  
 Dans chaque rangée, ou pour tous les enregistrements qui ne correspondent pas à une rangée ou pour lesquels le numéro de rangée est inconnu, ou pour tous ces enregistrements avec un nombre de rangées égales à SQL_NO_ROW_NUMBER, le premier enregistrement énuméré est déterminé en utilisant un ensemble de règles de tri. Après le premier enregistrement, l’ordre des autres enregistrements affectant une rangée n’est pas défini. Une application ne peut pas supposer que les erreurs précèdent les avertissements après le premier enregistrement. Les applications doivent numériser la structure complète des données diagnostiques pour obtenir des informations complètes sur un appel infructueux à une fonction.  
  
 Les règles suivantes sont utilisées pour déterminer le premier enregistrement dans une rangée. Le record avec le rang le plus élevé est le premier record. La source d’un dossier (Driver Manager, driver, gateway, etc.) n’est pas prise en compte lors du classement des enregistrements.  
  
-   **Erreurs** Les enregistrements d’état qui décrivent les erreurs ont le rang le plus élevé. Les règles suivantes s’appliquent aux erreurs de tri :  
  
    -   Les enregistrements qui indiquent une défaillance de transaction ou une éventuelle défaillance de transaction ont surclassé tous les autres enregistrements.  
  
    -   Si deux dossiers ou plus décrivent la même condition d’erreur, alors les SQLSTATes définies par les spécifications CLI du groupe ouvert (classes 03 par HZ) surclassent les SQLSTATes définies par ODBC et le conducteur.  
  
-   **Définition de la mise en œuvre Aucune valeur de données** Les enregistrements d’état qui décrivent les valeurs sans données définies par le conducteur (classe 02) ont le deuxième rang le plus élevé.  
  
-   **Avertissements** Les dossiers d’état qui décrivent les avertissements (classe 01) ont le rang le plus bas. Si deux dossiers ou plus décrivent la même condition d’avertissement, alors avertir sqLSTATEs définis par les spécifications CLI Open Group surclassé ODBC-défini et défini par le conducteur SQLSTATEs.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtenir plusieurs champs d’une structure de données diagnostiques|[SQLGetDiagRec, fonction](sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
