---
title: Exécution asynchrone (méthode de notification) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306410"
---
# <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)
ODBC permet l’exécution asynchrone des opérations de connexion et de déclaration. Un thread d’application peut appeler une fonction ODBC en mode asynchrone et la fonction peut revenir avant que l’opération soit terminée, permettant au fil d’application d’effectuer d’autres tâches. Dans le Windows 7 SDK, pour les opérations asynchrones de déclaration ou de connexion, une application a déterminé que l’opération asynchrone était complète en utilisant la méthode de vote. Pour plus d’informations, voir [Asynchrone Execution (Méthode de sondage)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). À partir de windows 8 SDK, vous pouvez déterminer qu’une opération asynchrone est terminée en utilisant la méthode de notification.  
  
 Dans la méthode de vote, les applications doivent appeler la fonction asynchrone chaque fois qu’il veut le statut de l’opération. La méthode de notification est similaire à la récupération et à l’attente dans ADO.NET. ODBC, cependant, utilise les événements Win32 comme objet de notification.  
  
 La bibliothèque de cursors de l’ODBC et la notification asynchrone de l’ODBC ne peuvent pas être utilisées en même temps. La définition des deux attributs retournera une erreur avec SQLSTATE S1119 (Cursor Library et Asynchrone Notification ne peuvent pas être activées en même temps).  
  
 Voir [Notification of Asynchronous Function Completion](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) pour plus d’informations pour les développeurs de pilotes.  
  
> [!NOTE]  
>  La méthode de notification n’est pas prise en charge par la bibliothèque de curseurs. Une application recevra un message d’erreur si elle tente d’activer la bibliothèque de curseurs via SQLSetConnectAttr, lorsque la méthode de notification est activée.  
  
## <a name="overview"></a>Vue d’ensemble  
 Lorsqu’une fonction ODBC est appelée en mode asynchrone, le contrôle est immédiatement retourné à l’application d’appel avec le code de retour SQL_STILL_EXECUTING. L’application doit à plusieurs reprises sonder la fonction jusqu’à ce qu’elle retourne autre chose que SQL_STILL_EXECUTING. La boucle de vote augmente l’utilisation du processeur, causant de mauvaises performances dans de nombreux scénarios asynchrones.  
  
 Chaque fois que le modèle de notification est utilisé, le modèle de sondage est désactivé. Les applications ne doivent pas rappeler la fonction d’origine. Appelez [SQLCompleteAsync Function](../../../odbc/reference/syntax/sqlcompleteasync-function.md) pour compléter l’opération asynchrone. Si une application appelle à nouveau la fonction d’origine avant que l’opération asynchrone ne soit terminée, l’appel retournera SQL_ERROR avec SQLSTATE IM017 (Le sondage est désactivé en mode notification asynchrone).  
  
 Lors de l’utilisation du modèle de notification, l’application peut appeler **SQLCancel** ou **SQLCancelHandle** pour annuler une opération de relevé ou de connexion. Si la demande d’annulation est acceptée, ODBC retournera SQL_SUCCESS. Ce message n’indique pas que la fonction a été effectivement annulée; il indique que la demande d’annulation a été traitée. La question de savoir si la fonction est effectivement annulée dépend du conducteur et dépend de la source de données. Lorsqu’une opération est annulée, le gestionnaire de pilote signale toujours l’événement. Le Gestionnaire de conducteur retourne SQL_ERROR dans le tampon de code de retour et l’état est SQLSTATE HY008 (Opération annulée) pour indiquer l’annulation est réussie. Si la fonction a terminé son traitement normal, le gestionnaire de conducteur retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO.  
  
### <a name="downlevel-behavior"></a>Comportement de niveau downlevel  
 La version ODBC Driver Manager à l’appui de cette notification complète est ODBC 3.81.  
  
|Application ODBC Version|Version gestionnaire de pilote|Version du pilote|Comportement|  
|------------------------------|----------------------------|--------------------|--------------|  
|Nouvelle application de toute version ODBC|ODBC 3,81|ODBC 3.80 Pilote|L’application peut utiliser cette fonctionnalité si le conducteur prend en charge cette fonctionnalité, sinon le gestionnaire de pilote se trompera.|  
|Nouvelle application de toute version ODBC|ODBC 3,81|Pré-ODBC 3.80 Pilote|Le gestionnaire de conducteur se trompe si le conducteur ne prend pas en charge cette fonctionnalité.|  
|Nouvelle application de toute version ODBC|Pré-ODBC 3,81|Quelconque|Lorsque l’application utilise cette fonctionnalité, un ancien gestionnaire de pilote considérera les nouveaux attributs comme des attributs spécifiques au conducteur, et le conducteur doit s’tromper. Un nouveau gestionnaire de conducteur ne transmettra pas ces attributs au conducteur.|  
  
 Une application doit vérifier la version Driver Manager avant d’utiliser cette fonctionnalité. Sinon, si un pilote mal écrit ne se trompe pas et que la version Driver Manager est pré ODBC 3.81, le comportement n’est pas défini.  
  
## <a name="use-cases"></a>Cas d'utilisation  
 Cette section montre l’utilisation des cas pour l’exécution asynchrone et le mécanisme de vote.  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>Intégrer les données de plusieurs sources ODBC  
 Une application d’intégration de données récupère asynchronement les données provenant de multiples sources de données. Certaines des données proviennent de sources de données à distance et certaines données proviennent de fichiers locaux. La demande ne peut pas se poursuivre tant que les opérations asynchrones ne sont pas terminées.  
  
 Au lieu de sonder à plusieurs reprises une opération pour déterminer si elle est complète, l’application peut créer un objet d’événement et l’associer à une poignée de connexion ODBC ou à une poignée de relevé oDBC. L’application appelle ensuite les API de synchronisation du système d’exploitation pour attendre sur un objet d’événement ou de nombreux objets événementiels (événements ODBC et autres événements Windows). ODBC signalera l’objet de l’événement lorsque l’opération asynchrone correspondante de l’ODBC sera terminée.  
  
 Sur Windows, les objets de l’événement Win32 seront utilisés et fourniront à l’utilisateur un modèle de programmation unifié. Les gestionnaires de pilotes sur d’autres plates-formes peuvent utiliser la mise en œuvre de l’objet événementiel spécifique à ces plates-formes.  
  
 L’échantillon de code suivant démontre l’utilisation de la connexion et de la notification asynchrone :  
  
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
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>Déterminer si un conducteur prend en charge la notification asynchrone  
 Une application ODBC peut déterminer si un conducteur ODBC prend en charge une notification asynchrone en appelant [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md). Le gestionnaire de conduite de l’ODBC appellera donc le **SQLGetInfo** du conducteur avec SQL_ASYNC_NOTIFICATION.  
  
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
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Associer une poignée d’événements Win32 avec une poignée ODBC  
 Les applications sont responsables de la création d’objets d’événements Win32 à l’aide des fonctions Win32 correspondantes. Une application peut associer une poignée d’événement Win32 à une poignée de connexion ODBC ou à une poignée de relevé ODBC.  
  
 Les attributs de connexion SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE et SQL_ATTR_ASYNC_DBC_EVENT déterminent si ODBC exécute en mode asynchrone et si ODBC permet le mode de notification pour une poignée de connexion. L’énoncé attribue SQL_ATTR_ASYNC_ENABLE et SQL_ATTR_ASYNC_STMT_EVENT déterminer si ODBC exécute en mode asynchrone et si ODBC permet le mode de notification pour une poignée de relevé.  
  
|SQL_ATTR_ASYNC_ENABLE ou SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT ou SQL_ATTR_ASYNC_DBC_EVENT|Mode|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|Activer|non-null|Notification asynchrone|  
|Activer|null|Sondage asynchrone|  
|Disable|n'importe laquelle|Synchrone|  
  
 Une application peut désactiver temporellement le mode de fonctionnement asynchrone. ODBC ignore les valeurs de SQL_ATTR_ASYNC_DBC_EVENT si le niveau de connexion opération asynchrone est désactivé. ODBC ignore les valeurs de SQL_ATTR_ASYNC_STMT_EVENT si le niveau d’instruction de l’opération asynchrone est désactivé.  
  
 Appel synchrone de **SQLSetStmtAttr** et **SQLSetConnectAttr**  
 -   **SQLSetConnectAttr** prend en charge les opérations asynchrones, mais l’invocation de **SQLSetConnectAttr** pour définir SQL_ATTR_ASYNC_DBC_EVENT est toujours synchrone.  
  
-   **SQLSetStmtAttr** n’est pas en faveur d’une exécution asynchrone.  
  
 Scénario d’erreur  
 Lorsque **SQLSetConnectAttr** est appelé avant de faire une connexion, le gestionnaire de conducteur ne peut pas déterminer quel pilote utiliser. Par conséquent, le gestionnaire de pilote retourne le succès pour **SQLSetConnectAttr,** mais l’attribut peut ne pas être prêt à mettre dans le pilote. Le gestionnaire de pilote définira ces attributs lorsque l’application appelle une fonction de connexion. Le gestionnaire de conducteur peut s’absenter parce que le conducteur ne prend pas en charge les opérations asynchrones.  
  
 Héritage des attributs de connexion  
 Habituellement, les déclarations d’une connexion hériteront des attributs de connexion. Toutefois, l’attribut SQL_ATTR_ASYNC_DBC_EVENT n’est pas héréditaire et n’affecte que les opérations de connexion.  
  
 Pour associer une poignée d’événement à une poignée de connexion ODBC, une application ODBC appelle ODBC API **SQLSetConnectAttr** et spécifie SQL_ATTR_ASYNC_DBC_EVENT comme attribut et la poignée de l’événement comme valeur d’attribut. Le nouvel attribut ODBC SQL_ATTR_ASYNC_DBC_EVENT est de type SQL_IS_POINTER.  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 Habituellement, les applications créent des objets d’événement auto-réinitialisation. ODBC ne réinitialisera pas l’objet de l’événement. Les applications doivent s’assurer que l’objet n’est pas en état signalé avant d’appeler une fonction asynchrone ODBC.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT est un attribut Driver Manager-seulement qui ne sera pas mis dans le conducteur.  
  
 La valeur par défaut de SQL_ATTR_ASYNC_DBC_EVENT est NULL. Si le conducteur ne prend pas en charge la notification asynchrone, obtenir ou SQL_ATTR_ASYNC_DBC_EVENT retournera SQL_ERROR avec SQLSTATE HY092 (identification d’attribut/option invalide).  
  
 Si la dernière valeur SQL_ATTR_ASYNC_DBC_EVENT fixée sur une poignée de connexion ODBC n’est pas NULL et que l’application a activé le mode asynchrone en définissant l’attribut SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE avec SQL_ASYNC_DBC_ENABLE_ON, en appelant toute fonction de connexion ODBC qui prend en charge le mode asynchrone recevra une notification d’achèvement. Si la dernière SQL_ATTR_ASYNC_DBC_EVENT valeur définie sur une poignée de connexion ODBC est NULL, ODBC n’enverra aucune notification à l’application, que le mode asynchrone soit activé ou non.  
  
 Une application peut définir SQL_ATTR_ASYNC_DBC_EVENT avant ou après la définition de l’attribut SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE.  
  
 Les applications peuvent définir l’attribut SQL_ATTR_ASYNC_DBC_EVENT sur une poignée de connexion ODBC avant d’appeler une fonction de connexion (**SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect**). Étant donné que le gestionnaire de conducteur ODBC ne sait pas quel pilote ODBC l’application utilisera, il retournera SQL_SUCCESS. Lorsque l’application appelle une fonction de connexion, le gestionnaire de pilote ODBC vérifiera si le conducteur prend en charge la notification asynchrone. Si le conducteur ne prend pas en charge la notification asynchrone, le gestionnaire de conduite de l’ODBC retournera SQL_ERROR avec SQLSTATE S1_118 (Le conducteur ne prend pas en charge la notification asynchrone). Si le conducteur prend en charge la notification asynchrone, le gestionnaire de pilote ODBC appellera le conducteur et définira les attributs correspondants SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK et SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT.  
  
 De même, une application appelle **SQLSetStmtAttr** sur une poignée de relevé ODBC et spécifie l’attribut SQL_ATTR_ASYNC_STMT_EVENT pour activer ou désactiver le niveau de déclaration asynchrone notification. Étant donné qu’une fonction d’instruction est toujours appelée après la mise en place de la connexion, **SQLSetStmtAttr** retournera SQL_ERROR avec SQLSTATE S1_118 (le conducteur ne prend pas en charge la notification asynchrone) immédiatement si le conducteur correspondant ne prend pas en charge les opérations asynchrones ou le conducteur prend en charge l’opération asynchrone, mais ne prend pas en charge la notification asynchrone.  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT, qui peut être réglé à NULL, est un attribut Driver Manager-seulement qui ne sera pas fixé dans le conducteur.  
  
 La valeur par défaut de SQL_ATTR_ASYNC_STMT_EVENT est NULL. Si le conducteur ne prend pas en charge la notification asynchrone, obtenir ou définir le SQL_ATTR_ASYNC_ STMT_EVENT attribut retournera SQL_ERROR avec SQLSTATE HY092 (identification d’attribut/option invalide).  
  
 Une application ne doit pas associer la même poignée d’événement à plus d’une poignée ODBC. Dans le cas contraire, une notification sera perdue si deux invocations de fonction asynchrone oDBC complètent sur deux poignées qui partagent la même poignée d’événement. Pour éviter qu’une poignée de déclaration hérite de la même poignée d’événement à partir de la poignée de connexion, ODBC renvoie SQL_ERROR avec SQLSTATE IM016 (impossible de définir l’attribut de déclaration dans la poignée de connexion) si une application définit SQL_ATTR_ASYNC_STMT_EVENT sur une poignée de connexion.  
  
### <a name="calling-asynchronous-odbc-functions"></a>Appel Asynchrone ODBC Fonctions  
 Après avoir permis une notification asynchrone et commencé une opération asynchrone, l’application peut appeler n’importe quelle fonction ODBC. Si la fonction appartient à l’ensemble des fonctions qui prennent en charge l’opération asynchrone, l’application recevra une notification d’achèvement lorsque l’opération se termine, que la fonction ait échoué ou réussi.  La seule exception est que l’application appelle une fonction ODBC avec une connexion ou une poignée de déclaration invalide. Dans ce cas, ODBC n’obtiendra pas la poignée d’événement et la fixera à l’état signalé.  
  
 L’application doit s’assurer que l’objet d’événement associé est dans un état non signalé avant de commencer une opération asynchrone sur la poignée correspondante ODBC. ODBC ne réinitialisera pas l’objet de l’événement.  
  
### <a name="getting-notification-from-odbc"></a>Obtenir une notification de l’ODBC  
 Un thread d’application peut appeler **WaitForSingleObject** pour attendre sur une poignée d’événement ou appeler **WaitForMultipleObjects** pour attendre sur un tableau de poignées d’événements et être suspendu jusqu’à ce qu’un ou la totalité des objets de l’événement deviennent signalés ou l’intervalle de temps d’attente s’écoule.  
  
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
