---
title: Fonction SQLSetConnectAttr | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dff8cfc38e71c2594ecbfb753d5e7b9b432f7263
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688197"
---
# <a name="sqlsetconnectattr-function"></a>Fonction SQLSetConnectAttr
**Conformité**  
 Version introduite : Conformité des normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLSetConnectAttr** définit les attributs qui régissent les aspects de connexions.  
  
> [!NOTE]  
>  Pour plus d’informations sur ce que le Gestionnaire de pilotes mappe cette fonction lorsqu’un ODBC 3 *.x* application fonctionne avec un ODBC 2 *.x* pilote, consultez [mappage des fonctions de remplacement pour vers l’arrière Compatibilité des Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLSetConnectAttr(  
     SQLHDBC       ConnectionHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>Arguments  
 *Handle de connexion*  
 [Entrée] Handle de connexion.  
  
 *Attribute*  
 [Entrée] Attribut à définir, répertoriés dans « Commentaires ».  
  
 *ValuePtr*  
 [Entrée] Pointeur vers la valeur à associer à *attribut*. Selon la valeur de *attribut*, *ValuePtr* sera une valeur d’entier non signé ou pointe vers une chaîne de caractères se terminant par null. Notez que le type de l’intégrale de la *attribut* argument ne peut pas être de longueur fixe, consultez la section de commentaires pour les détails.  
  
 *StringLength*  
 [Entrée] Si *attribut* est un attribut défini par ODBC et *ValuePtr* pointe vers une chaîne de caractères ou une mémoire tampon binaire, cet argument doit être la longueur de **ValuePtr*. Pour les données de chaîne de caractères, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *attribut* est un attribut défini par ODBC et *ValuePtr* est un entier, *StringLength* est ignoré.  
  
 Si *attribut* est un attribut définies par le pilote, l’application indique la nature de l’attribut pour le Gestionnaire de pilotes en définissant le *StringLength* argument. *StringLength* peut avoir les valeurs suivantes :  
  
-   Si *ValuePtr* est un pointeur vers une chaîne de caractères, puis *StringLength* est la longueur de la chaîne ou le SQL_NTS.  
  
-   Si *ValuePtr* est un pointeur vers une mémoire tampon binaire, puis l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur*) macro dans *StringLength*. Cela place une valeur négative dans *StringLength*.  
  
-   Si *ValuePtr* est un pointeur vers une valeur autre qu’une chaîne de caractères ou une chaîne binaire, puis *StringLength* doit avoir la valeur SQL_IS_POINTER.  
  
-   Si *ValuePtr* contient une valeur de longueur fixe, puis *StringLength* est SQL_IS_INTEGER ou SQL_IS_UINTEGER, comme il convient.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetConnectAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et un *gérer* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLSetConnectAttr** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
 Le pilote peut retourner SQL_SUCCESS_WITH_INFO pour fournir des informations sur le résultat de la définition d’une option.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur d’option modifiée|Le pilote ne prenait pas en charge la valeur spécifiée dans *ValuePtr* et remplacé une valeur similaire. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08002|Nom de la connexion en cours d’utilisation|Le *attribut* SQL_ATTR_ODBC_CURSORS a été l’argument et le pilote a été déjà connecté à la source de données.|  
|08003|Connexion non ouverte|(DM) un *attribut* valeur a été spécifiée nécessitant une connexion ouverte, mais la *ConnectionHandle* n’était pas dans un état connecté.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|24000|État de curseur non valide|Le *attribut* argument était SQL_ATTR_CURRENT_CATALOG, et un jeu de résultats en attente.|  
|25000|Opération non autorisée dans une transaction locale|Une connexion a été dans une transaction locale lors de la tentative d’inscription dans une connexion de transactions distribuées (DTC) en définissant l’attribut SQL_ATTR_ENLIST_IN_DTC de la connexion.<br /><br /> Une connexion est déjà inscrite dans un DTC.<br /><br /> Une connexion a été inscrite dans une connexion de transaction distribuée et une transaction locale a été démarrée en définissant SQL_ATTR_AUTOCOMMIT SQL_AUTOCOMMIT_OFF.|  
|3D000|Nom de catalogue non valide|Le *attribut* SQL_CURRENT_CATALOG a été l’argument et le nom de catalogue spécifié n’est pas valide.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *ConnectionHandle*. Le **SQLSetConnectAttr** fonction a été appelée et avant qu’il exécutée avec succès, le [sqlcancelhandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*, puis le **SQLSetConnectAttr** fonction a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> Ou, **SQLSetConnectAttr** fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancelHandle** a été appelé sur le *ConnectionHandle* d’un thread différent dans une application multithread.|  
|HY009|Utilisation non valide de pointeur null|Le *attribut* argument identifié un attribut de connexion qui requiert une valeur de chaîne, et le *ValuePtr* argument était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour un *au paramètre StatementHandle* associé à la *ConnectionHandle* et était en cours d’exécution lorsque **SQLSetConnectAttr**a été appelée.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *ConnectionHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelée pour l’une des descripteurs d’instruction associés à la *ConnectionHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour un *au paramètre StatementHandle*  associé à la *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) **SQLBrowseConnect** a été appelé pour le *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant **SQLBrowseConnect** a retourné SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS.|  
|HY011|Attribut ne peut pas être défini maintenant|Le *attribut* argument était SQL_ATTR_TXN_ISOLATION, et une transaction a été ouverte.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY024|Valeur d’attribut non valide|Étant donné le spécifié *attribut* , une valeur non valide a été spécifiée dans *ValuePtr*. (Le Gestionnaire de pilotes retourne ce SQLSTATE uniquement pour les connexions et les attributs d’instruction qui acceptent un ensemble discret de valeurs, telles que SQL_ATTR_ACCESS_MODE ou SQL_ATTR_ASYNC_ENABLE. Pour tous les autres attributs de connexion et instruction, le pilote doit vérifier la valeur spécifiée dans *ValuePtr*.)<br /><br /> Le *attribut* argument a été SQL_ATTR_TRACEFILE ou SQL_ATTR_TRANSLATE_LIB, et *ValuePtr* était une chaîne vide.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|*(DM) \*ValuePtr* est une chaîne de caractères et le *StringLength* argument était inférieure à 0 mais n’était pas SQL_NTS.|  
|HY092|Identificateur d’option/attribut non valide|(DM) la valeur spécifiée pour l’argument *attribut* n’était pas valide pour la version d’ODBC pris en charge par le pilote.<br /><br /> (DM) la valeur spécifiée pour l’argument *attribut* a un attribut en lecture seule.|  
|HY114|Pilote ne prend pas en charge l’exécution des fonctions asynchrones de niveau connexion|(DM) une application a tenté d’activer l’exécution de fonction asynchrone avec sql_attr_async_dbc_functions_enable ne pour un pilote qui ne prend pas en charge les opérations de connexion asynchrone.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HY121|Bibliothèque de curseurs et regroupement prenant en charge de pilote ne peut pas être activée en même temps|Pour plus d’informations, consultez [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La valeur spécifiée pour l’argument *attribut* a été une connexion ODBC valide ou attribut d’instruction pour la version d’ODBC pris en charge par le pilote, mais n’était pas pris en charge par le pilote.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *ConnectionHandle* ne prend pas en charge la fonction.|  
|IM009|Impossible de charger la DLL de traduction|Le pilote n’a pas pu charger la DLL qui a été spécifié pour la connexion de la traduction. Cette erreur peut être renvoyée uniquement lorsque *attribut* est SQL_ATTR_TRANSLATE_LIB.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
|S1118|Pilote ne prend pas en charge la notification asynchrone|SQL_ATTR_ASYNC_DBC_EVENT a été défini (après que la connexion a été effectuée), mais la notification asynchrone n’est pas pris en charge par le pilote.|  
  
 Lorsque *attribut* est un attribut d’instruction, **SQLSetConnectAttr** peut retourner n’importe quel SQLSTATE retournée par **SQLSetStmtAttr**.  
  
## <a name="comments"></a>Commentaires  
 Pour obtenir des informations générales sur les attributs de connexion, consultez [attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Les attributs actuellement définis et la version d’ODBC dans lequel ils ont été introduites sont affichés dans le tableau plus loin dans cette section. Il est probable que plusieurs attributs seront définis pour tirer parti de différentes sources de données. Une plage d’attributs est réservée par ODBC ; les développeurs de pilotes doivent réserver des valeurs pour leur propre usage spécifiques au pilote à partir d’Open Group.  
  
> [!NOTE]  
>  La possibilité de définir des attributs d’instruction au niveau de la connexion en appelant **SQLSetConnectAttr** a été déconseillée dans ODBC 3 *.x*. ODBC 3 *.x* applications ne doivent jamais définir les attributs d’instruction au niveau de la connexion. ODBC 3 *.x* attributs d’instruction ne peut pas être définis au niveau de la connexion, à l’exception des attributs SQL_ATTR_METADATA_ID et SQL_ATTR_ASYNC_ENABLE, qui sont des attributs de connexion et les attributs d’instruction et peut être Définissez au niveau de la connexion ou niveau de l’instruction.  
>   
>  ODBC 3 *.x* pilotes doivent prennent uniquement en charge cette fonctionnalité si elles doivent fonctionner avec ODBC 2 *.x* application qui définira ODBC 2 *.x* options d’instruction au niveau de la connexion. Pour plus d’informations, consultez [SQLSetConnectOption mappage](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) dans la section annexe g : pilote instructions pour la compatibilité descendante.  
  
 Une application peut appeler **SQLSetConnectAttr** à tout moment entre le moment où la connexion est allouée et libérée. Tous les attributs de connexion et d’instruction a été définies par l’application pour la connexion persistant jusqu'à **SQLFreeHandle** est appelée sur la connexion. Par exemple, si une application appelle **SQLSetConnectAttr** avant de vous connecter à une source de données, l’attribut persiste même si **SQLSetConnectAttr** échoue dans le pilote lors de l’application se connecte à la source de données ; Si une application définit un attribut spécifique au pilote, l’attribut persiste même si l’application se connecte à un autre pilote sur la connexion.  
  
 Certains attributs de connexion peuvent être définies uniquement avant une connexion a été établie ; d’autres utilisateurs peuvent être définies uniquement une fois une connexion a été établie. Le tableau suivant indique les attributs de connexion qui doivent être définies avant ou après qu’une connexion a été établie. *Soit* indique que l’attribut peut être défini avant ou après la connexion.  
  
|Attribute|Définir avant ou après la connexion ?|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|[1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|Avant ou après|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE N'|Soit [4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|Avant ou après|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|Avant ou après|  
|SQL_ATTR_ASYNC_ENABLE|Soit [2]|  
|SQL_ATTR_AUTO_IPD|Avant ou après|  
|SQL_ATTR_AUTOCOMMIT|Soit [5]|  
|SQL_ATTR_CONNECTION_DEAD|After|  
|SQL_ATTR_CONNECTION_TIMEOUT|Avant ou après|  
|SQL_ATTR_CURRENT_CATALOG|[1]|  
|SQL_ATTR_DBC_INFO_TOKEN|After|  
|SQL_ATTR_ENLIST_IN_DTC|After|  
|SQL_ATTR_LOGIN_TIMEOUT|Avant|  
|SQL_ATTR_METADATA_ID|Avant ou après|  
|SQL_ATTR_ODBC_CURSORS|Avant|  
|SQL_ATTR_PACKET_SIZE|Avant|  
|SQL_ATTR_QUIET_MODE|Avant ou après|  
|SQL_ATTR_TRACE|Avant ou après|  
|SQL_ATTR_TRACEFILE|Avant ou après|  
|SQL_ATTR_TRANSLATE_LIB|After|  
|SQL_ATTR_TRANSLATE_OPTION|After|  
|SQL_ATTR_TXN_ISOLATION|[3]|  
  
 [1] SQL_ATTR_ACCESS_MODE et SQL_ATTR_CURRENT_CATALOG peuvent être définis avant ou après la connexion, selon le pilote. Toutefois, applications interopérables les définir avant de vous connecter, car certains pilotes ne prennent pas en charge modifier ces après s’être connecté.  
  
 [2] SQL_ATTR_ASYNC_ENABLE doit être définie avant une instruction active.  
  
 [3] SQL_ATTR_TXN_ISOLATION peut être définie uniquement si aucune transaction ouverte sur la connexion. Certains attributs de connexion de prendre en charge la substitution d’une valeur semblable si la source de données ne prend pas en charge la valeur spécifiée dans \* *ValuePtr*. Dans ce cas, le pilote retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01 s 02 (valeur d’Option modifiée). Par exemple, si *attribut* est SQL_ATTR_PACKET_SIZE et \* *ValuePtr* dépasse la taille maximale du paquet, le pilote remplace la taille maximale. Pour déterminer la valeur substituée, une application appelle **SQLGetConnectAttr**.  
  
 [4] si sql_attr_async_dbc_functions_enable n’est définie avant une connexion est ouverte, le Gestionnaire de pilotes définira les attributs du pilote lorsque le pilote est chargé pendant un appel à **SQLBrowseConnect**, **SQLConnect**, ou **SQLDriverConnect**. Avant un appel à **SQLBrowseConnect**, **SQLConnect**, ou **SQLDriverConnect**, le Gestionnaire de pilotes ne sait pas quel pilote pour se connecter à et ne sait pas si le pilote prend en charge les opérations de connexion asynchrone. Par conséquent, le Gestionnaire de pilotes retourne toujours SQL_SUCCESS. Mais, au cas où le pilote ne prend pas en charge les opérations de connexion asynchrone, l’appel à **SQLBrowseConnect**, **SQLConnect**, ou **SQLDriverConnect** échouera.  
  
 [5] lorsque SQL_ATTR_AUTOCOMMIT est définie sur FALSE, les applications doivent appeler SQLEndTran(SQL_ROLLBACK) si n’importe quelle API retourne SQL_ERROR pour garantir la cohérence transactionnelle.  
  
 Le format des informations définies le \* *ValuePtr* tampon dépend spécifié *attribut*. **SQLSetConnectAttr** acceptera les informations d’attribut dans un des deux formats : une chaîne de caractères se terminant par null ou une valeur entière. Le format de chacun d’eux est indiqué dans la description de l’attribut. Caractères des chaînes vers lequel pointés le *ValuePtr* argument de **SQLSetConnectAttr** avoir une longueur de *StringLength* octets.  
  
 Le *StringLength* argument est ignoré si la longueur est définie par l’attribut, comme c’est le cas pour tous les attributs introduite dans ODBC 2 *.x* ou une version antérieure.  
  
|*Attribute*|*ValuePtr* contenu|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1.0)|Une valeur SQLUINTEGER. SQL_MODE_READ_ONLY est utilisé par le pilote ou d’une source de données comme un indicateur de la connexion n’est pas requise pour prendre en charge les instructions SQL qui génèrent des mises à jour. Ce mode peut être utilisé pour optimiser les stratégies de verrouillage, de gestion des transactions ou d’autres zones en fonction de la source de données ou de pilote. Le pilote n’est pas nécessaire pour éviter de telles instructions d’envoi vers la source de données. Le comportement du pilote et de la source de données lorsque vous êtes invité à traiter les instructions SQL qui ne sont pas en lecture seule lors d’une connexion en lecture seule est défini par l’implémentation. SQL_MODE_READ_WRITE est la valeur par défaut.|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3.8)|Une valeur SQLPOINTER qui est un handle d’événement.<br /><br /> Notification de la fin des fonctions asynchrones est activée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ASYNC_STMT_EVENT et en spécifiant le handle d’événement. **Remarque :** la méthode de notification n’est pas pris en charge avec la bibliothèque de curseurs. Une application message d’erreur si elle tente d’activer la bibliothèque de curseurs par le biais de SQLSetConnectAttr, lorsque la méthode de notification est activée.|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE NE (ODBC 3.8)|Une valeur SQLUINTEGER qui active ou désactive l’exécution asynchrone de fonctions sélectionnées sur le handle de connexion. Pour plus d’informations, consultez [exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).<br /><br /> SQL_ASYNC_DBC_ENABLE_ON = opération asynchrone d’activation pour les fonctions liées à la connexion spécifiées.<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF = opération asynchrone des désactiver (par défaut) pour les fonctions liées à la connexion spécifiées.<br /><br /> Paramètre sql_attr_async_dbc_functions_enable n’est toujours synchrone (autrement dit, il ne retourne jamais SQL_STILL_EXECUTING).<br /><br /> Exécution asynchrone des opérations de l’instruction sont activées avec SQL_ATTR_ASYNC_ENABLE.|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3.8)|Une valeur SQLPOINTER qui pointe vers une structure de contexte.<br /><br /> Seul le Gestionnaire de pilotes peut appeler un chauffeur **SQLSetStmtAttr** fonction avec cet attribut.|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3.8)|Une valeur SQLPOINTER qui pointe vers la structure de contexte.<br /><br /> Seul le Gestionnaire de pilotes peut appeler un chauffeur **SQLSetStmtAttr** fonction avec cet attribut.|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3.0)|Une valeur SQLULEN qui spécifie si une fonction appelée avec une instruction sur la connexion spécifiée est exécutée de façon asynchrone :<br /><br /> SQL_ASYNC_ENABLE_OFF = Disable connexion au niveau de l’exécution asynchrone prise en charge des opérations d’instruction (la valeur par défaut).<br /><br /> SQL_ASYNC_ENABLE_ON = Enable connexion au niveau de l’exécution asynchrone prise en charge des opérations de l’instruction.<br /><br /> Cet attribut peut être définie si **SQLGetInfo** avec les informations SQL_ASYNC_MODE type retourne SQL_AM_CONNECTION ou SQL_AM_STATEMENT.|  
|SQL_ATTR_AUTO_IPD (ODBC 3.0)|Une valeur SQLUINTEGER en lecture seule qui spécifie si l’alimentation automatique de l’IPD après un appel à **SQLPrepare** est pris en charge :<br /><br /> SQL_TRUE = remplissage automatique de l’IPD après un appel à **SQLPrepare** est pris en charge par le pilote.<br /><br /> SQL_FALSE = remplissage automatique de l’IPD après un appel à **SQLPrepare** n’est pas pris en charge par le pilote. Les serveurs ne prenant pas en charge des instructions préparées ne seront pas en mesure de remplir l’IPD automatiquement.<br /><br /> Si SQL_TRUE est retourné pour l’attribut de connexion SQL_ATTR_AUTO_IPD, vous pouvez définir l’attribut d’instruction SQL_ATTR_ENABLE_AUTO_IPD pour activer ou désactiver le remplissage automatique de l’IPD. Si SQL_ATTR_AUTO_IPD est SQL_FALSE, SQL_ATTR_ENABLE_AUTO_IPD ne peut pas être définie sur SQL_TRUE. La valeur par défaut de SQL_ATTR_ENABLE_AUTO_IPD est égale à la valeur de SQL_ATTR_AUTO_IPD.<br /><br /> Cet attribut de connexion peut être retourné par **SQLGetConnectAttr** mais ne peut pas être définie à **SQLSetConnectAttr**.|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1.0)|Une valeur SQLUINTEGER qui spécifie s’il faut utiliser le mode de validation automatique ou manuel :<br /><br /> SQL_AUTOCOMMIT_OFF = le pilote utilise le mode de validation manuelle et l’application doit explicitement valider ou restaurer les transactions avec **SQLEndTran**.<br /><br /> SQL_AUTOCOMMIT_ON = le pilote utilise le mode de validation automatique. Chaque instruction est validée immédiatement après son exécution. Il s'agit du paramètre par défaut. Toutes les transactions ouvertes sur la connexion sont validées lorsque SQL_ATTR_AUTOCOMMIT a la valeur SQL_AUTOCOMMIT_ON pour changer de mode de validation manuelle en mode de validation automatique.<br /><br /> Pour plus d’informations, consultez [Mode Commit](../../../odbc/reference/develop-app/commit-mode.md). **Important :** certaines sources de données supprimer les plans d’accès et fermer les curseurs pour toutes les instructions sur une connexion chaque fois qu’une instruction est validée ; mode de validation automatique peut entraîner cette situation après l’exécution de chaque instruction nonquery ou lorsque le curseur se trouve fermé pour une requête. Pour plus d’informations, consultez les types d’informations SQL_CURSOR_COMMIT_BEHAVIOR et SQL_CURSOR_ROLLBACK_BEHAVIOR dans [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) et [effet des Transactions sur les curseurs et les instructions préparées](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md). <br /><br /> Lorsqu’un lot est exécuté en mode de validation automatique, deux choses sont possibles. Le lot entier peut être traité comme une unité autocommitable ou chaque instruction dans un lot est traitée comme une unité autocommitable. Certaines sources de données peuvent prendre en charge les deux de ces comportements et peuvent fournir un moyen de choisir une ou l’autre. Il est également définie par le pilote indique si un lot est traité comme une unité autocommitable ou si chaque instruction du lot est autocommitable.|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> ODBC (3.5)|Une valeur SQLUINTEGER en lecture seule qui indique l’état de la connexion. Si SQL_CD_TRUE, la connexion a été perdue. Si SQL_CD_FALSE, la connexion est toujours active.|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3.0)|Une valeur SQLUINTEGER correspondant au nombre de secondes d’attente pour toutes les requêtes sur la connexion à effectuer avant de retourner à l’application. Le pilote doit retourner SQLSTATE HYT00 (délai d’attente expiré) à tout moment qu’il est possible de délai d’attente dans une situation non associée à l’exécution de requête ou de connexion.<br /><br /> Si *ValuePtr* est égal à 0 (valeur par défaut), il n’existe aucun délai d’expiration.|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2.0)|Une chaîne de caractères contenant le nom du catalogue à utiliser par la source de données. Par exemple, dans SQL Server, le catalogue étant une base de données, le pilote envoie un **utilisation** *base de données* instruction à la source de données, où *base de données* est la base de données spécifié dans \* *ValuePtr*. Pour un pilote de niveau unique, le catalogue peut être un répertoire, pour le pilote des modifications du répertoire spécifié dans l’annuaire actuel **ValuePtr*.|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3.8|Une valeur SQLPOINTER permet de définir dans le jeton d’informations de connexion dans DBC gérer lorsque [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)de (\**pRating*) paramètre n’est pas égal à 100.<br /><br /> SQL_ATTR_DBC_INFO_TOKEN est uniquement. Il n’est pas possible d’utiliser **SQLGetConnectAttr** ou **SQLGetConnectOption** pour récupérer cette valeur. Le Gestionnaire de pilotes **SQLSetConnectAttr** n’acceptera pas SQL_ATTR_DBC_INFO_TOKEN, dans la mesure où une application ne doit pas définir cet attribut.<br /><br /> Si un pilote retourne SQL_ERROR après avoir SQL_ATTR_DBC_INFO_TOKEN, la connexion simplement obtenue à partir du pool est libérée. Le Gestionnaire de pilotes tente alors d’obtenir une autre connexion à partir du pool. Consultez [développer la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md) pour plus d’informations.|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3.0)|Une valeur SQLPOINTER qui spécifie s’il faut utiliser le pilote ODBC dans des transactions distribuées coordonnées par les Services de composants de Microsoft.<br /><br /> Passer un objet OLE DTC transaction qui spécifie la transaction pour exporter vers SQL Server ou SQL_DTC_DONE pour terminer l’association de DTC de la connexion.<br /><br /> Le client appelle la méthode de service Microsoft Distributed Transaction Coordinator (MS DTC) OLE ITransactionDispenser::BeginTransaction pour commencer une transaction MS DTC et créer un objet de transaction MS DTC qui représente la transaction. L’application appelle ensuite SQLSetConnectAttr avec l’option SQL_ATTR_ENLIST_IN_DTC pour associer l’objet de transaction à la connexion ODBC. Toute l'activité de base de données connexe sera effectuée sous la protection de la transaction MS DTC. L’application appelle SQLSetConnectAttr avec SQL_DTC_DONE pour terminer l’association de DTC de la connexion. Pour plus d'informations, consultez la documentation MS DTC.|  
|SQL_ATTR_LOGIN_TIMEOUT PERMET DE CONTRÔLER (ODBC 1.0)|Une valeur SQLUINTEGER correspondant au nombre de secondes à attendre une demande de connexion soit terminée avant de retourner à l’application. La valeur par défaut dépend du pilote. Si *ValuePtr* est 0, le délai d’attente est désactivé et une tentative de connexion attend indéfiniment.<br /><br /> Si le délai d’expiration spécifié dépasse le délai d’expiration de connexion maximale dans la source de données, le pilote remplace cette valeur et retourne SQLSTATE 01 s 02 (valeur d’Option modifiée).|  
|SQL_ATTR_METADATA_ID (ODBC 3.0)|Une valeur SQLUINTEGER qui détermine la façon dont les arguments de chaîne de fonctions de catalogue sont traités.<br /><br /> Si SQL_TRUE, l’argument de chaîne de fonctions de catalogue sont traitées comme identificateurs. Le cas n’est pas significatif. Pour les chaînes non délimités, le pilote supprime les espaces de fin et la chaîne est assemblée en majuscules. Pour des chaînes délimitées, le pilote supprime les espaces de début ou de fin et prend littéralement tout ce qui est situé entre les délimiteurs. Si un de ces arguments est défini sur un pointeur null, la fonction retourne SQL_ERROR et SQLSTATE HY009 (utilisation non valide d’un pointeur null).<br /><br /> Si SQL_FALSE, les arguments de chaîne de fonctions de catalogue ne sont pas traitées comme identificateurs. Le cas est significatif. Ils peuvent contenir un modèle de recherche de chaîne ou pas, en fonction de l’argument.<br /><br /> La valeur par défaut est SQL_FALSE.<br /><br /> Le *TableType* argument de **SQLTables**, qui accepte une liste de valeurs, n’est pas affecté par cet attribut.<br /><br /> SQL_ATTR_METADATA_ID peut également être définie sur le niveau de l’instruction. (Il est l’attribut de connexion uniquement qui est également un attribut d’instruction).<br /><br /> Pour plus d’informations, consultez [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2.0)|Une valeur SQLULEN qui spécifie comment le Gestionnaire de pilotes utilise la bibliothèque de curseurs ODBC :<br /><br /> SQL_CUR_USE_IF_NEEDED = le Gestionnaire de pilote utilise la bibliothèque de curseurs ODBC uniquement s’il est nécessaire. Si le pilote prend en charge l’option SQL_FETCH_PRIOR dans **SQLFetchScroll**, le Gestionnaire de pilotes utilise les fonctionnalités de défilement du pilote. Sinon, il utilise la bibliothèque de curseurs ODBC.<br /><br /> SQL_CUR_USE_ODBC = le Gestionnaire de pilote utilise la bibliothèque de curseurs ODBC.<br /><br /> SQL_CUR_USE_DRIVER = le Gestionnaire de pilote utilise les fonctionnalités de défilement du pilote. Il s'agit du paramètre par défaut.<br /><br /> Pour plus d’informations sur la bibliothèque de curseurs ODBC, consultez [bibliothèque de curseurs ODBC annexe f :](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md). **Avertissement :** la bibliothèque de curseurs sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.|  
|SQL_ATTR_PACKET_SIZE (ODBC 2.0)|Une valeur SQLUINTEGER spécifiant la taille du paquet réseau en octets. **Remarque :** nombreuses sources de données ne prennent pas en charge cette option ou uniquement pouvez retour mais pas définir la taille du paquet réseau. <br /><br /> Si la taille spécifiée dépasse la taille maximale du paquet ou est inférieure à la taille minimum de paquets, le pilote remplace cette valeur et retourne SQLSTATE 01 s 02 (valeur d’Option modifiée).<br /><br /> Si l’application définit la taille du paquet après une connexion a déjà été établie, le pilote retourne SQLSTATE HY011 (attribut ne peut pas être défini maintenant).|  
|SQL_ATTR_QUIET_MODE (ODBC 2.0)|Un handle de fenêtre (HWND).<br /><br /> Si le handle de fenêtre est un pointeur null, le pilote n’affiche pas les boîtes de dialogue.<br /><br /> Si le handle de fenêtre n’est pas un pointeur null, il doit être le handle de fenêtre parent de l’application. Il s'agit du paramètre par défaut. Le pilote utilise ce handle pour afficher des boîtes de dialogue. **Remarque :** l’attribut de connexion SQL_ATTR_QUIET_MODE ne s’applique pas aux boîtes de dialogue affichées par **SQLDriverConnect**.|  
|SQL_ATTR_TRACE (ODBC 1.0)|Une valeur SQLUINTEGER indiquant le Gestionnaire de pilotes si vous souhaitez effectuer le suivi :<br /><br /> SQL_OPT_TRACE_OFF = suivi off (valeur par défaut)<br /><br /> SQL_OPT_TRACE_ON = suivi sur<br /><br /> Lorsque le traçage est activé, le Gestionnaire de pilotes écrit à chaque appel de fonction ODBC dans le fichier de trace. **Remarque :** lorsque le traçage est activé, le Gestionnaire de pilotes peut retourner SQLSTATE IM013 (erreur de fichier de Trace) à partir de n’importe quelle fonction. <br /><br /> Une application spécifie un fichier de trace avec l’option SQL_ATTR_TRACEFILE. Si le fichier existe déjà, le Gestionnaire de pilotes ajoute au fichier. Sinon, il crée le fichier. Si le suivi est activé et aucun fichier de trace n’a été spécifié, le Gestionnaire de pilotes est écrit dans le fichier SQL. Ouvrez une session dans le répertoire racine.<br /><br /> Une application peut définir la variable **ODBCSharedTraceFlag** pour activer le traçage de manière dynamique. Le suivi est alors activé pour toutes les applications ODBC en cours d’exécution. Si une application désactive le suivi, il est désactivé uniquement pour cette application.<br /><br /> Si le **Trace** mot clé dans les informations système est défini sur 1 lorsqu’une application appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV, le traçage est activé pour tous les handles. Il est activé uniquement pour l’application qui a appelé **SQLAllocHandle**.<br /><br /> Appel **SQLSetConnectAttr** avec un *attribut* de SQL_ATTR_TRACE ne nécessite pas que le *ConnectionHandle* argument soit valide et ne retourne SQL_ERROR si *ConnectionHandle* a la valeur NULL. Cet attribut s’applique à toutes les connexions.|  
|SQL_ATTR_TRACEFILE (ODBC 1.0)|Chaîne de caractères se terminant par null qui contient le nom du fichier de trace.<br /><br /> La valeur par défaut de l’attribut SQL_ATTR_TRACEFILE est spécifiée avec la **TraceFile** mot clé dans les informations système. Pour plus d’informations, consultez [sous-clé ODBC](../../../odbc/reference/install/odbc-subkey.md).<br /><br /> Appel **SQLSetConnectAttr** avec un *attribut* de SQL_ATTR_ TRACEFILE ne nécessite pas la *ConnectionHandle* argument soit valide et ne retourne SQL_ERROR si *ConnectionHandle* n’est pas valide. Cet attribut s’applique à toutes les connexions.|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1.0)|Une chaîne de caractères se terminant par null qui contient le nom d’une bibliothèque contenant les fonctions **SQLDriverToDataSource** et **SQLDataSourceToDriver** que le pilote accède pour effectuer des tâches telles que traduction de jeu de caractères. Cette option peut être spécifié uniquement si le pilote a connecté à la source de données. Le paramètre de cet attribut persistera entre les connexions. Pour plus d’informations sur la conversion de données, consultez [DLL de traduction](../../../odbc/reference/develop-app/translation-dlls.md) et [traduction de référence des fonctions DLL](../../../odbc/reference/syntax/translation-dll-api-reference.md).|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1.0)|Une valeur d’indicateur de 32 bits qui est passée à la DLL de traduction. Cet attribut peut être spécifié uniquement si le pilote a connecté à la source de données. Pour plus d’informations sur la conversion de données, consultez [DLL de traduction](../../../odbc/reference/develop-app/translation-dlls.md).|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1.0)|Un masque de bits 32 bits qui définit le niveau d’isolation de transaction pour la connexion actuelle. Une application doit appeler **SQLEndTran** pour valider ou restaurer les transactions ouvertes sur une connexion, avant d’appeler **SQLSetConnectAttr** avec cette option.<br /><br /> Les valeurs valides pour *ValuePtr* peut être déterminée en appelant **SQLGetInfo** avec *InfoType* égal à SQL_TXN_ISOLATION_OPTIONS.<br /><br /> Pour obtenir une description des niveaux d’isolement de transaction, consultez la description du type d’informations SQL_DEFAULT_TXN_ISOLATION dans [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) et [niveaux d’Isolation des transactions](../../../odbc/reference/develop-app/transaction-isolation-levels.md).|  
  
 [1], ces fonctions peuvent être appelées de façon asynchrone uniquement si le descripteur est un descripteur d’implémentation, pas un descripteur d’application.  
  
## <a name="code-example"></a>Exemple de code  
 Consultez [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Allocation d’un handle|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Retourner le paramètre d’un attribut de connexion|[SQLGetConnectAttr, fonction](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
