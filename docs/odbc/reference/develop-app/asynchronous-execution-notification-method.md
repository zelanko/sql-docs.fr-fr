---
title: Exécution asynchrone (méthode de notification) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 250e71dcb47d44a6e437d12c269ea23fa6fb3c2c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306410"
---
# <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)
ODBC permet l’exécution asynchrone d’opérations de connexion et d’instruction. Un thread d’application peut appeler une fonction ODBC en mode asynchrone et la fonction peut retourner avant que l’opération ne soit terminée, ce qui permet au thread d’application d’effectuer d’autres tâches. Dans le kit de développement logiciel (SDK) Windows 7, pour les opérations de connexion ou d’instruction asynchrones, une application a déterminé que l’opération asynchrone a été effectuée à l’aide de la méthode d’interrogation. Pour plus d’informations, consultez [exécution asynchrone (méthode d’interrogation)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). À compter du kit de développement logiciel (SDK) Windows 8, vous pouvez déterminer qu’une opération asynchrone est terminée à l’aide de la méthode de notification.  
  
 Dans la méthode d’interrogation, les applications doivent appeler la fonction asynchrone chaque fois qu’elle souhaite l’état de l’opération. La méthode de notification est semblable à callback et attend dans ADO.NET. Toutefois, ODBC utilise les événements Win32 comme objet de notification.  
  
 La bibliothèque de curseurs ODBC et la notification asynchrone ODBC ne peuvent pas être utilisées en même temps. La définition des deux attributs renverra une erreur avec SQLSTATE S1119 (la bibliothèque de curseurs et la notification asynchrone ne peuvent pas être activées en même temps).  
  
 Pour plus d’informations sur les développeurs de pilotes, consultez [notification de la saisie semi-automatique des fonctions asynchrones](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) .  
  
> [!NOTE]  
>  La méthode de notification n’est pas prise en charge avec la bibliothèque de curseurs. Une application recevra un message d’erreur si elle tente d’activer la bibliothèque de curseurs via SQLSetConnectAttr, lorsque la méthode de notification est activée.  
  
## <a name="overview"></a>Vue d’ensemble  
 Lorsqu’une fonction ODBC est appelée en mode asynchrone, le contrôle est retourné immédiatement à l’application appelante avec le code de retour SQL_STILL_EXECUTING. L’application doit interroger la fonction à plusieurs reprises jusqu’à ce qu’elle retourne une valeur autre que SQL_STILL_EXECUTING. La boucle d’interrogation augmente l’utilisation du processeur, ce qui entraîne des performances médiocres dans de nombreux scénarios asynchrones.  
  
 Chaque fois que le modèle de notification est utilisé, le modèle d’interrogation est désactivé. Les applications ne doivent pas appeler à nouveau la fonction d’origine. Appelez la [fonction SQLCompleteAsync](../../../odbc/reference/syntax/sqlcompleteasync-function.md) pour terminer l’opération asynchrone. Si une application appelle à nouveau la fonction d’origine avant la fin de l’opération asynchrone, l’appel retourne SQL_ERROR avec SQLSTATE IM017 (l’interrogation est désactivée en mode de notification asynchrone).  
  
 Lorsque vous utilisez le modèle de notification, l’application peut appeler **SQLCancel** ou **SQLCancelHandle** pour annuler une opération de connexion ou d’instruction. Si la demande d’annulation réussit, ODBC retourne SQL_SUCCESS. Ce message n’indique pas que la fonction a effectivement été annulée ; elle indique que la demande d’annulation a été traitée. Le fait que la fonction soit effectivement annulée dépend du pilote et de la source de données. Lorsqu’une opération est annulée, le gestionnaire de pilotes signale toujours l’événement. Le gestionnaire de pilotes retourne SQL_ERROR dans la mémoire tampon de code de retour et l’État est SQLSTATE HY008 (opération annulée) pour indiquer que l’annulation a réussi. Si la fonction a terminé son traitement normal, le gestionnaire de pilotes retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO.  
  
### <a name="downlevel-behavior"></a>Comportement de niveau inférieur  
 La version du gestionnaire de pilotes ODBC qui prend en charge cette notification est ODBC 3,81.  
  
|Version de l’application ODBC|Version du gestionnaire de pilotes|Version du pilote|Comportement|  
|------------------------------|----------------------------|--------------------|--------------|  
|Nouvelle application d’une version ODBC|ODBC 3,81|Pilote ODBC 3,80|L’application peut utiliser cette fonctionnalité si le pilote prend en charge cette fonctionnalité. dans le cas contraire, le gestionnaire de pilotes génère une erreur.|  
|Nouvelle application d’une version ODBC|ODBC 3,81|Pilote antérieur à ODBC 3,80|Le gestionnaire de pilotes génère une erreur si le pilote ne prend pas en charge cette fonctionnalité.|  
|Nouvelle application d’une version ODBC|Pré-ODBC 3,81|Quelconque|Lorsque l’application utilise cette fonctionnalité, un ancien gestionnaire de pilotes considère les nouveaux attributs comme des attributs spécifiques au pilote et le pilote doit générer une erreur. Un nouveau gestionnaire de pilotes ne passera pas ces attributs au pilote.|  
  
 Une application doit vérifier la version du gestionnaire de pilotes avant d’utiliser cette fonctionnalité. Dans le cas contraire, si un pilote mal écrit ne s’affiche pas et que la version du gestionnaire de pilotes est antérieure à ODBC 3,81, le comportement n’est pas défini.  
  
## <a name="use-cases"></a>Cas d'utilisation  
 Cette section présente les cas d’utilisation pour l’exécution asynchrone et le mécanisme d’interrogation.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Intégrer des données de plusieurs sources ODBC  
 Une application d’intégration de données extrait de manière asynchrone des données de plusieurs sources de données. Certaines données proviennent de sources de données distantes et certaines données proviennent de fichiers locaux. L’application ne peut pas continuer tant que les opérations asynchrones ne sont pas terminées.  
  
 Au lieu d’interroger à plusieurs reprises une opération pour déterminer si elle est terminée, l’application peut créer un objet d’événement et l’associer à un handle de connexion ODBC ou à un handle d’instruction ODBC. L’application appelle ensuite les API de synchronisation du système d’exploitation pour attendre un objet d’événement ou de nombreux objets d’événement (à la fois les événements ODBC et d’autres événements Windows). ODBC signalera l’objet d’événement lorsque l’opération ODBC asynchrone correspondante sera terminée.  
  
 Sur Windows, les objets d’événement Win32 seront utilisés et fournira à l’utilisateur un modèle de programmation unifié. Les gestionnaires de pilotes sur d’autres plateformes peuvent utiliser l’implémentation d’objet d’événement spécifique à ces plateformes.  
  
 L’exemple de code suivant illustre l’utilisation de la notification asynchrone de connexion et d’instruction :  
  
```  
// This function opens NUMBER_OPERATIONS connections and executes one query on statement of each connection.  
// Asynchronous Notification is used  
  
#define NUMBER_OPERATIONS 5  
int AsyncNotificationSample(void)  
{  
    RETCODE     rc;  
  
    SQLHENV     hEnv              = NULL;  
    SQLHDBC     arhDbc[NUMBER_OPERATIONS]         = {NULL};  
    SQLHSTMT    arhStmt[NUMBER_OPERATIONS]        = {NULL};  
  
    HANDLE      arhDBCEvent[NUMBER_OPERATIONS]    = {NULL};  
    RETCODE     arrcDBC[NUMBER_OPERATIONS]        = {0};  
    HANDLE      arhSTMTEvent[NUMBER_OPERATIONS]   = {NULL};  
    RETCODE     arrcSTMT[NUMBER_OPERATIONS]       = {0};  
  
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &hEnv);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    rc = SQLSetEnvAttr(hEnv,  
        SQL_ATTR_ODBC_VERSION,  
        (SQLPOINTER) SQL_OV_ODBC3_80,  
        SQL_IS_INTEGER);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    // Connection operations begin here  
  
    // Alloc NUMBER_OPERATIONS connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_DBC, hEnv, &arhDbc[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable DBC Async on all connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE, (SQLPOINTER)SQL_ASYNC_DBC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Application must create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhDBCEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhDBCEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all connection handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_EVENT, arhDBCEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate connect establishing  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLDriverConnect(arhDbc[i], NULL, (SQLTCHAR*)TEXT("Driver={ODBC Driver 11 for SQL Server};SERVER=dp-srv-sql2k;DATABASE=pubs;UID=sa;PWD=XYZ;"), SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE); // Wait All  
  
    // Complete connect API calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], & arrcDBC[i]);  
    }  
  
    BOOL fFail = FALSE; // Whether some connection openning fails.  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcDBC[i]) )   
            fFail = TRUE;  
    }  
  
    // If some SQLDriverConnect() fail, clean up.  
    if (fFail)  
    {  
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {  
                SQLDisconnect(arhDbc[i]); // This is also async  
            }  
            else  
            {  
                SetEvent(arhDBCEvent[i]); // Previous SQLDriverConnect() failed. No need to call SQLDisconnect().  
            }  
        }  
        WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE);   
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {     
                SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], &arrcDBC[i]);; // To Complete  
            }  
        }  
  
        goto Cleanup;  
    }  
  
    // Statement Operations begin here  
  
    // Alloc statement handle  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_STMT, arhDbc[i], &arhStmt[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable STMT Async on all statement handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_ENABLE, (SQLPOINTER)SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhSTMTEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhSTMTEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all statement handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_STMT_EVENT, arhSTMTEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate SQLExecDirect() calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLExecDirect(arhStmt[i], (SQLTCHAR*)TEXT("select au_lname, au_fname from authors"), SQL_NTS);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE); // Wait All  
  
    // Now, call SQLCompleteAsync to complete the operation and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return values  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        //Do some binding jobs here, set SQL_ATTR_ROW_ARRAY_SIZE   
    }  
  
    // Now, initiate fetching  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLFetch(arhStmt[i]);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE);   
  
    // Now, to complete the operations and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    // USE fetched data here!!  
  
Cleanup:  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhStmt[NUMBER_OPERATIONS])  
        {  
            SQLFreeHandle(SQL_HANDLE_STMT, arhStmt[i]);  
            arhStmt[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhSTMTEvent[i])  
        {  
            CloseHandle(arhSTMTEvent[i]);  
            arhSTMTEvent[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDbc[i])  
        {  
            SQLFreeHandle(SQL_HANDLE_DBC, arhDbc[i]);  
            arhDbc[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDBCEvent[i])  
        {  
            CloseHandle(arhDBCEvent[i]);  
            arhDBCEvent[i] = NULL;  
        }  
    }  
  
    if (hEnv)  
    {  
        SQLFreeHandle(SQL_HANDLE_ENV, hEnv);  
        hEnv = NULL;  
    }  
  
    return 0;  
}  
  
```  
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Détermination de la prise en charge des notifications asynchrones par un pilote  
 Une application ODBC peut déterminer si un pilote ODBC prend en charge la notification asynchrone en appelant [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md). Le gestionnaire de pilotes ODBC appellera donc la **SQLGetInfo** du pilote avec SQL_ASYNC_NOTIFICATION.  
  
```  
SQLUINTEGER InfoValue;  
SQLLEN      cbInfoLength;  
  
SQLRETURN retcode;  
retcode = SQLGetInfo (hDbc,   
                      SQL_ASYNC_NOTIFICATION,   
                      &InfoValue,  
                      sizeof(InfoValue),  
                      NULL);  
if (SQL_SUCCEEDED(retcode))  
{  
if (SQL_ASYNC_NOTIFICATION_CAPABLE == InfoValue)  
      {  
          // The driver supports asynchronous notification  
      }  
      else if (SQL_ASYNC_NOTIFICATION_NOT_CAPABLE == InfoValue)  
      {  
          // The driver does not support asynchronous notification  
      }  
}  
```  
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Association d’un handle d’événement Win32 à un handle ODBC  
 Les applications sont chargées de créer des objets d’événement Win32 à l’aide des fonctions Win32 correspondantes. Une application peut associer un handle d’événement Win32 à un handle de connexion ODBC ou à un handle d’instruction ODBC.  
  
 Les attributs de connexion SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE et SQL_ATTR_ASYNC_DBC_EVENT déterminer si ODBC s’exécute en mode asynchrone et si ODBC active le mode de notification pour un handle de connexion. Les attributs d’instruction SQL_ATTR_ASYNC_ENABLE et SQL_ATTR_ASYNC_STMT_EVENT déterminer si ODBC s’exécute en mode asynchrone et si ODBC active le mode de notification pour un descripteur d’instruction.  
  
|SQL_ATTR_ASYNC_ENABLE ou SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT ou SQL_ATTR_ASYNC_DBC_EVENT|Mode|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Activer|non null|Notification asynchrone|  
|Activer|null|Interrogation asynchrone|  
|Disable|n'importe laquelle|Synchrone|  
  
 Une application peut désactiver temporellement le mode d’opération asynchrone. ODBC ignore les valeurs de SQL_ATTR_ASYNC_DBC_EVENT si l’opération asynchrone au niveau de la connexion est désactivée. ODBC ignore les valeurs de SQL_ATTR_ASYNC_STMT_EVENT si l’opération asynchrone au niveau de l’instruction est désactivée.  
  
 Appel synchrone de **SQLSetStmtAttr** et **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** prend en charge les opérations asynchrones, mais l’appel de **sqlsetconnectattr** pour définir SQL_ATTR_ASYNC_DBC_EVENT est toujours synchrone.  
  
-   **SQLSetStmtAttr** ne prend pas en charge l’exécution asynchrone.  
  
 Scénario d’erreur  
 Lorsque la commande **SQLSetConnectAttr** est appelée avant d’établir une connexion, le gestionnaire de pilotes ne peut pas déterminer le pilote à utiliser. Par conséquent, le gestionnaire de pilotes renvoie une réussite pour **SQLSetConnectAttr** , mais l’attribut n’est peut-être pas prêt à être défini dans le pilote. Le gestionnaire de pilotes définit ces attributs lorsque l’application appelle une fonction de connexion. Le gestionnaire de pilotes peut échouer, car le pilote ne prend pas en charge les opérations asynchrones.  
  
 Héritage des attributs de connexion  
 En règle générale, les instructions d’une connexion héritent des attributs de connexion. Toutefois, l’attribut SQL_ATTR_ASYNC_DBC_EVENT n’est pas héritable et n’affecte que les opérations de connexion.  
  
 Pour associer un handle d’événement à un handle de connexion ODBC, une application ODBC appelle l’API ODBC **SQLSetConnectAttr** et spécifie SQL_ATTR_ASYNC_DBC_EVENT comme attribut et le descripteur d’événement comme valeur d’attribut. Le nouvel attribut ODBC SQL_ATTR_ASYNC_DBC_EVENT est de type SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 En règle générale, les applications créent des objets d’événement à réinitialisation automatique. ODBC ne réinitialise pas l’objet d’événement. Les applications doivent s’assurer que l’objet n’est pas dans l’état signalé avant d’appeler une fonction ODBC asynchrone.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT est un attribut gestionnaire de pilotes uniquement qui n’est pas défini dans le pilote.  
  
 La valeur par défaut de SQL_ATTR_ASYNC_DBC_EVENT est NULL. Si le pilote ne prend pas en charge la notification asynchrone, l’obtention ou la définition de SQL_ATTR_ASYNC_DBC_EVENT retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide).  
  
 Si la dernière valeur SQL_ATTR_ASYNC_DBC_EVENT définie sur un handle de connexion ODBC n’est pas NULL et que l’application a activé le mode asynchrone en définissant l’attribut SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE avec SQL_ASYNC_DBC_ENABLE_ON, l’appel d’une fonction de connexion ODBC qui prend en charge le mode asynchrone obtient une notification de fin d’exécution. Si la dernière valeur SQL_ATTR_ASYNC_DBC_EVENT définie sur un handle de connexion ODBC est NULL, ODBC n’envoie aucune notification à l’application, que le mode asynchrone soit activé ou non.  
  
 Une application peut définir SQL_ATTR_ASYNC_DBC_EVENT avant ou après la définition de l’attribut SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Les applications peuvent définir l’attribut SQL_ATTR_ASYNC_DBC_EVENT sur un handle de connexion ODBC avant d’appeler une fonction de connexion (**SQLConnect**, **SQLBrowseConnect**ou **SQLDriverConnect**). Le gestionnaire de pilotes ODBC ne connaissant pas le pilote ODBC que l’application utilisera, il renverra SQL_SUCCESS. Lorsque l’application appelle une fonction de connexion, le gestionnaire de pilotes ODBC vérifie si le pilote prend en charge les notifications asynchrones. Si le pilote ne prend pas en charge la notification asynchrone, le gestionnaire de pilotes ODBC retourne SQL_ERROR avec SQLSTATE S1_118 (le pilote ne prend pas en charge les notifications asynchrones). Si le pilote prend en charge les notifications asynchrones, le gestionnaire de pilotes ODBC appellera le pilote et définira les attributs correspondants SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK et SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT.  
  
 De même, une application appelle **SQLSetStmtAttr** sur un handle d’instruction ODBC et spécifie l’attribut SQL_ATTR_ASYNC_STMT_EVENT pour activer ou désactiver la notification asynchrone au niveau de l’instruction. Étant donné qu’une fonction d’instruction est toujours appelée après l’établissement de la connexion, **SQLSetStmtAttr** retourne SQL_ERROR avec SQLSTATE S1_118 (le pilote ne prend pas en charge la notification asynchrone) immédiatement si le pilote correspondant ne prend pas en charge les opérations asynchrones ou si le pilote prend en charge l’opération asynchrone, mais ne prend pas en charge les notifications asynchrones.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, qui peut avoir la valeur NULL, est un attribut gestionnaire de pilotes uniquement qui ne sera pas défini dans le pilote.  
  
 La valeur par défaut de SQL_ATTR_ASYNC_STMT_EVENT est NULL. Si le pilote ne prend pas en charge la notification asynchrone, l’obtention ou la définition de l’SQL_ATTR_ASYNC_ attribut STMT_EVENT retourne SQL_ERROR avec SQLSTATE HY092 (identificateur d’option/attribut non valide).  
  
 Une application ne doit pas associer le même descripteur d’événement à plusieurs descripteurs ODBC. Dans le cas contraire, une notification sera perdue si deux appels de fonction ODBC asynchrones sont terminés sur deux Handles qui partagent le même descripteur d’événement. Pour éviter qu’un descripteur d’instruction hérite du même descripteur d’événement du descripteur de connexion, ODBC retourne SQL_ERROR avec SQLSTATE IM016 (impossible de définir l’attribut d’instruction dans le handle de connexion) si une application définit SQL_ATTR_ASYNC_STMT_EVENT sur un handle de connexion.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Appel de fonctions ODBC asynchrones  
 Après l’activation de la notification asynchrone et le démarrage d’une opération asynchrone, l’application peut appeler n’importe quelle fonction ODBC. Si la fonction appartient à l’ensemble des fonctions qui prennent en charge l’opération asynchrone, l’application obtient une notification de fin d’exécution lorsque l’opération se termine, que la fonction ait échoué ou réussi.  La seule exception est que l’application appelle une fonction ODBC avec un handle de connexion ou d’instruction non valide. Dans ce cas, ODBC n’obtient pas le descripteur d’événement et le définit à l’état signalé.  
  
 L’application doit s’assurer que l’objet d’événement associé se trouve dans un État non signalé avant de démarrer une opération asynchrone sur le handle ODBC correspondant. ODBC ne réinitialise pas l’objet d’événement.  
  
### <a name="getting-notification-from-odbc"></a>Obtention de notifications à partir d’ODBC  
 Un thread d’application peut appeler **WaitForSingleObject** pour attendre un handle d’événement ou appeler **WaitForMultipleObjects** pour attendre un tableau de handles d’événements et être suspendu jusqu’à ce qu’un ou tous les objets d’événement soient signalés ou que l’intervalle de délai d’attente soit écoulé.  
  
```  
DWORD dwStatus = WaitForSingleObject(  
                        hEvent,  // The event associated with the ODBC handle  
                        5000     // timeout is 5000 millisecond   
);  
  
If (dwStatus == WAIT_TIMEOUT)  
{  
    // time-out interval elapsed before all the events are signaled.   
}  
Else  
{  
    // Call the corresponding Asynchronous ODBC API to complete all processing and retrieve the return code.  
}  
```
