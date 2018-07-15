---
title: Objet SqlContext | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
caps.latest.revision: 54
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 46ff059b14d5937d1214e0d97ad9aa13083e7fd3
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354011"
---
# <a name="sqlcontext-object"></a>Objet SqlContext
  Vous appelez le code managé dans le serveur lorsque vous appelez une procédure ou une fonction, lorsque vous appelez une méthode sur un type CLR défini par l'utilisateur ou lorsque votre action active un déclencheur défini dans l'un des langages du [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Comme l'exécution de ce code est demandée dans le cadre d'une connexion utilisateur, l'accès au contexte de l'appelant à partir du code en cours d'exécution dans le serveur est requis. De plus, certaines opérations d'accès aux données ne peuvent être valides que si elles sont exécutées sous le contexte de l'appelant. Par exemple, l'accès à des pseudo-tables insérées et supprimées utilisées dans les opérations de déclencheur n'est valide que sous le contexte de l'appelant.  
  
 Le contexte de l'appelant est soustrait dans un objet `SqlContext`. Pour plus d'informations sur les méthodes et les propriétés `SqlTriggerContext`, consultez la documentation de référence sur la classe `Microsoft.SqlServer.Server.SqlTriggerContext` dans le Kit de développement [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
 `SqlContext` fournit l'accès aux composants suivants :  
  
-   `SqlPipe` : l'objet `SqlPipe` représente le « canal » à travers lequel les résultats transitent vers le client. Pour plus d’informations sur la `SqlPipe` d’objets, consultez [objet SqlPipe](sqlpipe-object.md).  
  
-   `SqlTriggerContext` : l'objet `SqlTriggerContext` ne peut être extrait qu'à partir d'un déclencheur CLR. Il fournit des informations sur l'opération qui a provoqué l'activation du déclencheur et un mappage des colonnes mises à jour. Pour plus d’informations sur la `SqlTriggerContext` d’objets, consultez [objet SqlTriggerContext](sqltriggercontext-object.md).  
  
-   `IsAvailable` : la propriété `IsAvailable` est utilisée pour déterminer la disponibilité du contexte.  
  
-   `WindowsIdentity` : la propriété `WindowsIdentity` est utilisée pour extraire l'identité Windows de l'appelant.  
  
## <a name="determining-context-availability"></a>Détermination de la disponibilité du contexte  
 Interrogez la classe `SqlContext` pour voir si le code en cours s'exécute in-process. À cette fin, vérifiez la propriété `IsAvailable` de l'objet `SqlContext`. La propriété `IsAvailable` est en lecture seule, et retourne `True` si le code appelant s'exécute à l'intérieur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et si d'autres membres `SqlContext` peuvent être accédés. Si la propriété `IsAvailable` retourne `False`, tous les autres membres `SqlContext` lèvent une exception `InvalidOperationException`, en cas d'utilisation. Si `IsAvailable` retourne `False`, toute tentative d'ouvrir un objet de connexion dont la chaîne de connexion contient "context connection=true" échoue.  
  
## <a name="retrieving-windows-identity"></a>Extraction de l'identité Windows  
 Le code CLR qui s'exécute à l'intérieur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est toujours appelé dans le contexte du compte de processus. S'il est nécessaire que le code exécute certaines actions à l'aide de l'identité de l'utilisateur appelant plutôt qu'à l'aide de l'identité du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un jeton d'emprunt d'identité doit être obtenu par le biais de la propriété `WindowsIdentity` de l'objet `SqlContext`. La propriété `WindowsIdentity` retourne une instance `WindowsIdentity` représentant l'identité [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows de l'appelant ou null si le client a été authentifié par le biais de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Seuls les assemblys marqués avec les autorisations `EXTERNAL_ACCESS` ou `UNSAFE` peuvent accéder à cette propriété.  
  
 Après avoir obtenu l'objet `WindowsIdentity`, les appelants peuvent emprunter l'identité du compte client et effectuer des actions à sa place.  
  
 L'identité de l'appelant est uniquement disponible via `SqlContext.WindowsIdentity` si le client qui a initié l'exécution de la procédure stockée ou de la fonction s'est connecté au serveur à l'aide de l'authentification Windows. Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été utilisé à la place, cette propriété a la valeur Null et le code ne peut pas emprunter l'identité de l'appelant.  
  
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
 [Objet SqlPipe](sqlpipe-object.md)   
 [Objet SqlTriggerContext](sqltriggercontext-object.md)   
 [Déclencheurs CLR](../../database-engine/dev-guide/clr-triggers.md)   
 [Extensions spécifiques in-process de SQL Server à ADO.NET](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
