---
title: SQLAllocHandle Function | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLAllocHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLAllocHandle
helpviewer_keywords:
- SQLAllocHandle function [ODBC]
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db8bcf70823401f60efc316caabe283f5be59f48
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538102"
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLAllocHandle** alloue un handle d’environnement, connexion, instruction ou descripteur.  
  
> [!NOTE]  
>  Cette fonction est une fonction générique pour allouer des handles qui remplace les fonctions ODBC 2.0 **SQLAllocConnect**, **SQLAllocEnv**, et **SQLAllocStmt**. Pour permettre aux applications appelant **SQLAllocHandle** pour travailler avec ODBC 2. *x* pilotes, un appel à **SQLAllocHandle** est mappé dans le Gestionnaire de pilotes à **SQLAllocConnect**, **SQLAllocEnv**, ou  **SQLAllocStmt**, le cas échéant. Pour plus d’informations, consultez « Commentaires ». Pour plus d’informations sur quelles le Gestionnaire de pilotes mappe cette fonction lorsqu’un ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote, consultez [mappage des fonctions de remplacement pour une compatibilité descendante des Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type de handle doit être allouée par **SQLAllocHandle**. Doit être une des valeurs suivantes :  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 Handle SQL_HANDLE_DBC_INFO_TOKEN est utilisée uniquement par le Gestionnaire de pilotes et le pilote. Applications ne doivent pas utiliser ce type de handle. Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, consultez [développer la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *InputHandle*  
 [Entrée] Le handle d’entrée dans le contexte duquel le nouveau handle doit être allouée. Si *HandleType* est SQL_HANDLE_ENV, il s’agit de SQL_NULL_HANDLE. Si *HandleType* est SQL_HANDLE_DBC, cela doit être un handle d’environnement, et si elle est SQL_HANDLE_STMT ou SQL_HANDLE_DESC, il doit être un handle de connexion.  
  
 *OutputHandlePtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le handle à la structure de données nouvellement allouée.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_INVALID_HANDLE ou SQL_ERROR.  
  
 Lors de l’allocation d’un handle autre qu’un handle d’environnement, si **SQLAllocHandle** retourne SQL_ERROR, elle définit *OutputHandlePtr* SQL_NULL_HDBC, SQL_NULL_HSTMT ou SQL_NULL_HDESC, selon le valeur de *HandleType*, sauf si l’argument de sortie est un pointeur null. L’application peut obtenir ensuite des informations supplémentaires à partir de la structure de données de diagnostic associée au handle dans le *InputHandle* argument.  
  
## <a name="environment-handle-allocation-errors"></a>Environnement gérer les erreurs d’Allocation  
 Allocation de l’environnement se produit dans le Gestionnaire de pilotes et au sein de chaque pilote. L’erreur renvoyée par **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV varie selon le niveau dans lequel l’erreur s’est produite.  
  
 Si le Gestionnaire de pilotes ne peut pas allouer de la mémoire pour  *\*OutputHandlePtr* lorsque **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV est appelée, ou application fournit un pointeur null pour *OutputHandlePtr*, **SQLAllocHandle** retourne SQL_ERROR. Définit le Gestionnaire de pilotes **OutputHandlePtr* à SQL_NULL_HENV (sauf si l’application a fourni un pointeur null, ce qui retourne SQL_ERROR). Il n’existe aucun handle auquel associer les informations de diagnostic supplémentaires.  
  
 Le Gestionnaire de pilotes n’appelle pas la fonction d’allocation du handle d’environnement au niveau du pilote jusqu'à ce que l’application appelle **SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect**. Si une erreur se produit dans le niveau de pilote **SQLAllocHandle** (fonction), puis le Gestionnaire de pilotes-niveau **SQLConnect**, **SQLBrowseConnect**, ou  **SQLDriverConnect** fonction retourne SQL_ERROR. La structure de données de diagnostic contient SQLSTATE IM004 (chauffeur **SQLAllocHandle** a échoué). L’erreur est retournée sur un handle de connexion.  
  
 Pour plus d’informations sur le flux d’appels de fonction entre le Gestionnaire de pilotes et d’un pilote, consultez [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLAllocHandle** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec le bon *HandleType* et *gérer* la valeur de *InputHandle*. SQL_SUCCESS_WITH_INFO (mais pas SQL_ERROR) peuvent être retournées pour le *OutputHandle* argument. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLAllocHandle** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) le *HandleType* argument était SQL_HANDLE_STMT ou SQL_HANDLE_DESC, mais la connexion spécifiée par la *InputHandle* argument n’est pas ouvert. La connexion doit être terminée avec succès (et la connexion doit être ouverte) pour le pilote à allouer une instruction ou un descripteur de handle.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le **MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le Gestionnaire de pilotes (DM) n’a pas pu allouer de la mémoire pour le handle spécifié.<br /><br /> Le pilote n’a pas pu allouer de la mémoire pour le handle spécifié.|  
|HY009|Utilisation non valide de pointeur null|(DM) le *OutputHandlePtr* argument était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) le *HandleType* SQL_HANDLE_DBC, a été l’argument et **SQLSetEnvAttr** n’a pas été appelé pour définir l’attribut d’environnement SQL_ODBC_VERSION.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le **InputHandle** et était en cours d’exécution lorsque le **SQLAllocHandle** fonction a été appelée avec **HandleType** définie à SQL_HANDLE_STMT ou SQL_HANDLE_DESC.|  
|HY013|Erreur de gestion de mémoire|Le *HandleType* argument était SQL_HANDLE_DBC, SQL_HANDLE_STMT ou SQL_HANDLE_DESC ; et l’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, éventuellement en raison d’une mémoire insuffisante conditions.|  
|HY014|Limite du nombre de handles a été atteint|La limite définie par le pilote pour le nombre de handles qui peuvent être alloués pour le type de handle est indiqué par le *HandleType* argument a été atteint.|  
|HY092|Identificateur d’option/attribut non valide|(DM) le *HandleType* argument n’était pas : SQL_HANDLE_ENV, SQL_HANDLE_DBC, SQL_HANDLE_STMT, or SQL_HANDLE_DESC.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|Le *HandleType* SQL_HANDLE_DESC a été l’argument et le pilote a été un ODBC 2. *x* pilote.|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le *HandleType* SQL_HANDLE_STMT a été l’argument et le pilote n’a pas un pilote ODBC valid.<br /><br /> (DM) le *HandleType* SQL_HANDLE_DESC a été l’argument et le pilote ne prend pas en charge l’allocation d’un handle de descripteur.|  
  
## <a name="comments"></a>Commentaires  
 **SQLAllocHandle** est utilisé pour allouer des handles pour les environnements, les connexions, les instructions et les descripteurs, comme décrit dans les sections suivantes. Pour obtenir des informations générales sur les descripteurs, consultez [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Plus d’un handle d’environnement, de connexion ou de l’instruction peut être alloué par une application à la fois si plusieurs allocations sont pris en charge par le pilote. Dans ODBC, aucune limite n’est définie sur le nombre d’environnement, connexion, instruction ou les handles de descripteur qui peuvent être alloués à tout moment. Pilotes peuvent imposer une limite sur le nombre d’un certain type de handle qui peut être alloué à la fois. Pour plus d’informations, consultez la documentation du pilote.  
  
 Si l’application appelle **SQLAllocHandle** avec  *\*OutputHandlePtr* défini sur un environnement, connexion, instruction ou handle de descripteur qui existe déjà, le pilote remplace le informations associées à la *gérer*, sauf si l’application est à l’aide de connexion mise en pool (voir « Allocation d’un environnement attribut pour le regroupement de connexions » plus loin dans cette section). Le Gestionnaire de pilotes ne vérifie pas si le *gérer* entré dans  *\*OutputHandlePtr* est déjà utilisé, ni aucune vérifier le contenu d’une poignée précédent avant de les remplacer .  
  
> [!NOTE]  
>  Il s’agit de la programmation d’applications ODBC incorrecte pour appeler **SQLAllocHandle** deux fois avec la même variable d’application définie pour  *\*OutputHandlePtr* sans appeler  **SQLFreeHandle** pour libérer le handle avant de réallouer. Remplacement ODBC gère de manière peut entraîner un comportement incohérent ou erreur de la part des pilotes ODBC.  
  
 Sur les systèmes d’exploitation qui prennent en charge de plusieurs threads, les applications peuvent utiliser le même handle d’environnement, connexion, instruction ou descripteur sur différents threads. Pilotes doivent donc prendre en charge les accès multithread-safe à ces informations ; par exemple, il est une façon d’effectuer cette opération, à l’aide d’un sémaphore ou une section critique. Pour plus d’informations à propos du threading, consultez [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
 **SQLAllocHandle** ne définit pas l’attribut d’environnement SQL_ATTR_ODBC_VERSION lorsqu’elle est appelée pour allouer un handle d’environnement ; l’attribut de l’environnement doit être défini par l’application, ou SQLSTATE HY010 sera de (erreur de séquence de fonction) retourné lorsque **SQLAllocHandle** est appelée pour allouer un handle de connexion.  
  
 Pour les applications conformes aux normes, **SQLAllocHandle** est mappé à **SQLAllocHandleStd** au moment de la compilation. La différence entre ces deux fonctions est que **SQLAllocHandleStd** définit l’attribut d’environnement SQL_ATTR_ODBC_VERSION à SQL_OV_ODBC3 lorsqu’elle est appelée avec le *HandleType* définie SQL comme argument _HANDLE_ENV. Pour cela, car les applications conformes aux normes sont toujours ODBC 3. *x* applications. En outre, les normes ne nécessitent pas la version de l’application à inscrire. Ceci est la seule différence entre ces deux fonctions. Sinon, elles sont identiques. **SQLAllocHandleStd** est mappé à **SQLAllocHandle** à l’intérieur du Gestionnaire de pilotes. Par conséquent, les pilotes tiers n’ont pas à implémenter **SQLAllocHandleStd**.  
  
 Les applications ODBC 3.8 doivent utiliser :  
  
-   **SQLAllocHandle et pas SQLAllocHandleStd** pour allouer un handle d’environnement.  
  
-   **SQLSetEnvAttr** à la valeur de l’attribut d’environnement SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3_80.  
  
## <a name="allocating-an-environment-handle"></a>Allocation d'un handle d'environnement  
 Un handle d’environnement fournit l’accès aux informations globales telles que les handles de connexion valide et les handles de connexion active. Pour obtenir des informations générales sur les handles d’environnement, consultez [Handles d’environnement](../../../odbc/reference/develop-app/environment-handles.md).  
  
 Pour demander un handle d’environnement, une application appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV et un *InputHandle* de SQL_NULL_HANDLE. Le pilote alloue la mémoire pour les informations de l’environnement et les transmet la valeur du handle associé de nouveau la  *\*OutputHandlePtr* argument. L’application transmet le  *\*OutputHandle* valeur dans tous les appels ultérieurs qui nécessitent un argument de handle d’environnement. Pour plus d’informations, consultez [allouer le Handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Sous le handle d’environnement d’un gestionnaire de pilotes, s’il existe de déjà handle d’environnement d’un pilote, puis **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV n’est pas appelée dans ce pilote lorsqu’un connexion est établie uniquement **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC. Si le handle d’environnement d’un pilote n’existe pas sous le handle d’environnement du Gestionnaire de pilotes, SQLAllocHandle avec un HandleType égal à SQL_HANDLE_ENV et SQLAllocHandle avec un HandleType de SQL_HANDLE_DBC sont appelées dans le pilote lors de la première connexion handle de l’environnement est connecté au pilote.  
  
 Lorsque le Gestionnaire de pilotes traite le **SQLAllocHandle** fonctionne avec un *HandleType* de SQL_HANDLE_ENV, il vérifie le **Trace** mot clé dans la section [ODBC] du système plus d’informations. Si elle est définie sur 1, le Gestionnaire de pilotes permet le suivi de l’application actuelle. Si l’indicateur de trace est défini, le suivi commence lorsque le handle d’environnement est alloué et se termine lorsque le dernier handle d’environnement est libéré. Pour plus d’informations, consultez [configuration des Sources de données](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Après avoir alloué un handle d’environnement, une application doit appeler **SQLSetEnvAttr** sur le handle d’environnement pour définir l’attribut d’environnement SQL_ATTR_ODBC_VERSION. Si cet attribut n’est pas défini avant **SQLAllocHandle** est appelée pour allouer un handle de connexion sur l’environnement, l’appel à allouer la connexion retourne SQLSTATE HY010 (erreur de séquence de fonction). Pour plus d’informations, consultez [déclarant ODBC Version l’Application](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md).  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>Allocation des environnements partagés pour le regroupement de connexions  
 Environnements peuvent être partagés entre plusieurs composants sur un seul processus. Un environnement partagé peut être utilisé par plusieurs composants en même temps. Lorsqu’un composant utilise un environnement partagé, il peut utiliser des connexions regroupées, ce qui lui permettent d’allouer et d’utiliser une connexion existante sans recréer cette connexion.  
  
 Avant de l’allocation d’un environnement partagé qui peut être utilisé pour le regroupement de connexions, une application doit appeler **SQLSetEnvAttr** à la valeur de l’attribut d’environnement SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER ou SQL_CP_ONE_PER_ HENV. **SQLSetEnvAttr** dans ce cas est appelé avec *EnvironmentHandle* la valeur null, ce qui rend l’attribut à un attribut au niveau du processus.  
  
 Une fois que le regroupement de connexions a été activé, une application appelle **SQLAllocHandle** avec la *HandleType* argument défini à SQL_HANDLE_ENV. L’environnement alloué par cet appel peut être un environnement partagé implicit, car le regroupement de connexions a été activé.  
  
 Lorsqu’un environnement partagé est alloué, l’environnement qui sera utilisé n’est pas déterminée jusque **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC est appelée. À ce stade, le Gestionnaire de pilotes tente de trouver un environnement existant qui correspond aux attributs d’environnement demandés par l’application. Si aucun environnement n’existe, un est créé comme un environnement partagé. Le Gestionnaire de pilotes conserve un décompte de références pour chaque environnement partagé ; le nombre est défini sur 1 lorsque l’environnement est créé. Si un environnement correspondant est trouvé, le descripteur de cet environnement est renvoyé à l’application et le décompte de références est incrémenté. Un handle d’environnement alloué de cette manière peut être utilisé dans n’importe quelle fonction ODBC qui accepte un handle d’environnement comme argument d’entrée.  
  
## <a name="allocating-a-connection-handle"></a>Allocation d'un handle de connexion  
 Un handle de connexion fournit l’accès aux informations telles que l’instruction valide et ouvrir des handles de descripteur sur la connexion et indique si une transaction est en cours. Pour obtenir des informations générales sur les handles de connexion, consultez [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md).  
  
 Pour demander un handle de connexion, une application appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC. Le *InputHandle* argument est défini sur le handle d’environnement qui a été retourné par l’appel à **SQLAllocHandle** qui allouée ce descripteur. Le pilote alloue la mémoire pour les informations de connexion et passe de nouveau la valeur du handle associé  *\*OutputHandlePtr*. L’application transmet le  *\*OutputHandlePtr* valeur dans tous les appels ultérieurs qui nécessitent un handle de connexion. Pour plus d’informations, consultez [allouer un Handle de connexion](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md).  
  
 Le Gestionnaire de pilotes traite le **SQLAllocHandle** de fonction et appelle le pilote **SQLAllocHandle** fonctionner lorsque l’application appelle **SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect**. (Pour plus d’informations, consultez [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).)  
  
 Si l’attribut d’environnement SQL_ATTR_ODBC_VERSION n’est pas définie avant **SQLAllocHandle** est appelée pour allouer un handle de connexion sur l’environnement, l’appel à allouer la connexion retourne SQLSTATE HY010 (séquence de fonction erreur).  
  
 Lorsqu’une application appelle **SQLAllocHandle** avec la *InputHandle* argument ayant pour valeur SQL_HANDLE_DBC et également définie sur un handle d’environnement partagé, le Gestionnaire de pilotes essaie de trouver un partagée existante environnement qui correspond aux attributs d’environnement définies par l’application. Si aucun environnement n’existe, est créé, avec un décompte de références (géré par le Gestionnaire de pilotes) de 1. Si une correspondance partagé environnement est trouvé, ce handle est retourné à l’application et son décompte de références est incrémenté.  
  
 La connexion réelle qui sera utilisée n’est pas déterminée par le Gestionnaire de pilote jusqu'à ce que **SQLConnect** ou **SQLDriverConnect** est appelée. Le Gestionnaire de pilotes utilise les options de connexion dans l’appel à **SQLConnect** (ou les mots clés de connexion dans l’appel à **SQLDriverConnect**) et les attributs de connexion définie après l’allocation de connexion déterminer quelle connexion dans le pool doit être utilisée. Pour plus d’informations, consultez [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="allocating-a-statement-handle"></a>Allocation d'un descripteur d'instruction  
 Un descripteur d’instruction permet d’accéder aux informations de l’instruction, telles que les messages d’erreur, le nom du curseur et les informations d’état pour le traitement d’instruction SQL. Pour obtenir des informations générales sur les descripteurs d’instruction, consultez [descripteurs d’instruction](../../../odbc/reference/develop-app/statement-handles.md).  
  
 Pour demander un descripteur d’instruction, une application se connecte à une source de données, puis appelle **SQLAllocHandle** avant qu’il envoie les instructions SQL. Dans cet appel, *HandleType* doit être défini à SQL_HANDLE_STMT et *InputHandle* doit être défini sur le handle de connexion qui a été retourné par l’appel à **SQLAllocHandle** Ce handle attribuée. Le pilote alloue la mémoire pour les informations de l’instruction, associe le handle d’instruction avec la connexion spécifiée et passe de nouveau la valeur du handle associé  *\*OutputHandlePtr*. L’application transmet le  *\*OutputHandlePtr* valeur dans tous les appels ultérieurs qui nécessitent un descripteur d’instruction. Pour plus d’informations, consultez [allouer un Handle d’instruction](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md).  
  
 Quand le handle d’instruction est alloué, le pilote alloue un ensemble de descripteurs de quatre automatiquement et assigne les poignées pour ces descripteurs le SQL_ATTR_APP_ROW_DESC SQL_ATTR_APP_PARAM_DESC, SQL_ATTR_IMP_ROW_DESC et SQL_ATTR_IMP_PARAM_DESC attributs d’instruction. Ils sont désignés comme *implicitement* allouée descripteurs. Pour allouer un descripteur d’application explicitement, consultez la section suivante, « Allocation d’un Handle de descripteur ».  
  
## <a name="allocating-a-descriptor-handle"></a>Allocation d’un Handle de descripteur  
 Lorsqu’une application appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DESC, le pilote alloue un descripteur d’application. Ils sont désignés comme *explicitement* allouée descripteurs. L’application dirige un pilote à utiliser un descripteur d’application explicitement alloué au lieu d’un alloué automatiquement pour un descripteur d’instruction donné en appelant le **SQLSetStmtAttr** avec la SQL_ATTR_APP_ROW_DESC (fonction) ou un attribut SQL_ATTR_APP_PARAM_DESC. Un descripteur d’implémentation ne peut pas être alloué explicitement, ni un descripteur d’implémentation de données peut être spécifié dans un **SQLSetStmtAttr** appel de fonction.  
  
 Descripteurs alloués explicitement sont associés à un handle de connexion au lieu d’un descripteur d’instruction (comme descripteurs alloués automatiquement). Descripteurs restent allouées uniquement lorsqu’une application est réellement connectée à la base de données. Descripteurs alloués explicitement étant associés à un handle de connexion, une application peut associer un descripteur explicitement alloué plusieurs instructions au sein d’une connexion. Un descripteur d’application alloués implicitement, en revanche, ne peut pas être associé à plus d’un descripteur d’instruction. (Il ne peut pas être associé à n’importe quel handle d’instruction autre que celui qui il a été alloué pour.) Handles de descripteur alloué de manière explicite peuvent être libérées explicitement par l’application ou en appelant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DESC, ou implicitement lorsque la connexion est fermé.  
  
 Lorsque le descripteur explicitement alloué est libéré, le descripteur alloué implicitement est à nouveau associé avec l’instruction. (L’attribut SQL_ATTR_APP_ROW_DESC ou SQL_ATTR_APP_PARAM_DESC pour cette instruction est à nouveau défini sur le handle de descripteur alloué de manière implicite.) Cela est vrai pour toutes les instructions qui ont été associées dans le descripteur alloué de manière explicite sur la connexion.  
  
 Pour plus d’informations sur les descripteurs, consultez [descripteurs](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Exemple de code  
 Consultez [exemple de programme ODBC](../../../odbc/reference/sample-odbc-program.md), [fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), et [SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|L’exécution d’une instruction SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécuter une instruction SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Libération d’un handle d’environnement, connexion, instruction ou descripteur|[SQLFreeHandle, fonction](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Préparation d’une instruction pour l’exécution|[SQLPrepare, fonction](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Définition d’un attribut de connexion|[SQLSetConnectAttr, fonction](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Définition d’un champ de descripteur|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Définition d’un attribut d’environnement|[SQLSetEnvAttr, fonction](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Définition d’un attribut d’instruction|[SQLSetStmtAttr, fonction](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
