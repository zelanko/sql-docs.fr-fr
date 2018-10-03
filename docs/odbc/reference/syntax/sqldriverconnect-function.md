---
title: Fonction SQLDriverConnect | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDriverConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverConnect
helpviewer_keywords:
- SQLDriverConnect function [ODBC]
ms.assetid: e299be1d-5c74-4ede-b6a3-430eb189134f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d254fce8d7765c6248c6e060f2a225f595f804f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597174"
---
# <a name="sqldriverconnect-function"></a>Fonction SQLDriverConnect
**Conformité**  
 Version introduite : La mise en conformité des normes 1.0 ODBC : ODBC  
  
 **Résumé**  
 **SQLDriverConnect** est une alternative à **SQLConnect**. Il prend en charge les sources de données qui nécessitent des informations de connexion plus que les trois arguments dans **SQLConnect**, boîtes de dialogue pour inviter l’utilisateur pour toutes les informations de connexion et les sources de données qui ne sont pas définis dans le système plus d’informations.  
  
 **SQLDriverConnect** fournit les attributs de connexion suivants :  
  
-   Établir une connexion à l’aide d’une chaîne de connexion qui contient le nom de source de données, un ou plusieurs ID d’utilisateur, un ou plusieurs mots de passe et autres informations requises par la source de données.  
  
-   Établir une connexion à l’aide d’une chaîne de connexion partielle ou aucune information supplémentaire ; Dans ce cas, le Gestionnaire de pilotes et le pilote peuvent chaque invite l’utilisateur pour les informations de connexion.  
  
-   Établir une connexion à une source de données qui n’est pas définie dans les informations système. Si l’application fournit une chaîne de connexion partielle, le pilote peut inviter l’utilisateur pour les informations de connexion.  
  
-   Établir une connexion à une source de données à l’aide d’une chaîne de connexion construite à partir des informations dans un fichier .dsn.  
  
 Une fois une connexion est établie, **SQLDriverConnect** retourne la chaîne de connexion terminée. L’application peut utiliser cette chaîne pour les demandes de connexion ultérieures. Pour plus d’informations, consultez [connexion avec SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLDriverConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLHWND         WindowHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr,  
     SQLUSMALLINT    DriverCompletion);  
```  
  
## <a name="arguments"></a>Arguments  
 *Handle de connexion*  
 [Entrée] Handle de connexion.  
  
 *WindowHandle*  
 [Entrée] Handle de fenêtre. L’application peut passer le handle de la fenêtre parente, le cas échéant, ou un pointeur null si le handle de fenêtre n’est pas applicable ou **SQLDriverConnect** présentera pas les boîtes de dialogue.  
  
 *InConnectionString*  
 [Entrée] Une chaîne de connexion complète (voir la syntaxe dans « Commentaires »), une chaîne de connexion partielle ou une chaîne vide.  
  
 *StringLength1*  
 [Entrée] Longueur de **InConnectionString*, en caractères, si la chaîne est Unicode ou octets si la chaîne ANSI ou DBCS.  
  
 *OutConnectionString*  
 [Sortie] Pointeur vers une mémoire tampon pour la chaîne de connexion terminée. Lors de la connexion réussie à la source de données cible, cette mémoire tampon contient la chaîne de connexion terminée. Pour cette mémoire tampon d’applications doivent allouer au moins 1 024 caractères.  
  
 Si *OutConnectionString* est NULL, *StringLength2Ptr* retournera toujours le nombre total de caractères (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers lequel pointe *OutConnectionString*.  
  
 *BufferLength*  
 [Entrée] Longueur de la **OutConnectionString* mémoire tampon, en caractères.  
  
 *StringLength2Ptr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total de caractères (sans le caractère de fin de la valeur null) disponibles à renvoyer dans \* *OutConnectionString*. Si le nombre de caractères à retourner est supérieur ou égal à *BufferLength*, la fin de chaîne de connexion dans \* *OutConnectionString* est tronqué à  *BufferLength* moins la longueur d’un caractère du caractère nul de terminaison.  
  
 *DriverCompletion*  
 [Entrée] Indicateur qui indique si le Gestionnaire de pilotes ou le pilote doit demander les informations de connexion plus :  
  
 SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED ou SQL_DRIVER_NOPROMPT.  
  
 (Pour plus d’informations, consultez « Commentaires ».)  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDriverConnect** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *fHandleType*de SQL_HANDLE_DBC et un *hHandle* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLDriverConnect** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|La mémoire tampon \* *OutConnectionString* n’est pas suffisamment grande pour retourner la chaîne de connexion complète, donc la chaîne de connexion a été tronquée. La longueur de la chaîne de connexion non tronqué est retournée dans **StringLength2Ptr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01 S 00|Attribut de chaîne de connexion non valide|Un mot clé d’attribut non valide a été spécifié dans la chaîne de connexion (*InConnectionString*), mais le pilote n’a pas pu vous connecter à la source de données. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur d’option modifiée|Le pilote ne prenait pas en charge la valeur spécifiée vers lequel pointée le *ValuePtr* argument dans **SQLSetConnectAttr** et remplacé une valeur similaire. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S08|Erreur durant l’enregistrement du fichier DSN|La chaîne dans  *\*InConnectionString* contenait un **FILEDSN** mot clé, mais le fichier .dsn n’a pas été enregistré. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S09|Mot clé non valide|(DM) dans la chaîne de  *\*InConnectionString* contenait un **SAVEFILE** mot clé mais pas un **pilote** ou un **FILEDSN** mot clé. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08001|Impossible d’établir la connexion du client|Le pilote n’a pas pu établir une connexion avec la source de données.|  
|08002|Nom de la connexion en cours d’utilisation|(DM) spécifié *ConnectionHandle* avait déjà été utilisée pour établir une connexion avec une source de données, et la connexion a été ouverte.|  
|08004|Serveur a rejeté la connexion|La source de données a rejeté l’établissement de la connexion pour des raisons de défini par l’implémentation.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a tenté de se connecter avant le **SQLDriverConnect** traitement de la fonction a été exécutée.|  
|28000|Spécification d’autorisation non valide|L’identificateur d’utilisateur ou la chaîne d’autorisation ou les deux, comme spécifié dans la chaîne de connexion (*InConnectionString*), a violé les restrictions définies par la source de données.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*szMessageText* tampon décrit l’erreur et sa cause.|  
|HY000|Erreur générale : source de données de fichier non valide|(DM) la chaîne dans **InConnectionString* contenait un mot clé FILEDSN, mais Impossible de trouver le nom du fichier .dsn.|  
|HY000|Erreur générale : Impossible de créer la mémoire tampon de fichier|(DM) la chaîne dans **InConnectionString* contenait un mot clé FILEDSN, mais le fichier .dsn était illisible.|  
|HY001|Erreur d’allocation de mémoire|Le Gestionnaire de pilotes n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la **SQLDriverConnect** (fonction).<br /><br /> Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, le [sqlcancelhandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelé sur le *ConnectionHandle*, puis le **SQLDriverConnect** fonction a été appelée à nouveau sur le *ConnectionHandle*.<br /><br /> Ou, **SQLDriverConnect** fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancelHandle** a été appelé sur le *ConnectionHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) une autre fonction de façon asynchrone en cours d’exécution (pas **SQLDriverConnect**) a été appelé pour le *ConnectionHandle* et était en cours d’exécution lorsque le **SQLDriverConnect** fonction a été appelée.|  
|HY013|Erreur de gestion de mémoire|Le **SQLDriverConnect** appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur spécifiée pour l’argument *StringLength1* était inférieure à 0 et n’était pas égale à SQL_NTS.<br /><br /> (DM) la valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.|  
|HY092|Identificateur d’option/attribut non valide|(DM) le *DriverCompletion* SQL_DRIVER_PROMPT, a été l’argument et le *WindowHandle* argument était un pointeur null.|  
|HY110|Exécution de pilote non valide|(DM) la valeur spécifiée pour l’argument *DriverCompletion* n’était pas égale à SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED ou SQL_DRIVER_NOPROMPT.<br /><br /> (DM) le regroupement de connexions a été activé, et la valeur spécifiée pour l’argument *DriverCompletion* n’était pas égale à SQL_DRIVER_NOPROMPT.|  
|HYC00|Fonctionnalité optionnelle non implémentée|Le pilote ne prend pas en charge la version de comportement ODBC demandé par l’application.|  
|HYT00|Délai d'expiration dépassé|Le délai de connexion a expiré avant la connexion à la source de données terminée. Le délai d’expiration est défini via **SQLSetConnectAttr**, sql_attr_login_timeout permet de contrôler.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le pilote correspondant au nom de source de données spécifié ne prend pas en charge la fonction.|  
|IM002|Source de données introuvable et aucun pilote par défaut spécifié|(DM) le nom spécifié dans la chaîne de connexion de source de données (*InConnectionString*) n’a été trouvée dans les informations système et il n’existe aucune spécification de pilote par défaut.<br /><br /> (DM) ODBC par défaut et source de pilote de données est introuvable dans les informations système.|  
|IM003|Pilote spécifié n’a pas pu être chargé.|(DM) le pilote répertorié dans la spécification de source de données dans les informations système ou spécifié par le **pilote** mot clé est introuvable ou ne peut pas être chargé pour une raison quelconque.|  
|IM004|Chauffeur **SQLAllocHandle** sur SQL_HANDLE_ENV a échoué|(DM) au cours de **SQLDriverConnect**, le Gestionnaire de pilote appelé du pilote **SQLAllocHandle** fonctionne avec un *fHandleType* de SQL_HANDLE_ENV et du pilote retourné un erreur.|  
|IM005|Chauffeur **SQLAllocHandle** sur SQL_HANDLE_DBC a échoué.|(DM) au cours de **SQLDriverConnect**, le Gestionnaire de pilote appelé du pilote **SQLAllocHandle** fonctionne avec un *fHandleType* de SQL_HANDLE_DBC et du pilote retourné un erreur.|  
|IM006|Chauffeur **SQLSetConnectAttr** a échoué|(DM) au cours de **SQLDriverConnect**, le Gestionnaire de pilote appelé du pilote **SQLSetConnectAttr** (fonction) et le pilote a renvoyé une erreur.|  
|IM007|Aucune source de données ou d’un pilote spécifié ; boîte de dialogue interdite|Aucun nom de source de données ou le pilote a été spécifié dans la chaîne de connexion et *DriverCompletion* a été SQL_DRIVER_NOPROMPT.|  
|IM008|Échoué de la boîte de dialogue|Le pilote a tenté d’afficher sa boîte de dialogue de connexion et a échoué.<br /><br /> *WindowHandle* était un pointeur null, et *DriverCompletion* n’était pas SQL_DRIVER_NO_PROMPT.|  
|IM009|Impossible de charger la DLL de traduction|Le pilote n’a pas pu charger la DLL qui a été spécifiée pour la source de données ou pour la connexion de la traduction.|  
|IM010|Nom de source de données trop long|(DM) la valeur d’attribut pour le mot clé DSN a été SQL_MAX_DSN_LENGTH caractères.|  
|IM011|Nom du pilote trop long|Valeur de l’attribut (DM) pour le **pilote** mot clé a été plu de 255 caractères.|  
|IM012|Erreur de syntaxe du mot clé DRIVER|(DM) la mot clé-valeur paire pour le **pilote** mot clé contenait une erreur de syntaxe.<br /><br /> (DM) dans la chaîne de  *\*InConnectionString* contenait un **FILEDSN** mot clé, mais le fichier .dsn ne contenait pas un **pilote** mot clé ou un  **DSN** mot clé.|  
|IM014|La source de données spécifié contient une incompatibilité d’architecture du pilote et une Application|Application de 32 bits (DM) utilise un DSN de connexion à un pilote 64 bits. ou vice versa.|  
|IM015|SQLDriverConnect du pilote sur SQL_HANDLE_DBC_INFO_HANDLE a échoué|Si un pilote retourne SQL_ERROR, le Gestionnaire de pilotes retourne SQL_ERROR à l’application et la connexion échoue.<br /><br /> Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, consultez [développer la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
|S1118|Pilote ne prend pas en charge la notification asynchrone|Lorsque le pilote ne prend pas en charge la notification asynchrone, vous ne pouvez pas définir SQL_ATTR_ASYNC_DBC_EVENT ou SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="comments"></a>Commentaires  
 Une chaîne de connexion présente la syntaxe suivante :  
  
 *chaîne de connexion* :: = *une chaîne vide*[ ;] &#124; *attribut*[ ;] &#124; *attribut*; *chaîne de connexion*  
  
 *une chaîne vide* :: =*attribut* :: = *mot clé de l’attribut*=*attribut-valeur* &#124; pilote = [{}] *valeur d’attribut*[}]  
  
 *mot clé de l’attribut* :: = DSN &#124; UID &#124; PWD &#124; *-défini-attribut-mot clé driver*  
  
 *attribute-value* ::= *character-string*  
  
 *défini-attribut-mot clé Driver* :: = *identificateur*  
  
 où *chaîne de caractères* a zéro ou plusieurs caractères ; *identificateur* a un ou plusieurs caractères ; *mot clé de l’attribut* ne respecte pas la casse ; *attribut-valeur* peut respecter la casse ; et la valeur de la **DSN** mot clé n’est pas constitué uniquement d’espaces.  
  
 En raison de la connexion chaîne et l’initialisation de grammaire, mots clés et l’attribut valeurs du fichier qui contient les caractères **[]{}(), ? \*= ! @** ne figurant ne pas entre accolades doivent être évitées. La valeur de la **DSN** mot clé ne peut pas contenir uniquement des espaces et ne doit pas contenir des espaces. En raison de la grammaire des informations système, les noms de source de données et les mots clés ne peut pas contenir la barre oblique inverse (\\) caractères.  
  
 Les applications n’ont pas à ajouter des accolades autour de la valeur d’attribut après le **pilote** mot clé, sauf si l’attribut contient un point-virgule ( ;), auquel cas les accolades sont obligatoires. Si la valeur d’attribut que le pilote reçoit contient des accolades, le pilote ne doit pas les supprimer, mais ils doivent faire partie de la chaîne de connexion retournée.  
  
 Une valeur de chaîne de connexion ou de la source de données placée entre accolades ({}) contenant les caractères **[]{}(), ? \*= ! @** est passé intact au pilote. Toutefois, lorsque vous utilisez ces caractères dans un mot clé, le Gestionnaire de pilotes retourne une erreur lorsque vous travaillez avec un fichier DSN mais transmet la chaîne de connexion au pilote pour les chaînes de connexion normale. Évitez d’utiliser des accolades incorporées dans une valeur de mot clé.  
  
 La chaîne de connexion peut inclure n’importe quel nombre de mots clés définis par le pilote. Étant donné que le **pilote** mot clé n’utilise pas les informations à partir des informations système, le pilote doit définir suffisamment de mots clés afin qu’un pilote peut se connecter à une source de données à l’aide uniquement les informations dans la chaîne de connexion. (Pour plus d’informations, consultez « Instructions pilote », plus loin dans cette section.) Le pilote définit les mots clés qui sont requis pour se connecter à la source de données.  
  
 Le tableau suivant décrit les valeurs d’attribut de la **DSN**, **FILEDSN**, **pilote**, **UID**, **PWD**, et **SAVEFILE** mots clés.  
  
|Mot clé|Description de valeur d’attribut|  
|-------------|---------------------------------|  
|**DSN**|Nom d’une source de données, tel que retourné par **SQLDataSources** ou la boîte de dialogue de sources de données de **SQLDriverConnect**.|  
|**FILEDSN**|Nom de fichier .dsn à partir de laquelle une chaîne de connexion doit être générée pour la source de données. Ces sources de données sont appelés fichiers sources de données.|  
|**PILOTE**|Description du pilote tel que retourné par la **SQLDrivers** (fonction). Par exemple, Rdb ou SQL Server.|  
|**UID**|Un ID utilisateur.|  
|**PWD**|Le mot de passe correspondant à l’ID d’utilisateur, ou une chaîne vide s’il n’existe aucun mot de passe pour l’ID d’utilisateur (PWD = ;).|  
|**SAVEFILE**|Le nom de fichier d’un fichier .dsn dans lequel les valeurs d’attribut de mots clés utilisés dans l’établissement de la connexion à présente, réussite doivent être enregistrés.|  
  
 Pour plus d’informations sur la manière dont une application choisit une source de données ou le pilote, consultez [choisir une Source de données ou le pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Si tous les mots clés sont répétés dans la chaîne de connexion, le pilote utilise la valeur associée à la première occurrence du mot clé. Si le **DSN** et **pilote** mots clés sont inclus dans la même chaîne de connexion, le Gestionnaire de pilotes et le pilote utilisent le mot clé qui apparaît en premier.  
  
 Le **FILEDSN** et **DSN** mots clés s’excluent mutuellement : le mot clé qui apparaît en premier est utilisé, et celui qui apparaît la deuxième est ignoré. Le **FILEDSN** et **pilote** mots clés, en revanche, ne sont pas mutuellement exclusives. Si n’importe quel mot clé apparaît dans une chaîne de connexion avec **FILEDSN**, la valeur d’attribut du mot clé dans la chaîne de connexion est utilisée au lieu de la valeur d’attribut du même mot clé dans le fichier .dsn.  
  
 Si le **FILEDSN** mot clé est utilisé, les mots clés spécifiés dans un fichier .dsn sont utilisés pour créer une chaîne de connexion. (Pour plus d’informations, consultez « Sources de données fichier » plus loin dans cette section.) Le **UID** mot clé est facultatif ; un fichier .dsn peut-être être créé uniquement avec le **pilote** mot clé. Le **PWD** mot clé n’est pas stocké dans un fichier .dsn. Le répertoire par défaut pour enregistrer et charger un fichier .dsn sera une combinaison du chemin d’accès spécifié par **CommonFileDir** dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Windows\CurrentVersion et « ODBC\DataSources ». (Si CommonFileDir ont été « C:\Program Files\Common Files », le répertoire par défaut serait à « C:\Program Files\Common Files\ODBC\Data Sources ».)  
  
> [!NOTE]  
>  Un fichier .dsn peut être manipulé directement en appelant le [SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md) et [SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md) fonctions dans le programme d’installation DLL.  
  
 Si le **SAVEFILE** mot clé est utilisé, les valeurs d’attribut de mots clés utilisés dans l’établissement de la connexion à présente, la réussite seront enregistrés sous un fichier .dsn par le nom de la valeur d’attribut de la **SAVEFILE** mot clé. Le **SAVEFILE** mot clé doit être utilisée conjointement avec la **pilote** mot clé, le **FILEDSN** mot clé, ou les deux, ou la fonction retourne SQL_SUCCESS_WITH_INFO avec SQLSTATE 01S09 (mot clé non valide). Le **SAVEFILE** mot clé doit apparaître avant le **pilote** mot clé dans la chaîne de connexion, ou les résultats seront non défini.  
  
## <a name="driver-manager-guidelines"></a>Instructions de gestionnaire de pilotes  
 Le Gestionnaire de pilotes construit une chaîne de connexion à passer au pilote dans le *InConnectionString* argument du pilote **SQLDriverConnect** (fonction). Le Gestionnaire de pilotes ne modifie pas le *InConnectionString* argument passé par l’application.  
  
 L’action du Gestionnaire de pilotes est basée sur la valeur de la *DriverCompletion* argument :  
  
-   SQL_DRIVER_PROMPT : Si la chaîne de connexion ne contient-elle ni le **pilote**, **DSN**, ou **FILEDSN** mot clé, le Gestionnaire de pilotes affiche la boîte de dialogue Sources de données. Il construit une chaîne de connexion à partir du nom de source de données retourné par la boîte de dialogue et les autres mots clés passés par l’application. Si le nom de source de données retourné par la boîte de dialogue est vide, le Gestionnaire de pilotes spécifie la paire mot clé-valeur DSN = valeur par défaut. (Cette boîte de dialogue s’affiche pas une source de données avec le nom « Default »).  
  
-   SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED : si la chaîne de connexion spécifiée par l’application inclut le **DSN** mot clé, le Gestionnaire de pilotes copie la chaîne de connexion spécifiée par l’application. Sinon, elle prend les mêmes actions comme il le fait quand *DriverCompletion* est SQL_DRIVER_PROMPT.  
  
-   SQL_DRIVER_NOPROMPT : Le Gestionnaire de pilotes copie la chaîne de connexion spécifiée par l’application.  
  
 Si la chaîne de connexion spécifiée par l’application contient le **pilote** mot clé, le Gestionnaire de pilotes copie la chaîne de connexion spécifiée par l’application.  
  
 À l’aide de la chaîne de connexion qu’il a construit, le Gestionnaire de pilotes détermine le pilote à utiliser, se connecte à ce pilote et transmet la chaîne de connexion qu’il a construit le pilote ; Pour plus d’informations sur l’interaction du Gestionnaire de pilotes et le pilote, consultez la section « Commentaires » dans [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Si la chaîne de connexion ne contient-elle pas le **pilote** mot clé, le Gestionnaire de pilotes détermine le pilote à utiliser comme suit :  
  
1.  Si la chaîne de connexion contient le **DSN** mot clé, le Gestionnaire de pilotes récupère le pilote associé à la source de données à partir des informations système.  
  
2.  Si la chaîne de connexion ne contient-elle pas le **DSN** mot clé ou la source de données est introuvable, le Gestionnaire de pilotes récupère le pilote associé à la source de données par défaut à partir des informations système. (Pour plus d’informations, consultez [sous-clé par défaut](../../../odbc/reference/install/default-subkey.md).) Le Gestionnaire de pilotes modifie la valeur de la **DSN** mot clé dans la chaîne de connexion à « DEFAULT ».  
  
3.  Si le **DSN** mot clé dans la chaîne de connexion est définie sur « DEFAULT », le Gestionnaire de pilotes récupère le pilote associé à la source de données par défaut à partir des informations système.  
  
4.  Si la source de données est introuvable et que la source de données par défaut est introuvable, le Gestionnaire de pilotes retourne SQL_ERROR avec SQLSTATE IM002 (source de données introuvable et aucun pilote par défaut spécifié).  
  
## <a name="file-data-sources"></a>Sources de données de fichier  
 Si la chaîne de connexion spécifiée par l’application dans l’appel à **SQLDriverConnect** contient le **FILEDSN** mot clé et ce mot clé n’est pas remplacée à l’aide du **DSN**ou **pilote** mot clé, le Gestionnaire de pilotes, puis crée une chaîne de connexion en utilisant les informations dans le fichier .dsn et *InConnectionString* argument. Le Gestionnaire de pilotes procède comme suit :  
  
1.  Vérifie si le nom de fichier du fichier .dsn est valide. Sinon, elle retourne SQL_ERROR avec SQLSTATE IM014 (nom non valide de fichier DSN). Si le nom de fichier est une chaîne vide (« ») et SQL_DRIVER_NOPROMPT n’est pas spécifié, puis le **ouverture de fichier** boîte de dialogue s’affiche. Si le nom de fichier contient un chemin d’accès valide, mais aucun nom de fichier ou un nom de fichier non valide, et SQL_DRIVER_NOPROMPT n’est pas spécifié, puis le **ouverture de fichier** boîte de dialogue s’affiche avec le répertoire actif, la valeur est celle spécifiée dans le nom de fichier. Si le nom de fichier est une chaîne vide (" ») ou le nom de fichier contient un chemin d’accès valide, mais aucun nom de fichier ou un nom de fichier non valide, SQL_DRIVER_NOPROMPT est spécifié, puis SQL_ERROR est retourné avec SQLSTATE IM014 (nom non valide de fichier DSN).  
  
2.  Lit tous les mots clés dans la section [ODBC] du fichier .dsn. Si le **pilote** mot clé n’est pas présent, elle retourne SQL_ERROR avec SQLSTATE IM012 (erreur de syntaxe mot clé Driver,), à l’exception où le fichier .dsn est partageable et contient donc uniquement le **DSN** mot clé.  
  
     Si la source de données de fichier est partageable, le Gestionnaire de pilotes lit la valeur de la **DSN** mot clé et se connecte que nécessaire pour la source de données utilisateur ou système vers lequel pointée la source de données fichier partageable. Étapes 3 à 5 ne sont pas effectuées.  
  
3.  Construit une chaîne de connexion pour le pilote. La chaîne de connexion du pilote est l’union entre les mots clés spécifiés dans le fichier .dsn et ceux spécifiés dans la chaîne de connexion d’application d’origine. Règles pour la construction de la chaîne de connexion de pilote où les mots clés se chevauchent sont les suivantes :  
  
    -   Si le **pilote** mot clé existe dans la chaîne de connexion d’application et les pilotes spécifiés par le **pilote** mots clés ne sont pas les mêmes dans le fichier .dsn et la chaîne de connexion d’application, puis le informations sur les pilotes dans le fichier .dsn sont ignorées et les informations de pilote dans la chaîne de connexion d’application sont utilisées. Si les pilotes spécifiés par le **pilote** mot clé sont les mêmes dans le fichier .dsn et de la chaîne de connexion de l’application, puis où tous les mots clés se chevauchent, celles spécifiées dans la chaîne de connexion d’application ont priorité sur ceux spécifié dans le fichier .dsn.  
  
    -   Dans la nouvelle chaîne de connexion, le **FILEDSN** mot clé est éliminé.  
  
4.  Charge le pilote en consultant l’entrée de Registre HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. INI\\< nom du pilote\>\Driver où \<nom_pilote > est spécifié par le **pilote** mot clé.  
  
5.  Transmet le pilote de la nouvelle chaîne de connexion.  
  
 Pour obtenir des exemples de fichiers .dsn, consultez [se connectant à l’aide de fichiers Sources de données](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md).  
  
## <a name="savefile-keyword"></a>Mot clé SAVEFILE  
 Si la chaîne de connexion spécifiée par l’application contient le **SAVEFILE** mot clé, le Gestionnaire de pilotes, puis enregistre la chaîne de connexion dans un fichier .dsn. Le Gestionnaire de pilotes procède comme suit :  
  
1.  Vérifie si le nom de fichier du fichier .dsn inclus en tant que la valeur d’attribut de la **SAVEFILE** mot clé est valide. Sinon, elle retourne SQL_ERROR avec SQLSTATE IM014 (nom non valide de fichier DSN). La validité du nom de fichier est déterminée par les règles d’affectation de noms système standard. Si le nom de fichier est une chaîne vide (" ») et le *DriverCompletion* argument n’est pas SQL_DRIVER_NOPROMPT, puis le nom de fichier est valide. Si le nom de fichier existe déjà, puis si *DriverCompletion* est SQL_DRIVER_NOPROMPT, le fichier est remplacé. Si *DriverCompletion* est SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED, une boîte de dialogue invite l’utilisateur à spécifier si le fichier doit être remplacé. Si non est entrée, puis le **fichier-Enregistrer** boîte de dialogue s’affiche.  
  
2.  Si le pilote retourne SQL_SUCCESS et le nom de fichier n’est pas une chaîne vide, le Gestionnaire de pilotes écrit les informations de connexion retournées dans le *OutConnectionString* argument dans le fichier spécifié avec le format spécifié dans la section « Chaînes de connexion » plus haut dans cette section.  
  
3.  Si le pilote retourne SQL_SUCCESS, et le nom de fichier a été une chaîne vide (« »), puis appelle le Gestionnaire de pilotes le **fichier-Enregistrer** boîte de dialogue commune avec le *hwnd* spécifié et écrit les informations de connexion retournée dans *OutConnectionString* dans le fichier spécifié dans la boîte de dialogue Fichier-enregistrer avec le format spécifié dans la section « Chaînes de connexion » plus haut dans cette section.  
  
4.  Si le pilote retourne SQL_SUCCESS, elle retourne le *OutConnectionString* argument contenant la chaîne de connexion à l’application.  
  
5.  Si le pilote retourne SQL_SUCCESS_WITH_INFO ou SQL_ERROR, le Gestionnaire de pilotes retourne la valeur SQLSTATE à l’application.  
  
## <a name="driver-guidelines"></a>Conseils sur les pilotes  
 Le pilote vérifie si la chaîne de connexion lui est passée par le Gestionnaire de pilote contient le **DSN** ou **pilote** mot clé. Si la chaîne de connexion contient le **pilote** mot clé, le pilote ne peut pas récupérer des informations sur la source de données à partir des informations système. Si la chaîne de connexion contient le **DSN** mot clé ou ne contient ni le **DSN** ou **pilote** mot clé, le pilote peut récupérer des informations sur la source de données à partir des informations système comme suit :  
  
1.  Si la chaîne de connexion contient le **DSN** mot clé, le pilote récupère les informations pour la source de données spécifié.  
  
2.  Si la chaîne de connexion ne contient-elle pas le **DSN** mot clé, la source de données spécifiée est introuvable, ou le **DSN** mot clé est définie sur « DEFAULT », le pilote récupère les informations pour la source de données par défaut .  
  
 Le pilote utilise les informations qu’il récupère à partir des informations système pour transférer les informations passées dans la chaîne de connexion. Si les informations contenues dans les informations système duplique les informations contenues dans la chaîne de connexion, le pilote utilise les informations dans la chaîne de connexion.  
  
 Selon la valeur de *DriverCompletion*, le pilote invite l’utilisateur pour les informations de connexion, comme l’ID utilisateur et le mot de passe et se connecte à la source de données :  
  
-   SQL_DRIVER_PROMPT : Le pilote affiche une boîte de dialogue, en utilisant les valeurs des informations système et de la chaîne de connexion (le cas échéant) comme valeurs initiales. Lorsque l’utilisateur quitte la boîte de dialogue, le pilote se connecte à la source de données. Il construit également une chaîne de connexion à partir de la valeur de la **DSN** ou **pilote** mot clé dans \* *InConnectionString* et les informations retournées à partir de la boîte de dialogue. Il place cette chaîne de connexion dans le **OutConnectionString* mémoire tampon.  
  
-   SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED : si la chaîne de connexion contient suffisamment d’informations, et cette information est correcte, le pilote se connecte à la source de données et les copies \* *InConnectionString*à \* *OutConnectionString*. Si certaines informations sont manquantes ou incorrectes, le pilote accepte les mêmes actions comme il le fait quand *DriverCompletion* est SQL_DRIVER_PROMPT, sauf que si *DriverCompletion* est SQL_DRIVER_COMPLETE_ REQUIS, le pilote désactive les contrôles pour toute information ne pas obligé de se connecter à la source de données.  
  
-   SQL_DRIVER_NOPROMPT : Si la chaîne de connexion contient suffisamment d’informations, le pilote se connecte à la source de données et les copies \* *InConnectionString* à \* *OutConnectionString*. Sinon, le pilote retourne SQL_ERROR pour **SQLDriverConnect**.  
  
 La connexion établie à la source de données, le pilote définit également \* *StringLength2Ptr* à la longueur de la chaîne de connexion de sortie qui est disponible à renvoyer dans **OutConnectionString*.  
  
 Si l’utilisateur annule une boîte de dialogue présentée par le Gestionnaire de pilotes ou le pilote, **SQLDriverConnect** retourne SQL_NO_DATA.  
  
 Pour plus d’informations sur l’interaction entre le Gestionnaire de pilotes et le pilote pendant le processus de connexion, consultez [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Si un pilote prend en charge **SQLDriverConnect**, la section de mot clé driver des informations système pour le pilote doit contenir le **ConnectFunctions** mot clé par le deuxième caractère de la valeur « Y ».  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>Se connecter quand le regroupement de connexions est activé  
 Le regroupement de connexions permet à une application de réutiliser une connexion qui a déjà été créée. Lorsque **SQLDriverConnect** est appelée, le Gestionnaire de pilotes tente d’établir la connexion à l’aide d’une connexion qui fait partie d’un pool de connexions dans un environnement qui a été désigné pour le regroupement de connexions. Pour plus d’informations sur le regroupement de connexions, consultez [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Une application peut définir SQL_ATTR_RESET_CONNECTION avant d’appeler SQLDisconnect sur une connexion où le regroupement est activé. Pour plus d’informations, consultez [fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Les restrictions suivantes s’appliquent lorsqu’une application appelle **SQLDriverConnect** pour se connecter à une connexion regroupée :  
  
-   Aucune connexion mise en pool de traitement n’est effectuée lorsque le **SAVEFILE** mot clé est spécifié dans la chaîne de connexion.  
  
-   Si le regroupement de connexions est activé, **SQLDriverConnect** peut être appelée uniquement avec un *DriverCompletion* argument de SQL_DRIVER_NOPROMPT ; si **SQLDriverConnect** est appelée avec n’importe quel autre *DriverCompletion*, SQLSTATE HY110 (exécution de pilote non valide) est retournée.  
  
## <a name="connection-attributes"></a>Attributs de connexion  
 L’attribut de connexion sql_attr_login_timeout permet de contrôler, à l’aide de **SQLSetConnectAttr**, définit le nombre de secondes à attendre une demande de connexion terminer avec une connexion réussie par le pilote avant de retourner à l’application. Si l’utilisateur est invité à terminer la chaîne de connexion, un délai d’attente pour chaque demande de connexion commence lorsque le pilote démarre le processus de connexion.  
  
 Le pilote, la connexion s’ouvre en mode d’accès SQL_MODE_READ_WRITE, par défaut. Pour définir le mode d’accès à SQL_MODE_READ_ONLY, l’application doit appeler **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ACCESS_MODE avant d’appeler **SQLDriverConnect**.  
  
 Si une bibliothèque de traduction par défaut est spécifiée dans les informations système pour la source de données, le pilote le charge. Une bibliothèque de traduction différente peut être chargée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_LIB. Une option de traduction peut être spécifiée en appelant **SQLSetConnectAttr** avec l’option SQL_ATTR_TRANSLATE_OPTION.  
  
 Pour plus d’informations, consultez [connexion avec SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
```  
// SQLDriverConnect_ref.cpp  
// compile with: odbc32.lib user32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR OutConnStr[255];  
   SQLSMALLINT OutConnStrLen;  
  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            retcode = SQLDriverConnect( // SQL_NULL_HDBC  
               hdbc,   
               desktopHandle,   
               (SQLCHAR*)"driver=SQL Server",   
               _countof("driver=SQL Server"),  
               OutConnStr,  
               255,   
               &OutConnStrLen,  
               SQL_DRIVER_PROMPT );  
  
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
  
 Consultez également [exemple de programme ODBC](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Allocation d’un handle|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Découverte et l’énumération des valeurs requises pour se connecter à une source de données|[SQLBrowseConnect, fonction](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connexion à une source de données|[SQLConnect, fonction](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Déconnexion d’une source de données|[SQLDisconnect, fonction](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Renvoi de descriptions de pilote et attributs|[SQLDrivers, fonction](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Libération d’un descripteur|[SQLFreeHandle, fonction](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Définition d’un attribut de connexion|[SQLSetConnectAttr, fonction](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
