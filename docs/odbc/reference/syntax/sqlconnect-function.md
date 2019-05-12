---
title: Fonction SQLConnect | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConnect
helpviewer_keywords:
- SQLConnect function [ODBC]
ms.assetid: 59075e46-a0ca-47bf-972a-367b08bb518d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f2eabec895a0b56d396d5848c8f418451e0afb7
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537669"
---
# <a name="sqlconnect-function"></a>Fonction SQLConnect
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLConnect** établit des connexions à un pilote et une source de données. Le handle de connexion référence le stockage de toutes les informations sur la connexion à la source de données, y compris l’état, l’état de transaction et informations d’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLConnect(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      ServerName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      UserName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      Authentication,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnectionHandle*  
 [Entrée] Handle de connexion.  
  
 *ServerName*  
 [Entrée] Nom de source de données. Les données peuvent être situées sur le même ordinateur que le programme ou sur un autre ordinateur situé sur un réseau. Pour plus d’informations sur la façon dont une application sélectionne une source de données, consultez [choisir une Source de données ou le pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Entrée] Longueur de **nom_serveur* en caractères.  
  
 *UserName*  
 [Entrée] Identificateur d’utilisateur.  
  
 *NameLength2*  
 [Entrée] Longueur de **nom d’utilisateur* en caractères.  
  
 *Authentification*  
 [Entrée] Chaîne d’authentification (généralement le mot de passe).  
  
 *NameLength3*  
 [Entrée] Longueur de **authentification* en caractères.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLConnect** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_DBC et un *gérer* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLConnect** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur d’option modifiée|Le pilote ne prenait pas en charge la valeur spécifiée de la *ValuePtr* argument dans **SQLSetConnectAttr** et remplacé une valeur similaire. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08001|Impossible d’établir la connexion du client|Le pilote n’a pas pu établir une connexion avec la source de données.|  
|08002|Nom de la connexion en cours d’utilisation|(DM) spécifié *ConnectionHandle* avait déjà été utilisé pour établir une connexion avec une source de données et la connexion a été ouvert ou l’utilisateur a été de navigation pour une connexion.|  
|08004|Serveur a rejeté la connexion|La source de données a rejeté l’établissement de la connexion pour des raisons de défini par l’implémentation.|  
|08S01|Échec de lien de communication|Le lien de communication entre le pilote et de la source de données à laquelle le pilote a été tentative de connexion a échoué avant le traitement de la fonction a été exécutée.|  
|28000|Spécification d’autorisation non valide|La valeur spécifiée pour l’argument *nom d’utilisateur* ou la valeur spécifiée pour l’argument *authentification* violée restrictions définies par la source de données.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le Gestionnaire de pilotes (DM) n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *ConnectionHandle*. Le **SQLConnect** fonction a été appelée et avant qu’il exécutée avec succès, [sqlcancelhandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*et ensuite le **SQLConnect** fonction a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> Ou, **SQLConnect** fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancelHandle** a été appelé sur le *ConnectionHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *ConnectionHandle* et était en cours d’exécution quand cette fonction a été appelée.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur spécifiée pour l’argument *NameLength1*, *NameLength2*, ou *NameLength3* était inférieur à 0, mais pas égale à SQL_NTS.<br /><br /> (DM) la valeur spécifiée pour l’argument *NameLength1* a dépassé la longueur maximale pour un nom de source de données.|  
|HYT00|Délai d'expiration dépassé|Le délai d’expiration de requête a expiré avant la connexion à la source de données terminée. Le délai d’expiration est défini via **SQLSetConnectAttr**, sql_attr_login_timeout permet de contrôler.|  
|HY114|Pilote ne prend pas en charge l’exécution de fonction asynchrone au niveau de connexion|(DM) l’application activée à l’opération asynchrone sur le handle de connexion avant d’effectuer la connexion. Toutefois, le pilote ne prend pas en charge les opérations asynchrones sur le handle de connexion.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le pilote spécifié par le nom de source de données ne prend pas en charge la fonction.|  
|IM002|Source de données introuvable et aucun pilote par défaut spécifié|(DM) spécifié dans l’argument de nom de source de données *nom_serveur* est introuvable dans les informations système, ni y a-t-il eu une spécification de pilote par défaut.|  
|IM003|Pilote spécifié ne peut pas être connecté à|(DM) le pilote répertorié dans les données de spécification de la source dans les informations système est introuvable ou ne peut pas être connectée à une autre raison.|  
|IM004|Échec de SQLAllocHandle du pilote sur SQL_HANDLE_ENV|(DM) au cours de **SQLConnect**, le Gestionnaire de pilote appelé du pilote **SQLAllocHandle** fonctionne avec un *HandleType* de SQL_HANDLE_ENV et le pilote a renvoyé une erreur.|  
|IM005|Échec de SQLAllocHandle du pilote sur SQL_HANDLE_DBC|(DM) au cours de **SQLConnect**, le Gestionnaire de pilote appelé du pilote **SQLAllocHandle** fonctionne avec un *HandleType* de SQL_HANDLE_DBC et le pilote a renvoyé une erreur.|  
|IM006|Échec SQLSetConnectAttr du pilote|Au cours de **SQLConnect**, le Gestionnaire de pilote appelé du pilote **SQLSetConnectAttr** (fonction) et le pilote a renvoyé une erreur. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|IM009|Impossible de se connecter à la DLL de traduction|Le pilote n’a pas pu se connecter à la DLL qui a été spécifié pour la source de données de la traduction.|  
|IM010|Nom de source de données trop long|(DM)  *\*nom_serveur* dépasse SQL_MAX_DSN_LENGTH caractères.|  
|IM014|La source de données spécifié contient une incompatibilité d’architecture du pilote et une Application|Application de 32 bits (DM) utilise un DSN de connexion à un pilote 64 bits. ou vice versa.|  
|IM015|SQLConnect du pilote sur SQL_HANDLE_DBC_INFO_HANDLE a échoué|Si un pilote retourne SQL_ERROR, le Gestionnaire de pilotes retourne SQL_ERROR à l’application et la connexion échoue.<br /><br /> Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, consultez [développer la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
|S1118|Pilote ne prend pas en charge la notification asynchrone|Lorsque le pilote ne prend pas en charge la notification asynchrone, vous ne pouvez pas définir SQL_ATTR_ASYNC_DBC_EVENT ou SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="comments"></a>Commentaires  
 Pour plus d’informations sur la raison pour laquelle une application utilise **SQLConnect**, consultez [connexion avec SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md).  
  
 Le Gestionnaire de pilotes ne se connecte pas à un pilote jusqu'à ce que l’application appelle une fonction (**SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**) pour se connecter à la pilote. À ce stade, le Gestionnaire de pilotes fonctionne avec ses propres descripteurs et gère les informations de connexion. Lorsque l’application appelle une fonction de connexion, le Gestionnaire de pilotes vérifie si un pilote est actuellement connecté au spécifié *ConnectionHandle*:  
  
-   Si un pilote n’est pas connecté à, le Gestionnaire de pilote se connecte au pilote et des appels **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV, **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC, **SQLSetConnectAttr** (si l’application spécifiée des attributs de connexion) et la fonction de connexion dans le pilote. Le Gestionnaire de pilotes retourne SQLSTATE IM006 (chauffeur **SQLSetConnectOption** échec) et SQL_SUCCESS_WITH_INFO pour la fonction de connexion si le pilote a retourné une erreur pour **SQLSetConnectAttr**. Pour plus d’informations, consultez [connexion à une Source de données ou le pilote](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md).  
  
-   Si le pilote spécifié est déjà connecté à sur le *ConnectionHandle*, le Gestionnaire de pilotes appelle uniquement la fonction de la connexion dans le pilote. Dans ce cas, le pilote devez vous assurer que les attributs de toutes les connexions de la *ConnectionHandle* maintenir leurs paramètres actuels.  
  
-   Si un pilote différent est connecté à, le Gestionnaire de pilotes appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC, et, si aucun pilote n’est connecté dans cet environnement, il appelle ensuite **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV dans le pilote connecté et déconnecter ce pilote. Il effectue ensuite les mêmes opérations que quand un pilote n’est pas connecté à.  
  
 Ensuite, le pilote alloue des handles et initialise lui-même.  
  
 Lorsque l’application appelle **SQLDisconnect**, les appels du Gestionnaire de pilotes **SQLDisconnect** dans le pilote. Toutefois, il n’interrompt pas le pilote. Cela permet de conserver le pilote dans la mémoire pour les applications à plusieurs reprises connecter et déconnecter à partir d’une source de données. Lorsque l’application appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC, appelle le Gestionnaire de pilotes **SQLFreeHandle** avec un *HandleType*  de SQL_HANDLE_DBC, puis **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV dans le pilote, puis se déconnecte le pilote.  
  
 Une application ODBC peut établir plusieurs connexions.  
  
## <a name="driver-manager-guidelines"></a>Instructions de gestionnaire de pilotes  
 Le contenu de **nom_serveur* affectent le fonctionnement le Gestionnaire de pilotes et un pilote pour établir une connexion à une source de données.  
  
-   Si \* *nom_serveur* contient un nom de source de données valide, le Gestionnaire de pilotes localise la spécification de source de données correspondante dans les informations système et se connecte au pilote associé. Le Gestionnaire de pilotes transmet chaque **SQLConnect** argument au pilote.  
  
-   Si le nom de source de données est introuvable ou *nom_serveur* est un pointeur null, le Gestionnaire de pilotes localise la spécification de source de données par défaut et se connecte au pilote associé. Le Gestionnaire de pilotes transmet au pilote la *nom d’utilisateur* et *authentification* arguments tels quels et « DEFAULT » pour le *nom_serveur* argument.  
  
-   Si le *nom_serveur* argument est « DEFAULT », le Gestionnaire de pilotes localise la spécification de source de données par défaut et se connecte au pilote associé. Le Gestionnaire de pilotes transmet chaque **SQLConnect** argument au pilote.  
  
-   Si le nom de source de données est introuvable ou *nom_serveur* est un pointeur null et la valeur par défaut de spécification de source de données n’existe pas, le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE IM002 (source de données introuvable et nom sans valeur par défaut pilote spécifié).  
  
 Une fois qu’il est connecté à par le Gestionnaire de pilotes, un pilote peut localiser la spécification de source de données correspondante dans les informations système et utiliser des informations spécifiques au pilote de la spécification à son ensemble complet d’informations de connexion requises.  
  
 Si une bibliothèque de traduction par défaut est spécifiée dans les informations système pour la source de données, le pilote se connecte à ce dernier. Une bibliothèque de traduction différente peut être connectée à en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_LIB. Une option de traduction peut être spécifiée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_OPTION.  
  
 Si un pilote prend en charge **SQLConnect**, la section de mot clé driver des informations système pour le pilote doit contenir le **ConnectFunctions** mot clé par le premier caractère défini à « Y ».  
  
### <a name="connection-pooling"></a>Regroupement de connexions  
 Le regroupement de connexions permet à une application de réutiliser une connexion qui a déjà été créée. Lorsque le regroupement de connexions est activé et **SQLConnect** est appelée, le Gestionnaire de pilotes tente d’établir la connexion à l’aide d’une connexion qui fait partie d’un pool de connexions dans un environnement qui a été désigné pour le regroupement de connexions. Cet environnement est un environnement partagé qui est utilisé par toutes les applications qui utilisent les connexions dans le pool.  
  
 Le regroupement de connexions est activé avant l’environnement est alloué en appelant **SQLSetEnvAttr** à la valeur SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER (qui spécifie un pool par le pilote au maximum) ou SQL_CP_ONE_PER_HENV (qui spécifie un pool par environnement au maximum). **SQLSetEnvAttr** dans ce cas est appelé avec *EnvironmentHandle* la valeur null, ce qui rend l’attribut à un attribut au niveau du processus. Si SQL_ATTR_CONNECTION_POOLING est défini sur SQL_CP_OFF, le regroupement de connexions est désactivé.  
  
 Une fois que le regroupement de connexions a été activé, **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV est appelée pour allouer un environnement. L’environnement alloué par cet appel est un environnement partagé, car le regroupement de connexions a été activé. Toutefois, l’environnement qui sera utilisé n’est pas déterminée jusque **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC est appelée.  
  
 **SQLAllocHandle** avec un *HandleType* parle de SQL_HANDLE_DBC pour allouer une connexion. Le Gestionnaire de pilotes tente de trouver un environnement partagé existant qui correspond aux attributs d’environnement définies par l’application. Si aucun environnement n’existe, un est créé en tant qu’implicite *environnement partagé*. Si un environnement partagé correspondant est trouvé, le handle d’environnement est retourné à l’application et son décompte de références est incrémenté.  
  
 Toutefois, la connexion qui sera utilisée n’est pas déterminée jusque **SQLConnect** est appelée. À ce stade, le Gestionnaire de pilotes tente de trouver une connexion existante dans le pool de connexions qui correspond aux critères demandés par l’application. Ces critères incluent les options de connexion demandées dans l’appel à **SQLConnect** (les valeurs de la *nom_serveur*, *nom d’utilisateur*, et  *Authentification* mots clés) et des attributs de connexion définies depuis **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC a été appelée. Le Gestionnaire de pilotes vérifie ces critères que pour les mots clés de connexion correspondante et les attributs dans des connexions dans le pool. Si une correspondance est trouvée, la connexion dans le pool est utilisée. Si aucune correspondance n’est trouvée, une nouvelle connexion est créée.  
  
 Si l’attribut d’environnement SQL_ATTR_CP_MATCH est définie à SQL_CP_STRICT_MATCH, la correspondance doit être exacte pour une connexion dans le pool à utiliser. Si l’attribut d’environnement SQL_ATTR_CP_MATCH est définie à SQL_CP_RELAXED_MATCH, les options de la connexion dans l’appel à **SQLConnect** doivent correspondance, mais pas tous les attributs de connexion doit correspondre.  
  
 Les règles suivantes sont appliquées lorsqu’un attribut de connexion, tel que défini par l’application avant de **SQLConnect** est appelée, ne correspond pas à l’attribut de connexion de la connexion dans le pool :  
  
-   Si l’attribut de connexion doit être définie avant la connexion est établie :  
  
     Si SQL_ATTR_CP_MATCH est SQL_CP_STRICT_MATCH, SQL_ATTR_PACKET_SIZE dans la connexion regroupée doit être identique à l’attribut défini par l’application. Si SQL_CP_RELAXED_MATCH, les valeurs de SQL_ATTR_PACKET_SIZE peut être différent.  
  
     La valeur de SQL_ATTR_LOGIN_VALUE n’affecte pas la correspondance.  
  
-   Si l’attribut de connexion peut être défini avant ou après que la connexion est établie :  
  
     Si l’attribut de connexion n’a pas été définie par l’application, mais a été définie sur la connexion dans le pool, et qu’une valeur par défaut, l’attribut de connexion dans la connexion regroupée est rétabli à la valeur par défaut et une correspondance est déclarée. S’il n’existe aucune valeur par défaut, la connexion regroupée n’est pas considéré comme une correspondance.  
  
     Si l’attribut de connexion a été défini par l’application, mais n’a pas été définie sur la connexion dans le pool, l’attribut de connexion sur le pool est modifié à cet ensemble par l’application et une correspondance est déclarée.  
  
     Si l’attribut de connexion a été définie par l’application et a également été définie sur la connexion dans le pool, mais les valeurs sont différentes, la valeur de l’attribut de connexion de l’application est utilisée et une correspondance est déclarée.  
  
-   Si les valeurs des attributs de connexion spécifiques au pilote ne sont pas identiques et SQL_ATTR_CP_MATCH est défini sur SQL_CP_STRICT_MATCH, la connexion dans le pool n’est pas utilisée.  
  
 Lorsque l’application appelle **SQLDisconnect** pour vous déconnecter, la connexion est retournée au pool de connexions et est disponible pour une réutilisation.  
  
### <a name="optimizing-connection-pooling-performance"></a>Optimisation des performances de regroupement de connexions  
 Lorsque les transactions distribuées sont impliquées, il est possible d’optimiser les performances de regroupement à l’aide de connexions **SQL_DTC_TRANSITION_COST**, qui est un masque de bits SQLUINTEGER. Les transitions auquel sont les transitions de l’attribut de connexion SQL_ATTR_ENLIST_IN_DTC allant de la valeur 0 à différent de zéro et vice versa. Il s’agit d’une connexion allant ne pas inscrite dans une transaction distribuée soit inscrite dans une transaction distribuée et vice versa. Selon la façon dont le pilote a implémenté inscription (définition connexion de l’attribut SQL_ATTR_ENLIST_IN_DTC), ces transitions peuvent être coûteuses et doivent donc être évitées pour de meilleures performances.  
  
 La valeur retournée par le pilote contient n’importe quelle combinaison des bits suivants :  
  
-   **SQL_DTC_ENLIST_EXPENSIVE**, lorsque défini, implique le zéro transition différente de zéro est beaucoup plus onéreux qu’une transition à partir de zéro à une autre valeur différente de zéro (l’inscription d’une connexion précédemment inscrite dans sa transaction suivante).  
  
-   **SQL_DTC_UNENLIST_EXPENSIVE**, lorsque défini, implique la valeur différente de zéro à zéro transition est beaucoup plus onéreuse qu’à l’aide d’une connexion dont l’attribut SQL_ATTR_ENLIST_IN_DTC est déjà défini sur zéro.  
  
 Il existe de performances par rapport aux compromis entre l’utilisation de connexion. Si un pilote indique qu’un ou plusieurs de ces transitions sont coûteuses, pooler de connexion du Gestionnaire de pilotes répond à ceci en conservant des connexions plus dans le pool. Certaines des connexions dans le pool sont préférables pour une utilisation de non transactionnelles, et certaines sont par défaut pour une utilisation transactionnelle. Toutefois, si le pilote indique que ces transitions ne soient pas onéreux, moins connexions peuvent être utilisées, peut-être alternant entre non transactionnel et l’utilisation transactionnelle.  
  
 Les pilotes qui ne prennent pas en charge SQL_ATTR_ENLIST_IN_DTC n’avez pas besoin de prendre en charge SQL_DTC_TRANSITION_COST. Pour les pilotes qui prennent en charge SQL_ATTR_ENLIST_IN_DTC mais pas SQL_DTC_TRANSITION_COST, il est supposé que les transitions ne sont pas coûteuses, comme si le pilote a retourné 0 (aucun jeu de bits) pour cette valeur.  
  
 Bien que SQL_DTC_TRANSITION_COST a été introduit dans ODBC 3.5, un ODBC 2. *x* pilote peut également prendre en charge il, car le Gestionnaire de pilotes interrogera ces informations quel que soit la version du pilote.  
  
### <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application alloue de l’environnement et connexion handles. Ensuite, il se connecte à la source de données SalesOrders avec l’ID JohnS d’utilisateur et le mot de passe Sesame et traite les données. Lorsqu’il a terminé le traitement des données, il se déconnecte de la source de données et libère les handles.  
  
```cpp  
// SQLConnect_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR * OutConnStr = (SQLCHAR * )malloc(255);  
   SQLSMALLINT * OutConnStrLen = (SQLSMALLINT *)malloc(255);  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLCHAR*) "NorthWind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
### <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Allocation d’un handle|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Découverte et l’énumération des valeurs requises pour se connecter à une source de données|[SQLBrowseConnect, fonction](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Déconnexion d’une source de données|[SQLDisconnect, fonction](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Connexion à une source de données à l’aide d’une boîte de dialogue ou de chaîne de connexion|[SQLDriverConnect, fonction](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Retourner le paramètre d’un attribut de connexion|[SQLGetConnectAttr, fonction](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définition d’un attribut de connexion|[SQLSetConnectAttr, fonction](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
