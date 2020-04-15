---
title: Fonction SQLColAttribute (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c94de3dfc7036277f8be56c401326cdab07a9606
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301289"
---
# <a name="sqlcolattribute-function"></a>Fonction SQLColAttribute
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLColAttribute renvoie** des informations descripteur pour une colonne dans un ensemble de résultats. Les informations descripteur sont retournées comme une chaîne de caractère, une valeur dépendante du descripteur ou une valeur d’intégrateur.  
  
> [!NOTE]  
>  Pour plus d’informations sur ce que le Driver Manager cartographie cette fonction à quand un ODBC 3. *x* application fonctionne avec un ODBC 2. *x* pilote, voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLColAttribute (  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ColumnNumber,  
      SQLUSMALLINT    FieldIdentifier,  
      SQLPOINTER      CharacterAttributePtr,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLLEN *        NumericAttributePtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *ColumnNumber*  
 [Entrée] Le nombre d’enregistrements dans l’IRD à partir duquel la valeur du champ doit être récupérée. Cet argument correspond au nombre de données de résultat de colonne, commandées séquentiellement dans l’ordre croissant de colonne, à partir de 1. Les colonnes peuvent être décrites dans n’importe quel ordre.  
  
 La colonne 0 peut être spécifiée dans cet argument, mais toutes les valeurs, sauf SQL_DESC_TYPE et SQL_DESC_OCTET_LENGTH, retourneront des valeurs indéfinies.  
  
 *FieldIdentifier*  
 [Entrée] La poignée descripteur. Cette poignée définit le champ dans l’IRD doit être interrogé (par exemple, SQL_COLUMN_TABLE_NAME).  
  
 *CharacterAttributePtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la valeur dans le champ *FieldIdentifier* de la *colonneNbre* rangée de l’IRD, si le champ est une chaîne de caractère. Sinon, le champ n’est pas utilisé.  
  
 Si *CharacterAttributePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de non-termination pour les données de caractère) disponible pour revenir dans le tampon indiqué par *CharacterAttributePtr*.  
  
 *BufferLength*  
 [Entrée] Si *FieldIdentifier* est un champ défini par ODBC et *characterAttributePtr* pointe vers une \*chaîne de caractères ou un tampon binaire, cet argument devrait être la longueur de *CharacterAttributePtr*. Si *FieldIdentifier* est un champ défini \*par l’ODBC et *que CharacterAttribute*Ptr est un integer, ce champ est ignoré. Si le * \*CharacterAttributePtr* est une chaîne Unicode (lorsqu’il appelle **SQLColAttributeW**), l’argument *BufferLength* doit être un nombre pair. Si *FieldIdentifier* est un champ défini par le conducteur, l’application indique la nature du champ au gestionnaire de conducteur en définissant l’argument *De bufferLength.* *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si *CharacterAttributePtr* est un pointeur à un pointeur, *BufferLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si *CharacterAttributePtr* est un pointeur d’une chaîne de caractères, le *BufferLength* est la longueur du tampon.  
  
-   Si *CharacterAttributePtr* est un pointeur vers un tampon binaire, l’application place le résultat de la SQL_LEN_BINARY_ATTR(*longueur)* macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si *CharacterAttributePtr* est un pointeur sur un type de données à durée fixe, *BufferLength* doit être l’un des éléments suivants : SQL_IS_INTEGER, SQL_IS_UNINTEGER, SQL_SMALLINT ou SQLUSMALLINT.  
  
 *StringLengthPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total d’octets (à l’exclusion du octet de terminaison nulle pour les données de caractère) disponible pour revenir dans *'CharacterAttributePtr*.  
  
 Pour les données de caractère, si le nombre d’octets disponibles pour revenir est \*supérieur ou égal à *BufferLength*, les informations descripteur dans *CharacterAttributePtr* est tronquée à *BufferLength* moins la longueur d’un caractère de non-termination et est annulée par le conducteur.  
  
 Pour tous les autres types de données, la valeur de *BufferLength* est ignorée et le conducteur suppose que la taille de *' CharacterAttributePtr* est de 32 bits.  
  
 *NumericAttributePtr*  
 [Sortie] Pointeur vers un tampon d’intégrateur dans lequel retourner la valeur dans le champ *d’identification* de champ de la rangée *De l’IRD,* si le champ est un type de descripteur numérique, tel que SQL_DESC_COLUMN_LENGTH. Sinon, le champ n’est pas utilisé. Veuillez noter que certains conducteurs ne peuvent écrire que le moins bas 32 bits ou 16 bits d’un tampon et laisser le bit de l’ordre supérieur inchangé. Par conséquent, les applications devraient initialiser la valeur à 0 avant d’appeler cette fonction.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLColAttribute** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLColAttribute** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *CharacterAttributePtr* n’était pas assez grand pour retourner la valeur de la chaîne entière, de sorte que la valeur de la chaîne a été tronquée. La longueur de la valeur de la chaîne fausse est retournée dans*stringLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07005|Déclaration préparée et non *une spécification curseur*|La déclaration associée à la *DéclarationHandle* n’a pas retourné un ensemble de résultats et *FieldIdentifier* n’a pas été SQL_DESC_COUNT. Il n’y avait pas de colonnes à décrire.|  
|07009|Indice descripteur invalide|(DM) La valeur spécifiée pour *ColumnNumber* était égale à 0, et l’attribut SQL_ATTR_USE_BOOKMARKS énoncé était SQL_UB_OFF.<br /><br /> La valeur spécifiée pour l’argument *ColumnNumber* était supérieure au nombre de colonnes dans l’ensemble de résultats.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagField** de la structure de données diagnostiques décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle*. Puis la fonction a été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction aynchrone était encore en cours d’exécution lorsque SQLColAttribute a été appelé.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) La fonction a été appelée avant d’appeler **SQLPrepare**, **SQLExecDirect**, ou une fonction de catalogue pour le *StatementHandle*.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) * \*CharacterAttributePtr* est une chaîne de caractères, et *BufferLength* était inférieur à 0, mais pas égal à SQL_NTS.|  
|HY091 HY091|Identifiant de champ descripteur invalide|La valeur spécifiée pour l’argument *FieldIdentifier* n’était pas l’une des valeurs définies et n’était pas une valeur définie par la mise en œuvre.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Pilote non capable|La valeur spécifiée pour l’argument *FieldIdentifier* n’a pas été étayée par le conducteur.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
 Lorsqu’il est appelé après **SQLPrepare** et avant **SQLExecute**, **SQLColAttribute** peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLPrepare** ou **SQLExecute**, selon le moment où la source de données évalue la déclaration SQL associée à la *DéclarationHandle*.  
  
 Pour des raisons de rendement, une demande ne doit pas appeler **SQLColAttribute** avant d’exécuter une déclaration.  
  
## <a name="comments"></a>Commentaires  
 Pour plus d’informations sur la façon dont les applications utilisent les informations retournées par **SQLColAttribute**, voir [Métadonnées De résultat .](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
 **SQLColAttribute renvoie** \*des informations soit dans \* *NumericAttributePtr* ou dans *CharacterAttributePtr*. L’information d’integer est retournée dans \* *NumericAttributePtr* comme valeur SQLLEN ; tous les autres formats \*d’information sont retournés dans *CharacterAttributePtr*. Lorsque l’information \*est retournée dans *NumericAttributePtr*, le conducteur ignore *CharacterAttributePtr*, *BufferLength*, et *StringLengthPtr*. Lorsque l’information \*est retournée dans *CharacterAttributePtr*, le conducteur ignore *NumericAttributePtr*.  
  
 **SQLColAttribute renvoie** les valeurs des champs descripteur de l’IRD. La fonction est appelée avec une poignée de déclaration plutôt qu’une poignée descripteur. Les valeurs retournées par **SQLColAttribute** pour les valeurs *FieldIdentifier* énumérées plus tard dans cette section peuvent également être récupérées en appelant **SQLGetDescField** avec la poignée IRD appropriée.  
  
 Les champs descripteur actuellement définis, la version de l’ODBC dans laquelle ils ont été introduits, et les arguments dans lesquels l’information est retournée pour eux sont montrés plus tard dans cette section; plus de types descripteur peuvent être définis par les conducteurs pour tirer parti de différentes sources de données.  
  
 Un ODBC 3. *x* le conducteur doit retourner une valeur pour chacun des champs descripteur. Si un champ descripteur ne s’applique pas à un conducteur ou \*à une source de données et à moins d’être indiqué autrement, le conducteur retourne 0 dans *StringLengthPtr* ou une chaîne vide dans*le characterAttributePtr*.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 L’ODBC 3. *x* fonction **SQLColAttribute** remplace l’ODBC 2 déprécié. *x* fonction **SQLColAttributes**. Lors de la cartographie **SQLColAttributes** à **SQLColAttribute** (lorsqu’un ODBC 2.* x* application fonctionne avec un ODBC 3. *x* conducteur), ou la cartographie **SQLColAttribute** à **SQLColAttributes** (lorsqu’un ODBC 3.* x* application fonctionne avec un ODBC 2. *x* pilote), le Driver Manager passe soit la valeur de *FieldIdentifier* à travers, il cartographie à une nouvelle valeur, ou retourne une erreur, comme suit:  
  
> [!NOTE]  
>  Le préfixe utilisé dans les valeurs *FieldIdentifier* dans ODBC 3. *x* a été changé par à partir de celui utilisé dans ODBC 2. *x*. Le nouveau préfixe est "SQL_DESC"; l’ancien préfixe était "SQL_COLUMN".  
  
-   Si la **valeur #define** de l’ODBC 2. *x* *FieldIdentifier* est le même que la valeur **#define** de l’ODBC 3. *x* *FieldIdentifier*, la valeur de l’appel de fonction vient de passer.  
  
-   Les **valeurs #define** de l’ODBC 2. *x* *Les SQL_COLUMN_LENGTH,* les SQL_COLUMN_PRECISION et les SQL_COLUMN_SCALE sont différents des valeurs **#define** de l’ODBC 3. *x* *FieldIdentificateurs* SQL_DESC_PRECISION, SQL_DESC_SCALE et SQL_DESC_LENGTH. Un ODBC 2. *x* le conducteur n’a besoin que de soutenir l’ODBC 2. *x* valeurs. Un ODBC 3. *x* pilote doit soutenir à la fois "SQL_COLUMN" et "SQL_DESC" valeurs pour ces trois *FieldIdentifiers*. Ces valeurs sont différentes parce que la précision, l’échelle et la longueur sont définies différemment dans ODBC 3. *x* qu’ils ne l’étaient dans ODBC 2. *x*. Pour plus d’informations, voir [Taille de colonne, Chiffres décimaux, Longueur Octet de transfert, et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
-   Si la **valeur #define** de l’ODBC 2. *x* *FieldIdentifier* est différent de la valeur **#define** de l’ODBC 3. *x* *FieldIdentifier*, comme c’est le cas avec les valeurs COUNT, NOM et NULLABLE, la valeur de l’appel de fonction est cartographiée à la valeur correspondante. Par exemple, SQL_COLUMN_COUNT est cartographiée pour SQL_DESC_COUNT, et SQL_DESC_COUNT est cartographiée pour SQL_COLUMN_COUNT, selon la direction de la cartographie.  
  
-   Si *FieldIdentifier* est une nouvelle valeur dans ODBC 3. *x*, pour lequel il n’y avait pas de valeur correspondante dans ODBC 2. *x*, il ne sera pas cartographié lorsqu’un ODBC 3. *x* application l’utilise dans un appel à **SQLColAttribute** dans un ODBC 2. *x* conducteur, et l’appel retournera SQLSTATE HY091 (identificateur de champ descripteur invalide).  
  
 Le tableau suivant énumère les types descripteur retournés par **SQLColAttribute**. Le type pour les valeurs *NumericAttributePtr* est **SQLLEN \* **.  
  
|*FieldIdentifier*|Information<br /><br /> retourné dans|Description|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE si la colonne est une colonne d’augmentation automatique.<br /><br /> SQL_FALSE si la colonne n’est pas une colonne d’augmentation automatique ou n’est pas numérique.<br /><br /> Ce champ est valable uniquement pour les colonnes de type de données numériques. Une application peut insérer des valeurs dans une rangée contenant une colonne d’augmentation automatique, mais ne peut généralement pas mettre à jour les valeurs dans la colonne.<br /><br /> Lorsqu’un insert est transformé en colonne d’autoincrément, une valeur unique est insérée dans la colonne au moment de l’insertion. L’augmentation n’est pas définie, mais est spécifique à la source de données. Une application ne doit pas supposer qu’une colonne d’autoincrétion commence à un point ou une augmentation particulier par une valeur particulière.|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|Nom de colonne de base pour la colonne de jeu de résultat. Si un nom de colonne de base n’existe pas (comme dans le cas des colonnes qui sont des expressions), alors cette variable contient une chaîne vide.<br /><br /> Cette information est revenue du champ de SQL_DESC_BASE_COLUMN_NAME dossier de l’IRD, qui est un domaine de lecture seulement.|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Le nom de la table de base qui contient la colonne. Si le nom de la table de base ne peut pas être défini ou n’est pas applicable, cette variable contient une chaîne vide.<br /><br /> Cette information est revenue du champ de SQL_DESC_BASE_TABLE_NAME dossier de l’IRD, qui est un domaine de lecture seulement.|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE si la colonne est traitée comme sensible aux cas pour les collations et les comparaisons.<br /><br /> SQL_FALSE si la colonne n’est pas traitée comme sensible aux cas pour les collations et les comparaisons ou est non-caractéristique.|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|Le catalogue de la table qui contient la colonne. La valeur retournée est définie par implémentation si la colonne est une expression ou si la colonne fait partie d’une vue. Si la source de données ne prend pas en charge les catalogues ou si le nom du catalogue ne peut pas être déterminé, une chaîne vide est retournée. Ce champ d’enregistrement VARCHAR ne se limite pas à 128 caractères.|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*NumericAttributePtr*|Le type de données concis.<br /><br /> Pour les types de données de date et d’intervalle, ce champ renvoie le type de données concis ; par exemple, SQL_TYPE_TIME ou SQL_INTERVAL_YEAR. (Pour plus d’informations, voir [Identifiants et descripteurs de type de données](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) à l’annexe D : Types de données.)<br /><br /> Cette information est revenue du champ de SQL_DESC_CONCISE_TYPE dossier de l’IRD.|  
|SQL_DESC_COUNT (ODBC 1.0)|*NumericAttributePtr*|Nombre de colonnes disponibles dans l’ensemble de résultats. Cela renvoie 0 s’il n’y a pas de colonnes dans l’ensemble de résultats. La valeur de l’argument *de ColumnNumber* est ignorée.<br /><br /> Cette information est revenue du champ d’en-tête SQL_DESC_COUNT de l’IRD.|  
|SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*NumericAttributePtr*|Nombre maximum de caractères requis pour afficher les données de la colonne. Pour plus d’informations sur la taille de l’écran, voir [La taille de la colonne, les chiffres décimaux, la longueur d’octet de transfert et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe D : Data Types.|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE si la colonne a une précision fixe et une échelle non zéro qui sont spécifiques à la source de données.<br /><br /> SQL_FALSE si la colonne n’a pas une précision fixe et une échelle non zéro qui sont spécifiques à la source de données.|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|L’étiquette ou le titre de colonne. Par exemple, une colonne nommée EmpName peut être étiquetée Nom de l’employé ou peut être étiquetée avec un alias.<br /><br /> Si une colonne n’a pas d’étiquette, le nom de la colonne est retourné. Si la colonne n’est pas étiquetée et sans nom, une ficelle vide est retournée.|  
|SQL_DESC_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Une valeur numérique qui est soit la longueur maximale ou réelle du caractère d’une chaîne de caractères ou de type de données binaires. Il s’agit de la longueur maximale du caractère pour un type de données à durée fixe, ou de la longueur réelle du caractère pour un type de données à durée variable. Sa valeur exclut toujours le byte de terminaison nulle qui met fin à la chaîne de caractères.<br /><br /> Cette information est revenue du champ de SQL_DESC_LENGTH dossier de l’IRD.<br /><br /> Pour plus d’informations sur la longueur, voir [Taille de colonne, Chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|Ce champ d’enregistrement VARCHAR(128) contient le caractère ou les caractères que le conducteur reconnaît comme un préfixe pour un littéral de ce type de données. Ce champ contient une chaîne vide pour un type de données pour lequel un préfixe littéral n’est pas applicable. Pour plus d’informations, voir [Préfixes littérales et Suffixes](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|Ce champ d’enregistrement VARCHAR(128) contient le caractère ou les caractères que le conducteur reconnaît comme un suffixe pour un littéral de ce type de données. Ce champ contient une chaîne vide pour un type de données pour lequel un suffixe littéral n’est pas applicable. Pour plus d’informations, voir [Préfixes littérales et Suffixes](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Ce champ d’enregistrement VARCHAR(128) contient n’importe quel nom localisé (langue autochtone) pour le type de données qui peut être différent du nom régulier du type de données. S’il n’y a pas de nom localisé, une corde vide est retournée. Ce champ est uniquement à des fins d’affichage. L’ensemble de caractères de la chaîne est local-dépendant et est généralement l’ensemble de caractère par défaut du serveur.|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|Le pseudonyme de colonne, si elle s’applique. Si le pseudonyme de colonne ne s’applique pas, le nom de la colonne est retourné. Dans les deux cas, SQL_DESC_UNNAMED est prêt à SQL_NAMED. S’il n’y a pas de nom de colonne ou d’alias de colonne, une chaîne vide est retournée et SQL_DESC_UNNAMED est réglée pour SQL_UNNAMED.<br /><br /> Cette information est revenue du champ de SQL_DESC_NAME dossier de l’IRD.|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*NumericAttributePtr*|SQL_ NULLABLE si la colonne peut avoir des valeurs NULL; SQL_NO_NULLS si la colonne n’a pas de valeurs NULL; ou SQL_NULLABLE_UNKNOWN s’on ne sait pas si la colonne accepte les valeurs NULL.<br /><br /> Cette information est revenue du champ de SQL_DESC_NULLABLE dossier de l’IRD.|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*NumericAttributePtr*|Si le type de données dans le champ SQL_DESC_TYPE est un type de données numériques approximative, ce champ SQLINTEGER contient une valeur de 2 parce que le champ SQL_DESC_PRECISION contient le nombre de bits. Si le type de données dans le champ SQL_DESC_TYPE est un type de données numériques exact, ce champ contient une valeur de 10 parce que le champ SQL_DESC_PRECISION contient le nombre de chiffres décimaux. Ce champ est réglé à 0 pour tous les types de données non numériques.|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*NumericAttributePtr*|La longueur, dans les octets, d’une chaîne de caractères ou de type de données binaires. Pour les types de caractère fixe ou binaire, c’est la longueur réelle des octets. Pour les types de caractères à longueur variable ou binaires, c’est la longueur maximale des octets. Cette valeur n’inclut pas le terminateur nul.<br /><br /> Cette information est revenue du champ de SQL_DESC_OCTET_LENGTH dossier de l’IRD.<br /><br /> Pour plus d’informations sur la longueur, voir [Taille de colonne, Chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.|  
|SQL_DESC_PRECISION (ODBC 3.0)|*NumericAttributePtr*|Une valeur numérique qui, pour un type de données numériques, dénote la précision applicable. Pour les types de données SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP et tous les types de données d’intervalle qui représentent un intervalle de temps, sa valeur est la précision applicable du composant fractionnel secondes.<br /><br /> Cette information est revenue du champ de SQL_DESC_PRECISION dossier de l’IRD.|  
|SQL_DESC_SCALE (ODBC 3.0)|*NumericAttributePtr*|Une valeur numérique qui est l’échelle applicable pour un type de données numériques. Pour les types de données DECIMAL et NUMERIC, il s’agit de l’échelle définie. Il n’est pas défini pour tous les autres types de données.<br /><br /> Ces informations sont revenues du champ d’enregistrement SCALE de l’IRD.|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|Le schéma de la table qui contient la colonne. La valeur retournée est définie par implémentation si la colonne est une expression ou si la colonne fait partie d’une vue. Si la source de données ne prend pas en charge les schémas ou si le nom du schéma ne peut pas être déterminé, une chaîne vide est retournée. Ce champ d’enregistrement VARCHAR ne se limite pas à 128 caractères.|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*NumericAttributePtr*|SQL_PRED_NONE si la colonne ne peut pas être utilisée dans une clause WHERE. (C’est la même chose que la valeur SQL_UNSEARCHABLE dans ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR si la colonne peut être utilisée dans une clause WHERE, mais seulement avec le justiciant LIKE. (C’est la même chose que la valeur SQL_LIKE_ONLY dans ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC si la colonne peut être utilisée dans une clause WHERE avec tous les opérateurs de comparaison à l’exception de LIKE. (C’est la même chose que la valeur SQL_EXCEPT_LIKE dans ODBC 2. *x*.)<br /><br /> SQL_PRED_SEARCHABLE si la colonne peut être utilisée dans une clause WHERE avec n’importe quel opérateur de comparaison.<br /><br /> Les colonnes de type SQL_LONGVARCHAR et SQL_LONGVARBINARY retournent généralement SQL_PRED_CHAR.|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|Nom de la table qui contient la colonne. La valeur retournée est définie par implémentation si la colonne est une expression ou si la colonne fait partie d’une vue.<br /><br /> Si le nom de table ne peut pas être déterminé, une corde vide est retournée.|  
|SQL_DESC_TYPE (ODBC 3.0)|*NumericAttributePtr*|Une valeur numérique qui spécifie le type de données SQL.<br /><br /> Lorsque *ColumnNumber* est égal à 0, SQL_BINARY est retourné pour les signets à longueur variable et SQL_INTEGER est retourné pour les signets de longueur fixe.<br /><br /> Pour les types de données de date et d’intervalle, ce champ renvoie le type de données verbeux : SQL_DATETIME ou SQL_INTERVAL. (Pour plus d’informations, consultez [les identifiants et les descripteurs de type de données](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) à l’annexe D : Types de données.<br /><br /> Cette information est revenue du champ de SQL_DESC_TYPE dossier de l’IRD. **Note:**  Pour travailler contre ODBC 2. *x* conducteurs, utilisez SQL_DESC_CONCISE_TYPE à la place.|  
|SQL_DESC_TYPE_NAME (ODBC 1.0)|*CharacterAttributePtr*|Nom de type de données dépendante des sources de données; par exemple, "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY", ou "CHAR ( ) FOR BIT DATA".<br /><br /> Si le type est inconnu, une ficelle vide est retournée.|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*NumericAttributePtr*|SQL_NAMED ou SQL_UNNAMED. Si le champ SQL_DESC_NAME de l’IRD contient un pseudonyme de colonne ou un nom de colonne, SQL_NAMED est retourné. S’il n’y a pas de nom de colonne ou d’alias de colonne, SQL_UNNAMED est retournée.<br /><br /> Cette information est revenue du champ de SQL_DESC_UNNAMED dossier de l’IRD.|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE si la colonne n’est pas signée (ou non numérique).<br /><br /> SQL_FALSE si la colonne est signée.|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*NumericAttributePtr*|La colonne est décrite par les valeurs pour les constantes définies :<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE décrit la redatibilité de la colonne dans l’ensemble de résultats, et non la colonne dans le tableau de base. La facilité d’updatabilité de la colonne de base sur laquelle repose la colonne de l’ensemble de résultats peut être différente de la valeur dans ce domaine. La question de savoir si une colonne est updatable peut être basée sur le type de données, les privilèges des utilisateurs et la définition du résultat lui-même. S’il n’est pas clair si une colonne est updatable, SQL_ATTR_READWRITE_UNKNOWN doit être retourné.|  
  
 **SQLColAttribute** est une alternative extensible à **SQLDescribeCol**. **SQLDescribeCol** renvoie un ensemble fixe d’informations descripteur basées sur ANSI-89 SQL. **SQLColAttribute** permet d’accéder à l’ensemble plus complet d’informations descripteurs disponibles dans les extensions des fournisseurs ANSI SQL-92 et DBMS.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à une colonne dans un ensemble de résultats|[Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Informations de retour sur une colonne dans un ensemble de résultats|[Fonction SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Aller chercher un bloc de données ou faire défiler un ensemble de résultats|[Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Aller chercher plusieurs rangées de données|[SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>Exemple  
 Le code d’échantillon suivant ne libère pas les poignées et les connexions. Voir [SQLFreeHandle Function](../../../odbc/reference/syntax/sqlfreehandle-function.md), [Sample ODBC Program](../../../odbc/reference/sample-odbc-program.md), et [SQLFreeStmt Function](../../../odbc/reference/syntax/sqlfreestmt-function.md) pour les échantillons de code pour les poignées et les relevés gratuits.  
  
```cpp  
// SQLColAttibute.cpp  
// compile with: user32.lib odbc32.lib  
  
#define UNICODE  
  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printStatementResult(SQLHSTMT hstmt) {  
   int bufferSize = 1024, i;  
   SQLRETURN retCode;  
   SQLSMALLINT numColumn = 0, bufferLenUsed;
   
   retCode = SQLNumResultCols(hstmt, &numColumn);  
   
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   printf( "Columns from that table:\n" );  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );  
  
      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &bufferLenUsed, NULL);  
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );  
   }  
  
   // allocate memory for the binding  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnData[i].TargetType = SQL_C_CHAR;  
      columnData[i].BufferLength = (bufferSize+1);  
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );  
   }  
  
   // setup the binding   
   for ( i = 0 ; i < numColumn ; i++ ) {  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType,   
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &(columnData[i].StrLen_or_Ind));  
   }  
  
   printf( "Data from that table:\n" );  
   // fetch the data and print out the data  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {  
      int j;  
      for ( j = 0 ; j < numColumn ; j++ )  
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );  
      printf( "\n" );  
   }  
   printf( "\n" );   
}  
  
int main() {  
   int bufferSize = 1024, i, count = 1, numCols = 5;  
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen, bufferLen;  
   SQLRETURN retCode;  
  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );  
  
   // connect to database  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // display the database information  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferLen);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &bufferLen);  
  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );  
  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )  
      if ( count == 1 )  
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   wprintf( L"Select all data from the first table (%s)\n", firstTableName );  
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );  
  
   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);  
   printStatementResult(hstmt);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exemple de programme ODBC](../../../odbc/reference/sample-odbc-program.md)
