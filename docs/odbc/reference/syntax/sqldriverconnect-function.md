---
title: Fonction SQLDriverConnect (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88ec70d68b46beca97fd6b0d758e21aab5d4f4b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302770"
---
# <a name="sqldriverconnect-function"></a>Fonction SQLDriverConnect
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLDriverConnect** est une alternative à **SQLConnect**. Il prend en charge les sources de données qui nécessitent plus d’informations de connexion que les trois arguments de **SQLConnect**, les boîtes de dialogue pour inciter l’utilisateur à toutes les informations de connexion, et les sources de données qui ne sont pas définies dans les informations du système.  
  
 **SQLDriverConnect** fournit les attributs de connexion suivants :  
  
-   Établir une connexion à l’aide d’une chaîne de connexion qui contient le nom source de données, une ou plusieurs identifiants d’utilisateur, un ou plusieurs mots de passe et d’autres informations requises par la source de données.  
  
-   Établir une connexion à l’aide d’une chaîne de connexion partielle ou d’aucune information supplémentaire; dans ce cas, le gestionnaire de conducteur et le conducteur peuvent chacun inviter l’utilisateur pour des informations de connexion.  
  
-   Établir une connexion à une source de données qui n’est pas définie dans les informations du système. Si l’application fournit une chaîne de connexion partielle, le conducteur peut inciter l’utilisateur à obtenir des informations de connexion.  
  
-   Établir une connexion à une source de données à l’aide d’une chaîne de connexion construite à partir des informations dans un fichier .dsn.  
  
 Après la mise en place d’une connexion, **SQLDriverConnect** renvoie la chaîne de connexion terminée. L’application peut utiliser cette chaîne pour les demandes de connexion ultérieures. Pour plus d’informations, voir [Connecting with SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
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
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *WindowHandle (en)*  
 [Entrée] Poignée de fenêtre. L’application peut passer la poignée de la fenêtre parente, le cas échéant, ou un pointeur nul si la poignée de fenêtre n’est pas applicable ou **SQLDriverConnect** ne présentera pas de boîtes de dialogue.  
  
 *InConnectionString*  
 [Entrée] Une chaîne de connexion complète (voir la syntaxe dans "Comments"), une chaîne de connexion partielle, ou une chaîne vide.  
  
 *StringLength1 (en)*  
 [Entrée] Longueur de*InConnectionString*, en caractères si la chaîne est Unicode, ou octets si la chaîne est ANSI ou DBCS.  
  
 *OutConnectionString (en)*  
 [Sortie] Pointeur vers un tampon pour la chaîne de connexion terminée. Lors de la connexion réussie à la source de données cible, ce tampon contient la chaîne de connexion terminée. Les demandes doivent allouer au moins 1 024 caractères pour ce tampon.  
  
 Si *OutConnectionString* est NULL, *StringLength2Ptr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *OutConnectionString*.  
  
 *BufferLength*  
 [Entrée] Longueur du tampon*OutConnectionString,* en caractères.  
  
 *StringLength2Ptr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de caractères \*(à l’exclusion du caractère de résiliation nulle) disponible pour revenir dans *OutConnectionString*. Si le nombre de caractères disponibles pour revenir est supérieur ou \*égal à *BufferLength*, la chaîne de connexion complétée dans *OutConnectionString* est tronquée à *BufferLength* moins la longueur d’un caractère de désinsaison.  
  
 *Conformité du conducteur*  
 [Entrée] Indicateur indiquant si le gestionnaire de conducteur ou le conducteur doit demander plus d’informations sur la connexion :  
  
 SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED, ou SQL_DRIVER_NOPROMPT.  
  
 (Pour plus d’informations, voir «Commentaires).)  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDriverConnect** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *fHandleType* de SQL_HANDLE_DBC et un *hHandle* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLDriverConnect** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *OutConnectionString* n’était pas assez grand pour retourner toute la chaîne de connexion, de sorte que la chaîne de connexion a été tronquée. La longueur de la chaîne de connexion fausse est retournée dans*stringLength2Ptr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S00|Attribut de chaîne de connexion invalide|Un mot clé d’attribut invalide a été spécifié dans la chaîne de connexion (*InConnectionString*), mais le pilote a été en mesure de se connecter à la source de données de toute façon. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option modifiée|Le conducteur n’a pas appuyé la valeur spécifiée soulignée par l’argument *ValuePtr* dans **SQLSetConnectAttr** et a remplacé une valeur similaire. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S08|Fichier d’enregistrement d’erreur DSN|La chaîne * \*d’InConnectionString* contenait un mot-clé **FILEDSN,** mais le fichier .dsn n’a pas été enregistré. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S09|Mot-clé invalide|(DM) La chaîne * \*d’InConnectionString* contenait un mot clé **SAVEFILE,** mais pas un **MOT-clé DRIVER** ou **UN MOT-clé FILEDSN.** (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08001|Client incapable d’établir la connexion|Le conducteur n’a pas été en mesure d’établir une connexion avec la source de données.|  
|08002|Nom de connexion en cours d’utilisation|(DM) Le *ConnectionHandle* spécifié avait déjà été utilisé pour établir une connexion avec une source de données, et la connexion était toujours ouverte.|  
|08004|Server a rejeté la connexion|La source de données a rejeté l’établissement de la connexion pour des raisons définies par la mise en œuvre.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur tentait de se connecter a échoué avant que la fonction **SQLDriverConnect** ne termine le traitement.|  
|28000|Spécifications d’autorisation invalides|Soit l’identifiant de l’utilisateur ou la chaîne d’autorisation, ou les deux, comme spécifié dans la chaîne de connexion (*InConnectionString*), violé les restrictions définies par la source de données.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \*tampon szMessageText décrit l’erreur* et sa cause.|  
|HY000|Erreur générale: Fichier invalide dsn|(DM) La chaîne dans*InConnectionString* contenait un mot clé FILEDSN, mais le nom du fichier .dsn n’a pas été trouvé.|  
|HY000|Erreur générale : Incapable de créer un tampon de fichier|(DM) La chaîne dans*InConnectionString* contenait un mot clé FILEDSN, mais le fichier .dsn était illisible.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le gestionnaire de conducteur n’a pas été en mesure d’allouer la mémoire requise pour soutenir l’exécution ou l’achèvement de la fonction **SQLDriverConnect.**<br /><br /> Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *ConnectionHandle*. La fonction a été appelée, et avant qu’il ait terminé l’exécution, la [fonction SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) a été appelée sur le *ConnectionHandle*, puis la fonction **SQLDriverConnect** a été appelé à nouveau sur le *ConnectionHandle*.<br /><br /> Ou, la fonction **SQLDriverConnect** a été appelée, et avant qu’il ne termine l’exécution, **SQLCancelHandle** a été appelé sur le *ConnectionHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) Une autre fonction d’exécution asynchrone (pas **SQLDriverConnect**) a été appelée pour le *ConnectionHandle* et était toujours en exécution lorsque la fonction **SQLDriverConnect** a été appelé.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction **SQLDriverConnect** n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *StringLength1* était inférieure à 0 et n’était pas égale à SQL_NTS.<br /><br /> (DM) La valeur spécifiée pour l’argument *BufferLength* était inférieure à 0.|  
|HY092 HY092|Identification d’attribut/option invalide|(DM) *L’argument de DriverCompletion* était SQL_DRIVER_PROMPT, et l’argument *de WindowHandle* était un pointeur nul.|  
|HY110|Achèvement du conducteur invalide|(DM) La valeur spécifiée pour l’argument *DriverCompletion* n’était pas égale à SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, SQL_DRIVER_COMPLETE_REQUIRED ou SQL_DRIVER_NOPROMPT.<br /><br /> (DM) La mise en commun des connexions a été activée, et la valeur spécifiée pour l’argument *DriverCompletion* n’était pas égale à SQL_DRIVER_NOPROMPT.|  
|HYC00|Fonctionnalité facultative non implémentée|Le conducteur ne prend pas en charge la version du comportement ODBC que l’application a demandée.|  
|HYT00|Délai expiré|La période de délai de connexion a expiré avant que la connexion à la source de données ne soit terminée. La période de délai d’attente est fixée par **SQLSetConnectAttr**, SQL_ATTR_LOGIN_TIMEOUT.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur correspondant au nom spécifié de source de données ne prend pas en charge la fonction.|  
|IM002|Source de données non trouvée et aucun conducteur par défaut spécifié|(DM) Le nom de source de données spécifié dans la chaîne de connexion (*InConnectionString*) n’a pas été trouvé dans les informations du système, et il n’y avait aucune spécification de conducteur par défaut.<br /><br /> (DM) Les informations relatives aux données de l’ODBC et par défaut du conducteur n’ont pas pu être trouvées dans les informations du système.|  
|IM003|Le conducteur spécifié n’a pas pu être chargé|(DM) Le conducteur figurant dans les spécifications de source de données dans les informations du système ou spécifié par le mot clé **DRIVER** n’a pas été trouvé ou n’a pas pu être chargé pour une autre raison.|  
|IM004|Le **conducteur SQLAllocHandle** sur SQL_HANDLE_ENV a échoué|(DM) Pendant **SQLDriverConnect**, le gestionnaire de conducteur a appelé la fonction **SQLAllocHandle** du conducteur avec un *fHandleType* de SQL_HANDLE_ENV et le conducteur a retourné une erreur.|  
|IM005|Le **conducteur SQLAllocHandle** sur SQL_HANDLE_DBC a échoué.|(DM) Pendant **SQLDriverConnect**, le gestionnaire de conducteur a appelé la fonction **SQLAllocHandle** du conducteur avec un *fHandleType* de SQL_HANDLE_DBC et le conducteur a retourné une erreur.|  
|IM006|Le conducteur **SQLSetConnectAttr** a échoué|(DM) Pendant **SQLDriverConnect**, le gestionnaire de pilote a appelé la fonction **SQLSetConnectAttr** du conducteur et le conducteur a retourné une erreur.|  
|IM007|Aucune source de données ou pilote spécifié; dialogue interdit|Aucun nom ou pilote de source de données n’a été spécifié dans la chaîne de connexion, et *DriverCompletion* a été SQL_DRIVER_NOPROMPT.|  
|IM008|Le dialogue a échoué|Le conducteur a tenté d’afficher sa boîte de dialogue de connexion et a échoué.<br /><br /> *WindowHandle* était un pointeur nul, et *DriverCompletion* n’était pas SQL_DRIVER_NO_PROMPT.|  
|IM009|Incapable de charger la traduction DLL|Le conducteur n’a pas été en mesure de charger la traduction DLL qui a été spécifiée pour la source de données ou pour la connexion.|  
|IM010|Nom source de données trop long|(DM) La valeur d’attribut pour le mot clé DSN était plus longue que SQL_MAX_DSN_LENGTH caractères.|  
|IM011|Nom du conducteur trop long|(DM) La valeur d’attribut pour le mot clé **DRIVER** était supérieure à 255 caractères.|  
|IM012|ERREUR de syntaxe mot-clé DRIVER|(DM) La paire de mots-clés pour le mot clé **DRIVER** contenait une erreur de syntaxe.<br /><br /> (DM) La chaîne * \*d’InConnectionString* contenait un mot clé **FILEDSN,** mais le fichier .dsn ne contenait pas de mot clé **DRIVER** ou d’un mot clé **DSN.**|  
|IM014|Le DSN spécifié contient un décalage architectural entre le conducteur et l’application|(DM) L’application 32 bits utilise une connexion DSN à un conducteur 64 bits; ou vice versa.|  
|IM015|Le conducteur SQLDriverConnect sur SQL_HANDLE_DBC_INFO_HANDLE a échoué|Si un conducteur retourne SQL_ERROR, le gestionnaire de conducteur retournera SQL_ERROR à l’application et la connexion échouera.<br /><br /> Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, voir [Developing Connection-Pool Awareness in an ODBC Driver](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
|S1118|Le conducteur ne prend pas en charge la notification asynchrone|Lorsque le conducteur ne prend pas en charge la notification asynchrone, vous ne pouvez pas définir SQL_ATTR_ASYNC_DBC_EVENT ou SQL_ATTR_ASYNC_DBC_RETCODE_PTR.|  
  
## <a name="comments"></a>Commentaires  
 Une chaîne de connexion a la syntaxe suivante :  
  
 *connexion-corde* ::md *à chaîne vide*[;] &#124; *attribut*[;] &#124; *attribut*; *chaîne de connexion*  
  
 *à chaîne vide* ::*attribut* ::'attribut-mot-clé’valeur *attribute-keyword*=*attribute-value* &#124; DRIVER[]*attribut-valeur*[]  
  
 *attribut-mot-clé* :: DSN &#124; UID &#124; PWD &#124; *conducteur défini-attribut-mot-mot*  
  
 *attribut-valeur* ::md *caractère-corde*  
  
 *moteur-défini-attribut-mot-mot* ::' *identifiant*  
  
 où *la chaîne de caractères* a zéro ou plus de caractères; *l’identifiant* a un ou plusieurs caractères; *attribut-mot-clé* n’est pas sensible aux cas; *la valeur d’attribut* peut être sensible aux cas; et la valeur du mot clé **DSN** ne se compose pas uniquement de blancs.  
  
 En raison de la grammaire de fichier de connexion et de initialisation, mots clés et valeurs d’attribut qui contiennent les caractères **[]{}(),;? Il \*** faut éviter de ne pas être inclus avec des accolades. La valeur du mot clé **DSN** ne peut pas se composer uniquement de blancs et ne doit pas contenir de blancs de premier plan. En raison de la grammaire des informations du système, les mots\\clés et les noms de source de données ne peuvent pas contenir le caractère de barre oblique inverse ( ) .  
  
 Les applications n’ont pas à ajouter des accolades autour de la valeur d’attribut après le mot clé **DRIVER** à moins que l’attribut ne contienne un point-virgule (;), auquel cas les accolades sont nécessaires. Si la valeur d’attribut que le conducteur reçoit comprend des accolades, le conducteur ne doit pas les enlever, mais ils doivent faire partie de la chaîne de connexion retournée.  
  
 Une valeur DSN ou chaîne de{}connexion entourée d’accolades () contenant l’un des personnages **[]{}(),;? Le \*conducteur** est transmis intact. Toutefois, lors de l’utilisation de ces caractères dans un mot clé, le gestionnaire de pilote renvoie une erreur lorsque vous travaillez avec des DSN de fichier, mais passe la chaîne de connexion au pilote pour les chaînes de connexion régulières. Évitez d’utiliser des accolades intégrées dans une valeur de mot clé.  
  
 La chaîne de connexion peut inclure n’importe quel nombre de mots clés définis par le conducteur. Étant donné que le mot clé **DRIVER** n’utilise pas les informations provenant des informations du système, le pilote doit définir suffisamment de mots clés pour qu’un pilote puisse se connecter à une source de données en utilisant uniquement les informations contenues dans la chaîne de connexion. (Pour plus d’informations, voir « Lignes directrices sur les conducteurs », plus tard dans cette section.) Le conducteur définit les mots clés qui sont requis pour se connecter à la source de données.  
  
 Le tableau suivant décrit les valeurs d’attributs de la **DSN**, **FILEDSN**, **DRIVER**, **UID**, **PWD**, et les mots clés **SAVEFILE.**  
  
|Mot clé|Description de la valeur d’attribut|  
|-------------|---------------------------------|  
|**Dsn**|Nom d’une source de données retournée par **SQLDataSources** ou la boîte de dialogue des sources de données de **SQLDriverConnect**.|  
|**FILEDSN (EN)**|Nom d’un fichier .dsn à partir duquel une chaîne de connexion sera construite pour la source de données. Ces sources de données sont appelées sources de données de fichiers.|  
|**Pilote**|Description du conducteur tel que retourné par la fonction **SQLDrivers.** Par exemple, Rdb ou SQL Server.|  
|**Uid**|ID utilisateur.|  
|**Pwd**|Le mot de passe correspondant à l’identifiant de l’utilisateur, ou une chaîne vide s’il n’y a pas de mot de passe pour l’identifiant utilisateur (PWD-;).|  
|**SAVEFILE (EN)**|Le nom de fichier d’un fichier .dsn dans lequel les valeurs d’attribut des mots clés utilisés pour faire le présent, connexion réussie doivent être enregistrées.|  
  
 Pour plus d’informations sur la façon dont une application choisit une source de données ou un pilote, voir [Choisir une source de données ou un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Si des mots clés sont répétés dans la chaîne de connexion, le pilote utilise la valeur associée à la première occurrence du mot clé. Si les mots clés **DSN** et **DRIVER** sont inclus dans la même chaîne de connexion, le Gestionnaire de conducteur et le pilote utilisent le mot clé qui apparaît en premier.  
  
 Les mots-clés **FILEDSN** et **DSN** sont mutuellement exclusifs : quel que soit le mot clé qui apparaît en premier est utilisé, et celui qui apparaît en second est ignoré. Les mots-clés **FILEDSN** et **DRIVER,** en revanche, ne s’excluent pas mutuellement. Si un mot clé apparaît dans une chaîne de connexion avec **FILEDSN**, alors la valeur d’attribut du mot clé dans la chaîne de connexion est utilisée plutôt que la valeur d’attribut du même mot clé dans le fichier .dsn.  
  
 Si le mot clé **FILEDSN** est utilisé, les mots clés spécifiés dans un fichier .dsn sont utilisés pour créer une chaîne de connexion. (Pour plus d’informations, voir « Sources de données de fichiers », plus tard dans cette section.) Le mot clé **UID** est facultatif; un fichier .dsn peut être créé avec seulement le mot clé **DRIVER.** Le mot clé **PWD** n’est pas stocké dans un fichier .dsn. L’annuaire par défaut pour l’enregistrement et le chargement d’un fichier .dsn sera une combinaison du chemin spécifié par **CommonFileDir** dans HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft Windows-CurrentVersion et "ODBC-DataSources". (Si CommonFileDir était « Fichiers communs de programme de C , l’annuaire par défaut serait « C : Fichiers de programme - Fichiers communs -ODBC-Sources de données »).)  
  
> [!NOTE]  
>  Un fichier .dsn peut être manipulé directement en appelant les fonctions [SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md) et [SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md) dans l’installateur DLL.  
  
 Si le mot clé **SAVEFILE** est utilisé, les valeurs d’attribut des mots clés utilisés pour faire le présent, connexion réussie seront enregistrées comme un fichier .dsn avec le nom de la valeur d’attribut du mot clé **SAVEFILE.** Le mot clé **SAVEFILE** doit être utilisé en conjonction avec le mot-clé **DRIVER,** le mot clé **FILEDSN,** ou les deux, ou la fonction retourne SQL_SUCCESS_WITH_INFO avec SQLSTATE 01S09 (mot-clé invalide). Le mot clé **SAVEFILE** doit apparaître avant le mot clé **DRIVER** dans la chaîne de connexion, ou les résultats ne seront pas définis.  
  
## <a name="driver-manager-guidelines"></a>Lignes directrices sur le gestionnaire de conducteur  
 Le gestionnaire de conducteur construit une chaîne de connexion pour passer au conducteur dans l’argument *InConnectionString* de la fonction **SQLDriverConnect** du conducteur. Le gestionnaire de conducteur ne modifie pas l’argument *d’InConnectionString* qui lui a été transmis par la demande.  
  
 L’action du gestionnaire de conducteur est fondée sur la valeur de l’argument *de DriverCompletion* :  
  
-   SQL_DRIVER_PROMPT: Si la chaîne de connexion ne contient ni le **MOT-clé DRIVER**, **DSN**, ou **FILEDSN,** le gestionnaire de pilote affiche la boîte de dialogue Data Sources. Il construit une chaîne de connexion à partir du nom de source de données retourné par la boîte de dialogue et tous les autres mots clés qui lui sont transmis par l’application. Si le nom de source de données retourné par la boîte de dialogue est vide, le gestionnaire de pilote précise la paire de mots-clés DSN-Default. (Cette boîte de dialogue n’affichera pas de source de données avec le nom « Par défaut »).)  
  
-   SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED : Si la chaîne de connexion spécifiée par l’application inclut le mot clé **DSN,** le gestionnaire de conducteur copie la chaîne de connexion spécifiée par l’application. Sinon, il prend les mêmes mesures que lorsqu’il s’agit *de DriverCompletion* est SQL_DRIVER_PROMPT.  
  
-   SQL_DRIVER_NOPROMPT : Le gestionnaire de conducteur copie la chaîne de connexion spécifiée par l’application.  
  
 Si la chaîne de connexion spécifiée par l’application contient le mot clé **DRIVER,** le gestionnaire de pilote copie la chaîne de connexion spécifiée par l’application.  
  
 À l’aide de la chaîne de connexion qu’il a construite, le gestionnaire de conducteur détermine le conducteur à utiliser, se connecte à ce conducteur et passe la chaîne de connexion qu’il a construite au conducteur; pour plus d’informations sur l’interaction du gestionnaire de conducteur et du conducteur, consultez la section « Commentaires » dans [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md). Si la chaîne de connexion ne contient pas le mot clé **DRIVER,** le gestionnaire de conducteur détermine quel pilote utiliser comme suit :  
  
1.  Si la chaîne de connexion contient le mot clé **DSN,** le gestionnaire de pilote récupère le pilote associé à la source de données à partir des informations du système.  
  
2.  Si la chaîne de connexion ne contient pas le mot clé **DSN** ou si la source de données n’est pas trouvée, le gestionnaire de conducteur récupère le pilote associé à la source de données par défaut à partir des informations du système. (Pour plus d’informations, voir [Par défaut Subkey](../../../odbc/reference/install/default-subkey.md).) Le gestionnaire de pilote modifie la valeur du mot clé **DSN** dans la chaîne de connexion en «DEFAULT».  
  
3.  Si le mot clé **DSN** de la chaîne de connexion est défini comme « DEFAULT », le gestionnaire de conducteur récupère le pilote associé à la source de données par défaut à partir des informations du système.  
  
4.  Si la source de données n’est pas trouvée et que la source de données par défaut n’est pas trouvée, le gestionnaire de conducteur retourne SQL_ERROR avec SQLSTATE IM002 (source de données non trouvée et aucun conducteur par défaut spécifié).  
  
## <a name="file-data-sources"></a>Sources de données de fichier  
 Si la chaîne de connexion spécifiée par l’application dans l’appel à **SQLDriverConnect** contient le mot clé **FILEDSN,** et ce mot clé n’est pas remplacé par le mot clé **DSN** ou **DRIVER,** alors le gestionnaire de pilote crée une chaîne de connexion en utilisant les informations contenues dans le fichier .dsn et l’argument *InConnectionString.* Le Driver Manager procède comme suit :  
  
1.  Vérifie si le nom du fichier .dsn est valide. Si ce n’est pas le cas, il retourne SQL_ERROR avec SQLSTATE IM014 (nom invalide du fichier DSN). Si le nom du fichier est une chaîne vide ("") et SQL_DRIVER_NOPROMPT n’est pas spécifié, alors la boîte de dialogue **File-Open** est affichée. Si le nom du fichier contient un chemin valide mais qu’aucun nom de fichier ou nom de fichier invalide, et SQL_DRIVER_NOPROMPT n’est pas spécifié, la boîte de dialogue **File-Open** est affichée avec l’annuaire actuel défini à celui spécifié dans le nom du fichier. Si le nom du fichier est une chaîne vide (")) ou que le nom du fichier contient un chemin valide mais qu’aucun nom de fichier ou un nom de fichier invalide, et SQL_DRIVER_NOPROMPT est spécifié, alors SQL_ERROR est retourné avec SQLSTATE IM014 (nom invalide du fichier DSN).  
  
2.  Lit tous les mots clés dans la section [ODBC] du fichier .dsn. Si le mot clé **DRIVER** n’est pas présent, il renvoie SQL_ERROR avec SQLSTATE IM012 (erreur de syntaxe mot-clé de pilote), sauf lorsque le fichier .dsn est inshareable et ne contient donc que le mot clé **DSN.**  
  
     Si la source de données de fichier n’est pas partageable, le gestionnaire de pilote lit la valeur du mot clé **DSN** et se connecte au besoin à l’utilisateur ou à la source de données du système indiquée par la source de données de fichiers non partageable. Les étapes 3 à 5 ne sont pas exécutées.  
  
3.  Construit une chaîne de connexion pour le conducteur. La chaîne de connexion du conducteur est l’union des mots clés spécifiés dans le fichier .dsn et ceux spécifiés dans la chaîne de connexion d’application originale. Règles pour la construction de la chaîne de connexion du conducteur où les mots clés se chevauchent sont les suivants:  
  
    -   Si le mot clé **DRIVER** existe dans la chaîne de connexion d’application et que les pilotes spécifiés par les mots clés **DRIVER** ne sont pas les mêmes dans le fichier .dsn et la chaîne de connexion d’application, les informations du pilote dans le fichier .dsn sont ignorées et les informations du pilote dans la chaîne de connexion d’application sont utilisées. Si les pilotes spécifiés par le mot clé **DRIVER** sont les mêmes dans le fichier .dsn et la chaîne de connexion de l’application, alors lorsque tous les mots clés se chevauchent, ceux spécifiés dans la chaîne de connexion d’application ont préséance sur ceux spécifiés dans le fichier .dsn.  
  
    -   Dans la nouvelle chaîne de connexion, le mot clé **FILEDSN** est éliminé.  
  
4.  Charge le conducteur en regardant dans l’entrée du registre HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST. INI\\<Nom\>du conducteur \<'Driver où le nom du conducteur> est spécifié par le mot-clé **DRIVER.**  
  
5.  Passe le conducteur de la nouvelle chaîne de connexions.  
  
 Pour des exemples de fichiers .dsn, voir [Connecting Using File Data Sources](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md).  
  
## <a name="savefile-keyword"></a>Mot-clé SAVEFILE  
 Si la chaîne de connexion spécifiée par l’application contient le mot clé **SAVEFILE,** le gestionnaire de pilote enregistre la chaîne de connexion dans un fichier .dsn. Le Driver Manager procède comme suit :  
  
1.  Vérifie si le nom de fichier du fichier .dsn inclus comme valeur d’attribut du mot clé **SAVEFILE** est valide. Si ce n’est pas le cas, il retourne SQL_ERROR avec SQLSTATE IM014 (nom invalide du fichier DSN). La validité du nom du fichier est déterminée par des règles de nommage standard du système. Si le nom du fichier est une chaîne vide (")) et que *l’argument de DriverCompletion* n’est pas SQL_DRIVER_NOPROMPT, alors le nom du fichier est valide. Si le nom du fichier existe déjà, alors si *DriverCompletion* est SQL_DRIVER_NOPROMPT, le fichier est écrasé. Si *DriverCompletion* est SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED, une boîte de dialogue invite l’utilisateur à spécifier si le fichier doit être écrasé. Si le Non est entré, la boîte de dialogue **De File-Save** apparaît.  
  
2.  Si le conducteur retourne SQL_SUCCESS et que le nom du fichier n’était pas une chaîne vide, le gestionnaire de conducteur écrit les informations de connexion retournées dans *l’argument OutConnectionString* au fichier spécifié avec le format spécifié dans la section « Chaînes de connexion » plus tôt dans cette section.  
  
3.  Si le conducteur retourne SQL_SUCCESS et que le nom du fichier était une chaîne vide («), alors le gestionnaire de pilote appelle la boîte de dialogue commune **File-Save** avec le *hwnd* spécifié et écrit les informations de connexion retournées dans *OutConnectionString* au fichier spécifié dans la boîte de dialogue commune File-Save avec le format spécifié dans la section "Connection Strings" plus tôt dans cette section.  
  
4.  Si le conducteur retourne SQL_SUCCESS, il renvoie l’argument *OutConnectionString* contenant la chaîne de connexion à l’application.  
  
5.  Si le conducteur retourne SQL_SUCCESS_WITH_INFO ou SQL_ERROR, le gestionnaire de conducteur retourne le SQLSTATE à la demande.  
  
## <a name="driver-guidelines"></a>Lignes directrices sur les conducteurs  
 Le conducteur vérifie si la chaîne de connexion qui lui est transmise par le gestionnaire de conducteur contient le mot clé **DSN** ou **DRIVER.** Si la chaîne de connexion contient le mot clé **DRIVER,** le pilote ne peut pas récupérer d’informations sur la source de données à partir des informations du système. Si la chaîne de connexion contient le mot clé **DSN** ou ne contient ni le **DSN** ni le mot clé **DRIVER,** le pilote peut récupérer des informations sur la source de données à partir des informations du système comme suit :  
  
1.  Si la chaîne de connexion contient le mot clé **DSN,** le pilote récupère les informations pour la source de données spécifiée.  
  
2.  Si la chaîne de connexion ne contient pas le mot clé **DSN,** que la source de données spécifiée n’est pas trouvée ou que le mot clé **DSN** est défini comme « DEFAULT », le conducteur récupère les informations pour la source de données par défaut.  
  
 Le conducteur utilise toutes les informations qu’il récupère à partir des informations du système pour augmenter les informations qui lui sont transmises dans la chaîne de connexion. Si les informations contenues dans le système doublent les informations contenues dans la chaîne de connexion, le pilote utilise les informations contenues dans la chaîne de connexion.  
  
 Basé sur la valeur de *DriverCompletion*, le pilote invite l’utilisateur pour des informations de connexion, telles que l’identifiant de l’utilisateur et mot de passe, et se connecte à la source de données:  
  
-   SQL_DRIVER_PROMPT : Le conducteur affiche une boîte de dialogue, en utilisant les valeurs de la chaîne de connexion et des informations système (le cas échéant) comme valeurs initiales. Lorsque l’utilisateur sort de la boîte de dialogue, le pilote se connecte à la source de données. Il construit également une chaîne de connexion à **DRIVER** partir de \*la valeur du mot clé **DSN** ou DRIVER dans *InConnectionString* et les informations retournées de la boîte de dialogue. Il place cette chaîne de connexion dans le tampon*OutConnectionString.*  
  
-   SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED: Si la chaîne de connexion contient suffisamment d’informations, et que les informations \*sont correctes, \*le pilote se connecte à la source de données et des copies *InConnectionString* à *OutConnectionString*. Si des informations sont manquantes ou incorrectes, le conducteur prend les mêmes mesures que lorsque *DriverCompletion* est SQL_DRIVER_PROMPT, sauf que si *DriverCompletion* est SQL_DRIVER_COMPLETE_REQUIRED, le conducteur désactive les commandes pour toute information qui n’est pas requise pour se connecter à la source de données.  
  
-   SQL_DRIVER_NOPROMPT: Si la chaîne de connexion contient suffisamment d’informations, \*le pilote se \*connecte à la source de données et des copies *InConnectionString* à *OutConnectionString*. Sinon, le pilote retourne SQL_ERROR pour **SQLDriverConnect**.  
  
 Sur la connexion réussie à la \*source de données, le pilote définit également *StringLength2Ptr* à la longueur de la chaîne de connexion de sortie qui est disponible pour revenir dans *'OutConnectionString*.  
  
 Si l’utilisateur annule une boîte de dialogue présentée par le Driver Manager ou le pilote, **SQLDriverConnect** renvoie SQL_NO_DATA.  
  
 Pour plus d’informations sur la façon dont le gestionnaire de conducteur et le conducteur interagissent pendant le processus de connexion, consultez [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Si un pilote prend en charge **SQLDriverConnect**, la section mot-clé du pilote des informations du système pour le pilote doit contenir le mot clé **ConnectFunctions** avec le deuxième caractère réglé sur "Y".  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>Connexion lorsque la mise en commun des connexions est activée  
 La mise en commun des connexions permet à une application de réutiliser une connexion qui a déjà été créée. Lorsque **SQLDriverConnect** est appelé, le gestionnaire de conducteur tente de faire la connexion en utilisant une connexion qui fait partie d’un pool de connexions dans un environnement qui a été désigné pour la mise en commun des connexions. Pour plus d’informations sur la mise en commun des connexions, voir [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
 Une application peut définir SQL_ATTR_RESET_CONNECTION avant d’appeler SQLDisconnect sur une connexion où la mise en commun est activée. Pour plus d’informations, voir [SQLSetConnectAttr Function](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Les restrictions suivantes s’appliquent lorsqu’une demande appelle **SQLDriverConnect** pour se connecter à une connexion mise en commun :  
  
-   Aucun traitement de mise en commun de connexion n’est effectué lorsque le mot clé **SAVEFILE** est spécifié dans la chaîne de connexion.  
  
-   Si la mise en commun des connexions est activée, **SQLDriverConnect** ne peut être appelé qu’avec un argument *de conformité de conducteur* de SQL_DRIVER_NOPROMPT ; si **SQLDriverConnect** est appelé avec toute autre *conformité de conducteur,* SQLSTATE HY110 (achèvement du conducteur invalide) sera retourné.  
  
## <a name="connection-attributes"></a>Attributs de connexion  
 L’attribut de connexion SQL_ATTR_LOGIN_TIMEOUT, défini à l’aide de **SQLSetConnectAttr**, définit le nombre de secondes pour attendre une demande de connexion pour compléter avec une connexion réussie par le conducteur avant de revenir à l’application. Si l’utilisateur est invité à remplir la chaîne de connexion, une période d’attente pour chaque demande de connexion commence lorsque le pilote commence le processus de connexion.  
  
 Le conducteur ouvre la connexion en mode d’accès SQL_MODE_READ_WRITE par défaut. Pour définir le mode d’accès à SQL_MODE_READ_ONLY, l’application doit appeler **SQLSetConnectAttr** avec l’attribut SQL_ATTR_ACCESS_MODE avant d’appeler **SQLDriverConnect**.  
  
 Si une bibliothèque de traduction par défaut est spécifiée dans les informations système pour la source de données, le conducteur la charge. Une bibliothèque de traduction différente peut être chargée en appelant **SQLSetConnectAttr** avec l’attribut SQL_ATTR_TRANSLATE_LIB. Une option de traduction peut être spécifiée en appelant **SQLSetConnectAttr** avec l’option SQL_ATTR_TRANSLATE_OPTION.  
  
 Pour plus d’informations, voir [Connecting with SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md).  
  
```cpp  
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
  
 Voir aussi [l’exemple ODBC Program](../../../odbc/reference/sample-odbc-program.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Découvrir et énumérer les valeurs requises pour se connecter à une source de données|[Fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connexion à une source de données|[Fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Déconnecter d’une source de données|[SQLDisconnect, fonction](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|Retour des descriptions et attributs des conducteurs|[SQLDrivers, fonction](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|Libérer une poignée|[Fonction SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Définir un attribut de connexion|[Fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
