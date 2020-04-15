---
title: Fonction SQLSetDescField (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 122d4b26d1d75811d4a8e252378ce8f81ca2c66b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299549"
---
# <a name="sqlsetdescfield-function"></a>SQLSetDescField, fonction

**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLSetDescField** établit la valeur d’un seul champ d’un enregistrement descripteur.  
  
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
 [Entrée] Poignée descripteur.  
  
 *RecNumber*  
 [Entrée] Indique le dossier descripteur contenant le champ que la demande cherche à définir. Les enregistrements descripteur sont numérotés à partir de 0, avec le numéro 0 record étant le signet record. *L’argument RecNumber* est ignoré pour les champs d’en-tête.  
  
 *FieldIdentifier*  
 [Entrée] Indique le champ du descripteur dont la valeur doit être définie. Pour plus d’informations, voir "*FieldIdentifier* Argument " dans la section "Commentaires".  
  
 *ValuePtr*  
 [Entrée] Pointeur vers un tampon contenant les informations descripteur, ou une valeur d’intégrateur. Le type de données dépend de la valeur de *FieldIdentifier*. Si *ValuePtr* est une valeur integer, il peut être considéré comme 8 octets (SQLLEN), 4 octets (SQLINTEGER) ou 2 octets (SQLSMALLINT), selon la valeur de *l’argument FieldIdentifier.*  
  
 *BufferLength*  
 [Entrée] Si *FieldIdentifier* est un champ défini par L’ODBC et *que ValuePtr* indique une chaîne de caractères ou un tampon binaire, cet argument devrait être la longueur de*la valeurptr*. Pour les données de chaîne de caractère, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *FieldIdentifier* est un champ défini par L’ODBC et *que ValuePtr* est un intégrateur, *BufferLength* est ignoré.  
  
 Si *FieldIdentifier* est un champ défini par le conducteur, l’application indique la nature du champ au gestionnaire de conducteur en définissant l’argument *De bufferLength.* *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si *ValuePtr* est un pointeur d’une chaîne de caractères, alors *BufferLength* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si *ValuePtr* est un pointeur à un tampon binaire, alors l’application place le résultat de la SQL_LEN_BINARY_ATTR(*longueur)* macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si *ValuePtr* est un pointeur à une valeur autre qu’une chaîne de caractère ou une chaîne binaire, alors *BufferLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si *ValuePtr* contient une valeur de longueur fixe, *bufferLength* est soit SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_IS_USMALLINT, le cas échéant.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetDescField** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DESC et une *poignée* de *DescriptorHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLSetDescField** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option modifiée|Le conducteur n’a pas pris en charge la valeur spécifiée dans * \*ValuePtr* (si *ValuePtr* était un pointeur) ou la valeur de *ValuePtr* (si *ValuePtr* était une valeur integer), ou * \*ValuePtr* était invalide en raison des conditions de travail de mise en œuvre, de sorte que le conducteur a substitué une valeur similaire. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07009|Indice descripteur invalide|*L’argument de FieldIdentifier* était un champ de disques, *l’argument de RecNumber* était 0, et *l’argument de DescriptorHandle* faisait référence à une poignée ipD.<br /><br /> *L’argument de RecNumber* était inférieur à 0, et *l’argument de DescriptorHandle* faisait référence à un ARD ou à un APD.<br /><br /> *L’argument du RecNumber* était supérieur au nombre maximal de colonnes ou de paramètres que la source de données peut prendre en charge, et *l’argument de DescriptorHandle* faisait référence à une DPA ou à une ARD.<br /><br /> (DM) *L’argument de FieldIdentifier* était SQL_DESC_COUNT, et * \*l’argument de ValuePtr* était inférieur à 0.<br /><br /> *L’argument du RecNumber* était égal à 0, et *l’argument de DescriptorHandle* faisait référence à une DPA implicitement attribuée. (Cette erreur ne se produit pas avec un descripteur d’application explicitement attribué, car on ne sait pas si un descripteur d’application explicitement attribué est un APD ou une ARD jusqu’au moment de l’exécution.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22001|Données de chaîne, droite tronquées|*L’argument de FieldIdentifier* était SQL_DESC_NAME, et l’argument *de BufferLength* était une valeur plus grande que SQL_MAX_IDENTIFIER_LEN.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) Le *DescriptorHandle* a été associé à un *StatementHandle* pour lequel une fonction d’exécution asynchrone (pas celle-ci) a été appelée et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* avec lequel le *DescriptorHandle* a été associé et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *DescriptorHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLSetDescField** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour l’une des poignées de déclaration associées au *DescriptorHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY016|Impossible de modifier un descripteur de ligne de mise en œuvre|*L’argument de DescriptorHandle* était associé à un IRD, et *l’argument de FieldIdentifier* n’était pas SQL_DESC_ARRAY_STATUS_PTR ou SQL_DESC_ROWS_PROCESSED_PTR.|  
|HY021|Informations descripteur incohérentes|Les champs de SQL_DESC_TYPE et de SQL_DESC_DATETIME_INTERVAL_CODE ne forment pas un type SQL ODBC valide ou un type SQL valide spécifique au conducteur (pour les DPI) ou un type C ODBC valide (pour les APR ou les DR).<br /><br /> Les renseignements descripteur vérifiés lors d’une vérification de cohérence n’étaient pas cohérents. (Voir "Vérification de cohérence" dans **SQLSetDescRec**.)|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) * \*ValuePtr* est une chaîne de caractères, et *BufferLength* était inférieur à zéro, mais n’était pas égal à SQL_NTS.<br /><br /> (DM) Le conducteur était un conducteur ODBC 2 *.x,* le descripteur était un ARD, *l’argument de ColumnNumber* a été réglé à 0, et la valeur spécifiée pour l’argument *BufferLength* n’était pas égale à 4.|  
|HY091 HY091|Identifiant de champ descripteur invalide|La valeur spécifiée pour l’argument *de FieldIdentifier* n’était pas un champ défini par l’ODBC et n’était pas une valeur définie par la mise en œuvre.<br /><br /> *L’argument de FieldIdentifier* était invalide pour l’argument *de DescriptorHandle.*<br /><br /> *L’argument de FieldIdentifier* était un domaine défini par L’ODBC.|  
|HY092 HY092|Identification d’attribut/option invalide|La valeur de * \*ValuePtr* n’était pas valable pour l’argument *de l’identification de champ.*<br /><br /> *L’argument de FieldIdentifier* était SQL_DESC_UNNAMED, et *ValuePtr* était SQL_NAMED.|  
|Hy105|Type de paramètre invalide|(DM) La valeur spécifiée pour le champ SQL_DESC_PARAMETER_TYPE était invalide. (Pour plus d’informations, voir la section «*InputOutputType* Argument » dans **SQLBindParameter**.)|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [What’s New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *DescriptorHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLSetDescField** pour définir n’importe quel champ descripteur un à la fois. Un appel à **SQLSetDescField** place un seul champ dans un seul descripteur. Cette fonction peut être appelée à définir n’importe quel champ dans n’importe quel type de descripteur, à condition que le champ puisse être défini. (Voir la table plus tard dans cette section.)  
  
> [!NOTE]  
>  Si un appel à **SQLSetDescField** échoue, le contenu du dossier descripteur identifié par l’argument *du RecNumber* n’est pas défini.  
  
 D’autres fonctions peuvent être appelées à définir plusieurs champs descripteur avec un seul appel de la fonction. La fonction **SQLSetDescRec** définit une variété de champs qui affectent le type de données et la mémoire tampon liés à une colonne ou un paramètre (les champs SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR et SQL_DESC_INDICATOR_PTR). **SQLBindCol** ou **SQLBindParameter** peuvent être utilisés pour faire une spécification complète pour la liaison d’une colonne ou d’un paramètre. Ces fonctions établissent un groupe spécifique de champs descripteurs avec un appel de fonction.  
  
 **SQLSetDescField** peut être appelé à modifier les tampons de liaison en ajoutant un décalage aux pointeurs de liaison (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR ou SQL_DESC_OCTET_LENGTH_PTR). Cela modifie les tampons de liaison sans appeler **SQLBindCol** ou **SQLBindParameter**, ce qui permet à une application de changer SQL_DESC_DATA_PTR sans changer d’autres champs, comme SQL_DESC_DATA_TYPE.  
  
 Si une demande appelle **SQLSetDescField** pour définir n’importe quel champ autre que SQL_DESC_COUNT ou les champs différés SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR ou SQL_DESC_INDICATOR_PTR, le dossier devient non lié.  
  
 Les champs d’en-tête descripteur sont réglés en appelant **SQLSetDescField** avec *l’identification de champ*appropriée. Beaucoup de champs d’en-tête sont également attributs de déclaration, de sorte qu’ils peuvent également être fixés par un appel à **SQLSetStmtAttr**. Cela permet aux applications de définir un champ descripteur sans d’abord obtenir une poignée descripteur. Lorsque **SQLSetDescField** est appelé à définir un champ d’en-tête, *l’argument RecNumber* est ignoré.  
  
 Un *RecNumber* de 0 est utilisé pour définir des champs de signets.  
  
> [!NOTE]  
>  L’attribut d’énoncé SQL_ATTR_USE_BOOKMARKS doit toujours être réglé avant d’appeler **SQLSetDescField** pour définir des champs de signets. Bien que ce ne soit pas obligatoire, il est fortement recommandé.  
  
## <a name="sequence-of-setting-descriptor-fields"></a>Séquence de réglage des champs descripteur  
 Lors de la définition des champs descripteur en appelant **SQLSetDescField**, l’application doit suivre une séquence spécifique:  
  
1.  L’application doit d’abord définir le champ SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE ou SQL_DESC_DATETIME_INTERVAL_CODE.  
  
2.  Une fois qu’un de ces champs a été défini, l’application peut définir un attribut d’un type de données, et le pilote définit des champs d’attributs de type de données aux valeurs par défaut appropriées pour le type de données. Le défaut automatique des champs d’attribut de type garantit que le descripteur est toujours prêt à l’emploi une fois que l’application a spécifié un type de données. Si l’application définit explicitement un attribut de type de données, elle dépasse l’attribut par défaut.  
  
3.  Une fois que l’un des champs énumérés dans l’étape 1 a été défini et que des attributs de type de données ont été définis, l’application peut définir SQL_DESC_DATA_PTR. Cela incite à une vérification de cohérence des champs descripteur. Si l’application modifie le type de données ou les attributs après la mise en place du champ SQL_DESC_DATA_PTR, le pilote fixe SQL_DESC_DATA_PTR à un pointeur nul, débinant l’enregistrement. Cela oblige l’application à remplir les étapes appropriées dans l’ordre, avant que l’enregistrement descripteur est utilisable.  
  
## <a name="initialization-of-descriptor-fields"></a>Initialisation de champs de descripteur  
 Lorsqu’un descripteur est attribué, les champs du descripteur peuvent être paralés à une valeur par défaut, être paralés sans valeur par défaut ou être indéfinis pour le type de descripteur. Les tableaux suivants indiquent l’initialisation de chaque champ pour chaque type de descripteur, avec "D" indiquant que le champ est paralé avec un défaut, et "ND" indiquant que le champ est paraléized sans défaut. Si un numéro est affiché, la valeur par défaut du champ est ce nombre. Les tableaux indiquent également si un champ est lu/écrit (R/W) ou lu uniquement (R).  
  
 Les champs d’une IRD n’ont une valeur par défaut qu’après que la déclaration a été préparée ou exécutée et que l’IRD a été peuplée, et non lorsque le poignée ou le descripteur de déclaration a été attribué. Jusqu’à ce que l’IRD ait été peuplée, toute tentative d’accès à un champ d’IRD retournera une erreur.  
  
 Certains champs descripteurs sont définis pour un ou plusieurs, mais pas tous, des types descripteurs (ARD et DR, et AD AP et DPI). Lorsqu’un champ n’est pas défini pour un type de descripteur, il n’est pas nécessaire par aucune des fonctions qui utilisent ce descripteur.  
  
 Les champs accessibles par **SQLGetDescField** ne peuvent pas nécessairement être fixés par **SQLSetDescField**. Les champs qui peuvent être définis par **SQLSetDescField** sont répertoriés dans les tableaux suivants.  
  
 L’initialisation des champs d’en-tête est décrite dans le tableau qui suit.  
  
|Nom de champ d’en-tête|Type|R/W (Lecture/écriture)|Default|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD: R APD: R IRD: R IPD: R|ARD: SQL_DESC_ALLOC_AUTO pour implicite ou SQL_DESC_ALLOC_USER pour explicite<br /><br /> APD: SQL_DESC_ALLOC_AUTO pour implicite ou SQL_DESC_ALLOC_USER pour explicite<br /><br /> IRD: SQL_DESC_ALLOC_AUTO<br /><br /> IPD: SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN (SQLULEN)|ARD: R/W APD: R/W IRD: IPD inutilisé: Inutilisé|ARD:[1] APD:[1] IRD: IPD inutilisé: Inutilisé|  
|SQL_DESC_ARRAY_STATUS_PTR|SQLUSMALLINT|ARD: APD R/W: R/W IRD: R/W IPD: R/W|ARD: Null ptr APD: Null ptr IRD: Null ptr IPD: Null ptr|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLENMD|ARD: R/W APD: R/W IRD: IPD inutilisé: Inutilisé|ARD: Null ptr APD: Null ptr IRD: IPD inutilisé: Inutilisé|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD: R/W APD: R/W IRD: IPD inutilisé: Inutilisé|ARD: SQL_BIND_BY_COLUMN<br /><br /> APD: SQL_BIND_BY_COLUMN<br /><br /> IRD: Inutilisé<br /><br /> IPD: inutilisé|  
|SQL_DESC_COUNT|SQLSMALLINT|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: 0 APD: 0 IRD: D IPD: 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN|ARD: APD inutilisé: IRD inutilisé: R/W IPD: R/W|ARD: APD inutilisé: IRD inutilisé: Null ptr IPD: Null ptr|  
  
 [1] Ces champs ne sont définis que lorsque l’IPD est automatiquement peuplé par le conducteur. Si ce n’est pas le cas, ils ne sont pas définis. Si une application tente de définir ces champs, SQLSTATE HY091 (identificateur de champ descripteur invalide) sera retourné.  
  
 L’initialisation des champs de disques est comme le montre le tableau suivant.  
  
|Nom de champ d’enregistrement|Type|R/W (Lecture/écriture)|Default|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD: APD inutilisé: IRD inutilisé: R IPD: R|ARD: APD inutilisé: IRD inutilisé: D IPD: D[1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: SQL_C_ APD PAR DÉFAUT: SQL_C_ IRD PAR DÉFAUT: D IPD: ND|  
|SQL_DESC_DATA_PTR|SQLPOINTER (SQLPOINTER)|ARD: R/W APD: R/W IRD: IPD inutilisé: Inutilisé|ARD: Null ptr APD: Null ptr IRD: IPD inutilisé: Inutilisé[2]|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_DISPLAY_SIZE|SQLLEN (SQLLEN)|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD: APD inutilisé: IRD inutilisé: R IPD: R|ARD: APD inutilisé: IRD inutilisé: D IPD: D[1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN - France|ARD: R/W APD: R/W IRD: IPD inutilisé: Inutilisé|ARD: Null ptr APD: Null ptr IRD: IPD inutilisé: Inutilisé|  
|SQL_DESC_LABEL|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_LENGTH|SQLULEN (SQLULEN)|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: R|ARD: APD inutilisé: IRD inutilisé: D IPD: D[1]|  
|SQL_DESC_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD: APD inutilisé: IRD inutilisé: R IPD: R|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH|SQLLEN (SQLLEN)|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN - France|ARD: R/W APD: R/W IRD: IPD inutilisé: Inutilisé|ARD: Null ptr APD: Null ptr IRD: IPD inutilisé: Inutilisé|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD: APD inutilisé: IRD inutilisé: IPD inutilisé: R/W|ARD: APD inutilisé: IRD inutilisé: IPD inutilisé: D-SQL_PARAM_INPUT|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD: Inutilisé<br /><br /> APD: Inutilisé<br /><br /> IRD: R<br /><br /> IPD: R|ARD: Inutilisé<br /><br /> APD: Inutilisé<br /><br /> IRD: ND<br /><br /> IPD: ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_TABLE_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD: APD R/W: R/W IRD: R IPD: R/W|ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT IRD: D IPD: ND|  
|SQL_DESC_TYPE_NAME|SQLCHAR - France|ARD: APD inutilisé: IRD inutilisé: R IPD: R|ARD: APD inutilisé: IRD inutilisé: D IPD: D[1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD: APD inutilisé: IRD inutilisé: R IPD: R/W|ARD: APD ND: ND IRD: D IPD: ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD: APD inutilisé: IRD inutilisé: R IPD: R|ARD: APD inutilisé: IRD inutilisé: D IPD: D[1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD: APD inutilisé: IRD inutilisé: R IPD: Inutilisé|ARD: APD inutilisé: IRD inutilisé: D IPD: Inutilisé|  
  
 [1] Ces champs ne sont définis que lorsque l’IPD est automatiquement peuplé par le conducteur. Si ce n’est pas le cas, ils ne sont pas définis. Si une application tente de définir ces champs, SQLSTATE HY091 (identificateur de champ descripteur invalide) sera retourné.  
  
 [2] Le champ SQL_DESC_DATA_PTR dans l’IPD peut être réglé pour forcer une vérification de cohérence. Dans un appel ultérieur à **SQLGetDescField** ou **SQLGetDescRec**, le conducteur n’est pas tenu de retourner la valeur à laquelle SQL_DESC_DATA_PTR a été fixé.  
  
## <a name="fieldidentifier-argument"></a>FieldIdentifier Argument  
 *L’argument de FieldIdentifier* indique le champ descripteur à définir. Un descripteur contient *l’en-tête du descripteur,* composé des champs d’en-tête décrits dans la section suivante, «Header Fields», et de zéro ou plus *des enregistrements descripteur,* composé des champs d’enregistrement décrits dans la section suivant la section «Champs de tête».  
  
## <a name="header-fields"></a>Champs d’en-têtes  
 Chaque descripteur a un en-tête composé des champs suivants :  
  
 **SQL_DESC_ALLOC_TYPE [Tous]**  
 Ce champ d’en-tête SQLSMALLINT uniquement lu précise si le descripteur a été automatiquement attribué par le conducteur ou explicitement par la demande. L’application peut obtenir, mais pas modifier, ce champ. Le champ est réglé pour SQL_DESC_ALLOC_AUTO par le conducteur si le descripteur a été automatiquement attribué par le conducteur. Il est réglé pour SQL_DESC_ALLOC_USER par le conducteur si le descripteur a été explicitement attribué par la demande.  
  
 **SQL_DESC_ARRAY_SIZE [Descripteurs d’application]**  
 Dans les ARD, ce champ d’en-tête SQLULEN précise le nombre de rangées dans le ramage. Il s’agit du nombre de lignes à retourner par un appel à **SQLFetch** ou **SQLFetchScroll** ou à être opéré par un appel à **SQLBulkOperations** ou **SQLSetPos**.  
  
 Dans les AD APD, ce champ d’en-tête SQLULEN précise le nombre de valeurs pour chaque paramètre.  
  
 La valeur par défaut de ce champ est de 1. Si SQL_DESC_ARRAY_SIZE est supérieure à 1, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, et SQL_DESC_OCTET_LENGTH_PTR de l’APD ou ARD point à des tableaux. La cardinalité de chaque tableau est égale à la valeur de ce domaine.  
  
 Ce champ dans l’ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_ARRAY_SIZE. Ce champ dans l’APD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAMSET_SIZE.  
  
 **SQL_DESC_ARRAY_STATUS_PTR [Tous]**  
 Pour chaque type de descripteur, ce champ d’en-tête SQLUSMALLINT -en-tête indique un éventail de valeurs SQLUSMALLINT. Ces tableaux sont nommés comme suit : tableau d’état de la ligne (IRD), tableau d’état de paramètre (IPD), tableau d’opération de ligne (ARD) et tableau de fonctionnement des paramètres (APD).  
  
 Dans l’IRD, ce champ d’en-tête pointe vers un tableau d’état de ligne contenant des valeurs de statut après un appel à **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**. Le tableau a autant d’éléments qu’il ya des rangées dans le rowset. L’application doit allouer un éventail de SQLUSMALLINTs et définir ce champ pour pointer vers le tableau. Le champ est réglé à un pointeur nul par défaut. Le conducteur remplira le tableau - à moins que le champ SQL_DESC_ARRAY_STATUS_PTR est réglé à un pointeur nul, auquel cas aucune valeur de statut n’est générée et le tableau n’est pas peuplé.  
  
> [!CAUTION]  
>  Le comportement du conducteur n’est pas défini si l’application définit les éléments du tableau d’état de la ligne pointés par le champ SQL_DESC_ARRAY_STATUS_PTR de l’IRD.  
  
 Le tableau est d’abord peuplé d’un appel à **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**. Si l’appel n’est pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tableau pointé par ce champ n’est pas défini. Les éléments du tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_ROW_SUCCESS: La rangée a été récupérée avec succès et n’a pas changé depuis qu’elle a été récupérée pour la dernière fois.  
  
-   SQL_ROW_SUCCESS_WITH_INFO: La rangée a été récupérée avec succès et n’a pas changé depuis qu’il a été récupéré pour la dernière fois. Cependant, un avertissement a été retourné au sujet de la rangée.  
  
-   SQL_ROW_ERROR : Une erreur s’est produite en allant chercher la rangée.  
  
-   SQL_ROW_UPDATED: La rangée a été récupérée avec succès et a été mise à jour depuis qu’il a été récupéré pour la dernière fois. Si la ligne est récupérée à nouveau, son statut est SQL_ROW_SUCCESS.  
  
-   SQL_ROW_DELETED: La ligne a été supprimée depuis qu’il a été récupéré pour la dernière fois.  
  
-   SQL_ROW_ADDED: La rangée a été insérée par **SQLBulkOperations**. Si la ligne est récupérée à nouveau, son statut est SQL_ROW_SUCCESS.  
  
-   SQL_ROW_NOROW : Le jeu de ligne chevauchait la fin de l’ensemble de résultats, et aucune ligne n’a été retournée qui correspondait à cet élément du tableau d’état de la ligne.  
  
 Ce champ dans l’IRD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_STATUS_PTR.  
  
 Le champ SQL_DESC_ARRAY_STATUS_PTR de l’IRD n’est valable qu’après SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO a été retourné. Si le code de retour n’est pas l’un d’entre eux, l’emplacement indiqué par SQL_DESC_ROWS_PROCESSED_PTR n’est pas défini.  
  
 Dans l’IPD, ce champ d’en-tête indique un tableau d’état de paramètres contenant des informations d’état pour chaque ensemble de valeurs de paramètres après un appel à **SQLExecute** ou **SQLExecDirect**. Si l’appel à **SQLExecute** ou **SQLExecDirect** n’est pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tableau pointé par ce champ n’est pas défini. L’application doit allouer un éventail de SQLUSMALLINTs et définir ce champ pour pointer vers le tableau. Le conducteur remplira le tableau - à moins que le champ SQL_DESC_ARRAY_STATUS_PTR est réglé à un pointeur nul, auquel cas aucune valeur de statut n’est générée et le tableau n’est pas peuplé. Les éléments du tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_PARAM_SUCCESS : La déclaration sqL a été exécutée avec succès pour cet ensemble de paramètres.  
  
-   SQL_PARAM_SUCCESS_WITH_INFO : La déclaration de SQL a été exécutée avec succès pour cet ensemble de paramètres; cependant, des informations d’avertissement sont disponibles dans la structure de données de diagnostic.  
  
-   SQL_PARAM_ERROR : Une erreur s’est produite dans le traitement de cet ensemble de paramètres. Des informations supplémentaires sur les erreurs sont disponibles dans la structure de données de diagnostic.  
  
-   SQL_PARAM_UNUSED : Cet ensemble de paramètres n’a pas été utilisé, peut-être en raison du fait qu’un ensemble de paramètres antérieur a causé une erreur qui a avorté davantage de traitement, ou parce que SQL_PARAM_IGNORE a été défini pour cet ensemble de paramètres dans le tableau spécifié par le champ SQL_DESC_ARRAY_STATUS_PTR de l’APD.  
  
-   SQL_PARAM_DIAG_UNAVAILABLE : L’information diagnostique n’est pas disponible. Un exemple de ceci est quand le conducteur traite des tableaux de paramètres comme une unité monolithique et ne génère donc pas ce niveau d’information d’erreur.  
  
 Ce champ dans l’IPD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAM_STATUS_PTR.  
  
 Dans l’ARD, ce champ d’en-tête indique un éventail de valeurs d’opération de ligne qui peuvent être définies par l’application pour indiquer si cette ligne doit être ignorée pour les opérations **SQLSetPos.** Les éléments du tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_ROW_PROCEED: La ligne est incluse dans l’opération en vrac à l’aide **de SQLSetPos**. (Ce paramètre ne garantit pas que l’opération aura lieu sur la rangée. Si la ligne a le statut SQL_ROW_ERROR dans le tableau d’état de la rangée IRD, le conducteur pourrait ne pas être en mesure d’effectuer l’opération dans la rangée.)  
  
-   SQL_ROW_IGNORE: La ligne est exclue de l’opération en vrac à l’aide **de SQLSetPos**.  
  
 Si aucun élément du tableau n’est défini, toutes les lignes sont incluses dans l’opération en vrac. Si la valeur dans le champ SQL_DESC_ARRAY_STATUS_PTR de l’ARD est un pointeur nul, toutes les lignes sont incluses dans l’opération en vrac; l’interprétation est la même que si le pointeur pointait vers un tableau valide et tous les éléments du tableau étaient SQL_ROW_PROCEED. Si un élément du tableau est réglé pour SQL_ROW_IGNORE, la valeur du tableau d’état de la ligne pour la ligne ignorée n’est pas modifiée.  
  
 Ce champ dans l’ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_OPERATION_PTR.  
  
 Dans l’APD, ce champ d’en-tête indique un ensemble de paramètres de fonctionnement de valeurs qui peuvent être définis par l’application pour indiquer si cet ensemble de paramètres doit être ignoré lorsque **SQLExecute** ou **SQLExecDirect** est appelé. Les éléments du tableau peuvent contenir les valeurs suivantes :  
  
-   SQL_PARAM_PROCEED : L’ensemble des paramètres est inclus dans **l’appel SQLExecute** ou **SQLExecDirect.**  
  
-   SQL_PARAM_IGNORE : L’ensemble des paramètres est exclu de l’appel **SQLExecute** ou **SQLExecDirect.**  
  
 Si aucun élément du tableau n’est défini, tous les ensembles de paramètres du tableau sont utilisés dans les appels **SQLExecute** ou **SQLExecDirect.** Si la valeur dans le champ SQL_DESC_ARRAY_STATUS_PTR de l’APD est un pointeur nul, tous les ensembles de paramètres sont utilisés; l’interprétation est la même que si le pointeur pointait vers un tableau valide et tous les éléments du tableau étaient SQL_PARAM_PROCEED.  
  
 Ce champ dans l’APD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAM_OPERATION_PTR.  
  
 **SQL_DESC_BIND_OFFSET_PTR [Descripteurs d’application]**  
 Ce champ d’en-tête SQLLEN -pointe vers le décalage de liaison. Il est réglé à un pointeur nul par défaut. Si ce champ n’est pas un pointeur nul, le conducteur déreférence le pointeur et ajoute la valeur déreférée à chacun des champs différés qui a une valeur non nulle dans le dossier descripteur (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR) au moment d’aller chercher et utilise les nouvelles valeurs de pointeur lors de la liaison.  
  
 Le décalage contraignant est toujours ajouté directement aux valeurs dans les domaines de la SQL_DESC_DATA_PTR, de la SQL_DESC_INDICATOR_PTR et de la SQL_DESC_OCTET_LENGTH_PTR. Si le décalage est modifié à une valeur différente, la nouvelle valeur est toujours ajoutée directement à la valeur dans chaque champ descripteur. Le nouveau décalage n’est pas ajouté à la valeur du champ plus une compensation antérieure.  
  
 Ce champ est un *champ différé*: il n’est pas utilisé au moment où il est défini mais est utilisé ultérieurement par le conducteur lorsqu’il doit déterminer les adresses pour les tampons de données.  
  
 Ce champ dans l’ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROW_BIND_OFFSET_PTR. Ce champ dans l’ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAM_BIND_OFFSET_PTR.  
  
 Pour plus d’informations, voir la description de la liaison en ligne dans [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) et [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 **SQL_DESC_BIND_TYPE [Descripteurs d’application]**  
 Ce champ d’en-tête SQLUINTEGER définit l’orientation de liaison à utiliser pour lier des colonnes ou des paramètres.  
  
 Dans les DRR, ce champ spécifie l’orientation de liaison lorsque **SQLFetchScroll** ou **SQLFetch** est appelé sur la poignée de déclaration associée.  
  
 Pour sélectionner la liaison de colonnes pour les colonnes, ce champ est configuré pour SQL_BIND_BY_COLUMN (la valeur par défaut).  
  
 Ce champ dans l’ARD peut également être défini en appelant **SQLSetStmtAttr** avec *l’attribut*SQL_ATTR_ROW_BIND_TYPE .  
  
 Dans les APA, ce domaine spécifie l’orientation contraignante à utiliser pour les paramètres dynamiques.  
  
 Pour sélectionner la liaison de colonne-sage pour les paramètres, ce champ est configuré pour SQL_BIND_BY_COLUMN (la valeur par défaut).  
  
 Ce champ dans l’APD peut également être défini en appelant **SQLSetStmtAttr** avec *l’attribut*SQL_ATTR_PARAM_BIND_TYPE .  
  
 **SQL_DESC_COUNT [Tous]**  
 Ce champ d’en-tête SQLSMALLINT précise l’indice à 1 base de l’enregistrement le plus numéroté qui contient des données. Lorsque le conducteur définit la structure de données du descripteur, il doit également définir le champ SQL_DESC_COUNT pour montrer combien d’enregistrements sont significatifs. Lorsqu’une application attribue une instance de cette structure de données, elle n’a pas à préciser le nombre d’enregistrements pour réserver de la place. Au fur et à mesure que l’application spécifie le contenu des dossiers, le conducteur prend toutes les mesures nécessaires pour s’assurer que la poignée du descripteur se réfère à une structure de données de la taille adéquate.  
  
 SQL_DESC_COUNT n’est pas un décompte de toutes les colonnes de données qui sont liées (si le champ est dans une ARD) ou de tous les paramètres qui sont liés (si le champ est dans un APD), mais le nombre de l’enregistrement le plus numéroté. Si la colonne ou le paramètre le plus numéroté n’est pas lié, SQL_DESC_COUNT est changée pour le nombre de la colonne ou du paramètre le plus numéroté suivant. Si une colonne ou un paramètre avec un nombre inférieur au nombre de colonnes les plus numérotées n’est pas lié (en appelant **SQLBindCol** avec l’argument *TargetValuePtr* réglé à un pointeur nul, ou **SQLBindParameter** avec *l’argument ParameterValuePtr* réglé à un pointeur nul), SQL_DESC_COUNT n’est pas changé. Si des colonnes ou des paramètres supplémentaires sont liés avec des nombres supérieurs à l’enregistrement le plus élevé qui contient des données, le pilote augmente automatiquement la valeur dans le champ SQL_DESC_COUNT. Si toutes les colonnes ne sont pas liées en appelant **SQLFreeStmt** avec l’option SQL_UNBIND, les champs SQL_DESC_COUNT dans l’ARD et l’IRD sont réglés à 0. Si **SQLFreeStmt** est appelé avec l’option SQL_RESET_PARAMS, les champs SQL_DESC_COUNT dans l’APD et IPD sont réglés à 0.  
  
 La valeur dans SQL_DESC_COUNT peut être définie explicitement par une application en appelant **SQLSetDescField**. Si la valeur de SQL_DESC_COUNT est explicitement diminuée, tous les enregistrements dont le nombre est supérieur à la nouvelle valeur dans SQL_DESC_COUNT sont effectivement supprimés. Si la valeur dans SQL_DESC_COUNT est explicitement réglée à 0 et que le champ est dans une ARD, tous les tampons de données, à l’exception d’une colonne de signet lié, sont publiés.  
  
 Le nombre d’enregistrements dans ce domaine d’un ARD n’inclut pas une colonne de signets reliée. La seule façon de délier une colonne de signets est de définir le champ SQL_DESC_DATA_PTR à un pointeur nul.  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [Déscripteurs de mise en œuvre]**  
 Dans un IRD, ce \* champ d’en-tête SQLULEN indique un tampon contenant le nombre de rangées récupérées après un appel à **SQLFetch** ou **SQLFetchScroll**, ou le nombre de rangées touchées dans une opération en vrac effectuée par un appel à **SQLBulkOperations** ou **SQLSetPos**, y compris les lignes d’erreur.  
  
 Dans un IPD, ce champ d’en-tête SQLUINTEGER - indique un tampon contenant le nombre d’ensembles de paramètres qui ont été traités, y compris les ensembles d’erreurs. Aucun numéro ne sera retourné s’il s’agit d’un pointeur nul.  
  
 SQL_DESC_ROWS_PROCESSED_PTR n’est valable qu’après SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO a été retourné après un appel à **SQLFetch** ou **SQLFetchScroll** (pour un champ IRD) ou **SQLExecute**, **SQLExecDirect**, ou **SQLParamData** (pour un champ IPD). Si l’appel qui remplit le tampon pointé par ce champ ne renvoie pas SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tampon n’est pas défini, à moins qu’il ne retourne SQL_NO_DATA, auquel cas la valeur du tampon est fixée à 0.  
  
 Ce champ dans l’ARD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_ROWS_FETCHED_PTR. Ce champ dans l’APD peut également être défini en appelant **SQLSetStmtAttr** avec l’attribut SQL_ATTR_PARAMS_PROCESSED_PTR.  
  
 Le tampon indiqué par ce champ est attribué par l’application. Il s’agit d’un tampon de sortie différé qui est fixé par le conducteur. Il est réglé à un pointeur nul par défaut.  
  
## <a name="record-fields"></a>Champs d’enregistrement  
 Chaque descripteur contient un ou plusieurs enregistrements composés de champs qui définissent soit les données de colonne ou les paramètres dynamiques, selon le type de descripteur. Chaque enregistrement est une définition complète d’une seule colonne ou paramètre.  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [IRD]**  
 Ce champ d’enregistrement SQLINTEGER ne contient SQL_TRUE si la colonne est une colonne d’incrémentation automatique, ou SQL_FALSE si la colonne n’est pas une colonne d’incrémentation automatique. Ce champ est lu uniquement, mais la colonne sous-jacente d’incrémentation automatique n’est pas nécessairement lue seulement.  
  
 **SQL_DESC_BASE_COLUMN_NAME [IRD]**  
 Ce champ d’enregistrement SQLCHAR- situé uniquement en lecture contient le nom de colonne de base de la colonne d’ensemble de résultats. Si un nom de colonne de base n’existe pas (comme dans le cas des colonnes qui sont des expressions), cette variable contient une chaîne vide.  
  
 **SQL_DESC_BASE_TABLE_NAME [IRD]**  
 Ce champ d’enregistrement SQLCHAR- situé uniquement en lecture contient le nom de table de base de la colonne d’ensemble de résultats. Si un nom de table de base ne peut pas être défini ou n’est pas applicable, cette variable contient une chaîne vide.  
  
 **SQL_DESC_CASE_SENSITIVE [Déscripteurs de mise en œuvre]**  
 Ce champ d’enregistrement SQLINTEGER ne contient SQL_TRUE si la colonne ou le paramètre est traité comme sensible aux cas pour les collations et les comparaisons, ou SQL_FALSE si la colonne n’est pas traitée comme sensible aux cas pour les collations et les comparaisons ou si c’est une colonne non-caracteur.  
  
 **SQL_DESC_CATALOG_NAME [IRD]**  
 Ce champ d’enregistrement SQLCHAR- situé uniquement en lecture contient le catalogue de la table de base qui contient la colonne. La valeur de retour dépend du conducteur si la colonne est une expression ou si la colonne fait partie d’une vue. Si la source de données ne prend pas en charge les catalogues ou si le catalogue ne peut pas être déterminé, cette variable contient une chaîne vide.  
  
 **SQL_DESC_CONCISE_TYPE [Tous]**  
 Ce champ d’en-tête SQLSMALLINT spécifie le type de données concis pour tous les types de données, y compris les types de dates et de données d’intervalle.  
  
 Les valeurs dans les domaines de la SQL_DESC_CONCISE_TYPE, de la SQL_DESC_TYPE et de la SQL_DESC_DATETIME_INTERVAL_CODE sont interdépendantes. Chaque fois qu’un des champs est réglé, l’autre doit également être défini. SQL_DESC_CONCISE_TYPE peuvent être réglés par un appel à **SQLBindCol** ou **SQLBindParameter**, ou **SQLSetDescField**. SQL_DESC_TYPE peuvent être réglés par un appel à **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Si SQL_DESC_CONCISE_TYPE est réglée à un type de données concis autre qu’un type de données d’intervalle ou de date, le champ SQL_DESC_TYPE est réglé à la même valeur et le champ SQL_DESC_DATETIME_INTERVAL_CODE est réglé à 0.  
  
 Si SQL_DESC_CONCISE_TYPE est réglée au type de date ou de données d’intervalle concis, le champ SQL_DESC_TYPE est réglé sur le type verbeux correspondant (SQL_DATETIME ou SQL_INTERVAL) et le champ SQL_DESC_DATETIME_INTERVAL_CODE est réglé sur le sous-code approprié.  
  
 **SQL_DESC_DATA_PTR [Descripteurs d’application et DPI]**  
 Ce champ d’enregistrement SQLPOINTER indique une variable qui contiendra la valeur de paramètre (pour les AD) ou la valeur de la colonne (pour les D AR). Ce champ est un *champ différé*. Il n’est pas utilisé au moment où il est défini, mais est utilisé ultérieurement par le conducteur pour récupérer des données.  
  
 La colonne spécifiée par le champ SQL_DESC_DATA_PTR de l’ARD n’est pas liée si l’argument *TargetValuePtr* dans un appel à **SQLBindCol** est un pointeur nul ou si le champ SQL_DESC_DATA_PTR dans l’ARD est fixé par un appel à **SQLSetDescField** ou **SQLSetDescRec** à un pointeur nul. D’autres champs ne sont pas affectés si le champ SQL_DESC_DATA_PTR est réglé à un pointeur nul.  
  
 Si l’appel à **SQLFetch** ou **SQLFetchScroll** qui remplit le tampon pointé par ce champ n’est pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tampon n’est pas défini.  
  
 Chaque fois que le champ SQL_DESC_DATA_PTR d’une DPA, d’un ARD ou d’une DPI est défini, le conducteur vérifie que la valeur dans le champ SQL_DESC_TYPE contient l’un des types de données C D’ODBC valides ou un type de données spécifique au conducteur, et que tous les autres champs affectant les types de données sont cohérents. L’utilisation d’une DPI est la seule utilisation du champ SQL_DESC_DATA_PTR d’un DPI. Plus précisément, si une application définit le champ SQL_DESC_DATA_PTR d’un IPD et appelle plus tard **SQLGetDescField** sur ce champ, il n’est pas nécessairement retourné la valeur qu’il avait fixé. Pour plus d’informations, voir "Vérifications de cohérence" dans [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_CODE [Tous]**  
 Ce champ d’enregistrement SQLSMALLINT contient le sous-code pour le type de données de date ou d’intervalle spécifique lorsque le champ SQL_DESC_TYPE est SQL_DATETIME ou SQL_INTERVAL. Cela est vrai pour les types de données SQL et C. Le code se compose du nom de type de données avec "CODE" substitué à "TYPE" ou "C_TYPE" (pour les types de date), ou "CODE" substitué par "INTERVAL" ou "C_INTERVAL" (pour les types d’intervalle).  
  
 Si SQL_DESC_TYPE et SQL_DESC_CONCISE_TYPE dans un descripteur d’application sont configurés pour SQL_C_DEFAULT et que le descripteur n’est pas associé à une poignée de déclaration, le contenu de SQL_DESC_DATETIME_INTERVAL_CODE n’est pas défini.  
  
 Ce champ peut être défini pour les types de données datetime énumérés dans le tableau suivant.  
  
|Types d’heure de date|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP/ SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 Ce champ peut être défini pour les types de données d’intervalle répertoriés dans le tableau suivant.  
  
|Type d'intervalle|DATETIME_INTERVAL_CODE|  
|-------------------|------------------------------|  
|SQL_INTERVAL_DAY/SQL_C_INTERVAL_DAY|SQL_CODE_DAY|  
|SQL_INTERVAL_DAY_TO_HOUR/SQL_C_INTERVAL_DAY_TO_HOUR|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE/SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND/SQL_C_INTERVAL_DAY_TO_SECOND|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR/SQL_C_INTERVAL_HOUR|SQL_CODE_HOUR|  
|SQL_INTERVAL_HOUR_TO_MINUTE/ SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND/SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE/SQL_C_INTERVAL_MINUTE|SQL_CODE_MINUTE|  
|SQL_INTERVAL_MINUTE_TO_SECOND/SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_CODE_MINUTE_TO_SECOND|  
|SQL_INTERVAL_MONTH/ SQL_C_INTERVAL_MONTH|SQL_CODE_MONTH|  
|SQL_INTERVAL_SECOND/ SQL_C_INTERVAL_SECOND|SQL_CODE_SECOND|  
|SQL_INTERVAL_YEAR/SQL_C_INTERVAL_YEAR|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH/SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_CODE_YEAR_TO_MONTH|  
  
 Pour plus d’informations sur les intervalles de données et ce champ, voir [Identifiants de type de données et descripteurs](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_PRECISION [Tous]**  
 Ce champ d’enregistrement SQLINTEGER contient la précision de tête d’intervalle si le champ SQL_DESC_TYPE est SQL_INTERVAL. Lorsque le champ SQL_DESC_DATETIME_INTERVAL_CODE est réglé sur un type de données d’intervalle, ce champ est réglé à l’intervalle par défaut de précision de direction.  
  
 **SQL_DESC_DISPLAY_SIZE [IRD]**  
 Ce champ d’enregistrement SQLINTEGER en lecture seulement contient le nombre maximum de caractères requis pour afficher les données de la colonne.  
  
 **SQL_DESC_FIXED_PREC_SCALE [Déscripteurs de mise en œuvre]**  
 Ce champ d’enregistrement SQLSMALLINT est réglé pour SQL_TRUE si la colonne est une colonne numérique exacte et a une précision fixe et une échelle non zéro, ou pour SQL_FALSE si la colonne n’est pas une colonne numérique exacte avec une précision et une échelle fixes.  
  
 **SQL_DESC_INDICATOR_PTR [Descripteurs d’application]**  
 Dans les DR, ce champ de disque SQLLEN - indique la variable d’indicateur. Cette variable contient SQL_NULL_DATA si la valeur de la colonne est un NULL. Pour les ADA, la variable d’indicateur est définie pour SQL_NULL_DATA pour spécifier les arguments dynamiques NULL. Sinon, la variable est nulle (sauf si les valeurs dans SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR sont le même pointeur).  
  
 Si le champ SQL_DESC_INDICATOR_PTR dans une ARD est un pointeur nul, le conducteur est empêché de retourner des informations sur si la colonne est NULL ou non. Si la colonne est NULL et SQL_DESC_INDICATOR_PTR est un pointeur nul, SQLSTATE 22002 (variable d’indicateur requise mais non fournie) est retourné lorsque le conducteur tente de remplir le tampon après un appel à **SQLFetch** ou **SQLFetchScroll**. Si l’appel à **SQLFetch** ou **SQLFetchScroll** n’est pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tampon n’est pas défini.  
  
 Le champ SQL_DESC_INDICATOR_PTR détermine si le champ pointé par SQL_DESC_OCTET_LENGTH_PTR est fixé. Si la valeur de données d’une colonne est NULL, le pilote définit la variable de l’indicateur pour SQL_NULL_DATA. Le champ pointé par SQL_DESC_OCTET_LENGTH_PTR n’est alors pas défini. Si une valeur NULL n’est pas rencontrée pendant l’aller chercher, le tampon indiqué par SQL_DESC_INDICATOR_PTR est réglé à zéro et le tampon indiqué par SQL_DESC_OCTET_LENGTH_PTR est réglé à la longueur des données.  
  
 Si le champ SQL_DESC_INDICATOR_PTR dans une DPA est un pointeur nul, l’application ne peut pas utiliser ce dossier descripteur pour spécifier les arguments NULL.  
  
 Ce champ est un *champ différé*: Il n’est pas utilisé au moment où il est réglé mais est utilisé ultérieurement par le conducteur pour indiquer l’annulation (pour les DR) ou pour déterminer l’annulation (pour les APA).  
  
 **SQL_DESC_LABEL [IRD]**  
 Ce champ d’enregistrement SQLCHAR et en lecture seulement contient l’étiquette de colonne ou le titre. Si la colonne n’a pas d’étiquette, cette variable contient le nom de colonne. Si la colonne n’est pas nommée et non étiquetée, cette variable contient une chaîne vide.  
  
 **SQL_DESC_LENGTH [Tous]**  
 Ce champ d’enregistrement SQLULEN est soit la longueur maximale ou réelle d’une chaîne de caractères en caractères ou un type de données binaires dans les octets. Il s’agit de la longueur maximale pour un type de données à durée fixe, ou de la longueur réelle d’un type de données à durée variable. Sa valeur exclut toujours le caractère de terminaison nulle qui met fin à la chaîne de caractère. Pour les valeurs dont le type est SQL_TYPE_DATE, SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP ou l’un des types de données d’intervalle SQL, ce champ a la longueur des caractères dans la représentation de la chaîne de caractère de la date ou la valeur d’intervalle.  
  
 La valeur dans ce domaine peut être différente de la valeur pour la «longueur» telle que définie dans ODBC 2 *.x*. Pour plus d’informations, voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_LITERAL_PREFIX [IRD]**  
 Ce champ d’enregistrement SQLCHAR - situé uniquement en lecture contient le caractère ou les caractères que le conducteur reconnaît comme un préfixe pour un type de données littéral. Cette variable contient une chaîne vide pour un type de données pour lequel un préfixe littéral n’est pas applicable.  
  
 **SQL_DESC_LITERAL_SUFFIX [IRD]**  
 Ce champ d’enregistrement SQLCHAR - situé uniquement en lecture contient le caractère ou les caractères que le conducteur reconnaît comme un suffixe pour un littéal de ce type de données. Cette variable contient une chaîne vide pour un type de données pour lequel un suffixe littéral n’est pas applicable.  
  
 **SQL_DESC_LOCAL_TYPE_NAME [Déscripteurs de mise en œuvre]**  
 Ce champ d’enregistrement SQLCHAR - situé uniquement en lecture contient un nom localisé (langue autochtone) pour le type de données qui peut être différent du nom régulier du type de données. S’il n’y a pas de nom localisé, une corde vide est retournée. Ce champ est uniquement à des fins d’affichage.  
  
 **SQL_DESC_NAME [déscripteurs de mise en œuvre]**  
 Ce champ d’enregistrement SQLCHAR dans un descripteur d’affilée contient le pseudonyme de colonne, si elle s’applique. Si le pseudonyme de colonne ne s’applique pas, le nom de la colonne est retourné. Dans les deux cas, le conducteur met le champ SQL_DESC_UNNAMED à SQL_NAMED quand il définit le champ SQL_DESC_NAME. S’il n’y a pas de nom de colonne ou d’alias de colonne, le conducteur renvoie une chaîne vide dans le champ SQL_DESC_NAME et met le champ SQL_DESC_UNNAMED à SQL_UNNAMED.  
  
 Une application peut définir le champ SQL_DESC_NAME d’un IPD à un nom de paramètre ou un alias pour spécifier les paramètres de procédure stockés par leur nom. (Pour plus d’informations, voir [Paramètres contraignants par nom (Paramètres nommés)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md).) Le SQL_DESC_NAME domaine d’un IRD est un domaine de lecture seulement; SQLSTATE HY091 (identificateur de champ descripteur invalide) sera retourné si une demande tente de la définir.  
  
 Dans les DPI, ce champ n’est pas défini si le conducteur ne prend pas en charge les paramètres nommés. Si le conducteur prend en charge les paramètres désignés et est capable de décrire les paramètres, le nom du paramètre est retourné dans ce domaine.  
  
 **SQL_DESC_NULLABLE [Déscripteurs de mise en œuvre]**  
 Dans les DIV, ce champ d’enregistrement SQLSMALLINT uniquement lu est SQL_NULLABLE si la colonne peut avoir des valeurs NULL, SQL_NO_NULLS si la colonne n’a pas de valeurs NULL, ou SQL_NULLABLE_UNKNOWN si on ne sait pas si la colonne accepte les valeurs NULL. Ce champ se rapporte à la colonne de l’ensemble de résultats, et non à la colonne de base.  
  
 Dans les DPI, ce champ est toujours configuré pour SQL_NULLABLE parce que les paramètres dynamiques sont toujours in nullables et ne peuvent pas être définis par une application.  
  
 **SQL_DESC_NUM_PREC_RADIX [Tous]**  
 Ce champ SQLINTEGER contient une valeur de 2 si le type de données dans le champ SQL_DESC_TYPE est un type de données numériques approximative, parce que le champ SQL_DESC_PRECISION contient le nombre de bits. Ce champ contient une valeur de 10 si le type de données dans le champ SQL_DESC_TYPE est un type de données numériques exacte, parce que le champ SQL_DESC_PRECISION contient le nombre de chiffres décimaux. Ce champ est réglé à 0 pour tous les types de données non numériques.  
  
 **SQL_DESC_OCTET_LENGTH [Tous]**  
 Ce champ d’enregistrement SQLLEN contient la longueur, dans les octets, d’une chaîne de caractères ou d’un type de données binaire. Pour les types de caractère fixe ou binaire, c’est la longueur réelle des octets. Pour les types de caractères à longueur variable ou binaires, c’est la longueur maximale des octets. Cette valeur exclut toujours l’espace pour le caractère de résiliation nulle pour les descripteurs de mise en œuvre et comprend toujours l’espace pour le caractère de résiliation nulle pour les descripteurs d’application. Pour les données d’application, ce champ contient la taille du tampon. Pour les APA, ce champ n’est défini que pour les paramètres de sortie ou d’entrée/sortie.  
  
 **SQL_DESC_OCTET_LENGTH_PTR [Descripteurs d’application]**  
 Ce champ d’enregistrement SQLLEN - indique une variable qui contiendra la longueur totale des octets d’un argument dynamique (pour les descripteurs de paramètres) ou d’une valeur de colonne liée (pour les descripteurs de ligne).  
  
 Pour une APD, cette valeur est ignorée pour tous les arguments, sauf la chaîne de caractère et binaire; si ce champ indique SQL_NTS, l’argument dynamique doit être annulé. Pour indiquer qu’un paramètre lié sera un paramètre de données à l’exécution, une application définit ce champ dans l’enregistrement approprié de l’APD à une variable qui, au moment de l’exécution, contiendra la valeur SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC. S’il y a plus d’un de ces champs, SQL_DESC_DATA_PTR peut être définie à une valeur permettant d’identifier uniquement le paramètre pour aider l’application à déterminer quel paramètre est demandé.  
  
 Si le champ OCTET_LENGTH_PTR d’un ARD est un pointeur nul, le conducteur ne renvoie pas les informations de longueur pour la colonne. Si le champ SQL_DESC_OCTET_LENGTH_PTR d’un APD est un pointeur nul, le pilote suppose que les chaînes de caractères et les valeurs binaires sont non terminées. (Les valeurs binaires ne doivent pas être annulées, mais devraient être donnés une longueur pour éviter la troncation.)  
  
 Si l’appel à **SQLFetch** ou **SQLFetchScroll** qui remplit le tampon pointé par ce champ n’est pas retourné SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, le contenu du tampon n’est pas défini. Ce champ est un *champ différé*. Il n’est pas utilisé au moment où il est réglé, mais est utilisé ultérieurement par le conducteur pour déterminer ou indiquer la longueur de l’octet des données.  
  
 **SQL_DESC_PARAMETER_TYPE [IPDs]**  
 Ce champ d’enregistrement SQLSMALLINT est prêt à SQL_PARAM_INPUT pour un paramètre d’entrée, SQL_PARAM_INPUT_OUTPUT pour un paramètre d’entrée/sortie, SQL_PARAM_OUTPUT pour un paramètre de sortie, SQL_PARAM_INPUT_OUTPUT_STREAM pour un paramètre d’entrée/sortie écouté, ou SQL_PARAM_OUTPUT_STREAM pour un paramètre de sortie simplifié. Il est configuré à SQL_PARAM_INPUT par défaut.  
  
 Pour une DPI, le champ est configuré pour SQL_PARAM_INPUT par défaut si l’IPD n’est pas automatiquement peuplé par le conducteur (l’attribut SQL_ATTR_ENABLE_AUTO_IPD déclaration est SQL_FALSE). Une application doit définir ce champ dans l’IPD pour les paramètres qui ne sont pas des paramètres d’entrée.  
  
 **SQL_DESC_PRECISION [Tous]**  
 Ce champ d’enregistrement SQLSMALLINT contient le nombre de chiffres pour un type numérique exact, le nombre de bits dans la mantissa (précision binaire) pour un type numérique approximatif, ou le nombre de chiffres dans le composant fractionnaire secondes pour le SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP ou SQL_INTERVAL_SECOND type de données. Ce champ n’est pas défini pour tous les autres types de données.  
  
 La valeur dans ce domaine peut être différente de la valeur pour la «précision» telle que définie dans ODBC 2 *.x*. Pour plus d’informations, voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_ROWVER [Déscripteurs de mise en œuvre]**  
 Ce champ SQLSMALLINTrecord indique si une colonne est automatiquement modifiée par le DBMS lorsqu’une ligne est mise à jour (par exemple, une colonne du type " timestamp" dans SQL Server). La valeur de ce champ d’enregistrement est réglée pour SQL_TRUE si la colonne est une colonne de version de ligne, et pour SQL_FALSE autrement. Cet attribut de colonne est semblable à appeler **SQLSpecialColumns** avec IdentifierType de SQL_ROWVER pour déterminer si une colonne est automatiquement mise à jour.  
  
 **SQL_DESC_SCALE [Tous]**  
 Ce champ d’enregistrement SQLSMALLINT contient l’échelle définie pour les types décimaux et numériques. Le champ n’est pas défini pour tous les autres types de données.  
  
 La valeur dans ce domaine peut être différente de la valeur pour "échelle" telle que définie dans ODBC 2 *.x*. Pour plus d’informations, voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_SCHEMA_NAME [IRD]**  
 Ce champ d’enregistrement SQLCHAR- situé uniquement en lecture contient le nom schéma de la table de base qui contient la colonne. La valeur de retour dépend du conducteur si la colonne est une expression ou si la colonne fait partie d’une vue. Si la source de données ne prend pas en charge les schémas ou si le nom du schéma ne peut pas être déterminé, cette variable contient une chaîne vide.  
  
 **SQL_DESC_SEARCHABLE [IRD]**  
 Ce champ de disques SQLSMALLINT uniquement est fixé à l’une des valeurs suivantes :  
  
-   SQL_PRED_NONE si la colonne ne peut pas être utilisée dans une clause **WHERE.** (C’est la même chose que la valeur SQL_UNSEARCHABLE dans ODBC 2 *.x*.)  
  
-   SQL_PRED_CHAR si la colonne peut être utilisée dans une clause **WHERE,** mais seulement avec le **predicate LIKE.** (C’est la même chose que la valeur SQL_LIKE_ONLY dans ODBC 2 *.x*.)  
  
-   SQL_PRED_BASIC si la colonne peut être utilisée dans une clause **WHERE** avec tous les opérateurs de comparaison à l’exception **de LIKE**. (C’est la même chose que la valeur SQL_EXCEPT_LIKE dans ODBC 2 *.x*.)  
  
-   SQL_PRED_SEARCHABLE si la colonne peut être utilisée dans une clause **WHERE** avec n’importe quel opérateur de comparaison.  
  
 **SQL_DESC_TABLE_NAME [IRD]**  
 Ce champ d’enregistrement SQLCHAR- situé uniquement en lecture contient le nom de la table de base qui contient cette colonne. La valeur de retour dépend du conducteur si la colonne est une expression ou si la colonne fait partie d’une vue.  
  
 **SQL_DESC_TYPE [Tous]**  
 Ce champ d’enregistrement SQLSMALLINT spécifie le type concis de données SQL ou C pour tous les types de données, à l’exception des types de données de date et d’intervalle. Pour les types de données de date et d’intervalle, ce champ spécifie le type de données verbeux, qui est SQL_DATETIME ou SQL_INTERVAL.  
  
 Chaque fois que ce champ contient SQL_DATETIME ou SQL_INTERVAL, le champ SQL_DESC_DATETIME_INTERVAL_CODE doit contenir le sous-code approprié pour le type concis. Pour les types de données date, SQL_DESC_TYPE contient SQL_DATETIME, et le champ SQL_DESC_DATETIME_INTERVAL_CODE contient un sous-code pour le type de données de date spécifique. Pour les types de données d’intervalle, SQL_DESC_TYPE contient SQL_INTERVAL et le champ SQL_DESC_DATETIME_INTERVAL_CODE contient un sous-code pour le type spécifique de données d’intervalle.  
  
 Les valeurs dans les domaines de la SQL_DESC_TYPE et de la SQL_DESC_CONCISE_TYPE sont interdépendantes. Chaque fois qu’un des champs est réglé, l’autre doit également être défini. SQL_DESC_TYPE peuvent être réglés par un appel à **SQLSetDescField** ou **SQLSetDescRec**. SQL_DESC_CONCISE_TYPE peuvent être réglés par un appel à **SQLBindCol** ou **SQLBindParameter**, ou **SQLSetDescField**.  
  
 Si SQL_DESC_TYPE est réglée à un type de données concis autre qu’un type de données d’intervalle ou de date, le champ SQL_DESC_CONCISE_TYPE est réglé à la même valeur et le champ SQL_DESC_DATETIME_INTERVAL_CODE est réglé à 0.  
  
 Si SQL_DESC_TYPE est réglée au type de date verbeuse ou de données d’intervalle (SQL_DATETIME ou SQL_INTERVAL) et que le champ SQL_DESC_DATETIME_INTERVAL_CODE est réglé sur le sous-code approprié, le champ type SQL_DESC_CONCISE est réglé sur le type concis correspondant. Essayer de fixer SQL_DESC_TYPE à l’un des types de date ou d’intervalle concis retournera SQLSTATE HY021 (informations descripteur incohérentes).  
  
 Lorsque le champ SQL_DESC_TYPE est réglé par un appel à **SQLBindCol**, **SQLBindParameter**, ou **SQLSetDescField**, les champs suivants sont réglés sur les valeurs par défaut suivantes, comme indiqué dans le tableau ci-dessous. Les valeurs des champs restants d’un même enregistrement ne sont pas définies.  
  
|Valeur de SQL_DESC_TYPE|D’autres champs implicitement définis|  
|------------------------------|---------------------------------|  
|SQL_CHAR, SQL_VARCHAR, SQL_C_CHAR, SQL_C_VARCHAR|SQL_DESC_LENGTH est réglé 1. SQL_DESC_PRECISION est réglé à 0.|  
|SQL_DATETIME|Lorsque SQL_DESC_DATETIME_INTERVAL_CODE est réglée pour SQL_CODE_DATE ou SQL_CODE_TIME, SQL_DESC_PRECISION est réglée à 0. Lorsqu’il est réglé pour SQL_DESC_TIMESTAMP, SQL_DESC_PRECISION est réglé à 6.|  
|SQL_DECIMAL, SQL_NUMERIC, SQL_C_NUMERIC|SQL_DESC_SCALE est réglé 0. SQL_DESC_PRECISION est définie à la précision définie par la mise en œuvre pour le type de données respectif.<br /><br /> Voir [SQL à C: Numeric](../../../odbc/reference/appendixes/sql-to-c-numeric.md) pour plus d’informations sur la façon de lier manuellement une valeur SQL_C_NUMERIC.|  
|SQL_FLOAT, SQL_C_FLOAT|SQL_DESC_PRECISION est définie à la précision par défaut définie par la mise en œuvre pour SQL_FLOAT.|  
|SQL_INTERVAL|Lorsque SQL_DESC_DATETIME_INTERVAL_CODE est réglée à un type de données d’intervalle, SQL_DESC_DATETIME_INTERVAL_PRECISION est réglée à 2 (l’intervalle par défaut menant la précision). Lorsque l’intervalle a un composant de secondes, SQL_DESC_PRECISION est réglée à 6 (la précision des secondes d’intervalle par défaut).|  
  
 Lorsqu’une application appelle **SQLSetDescField** pour définir les champs d’un descripteur plutôt que d’appeler **SQLSetDescRec**, l’application doit d’abord déclarer le type de données. Lorsque c’est le cas, les autres champs indiqués dans le tableau précédent sont implicitement définis. Si l’une des valeurs implicitement définies est inacceptable, l’application peut alors appeler **SQLSetDescField** ou **SQLSetDescRec** pour définir la valeur inacceptable explicitement.  
  
 **SQL_DESC_TYPE_NAME [déscripteurs de mise en œuvre]**  
 Ce champ d’enregistrement SQLCHAR ne contient que le nom de type source de données (par exemple, "CHAR", "VARCHAR", et ainsi de suite). Si le nom du type de données est inconnu, cette variable contient une chaîne vide.  
  
 **SQL_DESC_UNNAMED [Déscripteurs de mise en œuvre]**  
 Ce champ de disques SQLSMALLINT dans un descripteur d’affilée est fixé par le conducteur à SQL_NAMED ou SQL_UNNAMED quand il définit le champ SQL_DESC_NAME. Si le champ SQL_DESC_NAME contient un pseudonyme de colonne ou si le pseudonyme de colonne ne s’applique pas, le conducteur définit le champ SQL_DESC_UNNAMED pour SQL_NAMED. Si une application définit le champ SQL_DESC_NAME d’un IPD sur un nom de paramètre ou un pseudonyme, le pilote définit le champ SQL_DESC_UNNAMED de l’IPD à SQL_NAMED. S’il n’y a pas de nom de colonne ou d’alias de colonne, le pilote définit le champ SQL_DESC_UNNAMED pour SQL_UNNAMED.  
  
 Une application peut définir le champ SQL_DESC_UNNAMED d’un IPD à SQL_UNNAMED. Un conducteur renvoie SQLSTATE HY091 (identificateur de champ descripteur invalide) si une application tente de définir le champ SQL_DESC_UNNAMED d’un IPD à SQL_NAMED. Le SQL_DESC_UNNAMED domaine d’un IRD est lu uniquement; SQLSTATE HY091 (identificateur de champ descripteur invalide) sera retourné si une demande tente de la définir.  
  
 **SQL_DESC_UNSIGNED [Déscripteurs de mise en œuvre]**  
 Ce champ d’enregistrement SQLSMALLINT ne fait l’SQL_TRUE si le type de colonne n’est pas signé ou non numérique, ou SQL_FALSE si le type de colonne est signé.  
  
 **SQL_DESC_UPDATABLE [IRD]**  
 Ce champ de disques SQLSMALLINT uniquement est fixé à l’une des valeurs suivantes :  
  
-   SQL_ATTR_READ_ONLY si la colonne de l’ensemble de résultats est lue uniquement.  
  
-   SQL_ATTR_WRITE si la colonne de l’ensemble de résultats est lue-écriture.  
  
-   SQL_ATTR_READWRITE_UNKNOWN s’il n’est pas connu si la colonne de jeu de résultat est updatable ou non.  
  
 SQL_DESC_UPDATABLE décrit la redatibilité de la colonne dans l’ensemble de résultats, et non la colonne dans le tableau de base. La facilité d’updatabilité de la colonne dans le tableau de base sur lequel cette colonne de jeu de résultat est basée peut être différente de la valeur dans ce domaine. La question de savoir si une colonne est updatable peut être basée sur le type de données, les privilèges des utilisateurs et la définition du résultat lui-même. S’il n’est pas clair si une colonne est updatable, SQL_ATTR_READWRITE_UNKNOWN doit être retourné.  
  
## <a name="consistency-checks"></a>Vérifications de cohérence  
 Une vérification de cohérence est effectuée automatiquement par le conducteur chaque fois qu’une application passe dans une valeur pour le champ SQL_DESC_DATA_PTR de l’ARD, APD, ou IPD. Si l’un des champs est incompatible avec d’autres champs, **SQLSetDescField** retournera SQLSTATE HY021 (information descripteur incohérente). Pour plus d’informations, voir "Cohérence Check" dans [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Reliser une colonne|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Lier un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Obtenir un champ descripteur|[Fonction SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Obtenir plusieurs champs descripteur|[SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Réglage de plusieurs champs descripteur|[SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Informations de référence sur l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)
