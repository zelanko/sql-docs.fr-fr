---
title: Objet SqlContext | Microsoft Docs
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
ms.openlocfilehash: 746ce8cec228b6fe9a9d36c4e0287ad7c2f3c517
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67951678"
---
# <a name="sqlcontext-object"></a>Objet SqlContext
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous appelez le code managé dans le serveur lorsque vous appelez une procédure ou une fonction, lorsque vous appelez une méthode sur un type CLR défini par l'utilisateur ou lorsque votre action active un déclencheur défini dans l'un des langages du [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Comme l'exécution de ce code est demandée dans le cadre d'une connexion utilisateur, l'accès au contexte de l'appelant à partir du code en cours d'exécution dans le serveur est requis. De plus, certaines opérations d'accès aux données ne peuvent être valides que si elles sont exécutées sous le contexte de l'appelant. Par exemple, l'accès à des pseudo-tables insérées et supprimées utilisées dans les opérations de déclencheur n'est valide que sous le contexte de l'appelant.  
  
 Le contexte de l’appelant est abstrait dans un objet **SqlContext** . Pour plus d’informations sur les méthodes et propriétés **SqlTriggerContext** , consultez la documentation de référence sur la classe **Microsoft. SqlServer. Server. SqlTriggerContext** dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Kit de développement logiciel (SDK).  
  
 **SqlContext** fournit l’accès aux composants suivants :  
  
-   **SqlPipe**: l’objet **SqlPipe** représente le « canal » dans lequel les résultats sont transmis au client. Pour plus d’informations sur l’objet **SqlPipe** , consultez l' [objet SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md).  
  
-   **SqlTriggerContext**: l’objet **SqlTriggerContext** peut uniquement être récupéré à partir d’un déclencheur CLR. Il fournit des informations sur l'opération qui a provoqué l'activation du déclencheur et un mappage des colonnes mises à jour. Pour plus d’informations sur l’objet **SqlTriggerContext** , consultez [objet SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md).  
  
-   **IsAvailable**: la propriété **IsAvailable** est utilisée pour déterminer la disponibilité du contexte.  
  
-   **WindowsIdentity**: la propriété **WindowsIdentity** est utilisée pour récupérer l’identité Windows de l’appelant.  
  
## <a name="determining-context-availability"></a>Détermination de la disponibilité du contexte  
 Interrogez la classe **SqlContext** pour voir si le code en cours d’exécution s’exécute in-process. Pour ce faire, vérifiez la propriété **IsAvailable** de l’objet **SqlContext** . La propriété **IsAvailable** est en lecture seule et retourne la **valeur true** si le code appelant s’exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans et si d’autres membres **SqlContext** sont accessibles. Si la propriété **IsAvailable** retourne la **valeur false**, tous les autres membres **SqlContext** lèvent une **exception InvalidOperationException**, si elle est utilisée. Si **IsAvailable** retourne la **valeur false**, toute tentative d’ouverture d’un objet de connexion ayant « context connection = true » dans la chaîne de connexion échoue.  
  
## <a name="retrieving-windows-identity"></a>Extraction de l'identité Windows  
 Le code CLR qui s'exécute à l'intérieur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est toujours appelé dans le contexte du compte de processus. Si le code doit exécuter certaines actions à l’aide de l’identité de l’utilisateur appelant, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au lieu de l’identité du processus, un jeton d’emprunt d’identité doit être obtenu via la propriété **WindowsIdentity** de l’objet **SqlContext** . La propriété **WindowsIdentity** retourne une instance **WindowsIdentity** représentant l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] identité Windows de l’appelant, ou null si le client a été authentifié à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’aide de l’authentification. Seuls les assemblys marqués avec des autorisations **EXTERNAL_ACCESS** ou **unsafe** peuvent accéder à cette propriété.  
  
 Après avoir obtenu l’objet **WindowsIdentity** , les appelants peuvent emprunter l’identité du compte client et effectuer des actions en leur nom.  
  
 L’identité de l’appelant est disponible uniquement via **SqlContext. WindowsIdentity** si le client qui a initié l’exécution de la procédure stockée ou de la fonction s’est connecté au serveur à l’aide de l’authentification Windows. Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été utilisé à la place, cette propriété a la valeur Null et le code ne peut pas emprunter l'identité de l'appelant.  
  
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
 [SqlPipe, objet](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)   
 [Objet SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)   
 [Déclencheurs CLR](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)   
 [Extensions spécifiques in-process de SQL Server à ADO.NET](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
