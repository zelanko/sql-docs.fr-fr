---
title: Objet SqlContext (fr) Microsoft Docs
description: Lorsque vous invoquez du code géré dans SQL Server dans une connexion utilisateur, l’accès au contexte de l’appelant est abstrait dans un objet SqlContext.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
ms.openlocfilehash: cd6d3091b155ae829e368bdd182b3da8286c7194
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487534"
---
# <a name="sqlcontext-object"></a>Objet SqlContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous appelez le code managé dans le serveur lorsque vous appelez une procédure ou une fonction, lorsque vous appelez une méthode sur un type CLR défini par l'utilisateur ou lorsque votre action active un déclencheur défini dans l'un des langages du [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Comme l'exécution de ce code est demandée dans le cadre d'une connexion utilisateur, l'accès au contexte de l'appelant à partir du code en cours d'exécution dans le serveur est requis. De plus, certaines opérations d'accès aux données ne peuvent être valides que si elles sont exécutées sous le contexte de l'appelant. Par exemple, l'accès à des pseudo-tables insérées et supprimées utilisées dans les opérations de déclencheur n'est valide que sous le contexte de l'appelant.  
  
 Le contexte de l’appelant est abstrait dans un objet **SqlContext.** Pour plus d’informations sur les méthodes et les propriétés **De SqlTriggerContext,** voir la documentation [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] de référence de la classe **Microsoft.SqlServer.Server.SqlTriggerContext** dans le SDK.  
  
 **SqlContext** donne accès aux composants suivants :  
  
-   **SqlPipe**: **L’objet SqlPipe** représente le « tuyau » par lequel les résultats s’écoulent au client. Pour plus d’informations sur l’objet **SqlPipe,** voir [SqlPipe Object](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md).  
  
-   **SqlTriggerContext**: **L’objet SqlTriggerContext** ne peut être récupéré qu’à l’intérieur d’un déclencheur CLR. Il fournit des informations sur l'opération qui a provoqué l'activation du déclencheur et un mappage des colonnes mises à jour. Pour plus d’informations sur l’objet **SqlTriggerContext,** voir [SqlTriggerContext Object](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md).  
  
-   **IsAvailable**: La propriété **IsAvailable** est utilisée pour déterminer la disponibilité du contexte.  
  
-   **WindowsIdentity**: La propriété **WindowsIdentity** est utilisée pour récupérer l’identité Windows de l’appelant.  
  
## <a name="determining-context-availability"></a>Détermination de la disponibilité du contexte  
 Interrogez la classe **SqlContext** pour voir si le code actuellement exécutant est en cours d’exécution en cours de traitement. Pour ce faire, vérifiez la propriété **IsAvailable** de l’objet **SqlContext.** La propriété **IsAvailable** est lue **True** uniquement, et retourne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Vrai si le code d’appel est en cours d’exécution à l’intérieur et si d’autres membres **SqlContext** peuvent être consultés. Si la propriété **IsAvailable** retourne **Faux**, tous les autres membres **SqlContext** jeter une **InvalidOperationException**, si utilisé. Si **IsAvailable** **renvoie False**, toute tentative d’ouvrir un objet de connexion qui a "contexte connexion-vrai" dans la chaîne de connexion échoue.  
  
## <a name="retrieving-windows-identity"></a>Extraction de l'identité Windows  
 Le code CLR qui s'exécute à l'intérieur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est toujours appelé dans le contexte du compte de processus. Si le code doit effectuer certaines actions en utilisant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’identité de l’utilisateur appelant, au lieu de l’identité du processus, alors un jeton d’usurpation d’identité doit être obtenu par la propriété **WindowsIdentity** de **l’objet SqlContext.** La propriété **WindowsIdentity** renvoie une [!INCLUDE[msCoName](../../includes/msconame-md.md)] instance **WindowsIdentity** représentant l’identité Windows de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’appelant, ou nulle si le client a été authentifié à l’aide de l’authentification. Seuls les assemblages marqués avec des autorisations **EXTERNAL_ACCESS** ou **UNSAFE** peuvent accéder à cette propriété.  
  
 Après avoir obtenu l’objet **WindowsIdentity,** les appelants peuvent se faire passer pour le compte client et effectuer des actions en leur nom.  
  
 L’identité de l’appelant n’est disponible que via **SqlContext.WindowsIdentity** si le client qui a initié l’exécution de la procédure stockée ou de la fonction connectée au serveur à l’aide de Windows Authentication. Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été utilisé à la place, cette propriété a la valeur Null et le code ne peut pas emprunter l'identité de l'appelant.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir l'identité Windows du client appelant et emprunter l'identité du client.  
  
 C#  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 Visual Basic  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)   
 [Objet SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [Déclencheurs CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [Extensions spécifiques in-process de SQL Server à ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
