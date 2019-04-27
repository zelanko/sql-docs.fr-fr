---
title: SQLSetDescField, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescField
helpviewer_keywords:
- SQLSetDescField function [ODBC]
ms.assetid: 8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce80e7b9c6e8cfcf15c0810986c1a34e8d881ade
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742255"
---
# <a name="sqlsetdescfield-function"></a>SQLSetDescField, fonction

**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLSetDescField** définit la valeur d’un champ unique d’un enregistrement de descripteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SQLRETURN SQLSetDescField(  
     SQLHDESC      DescriptorHandle,  
     SQLSMALLINT   RecNumber,  
     SQLSMALLINT   FieldIdentifier,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    BufferLength);  
```  
  
## <a name="arguments"></a>Arguments  
 *DescriptorHandle*  
 [Entrée] Handle du descripteur.  
  
 *RecNumber*  
 [Entrée] Indique que l’enregistrement de descripteur qui contient le champ de l’application cherche à définir. Enregistrements de descripteurs sont numérotés de 0, avec le numéro d’enregistrement 0 en cours de l’enregistrement de signet. Le *RecNumber* argument est ignoré pour les champs d’en-tête.  
  
 *FieldIdentifier*  
 [Entrée] Indique le champ du descripteur dont la valeur doit être défini. Pour plus d’informations, consultez «*FieldIdentifier* Argument » dans la section « Commentaires ».  
  
 *ValuePtr*  
 [Entrée] Pointeur vers une mémoire tampon contenant les informations de descripteur, ou une valeur entière. Le type de données dépend de la valeur de *FieldIdentifier*. Si *ValuePtr* est une valeur entière, elle peut être considérée comme 8 octets (SQLLEN), 4 octets (SQLINTEGER) ou 2 octets (SQLSMALLINT), selon la valeur de la *FieldIdentifier* argument.  
  
 *BufferLength*  
 [Entrée] Si *FieldIdentifier* est un champ défini par ODBC et *ValuePtr* pointe vers une chaîne de caractères ou une mémoire tampon binaire, cet argument doit être la longueur de **ValuePtr*. Pour les données de chaîne de caractères, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *FieldIdentifier* est un champ défini par ODBC et *ValuePtr* est un entier, *BufferLength* est ignoré.  
  
 Si *FieldIdentifier* est un champ défini par le pilote, l’application indique la nature du champ pour le Gestionnaire de pilotes en définissant le *BufferLength* argument. *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si *ValuePtr* est un pointeur vers une chaîne de caractères, puis *BufferLength* est la longueur de la chaîne ou le SQL_NTS.  
  
-   Si *ValuePtr* est un pointeur vers une mémoire tampon binaire, puis l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur*) macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si *ValuePtr* est un pointeur vers une valeur autre qu’une chaîne de caractères ou une chaîne binaire, puis *BufferLength* doit avoir la valeur SQL_IS_POINTER.  
  
-   Si *ValuePtr* contient une valeur de longueur fixe, puis *BufferLength* est SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_IS_USMALLINT, comme il convient.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetDescField** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DESC et un *gérer* de *DescriptorHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLSetDescField** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur d’option modifiée|Le pilote ne prenait pas en charge la valeur spécifiée dans  *\*ValuePtr* (si *ValuePtr* était un pointeur) ou la valeur *ValuePtr* (si *ValuePtr*  a une valeur entière), ou  *\*ValuePtr* n’est pas valide en raison de conditions de travail d’implémentation, afin du pilote remplacé une valeur similaire. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07009|Index de descripteur non valide|Le *FieldIdentifier* argument était un champ d’enregistrement, le *RecNumber* argument était égale à 0 et le *DescriptorHandle* argument auquel un descripteur IPD.<br /><br /> Le *RecNumber* argument était inférieure à 0 et le *DescriptorHandle* argument auquel une ARD ou un APD.<br /><br /> Le *RecNumber* argument était supérieur au nombre maximal de colonnes ou paramètres de la source de données peut prendre en charge, et le *DescriptorHandle* argument auquel une APD ou le ARD.<br /><br /> (DM) le *FieldIdentifier* SQL_DESC_COUNT, a été l’argument et  *\*ValuePtr* argument était inférieure à 0.<br /><br /> Le *RecNumber* argument était égal à 0 et le *DescriptorHandle* argument auquel une APD alloué implicitement. (Cette erreur ne se produit pas avec un descripteur d’application alloués explicitement, car il n’est pas connu si un descripteur d’application explicitement alloué soit un APD ARD jusqu'à ce que l’exécution.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|22001|Données de chaîne droite tronquées|Le *FieldIdentifier* SQL_DESC_NAME, a été l’argument et le *BufferLength* argument a une valeur supérieure à SQL_MAX_IDENTIFIER_LEN.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) le *DescriptorHandle* a été associé à un *au paramètre StatementHandle* pour laquelle une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée et l’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* avec lequel le *DescriptorHandle* a été associé et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *DescriptorHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLSetDescField** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelée pour l’une des descripteurs d’instruction associés à la *DescriptorHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY016|Impossible de modifier un descripteur de ligne d’implémentation|Le *DescriptorHandle* argument a été associé à un IRD et le *FieldIdentifier* argument n’était pas SQL_DESC_ARRAY_STATUS_PTR ou SQL_DESC_ROWS_PROCESSED_PTR.|  
|HY021|Informations de descripteur incohérentes|Les champs SQL_DESC_TYPE et SQL_DESC_DATETIME_INTERVAL_CODE ne forment pas un type ODBC SQL valide ou un type SQL spécifiques au pilote valide (pour l’IPD) ou un type ODBC C valide (pour ou à partir d’APD).<br /><br /> Informations de descripteur vérifiées pendant une vérification de cohérence n’étaient pas cohérentes. (Voir « Vérification de cohérence » dans **SQLSetDescRec**.)|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM)  *\*ValuePtr* est une chaîne de caractères, et *BufferLength* était inférieur à zéro mais pas égale à SQL_NTS.<br /><br /> (DM) le pilote a été un ODBC 2 *.x* pilote, le descripteur a été un ARD, le *ColumnNumber* argument a été défini sur 0 et la valeur spécifiée pour l’argument *BufferLength* a été non égal à 4.|  
|HY091|Identificateur de champ de descripteur non valide|La valeur spécifiée pour le *FieldIdentifier* argument n’était pas un champ défini par ODBC et n’était pas une valeur définie par l’implémentation.<br /><br /> Le *FieldIdentifier* argument n’était pas valide pour le *DescriptorHandle* argument.<br /><br /> Le *FieldIdentifier* argument était un champ en lecture seule, définie par ODBC.|  
|HY092|Identificateur d’option/attribut non valide|La valeur dans  *\*ValuePtr* n’était pas valide pour le *FieldIdentifier* argument.<br /><br /> Le *FieldIdentifier* SQL_DESC_UNNAMED, a été l’argument et *ValuePtr* a la valeur SQL_NAMED.|  
|HY105|Type de paramètre non valide|(DM) la valeur spécifiée pour le champ SQL_DESC_PARAMETER_TYPE n’était pas valide. (Pour plus d’informations, consultez le «*InputOutputType* Argument « section **SQLBindParameter**.)|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [What ' s New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLSetDescField** à définir n’importe quel champ de descripteur un à la fois. Un seul appel à **SQLSetDescField** définit un champ unique dans un descripteur unique. Cette fonction peut être appelé pour définir n’importe quel champ dans n’importe quel type de descripteur, fourni que le champ peut être défini. (Consultez le tableau plus loin dans cette section.)  
  
> [!NOTE]  
>  Si un appel à **SQLSetDescField** échoue, le contenu de l’enregistrement de descripteur identifié par le *RecNumber* argument ne sont pas définis.  
  
 Autres fonctions peuvent être appelées pour définir plusieurs champs de descripteur avec un seul appel de la fonction. Le **SQLSetDescRec** fonction définit une variété de champs qui affectent le type de données et de la mémoire tampon liées à une colonne ou un paramètre (SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_ Champs DESC_SCALE, SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_INDICATOR_PTR). **SQLBindCol** ou **SQLBindParameter** peut être utilisée pour rendre une spécification complète pour la liaison d’une colonne ou un paramètre. Ces fonctions définissent un groupe de champs de descripteur avec l’appel d’une fonction spécifique.  
  
 **SQLSetDescField** peut être appelé pour modifier les mémoires tampons de liaison en ajoutant un décalage pour les pointeurs de liaison (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR). Cela modifie les mémoires tampons de liaison sans appeler **SQLBindCol** ou **SQLBindParameter**, ce qui permet à une application modifier SQL_DESC_DATA_PTR sans modifier d’autres champs, tels que SQL_DESC_DATA_ TYPE.  
  
 Si une application appelle **SQLSetDescField** pour définir n’importe quel champ autre que SQL_DESC_COUNT ou champs différés SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR ou SQL_DESC_INDICATOR_PTR, l’enregistrement devient indépendant.  
  
 Champs d’en-tête de descripteur sont définies en appelant **SQLSetDescField** avec le bon *FieldIdentifier*. Plusieurs champs d’en-tête sont également les attributs d’instruction, afin qu’ils peuvent également être définies par un appel à **SQLSetStmtAttr**. Cela permet aux applications définir un champ de descripteur sans obtenir au préalable un handle du descripteur. Lorsque **SQLSetDescField** est appelée pour définir un champ d’en-tête, le *RecNumber* argument est ignoré.  
  
 Un *RecNumber* 0 est utilisé pour définir les champs de signet.  
  
> [!NOTE]  
>  L’attribut d’instruction SQL_ATTR_USE_BOOKMARKS doit toujours être définie avant d’appeler **SQLSetDescField** pour définir des champs de signet. Bien que cela ne soit pas obligatoire, il est fortement recommandé.  
  
## <a name="sequence-of-setting-descriptor-fields"></a>Séquence de la définition des champs de descripteur  
 Lors de la définition des champs de descripteur en appelant **SQLSetDescField**, l’application doit suivre une séquence spécifique :  
  
1.  L’application doit définir tout d’abord le champ SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE ou SQL_DESC_DATETIME_INTERVAL_CODE.  
  
2.  Une fois qu’un de ces champs a été défini, l’application peut définir un attribut d’un type de données et le pilote définit les champs d’attribut du type de données pour les valeurs par défaut appropriées pour le type de données. La définition par défaut automatique des champs d’attribut de type garantit que le descripteur est toujours prêt à utiliser une fois que l’application a spécifié un type de données. Si l’application définit explicitement un attribut de type de données, elle remplace l’attribut par défaut.  
  
3.  Une fois qu’un des champs répertoriés à l’étape 1 a été défini, et les attributs de type de données ont été définies, l’application peut définir SQL_DESC_DATA_PTR. Cela demande une vérification de cohérence des champs de descripteur. Si l’application change le type de données ou d’attributs après avoir défini le champ SQL_DESC_DATA_PTR, le pilote définit SQL_DESC_DATA_PTR à un pointeur null, la séparation de l’enregistrement. Cela force l’application pour effectuer les étapes appropriées dans l’ordre, avant l’enregistrement de descripteur est utilisable.  
  
## <a name="initialization-of-descriptor-fields"></a>Initialisation de champs de descripteur  
 Lorsqu’un descripteur est alloué, les champs dans le descripteur peuvent être initialisés à une valeur par défaut, être initialisés sans valeur par défaut ou être non défini pour le type de descripteur. Les tableaux suivants indiquent l’initialisation de chaque champ pour chaque type de descripteur, avec « D » indiquant que le champ est initialisé avec une valeur par défaut et « ND » indiquant que le champ est initialisé sans valeur par défaut. Si un nombre est indiqué, la valeur par défaut du champ est ce nombre. Les tables indiquent également si un champ est en lecture/écriture (R/W) ou en lecture seule (R).  
  
 Les champs d’un IRD ont une valeur par défaut uniquement une fois que l’instruction a été préparée ou exécutée et le descripteur IRD a été rempli, pas lorsque le descripteur d’instruction ou le descripteur a été alloué. Jusqu'à ce que le descripteur IRD a été rempli, toute tentative d’accéder à un champ d’un IRD retournera une erreur.  
  
 Certains champs de descripteur sont définis pour un ou plusieurs, mais pas tous les types de descripteur (à partir et IRDs et APD et IPD). Lorsqu’un champ n’est pas défini pour un type de descripteur, il n’est pas nécessaire par les fonctions qui utilisent ce descripteur.  
  
 Les champs qui sont accessibles par **SQLGetDescField** ne peut pas nécessairement être défini **SQLSetDescField**. Les champs qui peuvent être définies par **SQLSetDescField** sont répertoriés dans les tableaux suivants.  
  
 L’initialisation de champs d’en-tête est décrite dans le tableau suivant.  
  
|Nom de champ d’en-tête|Type|R/W (Lecture/écriture)|Par défaut|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD : R APD : R IRD : R IPD : R|ARD : SQL_DESC_ALLOC_AUTO pour implicite ou SQL_DESC_ALLOC_USER pour explicite<br /><br /> APD : SQL_DESC_ALLOC_AUTO pour implicite ou SQL_DESC_ALLOC_USER pour explicite<br /><br /> IRD : SQL_DESC_ALLOC_AUTO<br /><br /> IPD : SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN|ARD : R/W APD : R/W IRD : Inutilisé IPD : Inutilisé|ARD : APD [1] : [1] IRD : Inutilisé IPD : Inutilisé|  
|SQL_DESC_ARRAY_STATUS_PTR|SQLUSMALLINT*|ARD : R/W APD : R/W IRD : R/W IPD : R/W (Lecture/écriture)|ARD : Ptr null APD : Ptr null IRD : Ptr null IPD : Ptr null|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLEN *|ARD : R/W APD : R/W IRD : Inutilisé IPD : Inutilisé|ARD : Ptr null APD : Ptr null IRD : Inutilisé IPD : Inutilisé|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD : R/W APD : R/W IRD : Inutilisé IPD : Inutilisé|ARD : SQL_BIND_BY_COLUMN<br /><br /> APD : SQL_BIND_BY_COLUMN<br /><br /> IRD : Inutilisé<br /><br /> IPD : Inutilisé|  
|SQL_DESC_COUNT|SQLSMALLINT|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : APD 0 : 0 IRD : D IPD : 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN*|ARD : APD inutilisée : IRD inutilisée : R/W IPD : R/W (Lecture/écriture)|ARD : APD inutilisée : IRD inutilisée : Ptr null IPD : Ptr null|  
  
 [1] ces champs sont définis uniquement lors de l’IPD est automatiquement rempli par le pilote. Dans le cas contraire, ils sont non définis. Si une application tente de définir ces champs, SQLSTATE HY091 (identificateur de champ de descripteur non valide) est retournée.  
  
 L’initialisation de champs d’enregistrement est comme indiqué dans le tableau suivant.  
  
|Nom de champ d’enregistrement|Type|R/W (Lecture/écriture)|Par défaut|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD : APD inutilisée : IRD inutilisée : R IPD : R|ARD : APD inutilisée : IRD inutilisée : D IPD : D[1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : SQL_C_ PAR DÉFAUT APD : SQL_C_ PAR DÉFAUT IRD : D IPD : ND|  
|SQL_DESC_DATA_PTR|SQLPOINTER|ARD : R/W APD : R/W IRD : Inutilisé IPD : Inutilisé|ARD : Ptr null APD : Ptr null IRD : Inutilisé IPD : Inutilisé [2]|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_DISPLAY_SIZE|SQLLEN|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD : APD inutilisée : IRD inutilisée : R IPD : R|ARD : APD inutilisée : IRD inutilisée : D IPD : D[1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN *|ARD : R/W APD : R/W IRD : Inutilisé IPD : Inutilisé|ARD : Ptr null APD : Ptr null IRD : Inutilisé IPD : Inutilisé|  
|SQL_DESC_LABEL|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_LENGTH|SQLULEN|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : R|ARD : APD inutilisée : IRD inutilisée : D IPD : D[1]|  
|SQL_DESC_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD : APD inutilisée : IRD inutilisée : R IPD : R|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_OCTET_LENGTH|SQLLEN|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN *|ARD : R/W APD : R/W IRD : Inutilisé IPD : Inutilisé|ARD : Ptr null APD : Ptr null IRD : Inutilisé IPD : Inutilisé|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD : APD inutilisée : IRD inutilisée : Inutilisé IPD : R/W (Lecture/écriture)|ARD : APD inutilisée : IRD inutilisée : Inutilisé IPD : D=SQL_PARAM_INPUT|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD : Inutilisé<br /><br /> APD : Inutilisé<br /><br /> IRD : R<br /><br /> IPD : R|ARD : Inutilisé<br /><br /> APD : Inutilisé<br /><br /> IRD : ND<br /><br /> IPD : ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_TABLE_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD : R/W APD : R/W IRD : R IPD : R/W (Lecture/écriture)|ARD : SQL_C_DEFAULT APD : SQL_C_DEFAULT IRD : D IPD : ND|  
|SQL_DESC_TYPE_NAME|SQLCHAR *|ARD : APD inutilisée : IRD inutilisée : R IPD : R|ARD : APD inutilisée : IRD inutilisée : D IPD : D[1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD : APD inutilisée : IRD inutilisée : R IPD : R/W (Lecture/écriture)|ARD : ND APD : ND IRD : D IPD : ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD : APD inutilisée : IRD inutilisée : R IPD : R|ARD : APD inutilisée : IRD inutilisée : D IPD : D[1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD : APD inutilisée : IRD inutilisée : R IPD : Inutilisé|ARD : APD inutilisée : IRD inutilisée : D IPD : Inutilisé|  
  
 [1] ces champs sont définis uniquement lors de l’IPD est automatiquement rempli par le pilote. Dans le cas contraire, ils sont non définis. Si une application tente de définir ces champs, SQLSTATE HY091 (identificateur de champ de descripteur non valide) est retournée.  
  
 [2], le champ SQL_DESC_DATA_PTR dans l’IPD peut être défini pour forcer une vérification de cohérence. Dans un appel ultérieur à **SQLGetDescField** ou **SQLGetDescRec**, le pilote n’est pas nécessaire pour retourner la valeur SQL_DESC_DATA_PTR a été défini sur.  
  
## <a name="fieldidentifier-argument"></a>Argument de FieldIdentifier  
 Le *FieldIdentifier* argument indique le champ de descripteur à définir. Contient un descripteur de la *en-tête de descripteur,* comportant les champs d’en-tête décrits dans la section suivante, « Champs d’en-tête » et zéro ou plusieurs *enregistrements de descripteurs,* comportant les champs d’enregistrement décrit dans la section suivante de la section « Champs d’en-tête ».  
  
## <a name="header-fields"></a>Champs d’en-tête  
 Chaque descripteur a un en-tête composé des champs suivants :  
  
 **SQL_DESC_ALLOC_TYPE [All]**  
 Ce champ d’en-tête SQLSMALLINT en lecture seule indique si le descripteur a été alloué automatiquement par le pilote ou explicitement par l’application. L’application peut obtenir, mais pas modifier, ce champ. Le champ est défini par le pilote à SQL_DESC_ALLOC_AUTO si le descripteur a été alloué automatiquement par le pilote. Il est défini à SQL_DESC_ALLOC_USER par le pilote si le descripteur a été explicitement alloué par l’application.  
  
 **SQL_DESC_ARRAY_SIZE [descripteurs de l’Application]**  
 Dans à partir, ce champ d’en-tête SQLULEN Spécifie le nombre de lignes dans l’ensemble de lignes. Il s’agit du nombre de lignes à retourner par un appel à **SQLFetch** ou **SQLFetchScroll** ou à traiter par un appel à **SQLBulkOperations** ou **SQLSetPos** .  
  
 Dans APD, ce champ d’en-tête SQLULEN Spécifie le nombre de valeurs pour chaque paramètre.  
  
 La valeur par défaut de ce champ est 1. Si SQL_DESC_ARRAY_SIZE est supérieure à 1, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR du APD ou ARD pointent vers des tableaux. La cardinalité de chaque tableau est égale à la valeur de ce champ.  
  
 Ce champ dans le ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_ARRAY_SIZE. Ce champ dans le descripteur APD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAMSET_SIZE.  
  
 **SQL_DESC_ARRAY_STATUS_PTR [All]**  
 Pour chaque type de descripteur, ce SQLUSMALLINT * en-tête champ pointe vers un tableau de valeurs SQLUSMALLINT. Ces tableaux est nommés comme suit : ligne de tableau d’état (IRD), tableau d’état de paramètre (IPD), le tableau d’opérations ligne (ARD) et opération tableau de paramètres (APD).  
  
 Dans le descripteur IRD, ce champ d’en-tête pointe vers un tableau d’état de ligne qui contient des valeurs d’état après un appel à **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**. Le tableau a autant d’éléments qu’il existe des lignes dans l’ensemble de lignes. L’application doit allouer un tableau de SQLUSMALLINTs et paramétrez ce champ pour qu’il pointe vers le tableau. Le champ est défini sur un pointeur null par défaut. Le pilote remplira le tableau -, sauf si le champ SQL_DESC_ARRAY_STATUS_PTR est défini sur un pointeur null, auquel cas aucune valeur d’état n’est générés et le tableau n’est pas rempli.  
  
> [!CAUTION]  
>  Comportement du pilote est non défini si l’application définit les éléments du tableau d’état de ligne vers laquelle pointé le champ SQL_DESC_ARRAY_STATUS_PTR de l’IRD.  
  
 Le tableau est rempli initialement par un appel à **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**. Si l’appel n’a pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tableau vers lequel pointé ce champ n’est pas défini. Les éléments dans le tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_ROW_SUCCESS : La ligne a été récupérée avec succès et n’a pas changé depuis sa dernière extraction.  
  
-   SQL_ROW_SUCCESS_WITH_INFO : La ligne a été récupérée avec succès et n’a pas changé depuis sa dernière extraction. Toutefois, un avertissement a été retourné sur la ligne.  
  
-   SQL_ROW_ERROR : Une erreur s’est produite lors de l’extraction de la ligne.  
  
-   SQL_ROW_UPDATED : La ligne a été récupérée avec succès et a été mis à jour depuis sa dernière extraction. Si la ligne est extraite à nouveau, son état est SQL_ROW_SUCCESS.  
  
-   SQL_ROW_DELETED : La ligne a été supprimée depuis sa dernière extraction.  
  
-   SQL_ROW_ADDED : La ligne a été insérée par **SQLBulkOperations**. Si la ligne est extraite à nouveau, son état est SQL_ROW_SUCCESS.  
  
-   SQL_ROW_NOROW : L’ensemble de lignes avec chevauchement de la fin du jeu de résultats, et aucune ligne n’a été retourné qui correspondait à cet élément du tableau d’état de ligne.  
  
 Ce champ dans le descripteur IRD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_STATUS_PTR.  
  
 Le champ SQL_DESC_ARRAY_STATUS_PTR de l’IRD est valide uniquement une fois que SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO a été retourné. Si le code de retour n’est pas une d’elles, l’emplacement vers lequel pointé SQL_DESC_ROWS_PROCESSED_PTR est non défini.  
  
 Dans l’infrastructure ou IPD, ce champ d’en-tête pointe vers un tableau d’état de paramètres contenant des informations d’état pour chaque ensemble de valeurs de paramètre après un appel à **SQLExecute** ou **SQLExecDirect**. Si l’appel à **SQLExecute** ou **SQLExecDirect** n’a pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tableau vers lequel pointe ce champ ne sont pas définis. L’application doit allouer un tableau de SQLUSMALLINTs et paramétrez ce champ pour qu’il pointe vers le tableau. Le pilote remplira le tableau -, sauf si le champ SQL_DESC_ARRAY_STATUS_PTR est défini sur un pointeur null, auquel cas aucune valeur d’état n’est générés et le tableau n’est pas rempli. Les éléments dans le tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_PARAM_SUCCESS: L’instruction SQL a été exécutée avec succès pour ce jeu de paramètres.  
  
-   SQL_PARAM_SUCCESS_WITH_INFO: L’instruction SQL a été exécutée avec succès pour ce jeu de paramètres ; Toutefois, les informations d’avertissement sont disponibles dans la structure de données de diagnostic.  
  
-   SQL_PARAM_ERROR: Une erreur s’est produite lors du traitement de cet ensemble de paramètres. Informations d’erreur supplémentaires sont disponibles dans la structure de données de diagnostic.  
  
-   SQL_PARAM_UNUSED: Ce jeu de paramètres a été inutilisé, probablement dû au fait que certains précédent jeu de paramètres a provoqué une erreur qui a abandonné le traitement supplémentaire, ou parce que SQL_PARAM_IGNORE a été défini pour ce jeu de paramètres dans le tableau spécifié par le champ SQL_DESC_ARRAY_STATUS_PTR de le descripteur APD.  
  
-   SQL_PARAM_DIAG_UNAVAILABLE: Informations de diagnostic ne sont pas disponibles. Un exemple de ceci est lorsque le pilote traite les tableaux de paramètres comme une unité monolithique et donc ne génère ne pas de ce niveau d’informations sur l’erreur.  
  
 Ce champ dans l’IPD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAM_STATUS_PTR.  
  
 Dans le ARD, ce champ d’en-tête pointe vers un tableau d’opération de ligne de valeurs qui peuvent être définies par l’application pour indiquer si cette ligne doit être ignorée pour **SQLSetPos** operations. Les éléments dans le tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_ROW_PROCEED : La ligne est incluse dans l’opération en bloc en utilisant **SQLSetPos**. (Ce paramètre ne garantit pas que l’opération se produira sur la ligne. Si la ligne a l’état SQL_ROW_ERROR dans le tableau d’état de ligne IRD, le pilote ne peut pas être en mesure d’effectuer l’opération dans la ligne.)  
  
-   SQL_ROW_IGNORE : La ligne est exclue de l’opération en bloc en utilisant **SQLSetPos**.  
  
 Si aucun élément du tableau n’est définies, toutes les lignes sont incluses dans l’opération en bloc. Si la valeur dans le champ SQL_DESC_ARRAY_STATUS_PTR de la ARD est un pointeur null, toutes les lignes sont incluses dans l’opération en bloc ; l’interprétation est le même que si le pointeur pointe vers un tableau valid et que tous les éléments du tableau ont été SQL_ROW_PROCEED. Si un élément du tableau est défini sur SQL_ROW_IGNORE, la valeur dans le tableau d’état de ligne pour la ligne ignoré n’est pas modifiée.  
  
 Ce champ dans le ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_OPERATION_PTR.  
  
 Dans le descripteur APD, ce champ d’en-tête pointe vers un tableau d’opération de paramètres des valeurs qui peuvent être définies par l’application pour indiquer si cet ensemble de paramètres doit être ignorées lorsque **SQLExecute** ou **SQLExecDirect**est appelée. Les éléments dans le tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_PARAM_PROCEED : Le jeu de paramètres est inclus dans le **SQLExecute** ou **SQLExecDirect** appeler.  
  
-   SQL_PARAM_IGNORE: Le jeu de paramètres est exclu de la **SQLExecute** ou **SQLExecDirect** appeler.  
  
 Si aucun élément du tableau n’est définies, tous les jeux de paramètres dans le tableau sont utilisés dans le **SQLExecute** ou **SQLExecDirect** appels. Si la valeur dans le champ SQL_DESC_ARRAY_STATUS_PTR du descripteur APD est un pointeur null, tous les jeux de paramètres sont utilisés ; l’interprétation est le même que si le pointeur pointe vers un tableau valid et que tous les éléments du tableau ont été SQL_PARAM_PROCEED.  
  
 Ce champ dans le descripteur APD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAM_OPERATION_PTR.  
  
 **SQL_DESC_BIND_OFFSET_PTR [Application descriptors]**  
 Cette SQLLEN * en-tête champ pointe vers le décalage de la liaison. Il est défini sur un pointeur null par défaut. Si ce champ n’est pas un pointeur null, le pilote déréférence le pointeur et ajoute la valeur déréférencée à chacun des champs différés qui a une valeur non null de l’enregistrement de descripteur (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR) à récupérer le temps et utilise les nouvelles valeurs de pointeur lors de la liaison.  
  
 Le décalage de la liaison est toujours ajouté directement aux valeurs dans les champs SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR. Si le décalage est modifié sur une autre valeur, la nouvelle valeur est toujours ajoutée directement à la valeur de chaque champ de descripteur. Le nouveau décalage n’est pas ajouté à la valeur du champ plus un décalage quelconque antérieures.  
  
 Ce champ est un *champ différée*: Il n’est pas utilisé au moment il est défini, mais est utilisée ultérieurement par le pilote lorsqu’il a besoin pour déterminer les adresses pour les mémoires tampons de données.  
  
 Ce champ dans le ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_BIND_OFFSET_PTR. Ce champ dans le ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAM_BIND_OFFSET_PTR.  
  
 Pour plus d’informations, consultez la description de la liaison dans [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) et [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 **SQL_DESC_BIND_TYPE [Application descriptors]**  
 Ce champ d’en-tête SQLUINTEGER définit l’orientation de la liaison à utiliser pour la liaison de colonnes ou paramètres.  
  
 Dans à partir, ce champ spécifie l’orientation de la liaison lorsque **SQLFetchScroll** ou **SQLFetch** est appelée sur le handle d’instruction associée.  
  
 Pour sélectionner la liaison pour les colonnes, ce champ est défini à SQL_BIND_BY_COLUMN (la valeur par défaut).  
  
 Ce champ dans le ARD peut également être défini en appelant **SQLSetStmtAttr** avec le SQL_ATTR_ROW_BIND_TYPE *attribut*.  
  
 Dans APD, ce champ spécifie l’orientation de la liaison à utiliser pour les paramètres dynamiques.  
  
 Pour sélectionner la liaison des paramètres, ce champ est défini à SQL_BIND_BY_COLUMN (la valeur par défaut).  
  
 Ce champ dans le descripteur APD peut également être défini en appelant **SQLSetStmtAttr** avec le SQL_ATTR_PARAM_BIND_TYPE *attribut*.  
  
 **SQL_DESC_COUNT [All]**  
 Ce champ d’en-tête SQLSMALLINT Spécifie l’index de base 1 de l’enregistrement le plus élevé numérotés qui contient des données. Lorsque le pilote définit la structure de données pour le descripteur, il doit également définir le champ SQL_DESC_COUNT pour afficher le nombre d’enregistrements est significatif. Lorsqu’une application alloue une instance de cette structure de données, il n’a pas de spécifier le nombre d’enregistrements pour réserver une chambre pour. Comme l’application spécifie le contenu des enregistrements, le pilote prend toute action requise pour vous assurer que le handle de descripteur fait référence à une structure de données de la taille adéquate.  
  
 SQL_DESC_COUNT n’est pas un nombre de toutes les colonnes de données qui sont liés (si le champ est dans un ARD) ou de tous les paramètres qui sont liés (si le champ est dans un APD), mais le numéro de l’enregistrement le plus élevé numérotés. Si la colonne la plus élevée numérotées ou du paramètre est indépendant, SQL_DESC_COUNT est modifié pour le nombre de la colonne la plus élevée numérotés suivante ou du paramètre. Si une colonne ou un paramètre avec un nombre qui est inférieur au numéro de la colonne la plus élevée numérotées est indépendant (en appelant **SQLBindCol** avec la *TargetValuePtr* argument défini à un pointeur null, ou **SQLBindParameter** avec la *ParameterValuePtr* argument défini sur un pointeur null), SQL_DESC_COUNT n’est pas modifié. Si des colonnes supplémentaires ou des paramètres sont liées avec les nombres supérieurs à l’enregistrement le plus élevé numérotés qui contient les données, le pilote augmente automatiquement la valeur dans le champ SQL_DESC_COUNT. Si toutes les colonnes sont déliés en appelant **SQLFreeStmt** avec l’option SQL_UNBIND, les champs SQL_DESC_COUNT ARD et IRD sont définies sur 0. Si **SQLFreeStmt** est appelée avec l’option SQL_RESET_PARAMS, les champs SQL_DESC_COUNT APD et IPD sont définies sur 0.  
  
 La valeur dans SQL_DESC_COUNT peut être définie explicitement par une application en appelant **SQLSetDescField**. Si la valeur dans SQL_DESC_COUNT explicitement diminue, tous les enregistrements avec les nombres supérieurs à la nouvelle valeur dans SQL_DESC_COUNT sont effectivement supprimés. Si la valeur de SQL_DESC_COUNT est explicitement définie sur 0 et le champ est dans un ARD, toutes les mémoires tampons de données à l’exception d’une colonne liée de signet sont libérées.  
  
 Le nombre d’enregistrements dans ce champ d’un ARD n’inclut pas une colonne liée de signet. La seule façon d’annuler la liaison d’une colonne de signet consiste à définir le champ SQL_DESC_DATA_PTR à un pointeur null.  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [descripteurs d’implémentation]**  
 Dans un IRD, cette SQLULEN \* en-tête champ pointe vers une mémoire tampon qui contient le nombre de lignes extraites après un appel à **SQLFetch** ou **SQLFetchScroll**, ou le nombre de lignes affectées dans une opération en bloc effectuée par un appel à **SQLBulkOperations** ou **SQLSetPos**, y compris les lignes d’erreur.  
  
 Dans une infrastructure ou IPD, cette SQLUINTEGER * en-tête champ pointe vers une mémoire tampon contenant le nombre de jeux de paramètres qui ont été traités, y compris des ensembles de l’erreur. Aucun nombre n’est retourné s’il s’agit d’un pointeur null.  
  
 SQL_DESC_ROWS_PROCESSED_PTR est valide uniquement après que SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO a été retournée après un appel à **SQLFetch** ou **SQLFetchScroll** (pour un champ IRD) ou **SQLExecute** , **SQLExecDirect**, ou **SQLParamData** (pour un champ IPD). Si l’appel qui remplit la mémoire tampon désignée par ce champ ne retourne pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu de la mémoire tampon est indéfini, sauf si elle retourne SQL_NO_DATA, dans lequel cas la valeur dans la mémoire tampon est définie sur 0.  
  
 Ce champ dans le ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROWS_FETCHED_PTR. Ce champ dans le descripteur APD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAMS_PROCESSED_PTR.  
  
 La mémoire tampon désignée par ce champ est allouée par l’application. Il est une mémoire tampon de sortie différée qui est définie par le pilote. Il est défini sur un pointeur null par défaut.  
  
## <a name="record-fields"></a>Champs d’enregistrement  
 Chaque descripteur contient un ou plusieurs enregistrements comportant les champs qui définissent les données de la colonne ou des paramètres dynamiques, selon le type de descripteur. Chaque enregistrement est une définition complète d’une seule colonne ou un paramètre.  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [IRDs]**  
 Ce champ d’enregistrement SQLINTEGER en lecture seule contient SQL_TRUE si la colonne est une colonne à incrémentation automatique, ou SQL_FALSE si la colonne n’est pas une colonne à incrémentation automatique. Ce champ est en lecture seule, mais la colonne à incrémentation automatique sous-jacente n’est pas nécessairement en lecture seule.  
  
 **SQL_DESC_BASE_COLUMN_NAME [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient le nom de colonne de base pour le résultat de jeu de colonnes. Si un nom de colonne de base n’existe pas (comme dans le cas des colonnes qui sont des expressions), cette variable contient une chaîne vide.  
  
 **SQL_DESC_BASE_TABLE_NAME [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient le nom de la table de base pour le résultat de jeu de colonnes. Si un nom de table de base ne peut pas être défini ou n’est pas applicable, cette variable contient une chaîne vide.  
  
 **SQL_DESC_CASE_SENSITIVE [descripteurs d’implémentation]**  
 Ce champ d’enregistrement SQLINTEGER en lecture seule contient SQL_TRUE si la colonne ou du paramètre est considérée comme respectant la casse pour les classements et des comparaisons ou SQL_FALSE si la colonne n’est pas considérée comme respectant la casse pour les classements et les comparaisons ou s’il s’agit d’un type non caractère colonne.  
  
 **SQL_DESC_CATALOG_NAME [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient le catalogue pour la table de base qui contient la colonne. La valeur de retour est dépendant du pilote, si la colonne est une expression ou si la colonne fait partie d’une vue. Si la source de données ne prend pas en charge les catalogues ou le catalogue ne peut pas être déterminé, cette variable contient une chaîne vide.  
  
 **SQL_DESC_CONCISE_TYPE [All]**  
 Ce champ d’en-tête SQLSMALLINT Spécifie le type de données concise pour tous les types de données, y compris les types de données datetime et interval.  
  
 Les valeurs dans les champs SQL_DESC_CONCISE_TYPE, SQL_DESC_TYPE et SQL_DESC_DATETIME_INTERVAL_CODE sont interdépendants. Chaque fois qu’un des champs est définie, l’autre doit également être définie. SQL_DESC_CONCISE_TYPE peut être définie par un appel à **SQLBindCol** ou **SQLBindParameter**, ou **SQLSetDescField**. SQL_DESC_TYPE peut être définie par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Si SQL_DESC_CONCISE_TYPE est définie sur un type de données concis autre qu’un type de données intervalle ou date/heure, le champ SQL_DESC_TYPE est défini sur la même valeur et le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE est défini sur 0.  
  
 Si SQL_DESC_CONCISE_TYPE est défini sur le type de données datetime ou interval concis, le champ SQL_DESC_TYPE est défini sur le type de commentaires correspondant (SQL_DATETIME ou SQL_INTERVAL) et le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE est défini pour le sous-code approprié.  
  
 **SQL_DESC_DATA_PTR [descripteurs de l’Application et IPD]**  
 Ce champ d’enregistrement SQLPOINTER pointe vers une variable qui contiendra la valeur du paramètre (pour APD) ou la valeur de colonne (par à partir). Ce champ est un *champ différée*. Il n’est pas utilisé au moment il a la valeur mais est utilisé ultérieurement par le pilote pour récupérer des données.  
  
 La colonne spécifiée par le champ SQL_DESC_DATA_PTR de la ARD est détachée si le *TargetValuePtr* argument dans un appel à **SQLBindCol** est un pointeur null ou si le champ de la SQL_DESC_DATA_PTR dans le ARD est définie par un l’appel à **SQLSetDescField** ou **SQLSetDescRec** à un pointeur null. Autres champs ne sont pas affectées si le champ SQL_DESC_DATA_PTR est défini sur un pointeur null.  
  
 Si l’appel à **SQLFetch** ou **SQLFetchScroll** que remplit la mémoire tampon désignée par ce champ n’a pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu de la mémoire tampon n’est pas défini.  
  
 Chaque fois que le champ SQL_DESC_DATA_PTR d’APD, ARD ou IPD est défini, le pilote vérifie que la valeur dans le champ SQL_DESC_TYPE contient les types de données ODBC C valides ou un type de données spécifique au pilote, et que tous les autres champs qui affectent les types de données sont cohérentes. Demander une vérification de cohérence est l’utilisation seule du champ SQL_DESC_DATA_PTR d’une infrastructure ou IPD. Plus précisément, si une application définit le champ SQL_DESC_DATA_PTR d’une infrastructure ou IPD et les appels ultérieurs **SQLGetDescField** sur ce champ, il n'est pas nécessairement a retourné la valeur qu’il avait défini. Pour plus d’informations, consultez « Vérifications de cohérence » dans [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_CODE [All]**  
 Ce champ d’enregistrement SQLSMALLINT contient le sous-code pour le type de données datetime ou interval spécifique lorsque le champ SQL_DESC_TYPE est SQL_DATETIME ou SQL_INTERVAL. Cela est vrai pour les types de données SQL et C. Le code se compose du nom de type de données avec « CODE » est remplacé par « TYPE » ou « C_TYPE » (pour les types de date/heure) ou « CODE » est remplacé par « INTERVAL » ou « C_INTERVAL » (pour les types d’intervalle).  
  
 Si SQL_DESC_TYPE et SQL_DESC_CONCISE_TYPE dans un descripteur d’application sont définis sur SQL_C_DEFAULT et le descripteur n’est pas associé à un descripteur d’instruction, le contenu de la valeur SQL_DESC_DATETIME_INTERVAL_CODE n’est pas défini.  
  
 Ce champ peut être défini pour les types de données datetime répertoriés dans le tableau suivant.  
  
|Types de date/heure|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP/ SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 Ce champ peut être défini pour les types de données d’intervalle répertoriés dans le tableau suivant.  
  
|Type d'intervalle|DATETIME_INTERVAL_CODE|  
|-------------------|------------------------------|  
|SQL_INTERVAL_DAY/ SQL_C_INTERVAL_DAY|SQL_CODE_DAY|  
|SQL_INTERVAL_DAY_TO_HOUR/ SQL_C_INTERVAL_DAY_TO_HOUR|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE/ SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND/ SQL_C_INTERVAL_DAY_TO_SECOND|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR/ SQL_C_INTERVAL_HOUR|SQL_CODE_HOUR|  
|SQL_INTERVAL_HOUR_TO_MINUTE/ SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND/ SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE/ SQL_C_INTERVAL_MINUTE|SQL_CODE_MINUTE|  
|SQL_INTERVAL_MINUTE_TO_SECOND/ SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_CODE_MINUTE_TO_SECOND|  
|SQL_INTERVAL_MONTH/ SQL_C_INTERVAL_MONTH|SQL_CODE_MONTH|  
|SQL_INTERVAL_SECOND/ SQL_C_INTERVAL_SECOND|SQL_CODE_SECOND|  
|SQL_INTERVAL_YEAR/ SQL_C_INTERVAL_YEAR|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH/ SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_CODE_YEAR_TO_MONTH|  
  
 Pour plus d’informations sur les intervalles de données et ce champ, consultez [les identificateurs de Type de données et les descripteurs de](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_PRECISION [All]**  
 Ce champ d’enregistrement SQLINTEGER contient la précision interval si le champ SQL_DESC_TYPE est SQL_INTERVAL. Lorsque le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE est défini pour un type de données d’intervalle, ce champ est défini sur l’intervalle par défaut la précision de début.  
  
 **SQL_DESC_DISPLAY_SIZE [IRDs]**  
 Ce champ d’enregistrement SQLINTEGER en lecture seule contient le nombre maximal de caractères requis pour afficher les données à partir de la colonne.  
  
 **SQL_DESC_FIXED_PREC_SCALE [descripteurs d’implémentation]**  
 Ce champ d’enregistrement SQLSMALLINT en lecture seule est défini avec SQL_TRUE si la colonne est une colonne numérique exacte et a une précision fixe et une mise à l’échelle différente de zéro, ou à SQL_FALSE si la colonne n’est pas une colonne numérique exacte avec une précision et échelle fixes.  
  
 **SQL_DESC_INDICATOR_PTR [Application descriptors]**  
 Dans à partir, cette SQLLEN * noter les points de champ à la variable indicateur. Cette variable contient la valeur SQL_NULL_DATA si la valeur de colonne est une valeur NULL. Pour APD, la variable indicateur est définie à SQL_NULL_DATA pour spécifier des arguments dynamiques de valeur NULL. Sinon, la variable est zéro (sauf si les valeurs de SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR sont le même pointeur).  
  
 Si le champ SQL_DESC_INDICATOR_PTR dans un ARD est un pointeur null, le pilote ne peut pas retourner des informations indiquant si la colonne est NULL ou non. Si la colonne est NULL et SQL_DESC_INDICATOR_PTR est un pointeur null, SQLSTATE 22002 (variable indicateur requise mais non fournie) est retourné lorsque le pilote essaie de remplir la mémoire tampon après un appel à **SQLFetch** ou  **SQLFetchScroll**. Si l’appel à **SQLFetch** ou **SQLFetchScroll** n’a pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu de la mémoire tampon ne sont pas définis.  
  
 Le champ SQL_DESC_INDICATOR_PTR détermine si le champ désigné par SQL_DESC_OCTET_LENGTH_PTR est défini. Si la valeur de données pour une colonne est NULL, le pilote définit la variable indicateur avec la valeur SQL_NULL_DATA. Le champ désigné par SQL_DESC_OCTET_LENGTH_PTR puis exclut. Si une valeur NULL n’est pas rencontrée pendant l’extraction, la mémoire tampon vers laquelle pointée SQL_DESC_INDICATOR_PTR est définie à zéro et la mémoire tampon vers laquelle pointée SQL_DESC_OCTET_LENGTH_PTR est définie à la longueur des données.  
  
 Si le champ SQL_DESC_INDICATOR_PTR dans un APD est un pointeur null, l’application ne peut pas utiliser cet enregistrement de descripteur pour spécifier les arguments NULL.  
  
 Ce champ est un *champ différée*: Il n’est pas utilisé au moment il est défini, mais est utilisée ultérieurement par le pilote pour indiquer la possibilité de valeur null (pour à partir) ou pour déterminer la possibilité de valeur null (pour APD).  
  
 **SQL_DESC_LABEL [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient l’étiquette de colonne ou le titre. Si la colonne n’a pas d’une étiquette, cette variable contient le nom de colonne. Si la colonne est sans nom et sans titre, cette variable contient une chaîne vide.  
  
 **SQL_DESC_LENGTH [All]**  
 Ce champ d’enregistrement SQLULEN est soit la longueur maximale ou réelle d’une chaîne de caractères en caractères, soit un type de données binaires en octets. Il est la longueur maximale pour un type de données de longueur fixe ou la longueur réelle d’un type de données de longueur variable. Sa valeur exclut toujours le caractère du caractère nul de terminaison qui se termine par la chaîne de caractères. Pour les valeurs dont le type est SQL_TYPE_DATE, SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP ou l’un des types de données SQL intervalle, ce champ a la longueur en caractères de la représentation de chaîne de caractères de la valeur datetime ou interval.  
  
 La valeur dans ce champ peut être différente de la valeur pour « longueur » comme défini dans ODBC 2 *.x*. Pour plus d’informations, consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_LITERAL_PREFIX [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient l’ou les caractères que le pilote ne reconnaît en tant que préfixe pour un littéral de ce type de données. Cette variable contient une chaîne vide pour un type de données pour lequel un préfixe n’est pas applicable.  
  
 **SQL_DESC_LITERAL_SUFFIX [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient l’ou les caractères que le pilote ne reconnaît comme suffixe pour un littéral de ce type de données. Cette variable contient une chaîne vide pour un type de données pour lesquelles un suffixe littéral n’est pas applicable.  
  
 **SQL_DESC_LOCAL_TYPE_NAME [descripteurs d’implémentation]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient n’importe quel nom localisé (langue maternelle) pour le type de données qui peut être différent du nom standard du type de données. S’il n’existe aucun nom localisé, une chaîne vide est retournée. Ce champ est uniquement à des fins d’affichage.  
  
 **SQL_DESC_NAME [descripteurs d’implémentation]**  
 Cette SQLCHAR * champ d’enregistrement dans un descripteur de ligne contient l’alias de colonne, si elle s’applique. Si l’alias de colonne ne s’applique pas, le nom de colonne est retourné. Dans les deux cas, le pilote définit le champ de la définition de SQL_DESC_UNNAMED sur sql_named n’est lorsqu’elle définit le champ SQL_DESC_NAME. S’il existe aucun nom de colonne ou un alias de colonne, le pilote retourne une chaîne vide dans le champ SQL_DESC_NAME et définit le champ de la définition de SQL_DESC_UNNAMED sur la valeur SQL_UNNAMED.  
  
 Une application peut définir le champ SQL_DESC_NAME d’une infrastructure ou IPD à un nom de paramètre ou un alias pour spécifier les paramètres de procédure stockée par nom. (Pour plus d’informations, consultez [Binding Parameters by Name (Named Parameters)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md).) Le champ SQL_DESC_NAME d’un IRD est un champ en lecture seule ; SQLSTATE HY091 (identificateur de champ de descripteur non valide) est retournée si une application tente de définir.  
  
 Dans IPD, ce champ est non défini si le pilote ne prend pas en charge les paramètres nommés. Si le pilote prend en charge des paramètres nommés et est capable de décrire les paramètres, le nom de paramètre est retourné dans ce champ.  
  
 **SQL_DESC_NULLABLE [descripteurs d’implémentation]**  
 Dans IRDs, ce champ d’enregistrement SQLSMALLINT en lecture seule est SQL_NULLABLE si la colonne peut avoir des valeurs NULL, SQL_NO_NULLS si la colonne n’a pas de valeurs NULL ou SQL_NULLABLE_UNKNOWN si on ne sait pas si la colonne accepte les valeurs NULL. Ce champ se rapporte à la colonne du jeu de résultats, pas la colonne de base.  
  
 Dans IPD, ce champ est toujours défini sur SQL_NULLABLE, car les paramètres dynamiques sont toujours nullables et ne peut pas être définies par une application.  
  
 **SQL_DESC_NUM_PREC_RADIX [All]**  
 Ce champ SQLINTEGER contient une valeur de 2 si le type de données dans le champ SQL_DESC_TYPE est un type de données numérique approximatif, car le champ SQL_DESC_PRECISION contient le nombre de bits. Ce champ contient une valeur de 10 si le type de données dans le champ SQL_DESC_TYPE est un type de données numérique exact, car le champ SQL_DESC_PRECISION contient le nombre de chiffres décimaux. Ce champ est défini sur 0 pour tous les types de données non numériques.  
  
 **SQL_DESC_OCTET_LENGTH [All]**  
 Ce champ d’enregistrement SQLLEN contient la longueur, en octets, d’une chaîne de caractères ou d’un type de données binaires. Pour les caractères de longueur fixe ou de types binaires, il s’agit de la longueur réelle en octets. Pour la longueur de la variable de type caractère ou binaire, il s’agit de la longueur maximale en octets. Cette valeur exclut toujours espace pour le caractère de fin de la valeur null pour les descripteurs de l’implémentation et inclut toujours un espace pour le caractère de fin de la valeur null pour les descripteurs de l’application. Données d’application, ce champ contient la taille de la mémoire tampon. Pour APD, ce champ est défini uniquement pour les paramètres d’entrée/sortie ou de sortie.  
  
 **SQL_DESC_OCTET_LENGTH_PTR [Application descriptors]**  
 Cette SQLLEN * enregistrer le champ pointe vers une variable qui contiendra la longueur totale en octets d’un argument dynamique (pour les descripteurs de paramètre) ou d’une valeur de colonne dépendante (pour les descripteurs de ligne).  
  
 Pour un APD, cette valeur est ignorée pour tous les arguments à l’exception de la chaîne de caractères et binaires ; Si ce champ pointe vers SQL_NTS, l’argument dynamique doit être nul. Pour indiquer qu’un paramètre dépendant sera un paramètre data-at-execution, une application définit ce champ dans l’enregistrement de l’APD approprié à une variable qui, lors de l’exécution, contiendra la valeur SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC . S’il existe plus d’un tel champ, vous pouvez définir SQL_DESC_DATA_PTR sur une valeur qui identifie de façon unique le paramètre pour aider à l’application de déterminer quel paramètre est demandé.  
  
 Si le champ OCTET_LENGTH_PTR d’un ARD est un pointeur null, le pilote ne retourne pas d’informations sur la longueur de la colonne. Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un APD est un pointeur null, le pilote part du principe que les chaînes de caractères et les valeurs binaires sont se terminant par null. (Les valeurs binaires ne doivent pas être nul mais doivent disposer d’une longueur pour éviter la troncation.)  
  
 Si l’appel à **SQLFetch** ou **SQLFetchScroll** que remplit la mémoire tampon désignée par ce champ n’a pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu de la mémoire tampon n’est pas défini. Ce champ est un *champ différée*. Il n’est pas utilisé au moment il a la valeur mais est utilisé ultérieurement par le pilote pour déterminer ou indiquer la longueur en octets des données.  
  
 **SQL_DESC_PARAMETER_TYPE [IPDs]**  
 Ce champ d’enregistrement SQLSMALLINT est défini sur SQL_PARAM_INPUT pour un paramètre d’entrée, SQL_PARAM_INPUT_OUTPUT pour un paramètre d’entrée/sortie, SQL_PARAM_OUTPUT pour un paramètre de sortie, SQL_PARAM_INPUT_OUTPUT_STREAM pour un paramètre d’entrée/sortie transmis en continu ou SQL_ PARAM_OUTPUT_STREAM pour un paramètre de sortie diffusées en continu. Il est défini sur SQL_PARAM_INPUT par défaut.  
  
 Pour une infrastructure ou IPD, le champ est défini à SQL_PARAM_INPUT par défaut si l’IPD n’est pas remplie automatiquement par le pilote (l’attribut d’instruction SQL_ATTR_ENABLE_AUTO_IPD est SQL_FALSE). Une application doit définir ce champ dans l’IPD pour les paramètres qui ne sont pas des paramètres d’entrée.  
  
 **SQL_DESC_PRECISION [All]**  
 Ce champ d’enregistrement SQLSMALLINT contient le nombre de chiffres pour un type numérique exact, le nombre de bits dans la mantisse (précision binaire) pour un type numérique approximatif, ou le nombre de chiffres dans le composant fractions de secondes pour le SQL_TYPE_TIME, SQL_TYPE SQL_C_TYPE, ou un type de données SQL_INTERVAL_SECOND. Ce champ n’est pas défini pour tous les autres types de données.  
  
 La valeur dans ce champ peut être différente de la valeur de la « précision » comme définie dans ODBC 2 *.x*. Pour plus d’informations, consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_ROWVER [descripteurs d’implémentation]**  
 Ce champ SQLSMALLINTrecord indique si une colonne est automatiquement modifiée par le SGBD lorsqu’une ligne est mise à jour (par exemple, il s’agit d’une colonne de type « timestamp » dans SQL Server). La valeur de ce champ d’enregistrement est définie dans le cas contraire SQL_TRUE si la colonne est une colonne de contrôle de version de ligne et SQL_FALSE. Cet attribut de colonne est similaire à l’appel **SQLSpecialColumns** avec IdentifierType de SQL_ROWVER pour déterminer si une colonne est automatiquement mise à jour.  
  
 **SQL_DESC_SCALE [All]**  
 Ce champ d’enregistrement SQLSMALLINT contient la mise à l’échelle définie pour les types de données decimal et numeric. Le champ n’est pas défini pour tous les autres types de données.  
  
 La valeur dans ce champ peut être différente de la valeur pour « identique », tel que défini dans ODBC 2 *.x*. Pour plus d’informations, consultez [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_SCHEMA_NAME [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient le nom de schéma de la table de base qui contient la colonne. La valeur de retour est dépendant du pilote, si la colonne est une expression ou si la colonne fait partie d’une vue. Si la source de données ne prend pas en charge les schémas ou le nom de schéma ne peut pas être déterminé, cette variable contient une chaîne vide.  
  
 **SQL_DESC_SEARCHABLE [IRDs]**  
 Ce champ d’enregistrement SQLSMALLINT en lecture seule est défini à une des valeurs suivantes :  
  
-   SQL_PRED_NONE si la colonne ne peut pas être utilisée dans un **où** clause. (Il est identique à la valeur SQL_UNSEARCHABLE dans ODBC 2 *.x*.)  
  
-   SQL_PRED_CHAR si la colonne peut être utilisée dans un **où** clause, mais uniquement avec les **comme** prédicat. (Il est identique à la valeur SQL_LIKE_ONLY dans ODBC 2 *.x*.)  
  
-   SQL_PRED_BASIC si la colonne peut être utilisée dans un **où** clause avec tous les opérateurs de comparaison à l’exception **comme**. (Il est identique à la valeur SQL_EXCEPT_LIKE dans ODBC 2 *.x*.)  
  
-   SQL_PRED_SEARCHABLE si la colonne peut être utilisée dans un **où** clause avec n’importe quel opérateur de comparaison.  
  
 **SQL_DESC_TABLE_NAME [IRDs]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient le nom de la table de base qui contient cette colonne. La valeur de retour est dépendant du pilote, si la colonne est une expression ou si la colonne fait partie d’une vue.  
  
 **SQL_DESC_TYPE [All]**  
 Ce champ d’enregistrement SQLSMALLINT Spécifie le type de données SQL ou C concis pour tous les types de données à l’exception des types de données date/heure et intervalle. Pour les types de données datetime et interval, ce champ spécifie le type de données détaillées, ce qui est SQL_DATETIME ou SQL_INTERVAL.  
  
 Chaque fois que ce champ contient SQL_DATETIME ou SQL_INTERVAL, le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE doit contenir le sous-code approprié pour le type concis. Pour les types de données datetime, SQL_DESC_TYPE contient SQL_DATETIME, et le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE contient un sous-code pour le type de données date/heure spécifique. Pour les types de données d’intervalle, SQL_DESC_TYPE contient SQL_INTERVAL, et le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE contient un sous-code pour le type de données d’intervalle de temps spécifique.  
  
 Les valeurs dans les champs SQL_DESC_TYPE et SQL_DESC_CONCISE_TYPE sont interdépendants. Chaque fois qu’un des champs est définie, l’autre doit également être définie. SQL_DESC_TYPE peut être définie par un appel à **SQLSetDescField** ou **SQLSetDescRec**. SQL_DESC_CONCISE_TYPE peut être définie par un appel à **SQLBindCol** ou **SQLBindParameter**, ou **SQLSetDescField**.  
  
 Si SQL_DESC_TYPE est défini sur un type de données concis autre qu’un type de données intervalle ou date/heure, le champ SQL_DESC_CONCISE_TYPE est défini sur la même valeur et le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE est défini sur 0.  
  
 Si SQL_DESC_TYPE est défini avec la valeur type de données d’intervalle (SQL_DATETIME ou SQL_INTERVAL) ou verbose datetime et le champ de valeur SQL_DESC_DATETIME_INTERVAL_CODE est défini pour le sous-code approprié, le champ TYPE de SQL_DESC_CONCISE est défini pour le type concis correspondant. Essayez de définir SQL_DESC_TYPE à un des types datetime ou interval concis retourne SQLSTATE HY021 (informations de descripteur incohérent).  
  
 Lorsque le champ SQL_DESC_TYPE est défini par un appel à **SQLBindCol**, **SQLBindParameter**, ou **SQLSetDescField**, les champs suivants sont définis pour les valeurs par défaut suivantes, comme indiqué dans le tableau ci-dessous. Les valeurs des champs restants du même enregistrement sont indéfinies.  
  
|Valeur de SQL_DESC_TYPE|Autres champs définis implicitement|  
|------------------------------|---------------------------------|  
|SQL_CHAR, SQL_VARCHAR, SQL_C_CHAR, SQL_C_VARCHAR|SQL_DESC_LENGTH est défini sur 1. SQL_DESC_PRECISION est définie sur 0.|  
|SQL_DATETIME|Lorsque la valeur SQL_DESC_DATETIME_INTERVAL_CODE est définie sur SQL_CODE_DATE ou SQL_CODE_TIME, SQL_DESC_PRECISION est définie sur 0. Lorsqu’elle est définie sur SQL_DESC_TIMESTAMP, SQL_DESC_PRECISION est définie sur 6.|  
|SQL_DECIMAL, SQL_NUMERIC, SQL_C_NUMERIC|SQL_DESC_SCALE est définie sur 0. SQL_DESC_PRECISION est défini sur la précision définie par l’implémentation pour le type de données respectifs.<br /><br /> Consultez [SQL vers C: Numérique](../../../odbc/reference/appendixes/sql-to-c-numeric.md) pour plus d’informations sur la façon de lier manuellement une valeur SQL_C_NUMERIC.|  
|SQL_FLOAT, SQL_C_FLOAT|SQL_DESC_PRECISION est définie sur la précision par défaut définie par l’implémentation pour SQL_FLOAT.|  
|SQL_INTERVAL|Lorsque la valeur SQL_DESC_DATETIME_INTERVAL_CODE est définie sur un type de données d’intervalle, SQL_DESC_DATETIME_INTERVAL_PRECISION est défini sur 2 (la précision de début de l’intervalle de valeur par défaut). Lorsque l’intervalle a un composant « secondes », SQL_DESC_PRECISION est définie sur 6 (la précision par défaut intervalle secondes).|  
  
 Lorsqu’une application appelle **SQLSetDescField** pour définir des champs d’un descripteur au lieu d’appeler **SQLSetDescRec**, l’application doit déclarer tout d’abord le type de données. Lorsque cela arrive, les autres champs indiqués dans le tableau précédent sont implicitement définis. Si une des valeurs implicitement ensemble est inacceptable, l’application peut ensuite appeler **SQLSetDescField** ou **SQLSetDescRec** pour définir la valeur inacceptable explicitement.  
  
 **SQL_DESC_TYPE_NAME [descripteurs d’implémentation]**  
 Cette SQLCHAR en lecture seule * champ d’enregistrement contient le nom de type de dépend de la source de données (par exemple, « CHAR », « VARCHAR » et ainsi de suite). Si le nom de type de données est inconnu, cette variable contient une chaîne vide.  
  
 **Définition de SQL_DESC_UNNAMED [descripteurs d’implémentation]**  
 Ce champ d’enregistrement SQLSMALLINT dans un descripteur de ligne est défini par le pilote à la valeur SQL_NAMED ou valeur SQL_UNNAMED lors de la définition du champ SQL_DESC_NAME. Si le champ SQL_DESC_NAME contient un alias de colonne ou l’alias de colonne ne s’applique pas, le pilote définit le champ de la définition de SQL_DESC_UNNAMED sur sql_named n’est. Si une application définit le champ SQL_DESC_NAME d’une infrastructure ou IPD pour un alias ou nom de paramètre, le pilote définit le champ SQL_DESC_UNNAMED de l’IPD sur sql_named n’est. S’il existe aucun nom de colonne ou un alias de colonne, le pilote définit le champ de la définition de SQL_DESC_UNNAMED sur valeur SQL_UNNAMED.  
  
 Une application peut définir le champ de la définition de SQL_DESC_UNNAMED d’une infrastructure ou IPD à la valeur SQL_UNNAMED. Un pilote retourne SQLSTATE HY091 (identificateur de champ de descripteur non valide) si une application tente de définir le champ de la définition de SQL_DESC_UNNAMED d’une infrastructure ou IPD sur sql_named n’est. Le champ de la définition de SQL_DESC_UNNAMED d’un IRD est en lecture seule ; SQLSTATE HY091 (identificateur de champ de descripteur non valide) est retournée si une application tente de définir.  
  
 **SQL_DESC_UNSIGNED [descripteurs d’implémentation]**  
 Ce champ d’enregistrement SQLSMALLINT en lecture seule est défini à SQL_TRUE si le type de colonne est non signé ou non numériques ou SQL_FALSE si le type de colonne est signé.  
  
 **SQL_DESC_UPDATABLE [IRDs]**  
 Ce champ d’enregistrement SQLSMALLINT en lecture seule est défini à une des valeurs suivantes :  
  
-   SQL_ATTR_READ_ONLY si le jeu de résultats colonne est en lecture seule.  
  
-   SQL_ATTR_WRITE si le jeu de résultats colonne est en lecture-écriture.  
  
-   SQL_ATTR_READWRITE_UNKNOWN si on ne sait pas si le jeu de résultats colonne est modifiable ou pas.  
  
 SQL_DESC_UPDATABLE décrit la mise à jour de la colonne du jeu de résultats, pas la colonne dans la table de base. La mise à jour de la colonne dans la table de base sur laquelle repose cette colonne de jeu de résultats peut être différente de la valeur dans ce champ. Si une colonne doit être mise à jour peut reposer sur le type de données, des privilèges d’utilisateur et la définition du résultat de la définir lui-même. S’il est difficile de savoir si une colonne est modifiable, SQL_ATTR_READWRITE_UNKNOWN doit être retourné.  
  
## <a name="consistency-checks"></a>Vérifications de cohérence  
 Une vérification de cohérence est effectuée par le pilote automatiquement chaque fois qu’une application transmet une valeur pour le champ SQL_DESC_DATA_PTR du ARD, APD ou IPD. Si aucun champ n’est pas cohérente avec les autres champs, **SQLSetDescField** retourne SQLSTATE HY021 (informations de descripteur incohérent). Pour plus d’informations, consultez « Vérification de cohérence » dans [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une colonne|[SQLBindCol, fonction](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Un paramètre de liaison|[SQLBindParameter, fonction](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Obtention d’un champ de descripteur|[SQLGetDescField, fonction](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtention de plusieurs champs de descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Définition de plusieurs champs de descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Informations de référence sur l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)
