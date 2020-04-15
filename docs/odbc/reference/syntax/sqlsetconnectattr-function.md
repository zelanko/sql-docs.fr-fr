---
title: Fonction SQLSetConnectAttr (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectAttr
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC]
ms.assetid: 97fc7445-5a66-4eb9-8e77-10990b5fd685
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8424462ddde4f99196e26d633fddfa5bb2ed6ee9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301935"
---
# <a name="sqlsetconnectattr-function"></a>Fonction SQLSetConnectAttr
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLSetConnectAttr** définit les attributs qui régissent les aspects des connexions.  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Gestionnaire de conducteur cartographie cette fonction à quand une application ODBC 3 *.x* travaille avec un pilote ODBC 2 *.x,* voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLSetConnectAttr(  
     SQLHDBC       ConnectionHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *Attribut*  
 [Entrée] Attribuer à l’ensemble, énuméré dans "Commentaires".  
  
 *ValuePtr*  
 [Entrée] Pointeur à la valeur à associer à *Attribut*. Selon la valeur de *l’attribut*, *ValuePtr* sera une valeur insignable non signée ou pointera vers une chaîne de caractères non terminée. Notez que le type intégral de *l’argument d’attribut* peut ne pas être la longueur fixe, voir la section Commentaires pour plus de détails.  
  
 *StringLength (en)*  
 [Entrée] Si *Attribut* est un attribut défini par ODBC et *que ValuePtr* pointe vers une chaîne de caractères ou un tampon binaire, cet argument doit être la longueur de *'ValuePtr*' Pour les données de chaîne de caractère, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *Attribut* est un attribut défini par ODBC et *que ValuePtr* est un intégrateur, *StringLength* est ignoré.  
  
 Si *Attribut* est un attribut défini par le conducteur, l’application indique la nature de l’attribut au gestionnaire de conducteur en définissant l’argument *StringLength.* *StringLength* peut avoir les valeurs suivantes :  
  
-   Si *ValuePtr* est un pointeur d’une chaîne de caractères, *stringLength* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si *ValuePtr* est un pointeur à un tampon binaire, alors l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur)* macro dans *StringLength*. Cela place une valeur négative dans *StringLength*.  
  
-   Si *ValuePtr* est un pointeur à une valeur autre qu’une chaîne de caractère ou une chaîne binaire, alors *StringLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si *ValuePtr* contient une valeur fixe, *stringLength* est soit SQL_IS_INTEGER ou SQL_IS_UINTEGER, le cas échéant.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetConnectAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et une *poignée* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLSetConnectAttr** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
 Le conducteur peut retourner SQL_SUCCESS_WITH_INFO pour fournir des informations sur le résultat de la mise en place d’une option.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option modifiée|Le conducteur n’a pas supporté la valeur spécifiée dans *ValuePtr* et a remplacé une valeur similaire. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08002|Nom de connexion en cours d’utilisation|*L’argument d’attribut* était SQL_ATTR_ODBC_CURSORS, et le conducteur était déjà connecté à la source de données.|  
|08003|Connexion non ouverte|(DM) Une valeur *d’attribut* a été spécifiée qui nécessitait une connexion ouverte, mais le *ConnectionHandle* n’était pas dans un état connecté.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|24 000|État de curseur non valide|*L’argument d’attribut* était SQL_ATTR_CURRENT_CATALOG, et un ensemble de résultats était en attente.|  
|25000|Opération illégale lors d’une transaction locale|Une connexion se faisait dans le cadre d’une transaction locale alors qu’elle tentait de s’enrôler dans une transaction distribuée (DTC) en fixant l’attribut de connexion SQL_ATTR_ENLIST_IN_DTC.<br /><br /> Une connexion est déjà enrôlée dans un DTC.<br /><br /> Une connexion a été enrôlée dans une connexion de transaction distribuée et une transaction locale a été lancée en fixant SQL_ATTR_AUTOCOMMIT à SQL_AUTOCOMMIT_OFF.|  
|3D000|Nom du catalogue invalide|*L’argument d’attribut* était SQL_CURRENT_CATALOG, et le nom spécifié du catalogue était invalide.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction **SQLSetConnectAttr** a été appelée, et avant d’être exécutée, la [fonction SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelée sur le *ConnectionHandle*, puis la fonction **SQLSetConnectAttr** a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> Ou, la fonction **SQLSetConnectAttr** a été appelée, et avant qu’il ne termine l’exécution, **SQLCancelHandle** a été appelé sur le *ConnectionHandle* à partir d’un thread différent dans une application multitâli.|  
|HY009|Utilisation invalide du pointeur nul|*L’argument d’attribut* a identifié un attribut de connexion qui exigeait une valeur de chaîne, et l’argument *valuePtr* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour un *StatementHandle* associé à la *ConnectionHandle* et était toujours en exécution lorsque **SQLSetConnectAttr** a été appelé.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *ConnectionHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour l’une des poignées de déclaration associées à la *ConnectionHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour un *StatementHandle* associé à la *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) **SQLBrowseConnect** a été appelé pour le *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant **que SQLBrowseConnect** ne revienne SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS.|  
|HY011 HY011|L’attribut ne peut pas être défini maintenant|*L’argument d’Attribut* était SQL_ATTR_TXN_ISOLATION, et une transaction était ouverte.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY024|Valeur d’attribut invalide|Compte tenu de la valeur *d’attribut* spécifiée, une valeur invalide a été spécifiée dans *ValuePtr*. (Le gestionnaire de conducteur retourne ce SQLSTATE uniquement pour les attributs de connexion et de déclaration qui acceptent un ensemble discret de valeurs, telles que SQL_ATTR_ACCESS_MODE ou SQL_ATTR_ASYNC_ENABLE. Pour tous les autres attributs de connexion et de relevé, le conducteur doit vérifier la valeur spécifiée dans *ValuePtr*.)<br /><br /> *L’argument d’attribut* était SQL_ATTR_TRACEFILE ou SQL_ATTR_TRANSLATE_LIB, et *ValuePtr* était une chaîne vide.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|*(DM) \*ValuePtr* est une chaîne de caractères, et *l’argument StringLength* était inférieur à 0, mais n’était pas SQL_NTS.|  
|HY092 HY092|Identification d’attribut/option invalide|(DM) La valeur spécifiée pour l’argument *Attribut* n’était pas valide pour la version d’ODBC prise en charge par le conducteur.<br /><br /> (DM) La valeur spécifiée pour l’argument *Attribut* était un attribut de lecture seulement.|  
|HY114|Le conducteur ne prend pas en charge l’exécution de fonction asynchrone au niveau de connexion|(DM) Une application a tenté d’activer l’exécution de la fonction asynchrone avec SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE pour un conducteur qui ne prend pas en charge les opérations de connexion asynchrones.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HY121|La bibliothèque cursor et la mise en commun des conducteurs ne peuvent pas être activées en même temps|Pour plus d’informations, voir [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|HYC00|Fonctionnalité facultative non implémentée|La valeur spécifiée pour l’argument *Attribut* était un attribut de connexion ou de déclaration ODBC valide pour la version d’ODBC étayée par le conducteur, mais n’était pas pris en charge par le conducteur.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *ConnectionHandle* ne prend pas en charge la fonction.|  
|IM009|Incapable de charger la traduction DLL|Le conducteur n’a pas été en mesure de charger la traduction DLL qui a été spécifiée pour la connexion. Cette erreur ne peut être retournée que lorsque *l’attribut* est SQL_ATTR_TRANSLATE_LIB.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
|S1118|Le conducteur ne prend pas en charge la notification asynchrone|SQL_ATTR_ASYNC_DBC_EVENT a été définie (après la connexion a été faite), mais la notification asynchrone n’est pas prise en charge par le conducteur.|  
  
 Lorsque *l’attribut* est un attribut de déclaration, **SQLSetConnectAttr** peut retourner n’importe quel SQLSTATEs retournés par **SQLSetStmtAttr**.  
  
## <a name="comments"></a>Commentaires  
 Pour plus d’informations générales sur les attributs de connexion, voir [Attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Les attributs actuellement définis et la version de l’ODBC dans laquelle ils ont été introduits sont indiqués dans le tableau plus tard dans cette section; on s’attend à ce que davantage d’attributs soient définis pour tirer parti de différentes sources de données. Une gamme d’attributs est réservée par ODBC; les développeurs de pilotes doivent réserver des valeurs pour leur propre utilisation spécifique au conducteur de Open Group.  
  
> [!NOTE]
>  La capacité de définir les attributs de déclaration au niveau de connexion en appelant **SQLSetConnectAttr** a été dépréciée dans ODBC 3 *.x*. Les applications ODBC 3 *.x* ne doivent jamais définir les attributs de l’instruction au niveau de connexion. Les attributs de relevés de 3 *.x* D’ODBC ne peuvent pas être définis au niveau de connexion, à l’exception des attributs SQL_ATTR_METADATA_ID et SQL_ATTR_ASYNC_ENABLE, qui sont à la fois des attributs de connexion et des attributs de déclaration et peuvent être définis au niveau de connexion ou au niveau de l’instruction.  
> 
>  Les pilotes ODBC 3 *.x* n’ont besoin que de prendre en charge cette fonctionnalité s’ils doivent travailler avec des applications ODBC 2 *.x* qui définissent les options de relevéS ODBC 2*x* au niveau de connexion. Pour plus d’informations, consultez [SQLSetConnectOption Mapping](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) dans l’annexe G: Driver Guidelines for Backward Compatibility.  
  
 Une application peut appeler **SQLSetConnectAttr** à tout moment entre le moment où la connexion est attribuée et libérée. Tous les attributs de connexion et de relevé définis avec succès par la demande de connexion persistent jusqu’à ce que **SQLFreeHandle** soit appelé sur la connexion. Par exemple, si une application appelle **SQLSetConnectAttr** avant de se connecter à une source de données, l’attribut persiste même si **SQLSetConnectAttr** échoue dans le conducteur lorsque l’application se connecte à la source de données; si une application définit un attribut spécifique au conducteur, l’attribut persiste même si l’application se connecte à un pilote différent sur la connexion.  
  
 Certains attributs de connexion ne peuvent être définis qu’avant qu’une connexion ait été effectuée; d’autres ne peuvent être définis qu’après qu’une connexion a été faite. Le tableau suivant indique les attributs de connexion qui doivent être définis avant ou après qu’une connexion a été faite. *Indique que* l’attribut peut être défini avant ou après la connexion.  
  
|Attribut|Définir avant ou après la connexion?|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|Soit[1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|Vous pouvez soit utiliser|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE|Soit[4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|Vous pouvez soit utiliser|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|Vous pouvez soit utiliser|  
|SQL_ATTR_ASYNC_ENABLE|Soit[2]|  
|SQL_ATTR_AUTO_IPD|Vous pouvez soit utiliser|  
|SQL_ATTR_AUTOCOMMIT|Soit[5]|  
|SQL_ATTR_CONNECTION_DEAD|After|  
|SQL_ATTR_CONNECTION_TIMEOUT|Vous pouvez soit utiliser|  
|SQL_ATTR_CURRENT_CATALOG|Soit[1]|  
|SQL_ATTR_DBC_INFO_TOKEN|After|  
|SQL_ATTR_ENLIST_IN_DTC|After|  
|SQL_ATTR_LOGIN_TIMEOUT|Avant|  
|SQL_ATTR_METADATA_ID|Vous pouvez soit utiliser|  
|SQL_ATTR_ODBC_CURSORS|Avant|  
|SQL_ATTR_PACKET_SIZE|Avant|  
|SQL_ATTR_QUIET_MODE|Vous pouvez soit utiliser|  
|SQL_ATTR_TRACE|Vous pouvez soit utiliser|  
|SQL_ATTR_TRACEFILE|Vous pouvez soit utiliser|  
|SQL_ATTR_TRANSLATE_LIB|After|  
|SQL_ATTR_TRANSLATE_OPTION|After|  
|SQL_ATTR_TXN_ISOLATION|Soit[3]|  
  
 [1] SQL_ATTR_ACCESS_MODE et SQL_ATTR_CURRENT_CATALOG peuvent être réglés avant ou après la connexion, selon le conducteur. Cependant, les applications interopérables les définissent avant de se connecter parce que certains pilotes ne prennent pas en charge de les modifier après la connexion.  
  
 [2] SQL_ATTR_ASYNC_ENABLE doit être défini avant qu’il n’y ait une déclaration active.  
  
 [3] SQL_ATTR_TXN_ISOLATION ne peut être défini que s’il n’y a pas de transactions ouvertes sur la connexion. Certains attributs de connexion prennent en charge la substitution d’une valeur similaire si la source de données ne prend pas en charge la valeur spécifiée dans \* *ValuePtr*. Dans de tels cas, le conducteur retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01S02 (valeur d’option modifiée). Par exemple, si *l’attribut* \*est SQL_ATTR_PACKET_SIZE et *que ValuePtr* dépasse la taille maximale du paquet, le conducteur remplace la taille maximale. Pour déterminer la valeur substituée, une application appelle **SQLGetConnectAttr**.  
  
 [4] Si SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE est réglée avant qu’une connexion soit ouverte, le gestionnaire de conducteur définira l’attribut du conducteur lorsque le conducteur est chargé lors d’un appel à **SQLBrowseConnect**, **SQLConnect**, ou **SQLDriverConnect**. Avant un appel à **SQLBrowseConnect**, **SQLConnect**, ou **SQLDriverConnect**, le gestionnaire de conducteur ne sait pas à quel conducteur se connecter et ne sait pas si le conducteur prend en charge les opérations de connexion asynchrone. Par conséquent, le gestionnaire de conducteur retourne toujours SQL_SUCCESS. Mais, dans le cas où le conducteur ne prend pas en charge les opérations de connexion asynchrone, l’appel à **SQLBrowseConnect**, **SQLConnect**, ou **SQLDriverConnect** échouera.  
  
 [5] Lorsque SQL_ATTR_AUTOCOMMIT est réglée sur FALSE, les applications doivent appeler SQLEndTran (SQL_ROLLBACK) si un API retourne SQL_ERROR pour assurer la cohérence transactionnelle.  
  
 Le format d’information \*défini dans le tampon *ValuePtr* dépend de l’attribut spécifié . *Attribute* **SQLSetConnectAttr** acceptera l’information d’attribut dans l’un des deux formats différents : une chaîne de caractères non terminée ou une valeur d’intégrateur. Le format de chacun est noté dans la description de l’attribut. Les chaînes de caractères soulignées par l’argument *ValuePtr* de **SQLSetConnectAttr** ont une longueur d’octets *StringLength.*  
  
 *L’argument StringLength* est ignoré si la longueur est définie par l’attribut, comme c’est le cas pour tous les attributs introduits dans ODBC 2 *.x* ou plus tôt.  
  
|*Attribut*|*Contenu ValuePtr*|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1.0)|Une valeur SQLUINTEGER. SQL_MODE_READ_ONLY est utilisé par le conducteur ou la source de données comme un indicateur que la connexion n’est pas nécessaire pour prendre en charge les déclarations SQL qui causent des mises à jour. Ce mode peut être utilisé pour optimiser les stratégies de verrouillage, la gestion des transactions ou d’autres domaines, le cas échéant, au conducteur ou à la source de données. Le conducteur n’est pas tenu d’empêcher que de telles déclarations ne soient soumises à la source de données. Le comportement du conducteur et de la source de données lorsqu’on lui demande de traiter les déclarations SQL qui ne sont pas lus uniquement au cours d’une connexion de lecture uniquement est définie par implémentation. SQL_MODE_READ_WRITE est la valeur par défaut.|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)|Une valeur SQLPOINTER qui est une poignée d’événements.<br /><br /> La notification de l’achèvement des fonctions asynchrones est activée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ASYNC_STMT_EVENT et en spécifiant la poignée de l’événement. **Note:**  La méthode de notification n’est pas prise en charge par la bibliothèque de curseurs. Une application recevra un message d’erreur si elle tente d’activer la bibliothèque de curseurs via SQLSetConnectAttr, lorsque la méthode de notification est activée.|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3.8)|Une valeur SQLUINTEGER qui permet ou désactive l’exécution asynchrone de fonctions sélectionnées sur la poignée de connexion. Pour plus d’informations, voir [Asynchrone Execution (Méthode de sondage)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).<br /><br /> SQL_ASYNC_DBC_ENABLE_ON - Activez l’opération asynchrone pour des fonctions spécifiques liées à la connexion.<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF (Par défaut) Désactiver l’opération asynchrone pour des fonctions spécifiques liées à la connexion.<br /><br /> Réglage SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE est toujours synchrone (c’est-à-dire qu’il ne reviendra jamais SQL_STILL_EXECUTING).<br /><br /> L’exécution asynchrone des opérations de déclaration est activée avec SQL_ATTR_ASYNC_ENABLE.|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)|Une valeur SQLPOINTER qui pointe vers la structure du contexte.<br /><br /> Seul le gestionnaire de conducteur peut appeler la fonction **SQLSetStmtAttr** d’un conducteur avec cet attribut.|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)|Une valeur SQLPOINTER qui indique la structure contextuelle.<br /><br /> Seul le gestionnaire de conducteur peut appeler la fonction **SQLSetStmtAttr** d’un conducteur avec cet attribut.|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)|Une valeur SQLULEN qui précise si une fonction appelée avec une déclaration sur la connexion spécifiée est exécutée asynchrone:<br /><br /> SQL_ASYNC_ENABLE_OFF - Désactiver le niveau de connexion asynchrone support d’exécution pour les opérations de déclaration (le défaut).<br /><br /> SQL_ASYNC_ENABLE_ON - Activez le support d’exécution asynchrone de niveau de connexion pour les opérations de déclaration.<br /><br /> Cet attribut peut être défini, que ce soit **SQLGetInfo** avec le type d’information SQL_ASYNC_MODE retourne SQL_AM_CONNECTION ou SQL_AM_STATEMENT.|  
|SQL_ATTR_AUTO_IPD (ODBC 3.0)|Une valeur SQLUINTEGER qui précise si la population automatique de l’IPD après un appel à **SQLPrepare** est prise en charge :<br /><br /> SQL_TRUE - La population automatique de l’IPD après un appel à **SQLPrepare** est soutenue par le conducteur.<br /><br /> SQL_FALSE - La population automatique de l’IPD après un appel à **SQLPrepare** n’est pas pris en charge par le conducteur. Les serveurs qui ne prennent pas en charge les instructions préparées ne seront pas en mesure de remplir automatiquement l’IPD.<br /><br /> Si SQL_TRUE est retournée pour l’attribut de connexion SQL_ATTR_AUTO_IPD, l’attribut de déclaration SQL_ATTR_ENABLE_AUTO_IPD peut être réglé pour activer ou désactiver automatiquement la population de l’IPD. Si SQL_ATTR_AUTO_IPD est SQL_FALSE, SQL_ATTR_ENABLE_AUTO_IPD ne peut pas être mis à SQL_TRUE. La valeur par défaut de SQL_ATTR_ENABLE_AUTO_IPD est égale à la valeur de SQL_ATTR_AUTO_IPD.<br /><br /> Cet attribut de connexion peut être retourné par **SQLGetConnectAttr** mais ne peut pas être défini par **SQLSetConnectAttr**.|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1.0)|Une valeur SQLUINTEGER qui précise s’il faut utiliser le mode autocommit ou manuel :<br /><br /> SQL_AUTOCOMMIT_OFF - Le conducteur utilise le mode de validation manuelle, et l’application doit explicitement valider ou annuler les transactions avec **SQLEndTran**.<br /><br /> SQL_AUTOCOMMIT_ON le conducteur utilise le mode autocommit. Chaque déclaration est commise immédiatement après son exécution. Il s’agit de la valeur par défaut. Toutes les transactions ouvertes sur la connexion sont validées lorsque SQL_ATTR_AUTOCOMMIT est configuré pour SQL_AUTOCOMMIT_ON de passer du mode de validation manuelle au mode autocommit.<br /><br /> Pour plus d’informations, voir [Mode Commit](../../../odbc/reference/develop-app/commit-mode.md). **Important:**  Certaines sources de données suppriment les plans d’accès et ferment les curseurs pour toutes les déclarations sur une connexion chaque fois qu’une déclaration est validée; le mode autocommit peut provoquer cela après l’exécution de chaque relevé non-quier ou lorsque le curseur est fermé pour une requête. Pour plus d’informations, consultez les types d’information SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) et [Effect of Transactions on Cursors et Prepared Statements](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md). <br /><br /> Lorsqu’un lot est exécuté en mode autocommit, deux choses sont possibles. L’ensemble du lot peut être traité comme une unité autocommitable, ou chaque relevé d’un lot est traité comme une unité autocommitable. Certaines sources de données peuvent prendre en charge ces deux comportements et peuvent fournir un moyen de choisir l’un ou l’autre. Il est défini par le conducteur si un lot est traité comme une unité autocommitable ou si chaque relevé individuel dans le lot est autocommitable.|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> (ODBC 3.5)|Une valeur SQLUINTEGER qui indique l’état de la connexion. Si SQL_CD_TRUE, la connexion a été perdue. Si SQL_CD_FALSE, la connexion est toujours active.|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)|Une valeur SQLUINTEGER correspondant au nombre de secondes pour attendre que toute demande sur la connexion soit terminée avant de revenir à la demande. Le conducteur doit retourner SQLSTATE HYT00 (Timeout expiré) chaque fois qu’il est possible de s’absenter dans une situation non associée à l’exécution des requêtes ou de connexion.<br /><br /> Si *ValuePtr* est égal à 0 (la valeur par défaut), il n’y a pas de délai d’attente.|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)|Une chaîne de caractères contenant le nom du catalogue à utiliser par la source de données. Par exemple, dans SQL Server, le catalogue est une base de données, de sorte que \*le pilote envoie une déclaration de base de _données_ **USE** à la source de données, où la base de *données* est la base de données spécifiée dans *ValuePtr*. Pour un pilote à un seul niveau, le catalogue peut être un répertoire, de sorte que le pilote change son répertoire actuel à l’annuaire spécifié dans *'ValuePtr*.|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3,8|Une valeur SQLPOINTER utilisée pour mettre en arrière le jeton d’information de connexion dans la poignée DBC lorsque [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)\**(pRating*) paramètre n’est pas égal à 100.<br /><br /> SQL_ATTR_DBC_INFO_TOKEN est réglé uniquement. Il n’est pas possible d’utiliser **SQLGetConnectAttr** ou **SQLGetConnectOption** pour récupérer cette valeur. **SqLSetConnectAttr** du gestionnaire de conducteur n’acceptera pas SQL_ATTR_DBC_INFO_TOKEN, puisqu’une application ne doit pas définir cet attribut.<br /><br /> Si un conducteur retourne SQL_ERROR après le réglage SQL_ATTR_DBC_INFO_TOKEN, la connexion vient d’être obtenue de la piscine sera libérée. Le gestionnaire de conducteur tentera alors d’obtenir une autre connexion de la piscine. Voir [La sensibilisation à la connexion-pool dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md) pour plus d’informations.|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)|Une valeur SQLPOINTER qui précise s’il faut utiliser le pilote ODBC dans les transactions distribuées coordonnées par Microsoft Component Services.<br /><br /> Passez un objet de transaction DTC OLE qui spécifie la transaction à exporter vers SQL Server, ou SQL_DTC_DONE pour mettre fin à l’association DTC de la connexion.<br /><br /> Le client appelle le coordinateur microsoft Des transactions distribuées (MS DTC) OLE ITransactionDispenser::BeginTransaction méthode pour commencer une transaction MS DTC et créer un objet de transaction MS DTC qui représente la transaction. L’application appelle ensuite SQLSetConnectAttr avec la SQL_ATTR_ENLIST_IN_DTC option d’associer l’objet de transaction à la connexion ODBC. Toute l'activité de base de données connexe sera effectuée sous la protection de la transaction MS DTC. L'application appelle SQLSetConnectAttr avec SQL_DTC_DONE pour mettre un terme à l'association de DTC avec la connexion. Pour plus d'informations, consultez la documentation MS DTC.|  
|SQL_ATTR_LOGIN_TIMEOUT (ODBC 1.0)|Une valeur SQLUINTEGER correspondant au nombre de secondes à attendre qu’une demande de connexion soit terminée avant de revenir à la demande. La valeur par défaut dépend du conducteur. Si *ValuePtr* est de 0, le délai d’attente est désactivé et une tentative de connexion attendra indéfiniment.<br /><br /> Si le délai d’attente spécifié dépasse le délai de connexion maximal dans la source de données, le conducteur remplace cette valeur et retourne SQLSTATE 01S02 (valeur d’option modifiée).|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|Une valeur SQLUINTEGER qui détermine la façon dont les arguments de chaîne des fonctions du catalogue sont traités.<br /><br /> Si SQL_TRUE, l’argument de chaîne des fonctions de catalogue est traité comme des identificateurs. L’affaire n’est pas importante. Pour les cordes non-démocratiques, le conducteur enlève tous les espaces de fuite et la corde est pliée à la majuscule. Pour les cordes délimitées, le conducteur enlève tous les espaces de tête ou de fuite et prend littéralement tout ce qui se trouve entre les délimitations. Si l’un de ces arguments est réglé sur un pointeur nul, la fonction renvoie SQL_ERROR et SQLSTATE HY009 (utilisation invalide du pointeur nul).<br /><br /> Si SQL_FALSE, les arguments de chaîne des fonctions de catalogue ne sont pas traités comme des identificateurs. L’affaire est importante. Ils peuvent contenir soit un modèle de recherche de cordes ou non, selon l’argument.<br /><br /> La valeur par défaut est SQL_FALSE.<br /><br /> *L’argument de TableType* de **SQLTables**, qui prend une liste de valeurs, n’est pas affecté par cet attribut.<br /><br /> SQL_ATTR_METADATA_ID peut également être fixé au niveau de l’instruction. (C’est le seul attribut de connexion qui est également un attribut de déclaration.)<br /><br /> Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2.0)|Une valeur SQLULEN précise comment le gestionnaire de conducteur utilise la bibliothèque de curseurs ODBC :<br /><br /> SQL_CUR_USE_IF_NEEDED - Le Driver Manager n’utilise la bibliothèque de curseurs ODBC que si nécessaire. Si le conducteur prend en charge l’option SQL_FETCH_PRIOR dans **SQLFetchScroll**, le Gestionnaire de conducteur utilise les capacités de défilement du conducteur. Sinon, il utilise la bibliothèque de curseurs ODBC.<br /><br /> SQL_CUR_USE_ODBC - Le Driver Manager utilise la bibliothèque de curseurs ODBC.<br /><br /> SQL_CUR_USE_DRIVER - Le Driver Manager utilise les capacités de défilement du pilote. Il s'agit du paramètre par défaut.<br /><br /> Pour plus d’informations sur la bibliothèque de curseurs ODBC, voir [Annexe F: ODBC Cursor Library](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md). **Avertissement:**  La bibliothèque de curseurs sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.|  
|SQL_ATTR_PACKET_SIZE (ODBC 2.0)|Une valeur SQLUINTEGER spécifiant la taille du paquet réseau dans les octets. **Note:**  De nombreuses sources de données ne prennent pas en charge cette option ou ne peuvent revenir, mais ne pas définir la taille du paquet réseau. <br /><br /> Si la taille spécifiée dépasse la taille maximale du paquet ou est inférieure à la taille minimale du paquet, le conducteur remplace cette valeur et retourne SQLSTATE 01S02 (valeur d’option modifiée).<br /><br /> Si l’application définit la taille du paquet après qu’une connexion a déjà été faite, le conducteur retournera SQLSTATE HY011 (Attribut ne peut pas être défini dès maintenant).|  
|SQL_ATTR_QUIET_MODE (ODBC 2.0)|Une poignée de fenêtre (HWND).<br /><br /> Si la poignée de fenêtre est un pointeur nul, le conducteur n’affiche aucune boîte de dialogue.<br /><br /> Si la poignée de fenêtre n’est pas un pointeur nul, il devrait être la poignée de fenêtre parent de l’application. Il s’agit de la valeur par défaut. Le conducteur utilise cette poignée pour afficher des boîtes de dialogue. **Note:**  L’attribut de connexion SQL_ATTR_QUIET_MODE ne s’applique pas aux boîtes de dialogue affichées par **SQLDriverConnect**.|  
|SQL_ATTR_TRACE (ODBC 1.0)|Une valeur SQLUINTEGER indiquant au gestionnaire de conducteur s’il faut effectuer le traçage :<br /><br /> SQL_OPT_TRACE_OFF - Traçage (par défaut)<br /><br /> SQL_OPT_TRACE_ON - Traçage sur<br /><br /> Lorsque le suivi est allumé, le gestionnaire de conducteur écrit chaque appel de fonction ODBC au fichier de traces. **Note:**  Lorsque le suivi est activé, le gestionnaire de conducteur peut retourner SQLSTATE IM013 (erreur de fichier trace) de n’importe quelle fonction. <br /><br /> Une application spécifie un fichier de traces avec l’option SQL_ATTR_TRACEFILE. Si le fichier existe déjà, le gestionnaire de conducteur s’joint au fichier. Sinon, il crée le fichier. Si le traçage est allumé et qu’aucun fichier de trace n’a été spécifié, le gestionnaire de conducteur écrit au fichier SQL. LOG dans le répertoire racine.<br /><br /> Une application peut définir la variable **ODBCSharedTraceFlag** pour activer le traçage dynamiquement. Le traçage est ensuite activé pour toutes les applications ODBC actuellement en cours d’exécution. Si une application tourne le traçage, elle n’est désactivée que pour cette application.<br /><br /> Si le mot clé **Trace** dans les informations du système est réglé à 1 lorsqu’une application appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV, le traçage est activé pour toutes les poignées. Il n’est activé que pour l’application qui a appelé **SQLAllocHandle**.<br /><br /> Appeler **SQLSetConnectAttr** avec un *attribut* de SQL_ATTR_TRACE n’exige pas que *l’argument ConnectionHandle* soit valide et ne retournera pas SQL_ERROR si *ConnectionHandle* est NULL. Cet attribut s’applique à toutes les connexions.|  
|SQL_ATTR_TRACEFILE (ODBC 1.0)|Une chaîne de caractères non terminée contenant le nom du fichier de traces.<br /><br /> La valeur par défaut de l’attribut SQL_ATTR_TRACEFILE est spécifiée avec le mot clé **TraceFile** dans les informations du système. Pour plus d’informations, voir [ODBC Subkey](../../../odbc/reference/install/odbc-subkey.md).<br /><br /> Appeler **SQLSetConnectAttr** avec un *attribut* de SQL_ATTR_ TRACEFILE n’exige pas que *l’argument de ConnectionHandle* soit valide et ne reviendra pas SQL_ERROR si *ConnectionHandle* est invalide. Cet attribut s’applique à toutes les connexions.|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)|Une chaîne de caractères à durée nulle contenant le nom d’une bibliothèque contenant les fonctions **SQLDriverToDataSource** et **SQLDataSourceToDriver** auxquelles le conducteur accède pour effectuer des tâches telles que la traduction de l’ensemble de caractères. Cette option ne peut être spécifiée que si le conducteur s’est connecté à la source de données. Le paramètre de cet attribut persistera entre les connexions. Pour plus d’informations sur la traduction des données, voir [traduction DLLs](../../../odbc/reference/develop-app/translation-dlls.md) et [Traduction DLL Function Reference](../../../odbc/reference/syntax/translation-dll-api-reference.md).|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)|Une valeur de drapeau 32 bits qui est transmise à la traduction DLL. Cet attribut ne peut être spécifié que si le conducteur s’est connecté à la source de données. Pour plus d’informations sur la traduction des données, voir [traduction DLLs](../../../odbc/reference/develop-app/translation-dlls.md).|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1.0)|Un bitmask 32 bits qui définit le niveau d’isolement des transactions pour la connexion actuelle. Une application doit appeler **SQLEndTran** pour valider ou annuler toutes les transactions ouvertes sur une connexion, avant d’appeler **SQLSetConnectAttr** avec cette option.<br /><br /> Les valeurs valides pour *ValuePtr* peuvent être déterminées en appelant **SQLGetInfo** avec *InfoType* égal à SQL_TXN_ISOLATION_OPTIONS.<br /><br /> Pour une description des niveaux d’isolement des transactions, consultez la description du type d’information SQL_DEFAULT_TXN_ISOLATION dans [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) et [les niveaux d’isolement des transactions.](../../../odbc/reference/develop-app/transaction-isolation-levels.md)|  
  
 [1] Ces fonctions ne peuvent être appelées asynchronement que si le descripteur est un descripteur de mise en œuvre, et non un descripteur d’application.  
  
## <a name="code-example"></a>Exemple de code  
 Voir [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Retour du paramètre d’un attribut de connexion|[Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
