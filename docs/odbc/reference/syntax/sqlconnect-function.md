---
title: Fonction SQLConnect (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab0a31845efeb484c554a9c9cf1afeaeab1a8bea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301215"
---
# <a name="sqlconnect-function"></a>Fonction SQLConnect
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLConnect** établit des connexions à un conducteur et à une source de données. La connexion gère le stockage des références de toutes les informations sur la connexion à la source de données, y compris l’état, l’état de transaction et les informations d’erreur.  
  
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
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *Servername*  
 [Entrée] Nom de source de données. Les données peuvent être localisées sur le même ordinateur que le programme, ou sur un autre ordinateur quelque part sur un réseau. Pour plus d’informations sur la façon dont une application choisit une source de données, voir [Choisir une source de données ou un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Entrée] Longueur de*ServerName* en caractères.  
  
 *nom d'utilisateur*  
 [Entrée] Identifiant utilisateur.  
  
 *NomLength2*  
 [Entrée] Longueur de*l’UserName* en caractères.  
  
 *Authentification*  
 [Entrée] Chaîne d’authentification (généralement le mot de passe).  
  
 *NomLength3*  
 [Entrée] Longueur de*l’authentification* en caractères.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLConnect** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et une *poignée* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLConnect** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option modifiée|Le conducteur n’a pas supporté la valeur spécifiée de *l’argument ValuePtr* dans **SQLSetConnectAttr** et a remplacé une valeur similaire. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08001|Client incapable d’établir la connexion|Le conducteur n’a pas été en mesure d’établir une connexion avec la source de données.|  
|08002|Nom de connexion en cours d’utilisation|(DM) Le *ConnectionHandle* spécifié avait déjà été utilisé pour établir une connexion avec une source de données, et la connexion était toujours ouverte ou l’utilisateur naviguait pour une connexion.|  
|08004|Server a rejeté la connexion|La source de données a rejeté l’établissement de la connexion pour des raisons définies par la mise en œuvre.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur tentait de se connecter a échoué avant que la fonction ne termine le traitement.|  
|28000|Spécifications d’autorisation invalides|La valeur spécifiée pour l’argument *UserName* ou la valeur spécifiée pour l’argument *Authentification* violé les restrictions définies par la source de données.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|(DM) Le gestionnaire de conducteur n’a pas été en mesure d’allouer la mémoire requise pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction **SQLConnect** a été appelée, et avant qu’elle ait terminé l’exécution, [SQLCancelHandle Function](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*, puis la fonction **SQLConnect** a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> Ou, la fonction **SQLConnect** a été appelée, et avant qu’il ne termine l’exécution, **SQLCancelHandle** a été appelé sur le *ConnectionHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *ConnectionHandle* et était toujours en exécution lorsque cette fonction a été appelée.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *NameLength1*, *NameLength2*, ou *NameLength3* était inférieure à 0 mais pas égale à SQL_NTS.<br /><br /> (DM) La valeur spécifiée pour l’argument *NameLength1* a dépassé la durée maximale d’un nom de source de données.|  
|HYT00|Délai expiré|La période de délai de requête a expiré avant que la connexion à la source de données ne soit terminée. La période de délai d’attente est fixée par **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HY114|Le conducteur ne prend pas en charge l’exécution de la fonction asynchrone de niveau de connexion|(DM) L’application a activé l’opération asynchrone sur la poignée de connexion avant de faire la connexion. Toutefois, le conducteur ne prend pas en charge les opérations asynchrones sur la poignée de connexion.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur spécifié par le nom de source de données ne prend pas en charge la fonction.|  
|IM002|Source de données non trouvée et aucun conducteur par défaut spécifié|(DM) Le nom de source de données spécifié dans l’argument *ServerName* n’a pas été trouvé dans les informations du système, ni il n’y avait de spécification de conducteur par défaut.|  
|IM003|Le conducteur spécifié ne pouvait pas être connecté à|(DM) Le conducteur figurant dans les spécifications de source de données dans les informations du système n’a pas été trouvé ou n’a pas pu être connecté à pour une autre raison.|  
|IM004|Le conducteur SQLAllocHandle sur SQL_HANDLE_ENV a échoué|(DM) Pendant **SQLConnect**, le gestionnaire de conducteur a appelé la fonction **SQLAllocHandle** du conducteur avec un *HandleType* de SQL_HANDLE_ENV et le conducteur a retourné une erreur.|  
|IM005|Le conducteur SQLAllocHandle sur SQL_HANDLE_DBC a échoué|(DM) Pendant **SQLConnect**, le gestionnaire de conducteur a appelé la fonction **SQLAllocHandle** du conducteur avec un *HandleType* de SQL_HANDLE_DBC et le conducteur a retourné une erreur.|  
|IM006|Le conducteur SQLSetConnectAttr a échoué|Pendant **SQLConnect**, le gestionnaire de conducteur a appelé la fonction **SQLSetConnectAttr** du conducteur et le conducteur a retourné une erreur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|IM009|Impossible de se connecter à la traduction DLL|Le conducteur n’a pas été en mesure de se connecter à la traduction DLL qui a été spécifiée pour la source de données.|  
|IM010|Nom source de données trop long|(DM) * \*ServerName* était plus long que SQL_MAX_DSN_LENGTH caractères.|  
|IM014|Le DSN spécifié contient un décalage architectural entre le conducteur et l’application|(DM) L’application 32 bits utilise une connexion DSN à un conducteur 64 bits; ou vice versa.|  
|IM015|SQLConnect du conducteur sur SQL_HANDLE_DBC_INFO_HANDLE échoué|Si un conducteur retourne SQL_ERROR, le gestionnaire de conducteur retournera SQL_ERROR à l’application et la connexion échouera.<br /><br /> Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, voir [Developing Connection-Pool Awareness in an ODBC Driver](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
|S1118|Le conducteur ne prend pas en charge la notification asynchrone|Lorsque le conducteur ne prend pas en charge la notification asynchrone, vous ne pouvez pas définir SQL_ATTR_ASYNC_DBC_EVENT ou SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="comments"></a>Commentaires  
 Pour plus d’informations sur les raisons pour lesquelles une application utilise **SQLConnect**, voir [Connecting avec SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md).  
  
 Le gestionnaire de conducteur ne se connecte pas à un conducteur jusqu’à ce que l’application appelle une fonction (**SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**) pour se connecter au conducteur. Jusque-là, le Driver Manager travaille avec ses propres poignées et gère les informations de connexion. Lorsque l’application appelle une fonction de connexion, le Gestionnaire de conducteur vérifie si un pilote est actuellement connecté à la *Connexion*spécifiée :  
  
-   Si un conducteur n’est pas connecté, le gestionnaire de conducteur se connecte au conducteur et appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV, **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC, **SQLSetConnectAttr** (si l’application spécifié attributs de connexion), et la fonction de connexion dans le conducteur. Le gestionnaire de conducteur retourne SQLSTATE IM006 (Driver’s **SQLSetConnectOption** a échoué) et SQL_SUCCESS_WITH_INFO pour la fonction de connexion si le conducteur a retourné une erreur pour **SQLSetConnectAttr**. Pour plus d’informations, voir [Connecting to a Data Source or Driver](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md).  
  
-   Si le pilote spécifié est déjà connecté à sur le *ConnectionHandle*, le Gestionnaire de conducteur n’appelle que la fonction de connexion dans le conducteur. Dans ce cas, le conducteur doit s’assurer que tous les attributs de connexion pour le *ConnectionHandle* maintiennent leurs paramètres actuels.  
  
-   Si un autre conducteur est connecté à, le gestionnaire de conducteur appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC, et puis, si aucun autre conducteur n’est connecté à cet environnement, il appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV dans le conducteur connecté, puis déconnecte ce conducteur. Il effectue ensuite les mêmes opérations que lorsqu’un conducteur n’est pas connecté.  
  
 Le conducteur alloue ensuite les poignées et les initialisations.  
  
 Lorsque l’application appelle **SQLDisconnect**, le gestionnaire de conducteur appelle **SQLDisconnect** dans le conducteur. Cependant, il ne déconnecte pas le conducteur. Cela maintient le pilote en mémoire pour les applications qui se connectent à plusieurs reprises à une source de données et se déconnectent. Lorsque l’application appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC, le gestionnaire de conducteur appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC puis **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV dans le conducteur, puis débranche le conducteur.  
  
 Une application ODBC peut établir plus d’une connexion.  
  
## <a name="driver-manager-guidelines"></a>Lignes directrices sur le gestionnaire de conducteur  
 Le contenu de*l’entreprise ServerName influe* sur la façon dont le Gestionnaire de conducteur et un conducteur travaillent ensemble pour établir une connexion à une source de données.  
  
-   Si \* *ServerName* contient un nom de source de données valide, le gestionnaire de pilote localise les spécifications de source de données correspondantes dans les informations du système et se connecte au pilote associé. Le gestionnaire de conducteur transmet chaque argument **SQLConnect** au conducteur.  
  
-   Si le nom de source de données ne peut pas être trouvé ou *que ServerName* est un pointeur nul, le gestionnaire de pilote localise les spécifications de source de données par défaut et se connecte au pilote associé. Le Driver Manager transmet au conducteur les arguments *UserName* et *Authentication* non modifiés, et "DEFAULT" pour l’argument *ServerName.*  
  
-   Si l’argument *serverName* est « DEFAULT », le gestionnaire de pilote localise les spécifications de source de données par défaut et se connecte au pilote associé. Le gestionnaire de conducteur transmet chaque argument **SQLConnect** au conducteur.  
  
-   Si le nom de la source de données ne peut pas être trouvé ou *que ServerName* est un pointeur nul, et que la spécification de source de données par défaut n’existe pas, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE IM002 (nom source de données non trouvé et aucun pilote par défaut spécifié).  
  
 Une fois qu’il est connecté par le Gestionnaire de conducteur, un conducteur peut localiser ses spécifications de source de données correspondantes dans les informations du système et utiliser des informations spécifiques au conducteur à partir des spécifications pour compléter son ensemble d’informations de connexion requises.  
  
 Si une bibliothèque de traduction par défaut est spécifiée dans les informations système pour la source de données, le pilote s’y connecte. Une bibliothèque de traduction différente peut être connectée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_LIB. Une option de traduction peut être spécifiée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_OPTION.  
  
 Si un conducteur prend en charge **SQLConnect**, la section mot-clé du conducteur des informations du système pour le conducteur doit contenir le mot clé **ConnectFunctions** avec le premier personnage réglé sur "Y".  
  
### <a name="connection-pooling"></a>Regroupement de connexions  
 La mise en commun des connexions permet à une application de réutiliser une connexion qui a déjà été créée. Lorsque la mise en commun des connexions est activée et **que SQLConnect** est appelée, le gestionnaire de conducteur tente de faire la connexion à l’aide d’une connexion qui fait partie d’un pool de connexions dans un environnement qui a été désigné pour la mise en commun des connexions. Cet environnement est un environnement partagé qui est utilisé par toutes les applications qui utilisent les connexions dans la piscine.  
  
 La mise en commun des connexions est activée avant que l’environnement ne soit alloué en appelant **SQLSetEnvAttr** pour régler SQL_ATTR_CONNECTION_POOLING à SQL_CP_ONE_PER_DRIVER (ce qui spécifie un maximum d’une piscine par conducteur) ou SQL_CP_ONE_PER_HENV (ce qui spécifie un maximum d’une piscine par environnement). **SQLSetEnvAttr** dans ce cas est appelé avec *EnvironmentHandle* réglé à null, ce qui rend l’attribut un attribut de niveau de processus. Si SQL_ATTR_CONNECTION_POOLING est réglée pour SQL_CP_OFF, la mise en commun des connexions est désactivée.  
  
 Une fois la mise en commun des connexions activée, **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV est appelé à allouer un environnement. L’environnement alloué par cet appel est un environnement partagé car la mise en commun des connexions a été activée. Cependant, l’environnement qui sera utilisé n’est pas déterminé jusqu’à ce que **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC est appelé.  
  
 **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC est appelé à allouer une connexion. Le Driver Manager tente de trouver un environnement partagé existant qui correspond aux attributs de l’environnement définis par l’application. Si un tel environnement n’existe pas, on est créé comme un *environnement implicite partagé.* Si un environnement partagé assorti est trouvé, la poignée de l’environnement est retournée à l’application et son nombre de références est incrémenté.  
  
 Toutefois, la connexion qui sera utilisée n’est pas déterminée jusqu’à ce que **SQLConnect** soit appelé. À ce moment-là, le gestionnaire de conducteur tente de trouver une connexion existante dans le pool de connexion qui correspond aux critères demandés par la demande. Ces critères comprennent les options de connexion demandées dans l’appel à **SQLConnect** (les valeurs du *ServerName*, *UserName*, et *Authentication* mots clés) et tous les attributs de connexion définis depuis **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC a été appelé. Le Gestionnaire de pilote vérifie ces critères par rapport aux mots clés de connexion correspondants et attribue dans les connexions dans le pool. Si une correspondance est trouvée, la connexion dans la piscine est utilisée. Si aucune correspondance n’est trouvée, une nouvelle connexion est créée.  
  
 Si l’attribut SQL_ATTR_CP_MATCH environnement est réglé pour SQL_CP_STRICT_MATCH, le match doit être exact pour une connexion dans la piscine à utiliser. Si l’attribut SQL_ATTR_CP_MATCH environnement est réglé pour SQL_CP_RELAXED_MATCH, les options de connexion dans l’appel à **SQLConnect** doivent correspondre, mais pas tous les attributs de connexion doivent correspondre.  
  
 Les règles suivantes sont appliquées lorsqu’un attribut de connexion, tel qu’défini par l’application avant **l’appel de SQLConnect,** ne correspond pas à l’attribut de connexion de la connexion dans le pool :  
  
-   Si l’attribut de connexion doit être défini avant que la connexion ne soit effectuée :  
  
     Si SQL_ATTR_CP_MATCH est SQL_CP_STRICT_MATCH, SQL_ATTR_PACKET_SIZE dans la connexion commune doit être identique à l’attribut défini par l’application. Si SQL_CP_RELAXED_MATCH, les valeurs de SQL_ATTR_PACKET_SIZE peuvent être différentes.  
  
     La valeur de SQL_ATTR_LOGIN_VALUE n’affecte pas le match.  
  
-   Si l’attribut de connexion peut être défini avant ou après la connexion :  
  
     Si l’attribut de connexion n’a pas été défini par l’application mais a été défini sur la connexion dans le pool, et il y a un défaut, l’attribut de connexion dans la connexion mise en commun est remis à la valeur par défaut et une correspondance est déclarée. S’il n’y a pas de défaut, la connexion mise en commun n’est pas considérée comme une correspondance.  
  
     Si l’attribut de connexion a été défini par l’application mais n’a pas été défini sur la connexion dans le pool, l’attribut de connexion sur le pool est modifié à cet ensemble par l’application et une correspondance est déclarée.  
  
     Si l’attribut de connexion a été défini par l’application, et a également été défini sur la connexion dans le pool, mais les valeurs sont différentes, la valeur de l’attribut de connexion de l’application est utilisée et une correspondance est déclarée.  
  
-   Si les valeurs des attributs de connexion spécifiques au conducteur ne sont pas identiques et SQL_ATTR_CP_MATCH est réglée pour SQL_CP_STRICT_MATCH, la connexion dans le pool n’est pas utilisée.  
  
 Lorsque l’application appelle **SQLDisconnect** à se déconnecter, la connexion est retournée au pool de connexion et est disponible pour la réutilisation.  
  
### <a name="optimizing-connection-pooling-performance"></a>Optimiser les performances de mise en commun des connexions  
 Lorsque des transactions distribuées sont en cause, il est possible d’optimiser les performances de mise en commun des **connexions**en utilisant SQL_DTC_TRANSITION_COST , qui est un bitmask SQLUINTEGER. Les transitions mentionnées sont les transitions de l’attribut de connexion SQL_ATTR_ENLIST_IN_DTC passant de la valeur 0 à non zéro, et vice versa. Il s’agit d’une connexion qui passe de non-enrôlé dans une transaction distribuée à enrôlée dans une transaction distribuée, et vice versa. Selon la façon dont le conducteur a mis en place l’enrôlement (réglage de l’attribut de connexion SQL_ATTR_ENLIST_IN_DTC), ces transitions peuvent être coûteuses et doivent donc être évitées pour les meilleures performances.  
  
 La valeur retournée par le conducteur contient n’importe quelle combinaison des bits suivants :  
  
-   **SQL_DTC_ENLIST_EXPENSIVE**, lorsqu’elle est définie, implique que la transition zéro à non zéro est beaucoup plus coûteuse qu’une transition de nonzero à une autre valeur non zéro (enrôlant une connexion précédemment enrôlée dans sa prochaine transaction).  
  
-   **SQL_DTC_UNENLIST_EXPENSIVE,** lorsqu’il est réglé, implique que la transition non zéro est beaucoup plus coûteuse que l’utilisation d’une connexion dont l’attribut SQL_ATTR_ENLIST_IN_DTC est déjà réglé à zéro.  
  
 Il y a un compromis d’utilisation de performance par rapport à l’utilisation de connexion. Si un conducteur indique qu’une ou plusieurs de ces transitions sont coûteuses, le pooler de connexion du gestionnaire de conducteur y répond en conservant plus de connexions dans la piscine. Certaines des connexions dans le pool sont préférées pour une utilisation non comportementale, et certaines sont préférées pour une utilisation transactionnelle. Toutefois, si le conducteur indique que ces transitions ne sont pas coûteuses, moins de connexions peuvent être utilisées, peut-être en alternance entre l’utilisation nontransactionale et transactionnelle.  
  
 Les conducteurs qui ne prennent pas en charge SQL_ATTR_ENLIST_IN_DTC n’ont pas besoin de soutenir SQL_DTC_TRANSITION_COST. Pour les conducteurs qui prennent en charge SQL_ATTR_ENLIST_IN_DTC mais pas SQL_DTC_TRANSITION_COST, on suppose que les transitions ne sont pas coûteuses, comme si le conducteur avait retourné 0 (pas de bits) pour cette valeur.  
  
 Bien que SQL_DTC_TRANSITION_COST ait été introduit dans ODBC 3.5, un ODBC 2. *x* le conducteur peut également le prendre en charge parce que le gestionnaire de pilote va interroger ces informations indépendamment de la version du conducteur.  
  
### <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application alloue des poignées d’environnement et de connexion. Il se connecte ensuite à la source de données SalesOrders avec l’utilisateur ID JohnS et le mot de passe Sésame et traite les données. Lorsqu’il a terminé le traitement des données, il se déconnecte de la source de données et libère les poignées.  
  
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
|Répartition d’une poignée|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Découvrir et énumérer les valeurs requises pour se connecter à une source de données|[Fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Déconnecter d’une source de données|[SQLDisconnect, fonction](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Connexion à une source de données à l’aide d’une chaîne de connexion ou d’une boîte de dialogue|[Fonction SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Retour du paramètre d’un attribut de connexion|[Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définir un attribut de connexion|[Fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
