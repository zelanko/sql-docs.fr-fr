---
title: Fonction SQLBrowseConnect (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBrowseConnect
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBrowseConnect
helpviewer_keywords:
- SQLBrowseConnect function [ODBC]
ms.assetid: b7f1be66-e6c7-4790-88ec-62b7662103c0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607b0d764a694098a23111e9d7f4ce9755ea982d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301339"
---
# <a name="sqlbrowseconnect-function"></a>Fonction SQLBrowseConnect
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLBrowseConnect** prend en charge une méthode itérative de découverte et d’énumération des attributs et des valeurs d’attribut nécessaires pour se connecter à une source de données. Chaque appel à **SQLBrowseConnect renvoie** des niveaux successifs d’attributs et de valeurs d’attribut. Lorsque tous les niveaux ont été énumérés, une connexion à la source de données est terminée et une chaîne de connexion complète est retournée par **SQLBrowseConnect**. Un code de retour de SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO indique que toutes les informations de connexion ont été spécifiées et que l’application est maintenant connectée à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLBrowseConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *InConnectionString*  
 [Entrée] Parcourir la chaîne de connexion de demande (voir "*InConnectionString* Argument " dans "Commentaires").  
  
 *StringLength1 (en)*  
 [Entrée] Longueur de *'InConnectionString* en caractères.  
  
 *OutConnectionString (en)*  
 [Sortie] Pointeur vers un tampon de caractère dans lequel retourner la chaîne de connexion de résultat de navigation (voir «*OutConnectionString* Argument » dans « Commentaires »).  
  
 Si *OutConnectionString* est NULL, *StringLength2Ptr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *OutConnectionString*.  
  
 *BufferLength*  
 [Entrée] Longueur, en caractères, du tampon*OutConnectionString.*  
  
 *StringLength2Ptr*  
 [Sortie] Le nombre total de caractères (à l’exclusion de la résiliation nulle) disponibles pour revenir dans \* *OutConnectionString*. Si le nombre de caractères disponibles pour revenir est supérieur ou \*égal à *BufferLength*, la chaîne de connexion dans *OutConnectionString* est tronquée à *BufferLength* moins la longueur d’un caractère de désinsaison.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLBrowseConnect** retourne SQL_ERROR, SQL_SUCCESS_WITH_INFO ou SQL_NEED_DATA, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée de ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLBrowseConnect** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *OutConnectionString* n’était pas assez grand pour retourner la chaîne de connexion de résultat de navigation entière, de sorte que la chaîne a été tronquée. Le tampon*stringLength2Ptr* contient la longueur de la chaîne de connexion de résultat de navigation fausse. (Les retours de fonction SQL_NEED_DATA.)|  
|01S00|Attribut de chaîne de connexion invalide|Un mot clé d’attribut invalide a été spécifié dans la chaîne de connexion de demande de navigation (*InConnectionString*). (Les retours de fonction SQL_NEED_DATA.)<br /><br /> Un mot clé d’attribut a été spécifié dans la chaîne de connexion de demande de navigation (*InConnectionString*) qui ne s’applique pas au niveau de connexion actuel. (Les retours de fonction SQL_NEED_DATA.)|  
|01S02|Valeur modifiée|Le conducteur n’a pas supporté la valeur spécifiée de *l’argument ValuePtr* dans **SQLSetConnectAttr** et a remplacé une valeur similaire. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08001|Client incapable d’établir la connexion|Le conducteur n’a pas été en mesure d’établir une connexion avec la source de données.|  
|08002|Nom de connexion en cours d’utilisation|(DM) La connexion spécifiée avait déjà été utilisée pour établir une connexion avec une source de données, et la connexion était ouverte.|  
|08004|Server a rejeté la connexion|La source de données a rejeté l’établissement de la connexion pour des raisons définies par la mise en œuvre.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur tentait de se connecter a échoué avant que la fonction ne termine le traitement.|  
|28000|Spécifications d’autorisation invalides|Soit l’identifiant de l’utilisateur ou la chaîne d’autorisation ou les deux, comme spécifié dans la chaîne de connexion de demande de navigation (*InConnectionString*), violé les restrictions définies par la source de données.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|(DM) Le gestionnaire de conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.<br /><br /> Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Une opération asynchrone a été annulée en appelant [SQLCancelHandle Function](../../../odbc/reference/syntax/sqlcancelhandle-function.md). Puis, la fonction originale a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> Une opération a été annulée en appelant **SQLCancelHandle** sur le *ConnectionHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *ConnectionHandle* et était toujours en exécution lorsque cette fonction a été appelée.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *StringLength1* était inférieure à 0 et n’était pas égale à SQL_NTS.<br /><br /> (DM) La valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.|  
|HY114|Le conducteur ne prend pas en charge l’exécution de la fonction asynchrone de niveau de connexion|(DM) L’application a activé l’opération asynchrone sur la poignée de connexion avant de faire la connexion. Cependant, le conducteur ne prend pas en charge l’opération asynchrone sur la poignée de connexion.|  
|HYT00|Délai expiré|La période de délai de connexion a expiré avant que la connexion à la source de données ne soit terminée. La période de délai d’attente est fixée par **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur correspondant au nom spécifié de source de données ne prend pas en charge la fonction.|  
|IM002|Source de données non trouvée et aucun conducteur par défaut spécifié|(DM) Le nom de source de données spécifié dans la chaîne de connexion de demande de navigation (*InConnectionString*) n’a pas été trouvé dans les informations du système, ni dans les spécifications du conducteur par défaut.<br /><br /> (DM) Les informations relatives aux données de l’ODBC et par défaut du conducteur n’ont pas pu être trouvées dans les informations du système.|  
|IM003|Le conducteur spécifié n’a pas pu être chargé|(DM) Le conducteur figurant dans les spécifications de source de données dans les informations du système ou spécifié par le mot clé **DRIVER** n’a pas été trouvé ou n’a pas pu être chargé pour une autre raison.|  
|IM004|Le **conducteur SQLAllocHandle** sur SQL_HANDLE _ENV a échoué|(DM) Pendant **SQLBrowseConnect**, le gestionnaire de conducteur a appelé la fonction **SQLAllocHandle** du conducteur avec un *HandleType* de SQL_HANDLE_ENV et le conducteur a retourné une erreur.|  
|IM005|Le **conducteur SQLAllocHandle** sur SQL_HANDLE_DBC a échoué|(DM) Pendant **SQLBrowseConnect**, le gestionnaire de conducteur a appelé la fonction **SQLAllocHandle** du conducteur avec un *HandleType* de SQL_HANDLE_DBC et le conducteur a retourné une erreur.|  
|IM006|Le conducteur **SQLSetConnectAttr** a échoué|(DM) Pendant **SQLBrowseConnect**, le gestionnaire de conducteur a appelé la fonction **SQLSetConnectAttr** du conducteur et le conducteur a retourné une erreur.|  
|IM009|Incapable de charger la traduction DLL|Le conducteur n’a pas été en mesure de charger la traduction DLL qui a été spécifiée pour la source de données ou pour la connexion.|  
|IM010|Nom source de données trop long|(DM) La valeur d’attribut pour le mot clé DSN était plus longue que SQL_MAX_DSN_LENGTH caractères.|  
|IM011|Nom du conducteur trop long|(DM) La valeur d’attribut pour le mot clé DRIVER était supérieure à 255 caractères.|  
|IM012|ERREUR de syntaxe mot-clé DRIVER|(DM) La paire de mots-clés pour le mot clé DRIVER contenait une erreur de syntaxe.|  
|IM014|Le DSN spécifié contient un décalage architectural entre le conducteur et l’application|(DM) L’application 32 bits utilise une connexion DSN à un conducteur 64 bits; ou vice versa.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
|S1118|Le conducteur ne prend pas en charge la notification asynchrone|Lorsque le conducteur ne prend pas en charge la notification asynchrone, vous ne pouvez pas définir SQL_ATTR_ASYNC_DBC_EVENT ou SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="inconnectionstring-argument"></a>InConnectionString Argument  
 Une chaîne de connexion de demande de navigation a la syntaxe suivante :  
  
 *connexion-chaîne* ::'attribut`;`[] &#124; *attribut* `;` *connection-string*; *attribute*<br>
 *attribut* ::' *attribut-mot-clé*`=`*attribut-valeur* &#124; `DRIVER=``{`[ ]*attribut-valeur*[`}`] ]<br>
 *attribut-mot-clé* `DSN` :: &#124; `UID` &#124; `PWD` &#124; *conducteur-défini-attribut-mot-mot*<br>
 *attribut-valeur* ::md *caractère-corde*<br>
 *moteur-défini-attribut-mot-mot* ::' *identifiant*<br>
  
 où *la chaîne de caractères* a zéro ou plus de caractères; *l’identifiant* a un ou plusieurs caractères; *attribut-mot-clé* n’est pas sensible aux cas; *la valeur d’attribut* peut être sensible aux cas; et la valeur du mot clé **DSN** ne se compose pas uniquement de blancs. En raison de la grammaire de fichier de connexion et de initialisation, mots clés et valeurs d’attribut qui contiennent les caractères **[]{}(),;? Il \*** faut éviter. En raison de la grammaire dans les informations du système, les\\mots clés et les noms de source de données ne peuvent pas contenir le caractère de barre oblique inverse ( ) . Pour un ODBC 2. *x* pilote, accolades sont nécessaires autour de la valeur d’attribut pour le mot clé DRIVER.  
  
 Si des mots clés sont répétés dans la chaîne de connexion de demande de navigation, le pilote utilise la valeur associée à la première occurrence du mot clé. Si les mots clés **DSN** et **DRIVER** sont inclus dans la même chaîne de connexion de demande de navigation, le Gestionnaire de conducteur et le pilote utilisent le mot clé qui apparaît en premier.  
  
 Pour plus d’informations sur la façon dont une application choisit une source de données ou un pilote, voir [Choisir une source de données ou un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
## <a name="outconnectionstring-argument"></a>OutConnectionString Argument  
 La chaîne de connexion de résultat de navigation est une liste d’attributs de connexion. Un attribut de connexion se compose d’un mot clé d’attribut et d’une valeur d’attribut correspondante. La chaîne de connexion de résultat de navigation a la syntaxe suivante :  
  
 *connexion-chaîne* ::'attribut`;`[] &#124; *attribut* `;` *connection-string* *attribute*<br>
 *attribut* ::'`*`[ ]*attribut-mot-clé*`=`*attribut-valeur*<br>
 *attribut-mot-clé* :: *ODBC-attribut-mot-clé* &#124; *conducteur défini-attribut-mot-mot*<br>
 *ODBC-attribut-mot-clé* `UID` - &#124; `PWD``:`*'[localisé-identifiant]* *conducteur-défini-attribut-mot::'identifiant* *identifier*`:`*[localisé-identifiant*] *attribut-valeur* ::'attribut-valeur-liste `{` *attribute-value-list* `}` &#124; `?` (Les accolades sont littérales; ils sont retournés par le conducteur.)<br>
 *attribut-value-list* ::md *caractère-corde* `:`[*chaîne de caractère localisé*] &#124; *caractère-corde* [`:`*chaîne de caractère localisé*] `,` *attribut-valeur-liste*<br>
  
 où la *chaîne* de *caractères* et la chaîne de caractère localisé ont zéro caractère ou plus; *l’identifiant* et *l’identification localisée* ont un ou plusieurs caractères; *attribut-mot-clé* n’est pas sensible aux cas; et *la valeur d’attribut* peut être sensible aux cas. En raison de la grammaire des fichiers de connexion et d’initialisation, des mots clés, des identificateurs localisés et des valeurs d’attribut qui contiennent les caractères **[]{}(),;? Il \*** faut éviter. En raison de la grammaire dans les informations du système, les\\mots clés et les noms de source de données ne peuvent pas contenir le caractère de barre oblique inverse ( ) .  
  
 La syntaxe de chaîne de connexion de résultat de navigation est utilisée selon les règles sémantiques suivantes :  
  
-   \*Si un astérisque ( ) précède un *mot-clé d’attribut,* *l’attribut* est facultatif et peut être omis dans le prochain appel à **SQLBrowseConnect**.  
  
-   Les mots-clés **d’attribut UID** et **PWD** ont la même signification que définie dans **SQLDriverConnect**.  
  
-   Un *mot clé défini par* le conducteur désigne le type d’attribut pour lequel une valeur d’attribut peut être fournie. Par exemple, il peut s’agir **de SERVER**, **DATABASE**, **HOST**, ou **DBMS**.  
  
-   *Les mots clés-attributs ODBC-attribut* et *les mots-clés définis par* le conducteur comprennent une version localisée ou conviviale du mot clé. Cela peut être utilisé par les applications comme une étiquette dans une boîte de dialogue. Cependant, **UID**, **PWD**, ou *l’identifiant* seul doit être utilisé lors de la transmission d’une chaîne de demande de navigation au conducteur.  
  
-   La*liste d’attributs-valeur*est un recensement des valeurs réelles valides pour le *mot-clé d’attribut*correspondant. Notez que les{}accolades ( ) n’indiquent pas une liste de choix; ils sont retournés par le conducteur. Par exemple, il peut s’agir d’une liste de noms de serveurs ou d’une liste de noms de bases de données.  
  
-   Si la *valeur d’attribut* est un point d’interrogation unique (?), une seule valeur correspond à *l’attribut-mot-clé*. Par exemple, UID-JohnS; PWD-Sésame.  
  
-   Chaque appel à **SQLBrowseConnect** ne renvoie que les informations requises pour satisfaire au niveau suivant du processus de connexion. Le conducteur associe les informations d’état à la poignée de connexion afin que le contexte puisse toujours être déterminé à chaque appel.  
  
## <a name="using-sqlbrowseconnect"></a>Utilisation de SQLBrowseConnect  
 **SQLBrowseConnect** nécessite une connexion allouée. Le gestionnaire de conducteur charge le conducteur qui a été spécifié dans ou qui correspond au nom de source de données spécifié dans la chaîne initiale de connexion de demande de navigation; pour plus d’informations sur le moment où cela se produit, voir la section "Commentaires" dans [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md). Le conducteur peut établir une connexion avec la source de données pendant le processus de navigation. Si **SQLBrowseConnect** revient SQL_ERROR, les connexions en circulation sont terminées et la connexion est retournée à un état non relié.  
  
> [!NOTE]  
>  **SQLBrowseConnect** ne prend pas en charge la mise en commun des connexions. Si **SQLBrowseConnect** est appelé pendant la mise en commun des connexions, SQLSTATE HY000 (erreur générale) sera retourné.  
  
 Lorsque **SQLBrowseConnect** est appelé pour la première fois sur une connexion, la chaîne de connexion de demande de navigation doit contenir le mot clé **DSN** ou le mot clé **DRIVER.** Si la chaîne de connexion de demande de navigation contient le mot clé **DSN,** le gestionnaire de pilote localise une spécification de source de données correspondante dans les informations du système :  
  
-   Si le gestionnaire de conducteur trouve les spécifications correspondantes de source de données, il charge le pilote associé DLL; le conducteur peut récupérer des informations sur la source de données à partir des informations du système.  
  
-   Si le gestionnaire de conducteur ne peut pas trouver les spécifications correspondantes de source de données, il localise les spécifications de source de données par défaut et charge le pilote associé DLL; le conducteur peut récupérer des informations sur la source de données par défaut à partir des informations du système. "DEFAULT" est transmis au conducteur pour la DSN.  
  
-   Si le gestionnaire de pilote ne peut pas trouver les spécifications correspondantes de source de données et qu’il n’y a pas de spécification de source de données par défaut, il retourne SQL_ERROR avec SQLSTATE IM002 (Source de données non trouvée et aucun conducteur par défaut spécifié).  
  
 Si la chaîne de connexion de demande de navigation contient le mot clé **DRIVER,** le gestionnaire de conducteur charge le pilote spécifié; il ne tente pas de localiser une source de données dans les informations du système. Étant donné que le mot clé **DRIVER** n’utilise pas les informations provenant des informations du système, le pilote doit définir suffisamment de mots clés pour qu’un pilote puisse se connecter à une source de données en utilisant uniquement les informations contenues dans les chaînes de connexion de demande de navigation.  
  
 À chaque appel à **SQLBrowseConnect**, l’application spécifie les valeurs d’attribut de connexion dans la chaîne de connexion de demande de navigation. Le conducteur retourne des niveaux successifs d’attributs et attribue des valeurs dans la chaîne de connexion de résultat de navigation; il renvoie SQL_NEED_DATA tant qu’il y a des attributs de connexion qui n’ont pas encore été énumérés dans la chaîne de connexion de demande de navigation. L’application utilise le contenu de la chaîne de connexion de résultat de navigation pour construire la chaîne de connexion de demande de navigation pour le prochain appel à **SQLBrowseConnect**. Tous les attributs obligatoires (ceux qui ne sont pas précédés d’un astérisque dans l’argument *OutConnectionString)* doivent être inclus dans le prochain appel à **SQLBrowseConnect**. Notez que l’application ne peut pas utiliser le contenu des chaînes de connexion de résultat de navigation précédente lors de la construction de la chaîne de connexion de demande de navigation actuelle; c’est-à-dire qu’il ne peut pas spécifier des valeurs différentes pour les attributs définis dans les niveaux précédents.  
  
 Lorsque tous les niveaux de connexion et leurs attributs associés ont été énumérés, le pilote retourne SQL_SUCCESS, la connexion à la source de données est terminée et une chaîne de connexion complète est retournée à l’application. La chaîne de connexion est appropriée à utiliser, en conjonction avec **SQLDriverConnect**, avec la SQL_DRIVER_NOPROMPT option d’établir une autre connexion. La chaîne de connexion complète ne peut pas être utilisée dans un autre appel à **SQLBrowseConnect**, cependant; si **SQLBrowseConnect** était rappelé, toute la séquence d’appels devrait être répétée.  
  
 **SQLBrowseConnect** retourne également SQL_NEED_DATA s’il y a des erreurs récupérables et non mortelles pendant le processus de navigation; par exemple, un mot de passe invalide ou un mot clé d’attribut fourni par l’application. Lorsque SQL_NEED_DATA est retournée et que la chaîne de connexion de résultat de navigation est inchangée, une erreur s’est produite et l’application peut appeler **SQLGetDiagRec** pour renvoyer le SQLSTATE pour les erreurs de navigation. Cela permet à l’application de corriger l’attribut et de continuer la navigation.  
  
 Une application peut mettre fin au processus de navigation à tout moment en appelant **SQLDisconnect**. Le conducteur mettra fin à toute connexion en suspens et retournera la connexion à un état non relié.  
  
 Si des opérations asynchrones sont activées sur la poignée de connexion, **SQLBrowseConnect** peut également retourner SQL_STILL_EXECUTING. Lorsqu’elle revient SQL_NEED_DATA, une application doit utiliser **SQLDisconnect** pour annuler le processus de navigation. Si **SQLBrowseConnect** retourne SQL_STILL_EXECUTING, une application doit utiliser **SQLCancelHandle** pour annuler l’opération en cours. Appeler **SQLCancelHandle** après le retour de la fonction SQL_NEED_DATA n’a aucun effet.  
  
 Pour plus d’informations, voir [Connecting with SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md).  
  
 Si un conducteur prend en charge **SQLBrowseConnect**, la section mot-clé du conducteur dans les informations du système pour le conducteur doit contenir le mot clé **ConnectFunctions** avec le troisième personnage réglé sur "Y".  
  
## <a name="code-example"></a>Exemple de code  
  
> [!NOTE]  
>  Si vous vous connectez à un fournisseur de sources `Trusted_Connection=yes` de données qui prend en charge l’authentification de Windows, vous devez spécifier au lieu d’informations d’identification et de mot de passe de l’utilisateur dans la chaîne de connexion.  
  
 Dans l’exemple suivant, une application appelle **SQLBrowseConnect** à plusieurs reprises. Chaque fois **que SQLBrowseConnect** retourne SQL_NEED_DATA, il transmet des \*informations sur les données dont elle a besoin dans *OutConnectionString*. L’application passe *OutConnectionString* à sa routine **GetUserInput** (non montré). **GetUserInput** analyse les informations, construit et affiche une boîte de dialogue, et \*renvoie les informations saisies par l’utilisateur dans *InConnectionString*. L’application transmet les informations de l’utilisateur au conducteur lors du prochain appel à **SQLBrowseConnect**. Une fois que l’application a fourni toutes les informations nécessaires pour que le conducteur se connecte à la source de données, **SQLBrowseConnect** retourne SQL_SUCCESS et le produit de l’application.  
  
 Pour un exemple plus détaillé de connexion à un pilote DE serveur SQL en appelant **SQLBrowseConnect**, voir [SQL Server Browsing Exemple](../../../odbc/reference/develop-app/sql-server-browsing-example.md).  
  
 Par exemple, pour se connecter à la source de données Ventes, les actions suivantes peuvent se produire. Tout d’abord, l’application passe la chaîne suivante à **SQLBrowseConnect**:  
  
```  
"DSN=Sales"  
```  
  
 Le Gestionnaire de pilote charge le conducteur associé à la source de données Ventes. Il appelle ensuite la fonction **SQLBrowseConnect** du conducteur avec les mêmes arguments qu’il a reçus de la demande. Le pilote renvoie la chaîne suivante dans*OutConnectionString*:  
  
```  
"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"  
```  
  
 L’application passe cette chaîne à sa routine **GetUserInput,** qui construit une boîte de dialogue qui demande à l’utilisateur de sélectionner le serveur rouge, bleu ou vert et d’entrer un identifiant et un mot de passe de l’utilisateur. La routine transmet les informations suivantes \*spécifiées par l’utilisateur dans *InConnectionString*, que l’application passe à **SQLBrowseConnect**:  
  
```  
"HOST=red;UID=Smith;PWD=Sesame"  
```  
  
 **SQLBrowseConnect** utilise ces informations pour se connecter au serveur rouge comme Smith avec le mot de passe Sésame, puis retourne la chaîne suivante dans*OutConnectionString:*  
  
```  
"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"  
```  
  
 L’application passe cette chaîne à sa routine **GetUserInput,** qui construit une boîte de dialogue qui demande à l’utilisateur de sélectionner une base de données. L’utilisateur sélectionne empdata et l’application appelle **SQLBrowseConnect** une dernière fois avec cette chaîne:  
  
```  
"DATABASE=SalesOrders"  
```  
  
 Il s’agit de la dernière information dont le conducteur a besoin pour se connecter à la source de données; **SQLBrowseConnect** retourne SQL_SUCCESS, et*OutConnectionString* contient la chaîne de connexion terminée :  
  
```cpp  
// SQLBrowseConnect_Function.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define BRWS_LEN 100  
SQLHENV henv;  
SQLHDBC hdbc;  
SQLHSTMT hstmt;  
SQLRETURN retcode;  
SQLCHAR szConnStrIn[BRWS_LEN], szConnStrOut[BRWS_LEN];  
SQLSMALLINT cbConnStrOut;  
  
void GetUserInput(SQLCHAR * szConnStrOut, SQLCHAR * szConnStrIn) {}  
  
int main() {  
   // Allocate the environment handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);        
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
      // Set the version environment attribute.  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
         // Allocate the connection handle.  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            // Call SQLBrowseConnect until it returns a value other than SQL_NEED_DATA   
            // (pass data source name the first time).  If SQL_NEED_DATA is returned, call GetUserInput   
            // (not shown) to build a dialog from the values in szConnStrOut.  The user-supplied values   
            // are returned in szConnStrIn, which is passed in the next call to SQLBrowseConnect.  
  
            strcpy_s((char*)szConnStrIn, _countof(szConnStrIn), "DSN=Sales");  
            do {  
               retcode = SQLBrowseConnect(hdbc, szConnStrIn, SQL_NTS,  
                  szConnStrOut, BRWS_LEN, &cbConnStrOut);  
               if (retcode == SQL_NEED_DATA)  
                  GetUserInput(szConnStrOut, szConnStrIn);  
            } while (retcode == SQL_NEED_DATA);  
  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
               // Allocate the statement handle.  
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                  // Process data after successful connection  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               SQLDisconnect(hdbc);  
            }  
         }  
         SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      }  
   }  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée de connexion|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Connexion à une source de données|[Fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Déconnecter d’une source de données|[SQLDisconnect, fonction](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Connexion à une source de données à l’aide d’une chaîne de connexion ou d’une boîte de dialogue|[Fonction SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Retour des descriptions et attributs des conducteurs|[SQLDrivers, fonction](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Libérer une poignée de connexion|[Fonction SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
