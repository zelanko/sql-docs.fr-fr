---
title: Utilisation de connexions et Sessions dans ADOMD.NET | Documents Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- sessions [ADOMD.NET]
- connections [ADOMD.NET]
ms.assetid: 72b43c06-f3e4-42c3-a696-4a3419c3b884
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a4f51a9e0939612e490ed96c93c06a6931fa3f21
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="connections-in-adomdnet---working-with-connections-and-sessions"></a>Connexions dans ADOMD.NET - utilisation des connexions et Sessions
  Dans le cadre de XMLA (XML for Analysis), les sessions fournissent une prise en charge des opérations avec état pendant l'accès à des données analytiques. Les sessions définissent la portée et le contexte des commandes et des transactions pour une source de données analytiques. Les éléments XMLA utilisés pour gérer les sessions sont [BeginSession](../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md), [Session](../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)et [EndSession](../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md).  
  
 ADOMD.NET utilise ces trois éléments de session XMLA lorsque vous démarrez une session, exécutez des requêtes ou récupérez des données pendant la session et fermez une session.  
  
## <a name="starting-a-session"></a>Démarrage d'une session  
 La propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> contient l'identificateur de la session active associée à l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Par une utilisation appropriée de cette propriété, vous pouvez contrôler de façon efficace l'état du client et du serveur dans votre application :  
  
-   Si la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> n'indique pas un ID de session valide lorsque la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> est appelée, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> demande un nouvel ID de session auprès du fournisseur. ADOMD.NET initie une session en envoyant un en-tête **BeginSession** XMLA au fournisseur. Si ADOMD.NET parvient à démarrer une session, ADOMD.NET définit la valeur de la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> en lui attribuant l'ID de la session nouvellement créée.  
  
-   Si la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> indique un ID de session valide lorsque la méthode <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> est appelée, l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> tente de se connecter à la session spécifiée.  
  
 Si l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> ne parvient pas à se connecter à la session spécifiée ou si le fournisseur ne prend pas en charge les sessions, une exception est levée.  
  
> [!NOTE]  
>  Dès lors qu'ADOMD.NET a créé une session, vous pouvez connecter plusieurs objets <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> à cette session active unique, ou vous pouvez déconnecter un objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> unique de cette session et le reconnecter à une autre session.  
  
## <a name="working-in-a-session"></a>Utilisation d'une session  
 Après avoir connecté le <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> de l’objet à une session valide, ADOMD.NET envoie un XMLA **Session** en-tête pour le fournisseur avec chaque demande de données ou de métadonnées formulée par une application. Pour chaque demande, l'ID de session correspond à la valeur de la propriété <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A>.  
  
 Un ID de session ne garantit pas qu'une session reste valide. Si la session expire (par exemple, en cas de dépassement de délai de la session ou de perte de la connexion), le fournisseur peut choisir de terminer et d'annuler les actions de cette session. Dans ce cas, tous les appels de méthode suivants de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> lèveront une exception. Les exceptions n'étant levées qu'au moment de l'envoi de la demande suivante au fournisseur, et non au moment où la session expire, votre application doit être en mesure de gérer ces exceptions chaque fois que votre application récupère des données ou des métadonnées auprès du fournisseur.  
  
## <a name="closing-a-session"></a>Fermeture d'une session  
 Si le <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> méthode est appelée sans spécifier la valeur de la *endSession* paramètre, ou si le *endSession* paramètre est défini sur True, la connexion à la session et la session associée le <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> objet sont fermées. Pour fermer une session, ADOMD.NET envoie un XMLA **EndSession** en-tête au fournisseur, avec l’ID de session est défini à la valeur de la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> propriété.  
  
 Si le <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A> méthode est appelée avec le *endSession* paramètre défini sur False, la session associée à la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> objet reste actif mais la connexion à la session est fermée.  
  
## <a name="example-of-managing-a-session"></a>Exemple de gestion d'une session  
 L'exemple suivant montre comment ouvrir une connexion, créer une session et fermer la connexion tout en maintenant la session ouverte dans ADOMD.NET :  
  
```vb  
Public Function CreateSession(ByVal connectionString As String) As String  
    Dim strSessionID As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' First, try to connect to the specified data source.  
        ' If the connection string is not valid, or if the specified  
        ' provider does not support sessions, an exception is thrown.  
        objConnection.ConnectionString = connectionString  
        objConnection.Open()  
  
        ' Now that the connection is open, retrieve the new  
        ' active session ID.  
        strSessionID = objConnection.SessionID  
        ' Close the connection, but leave the session open.  
        objConnection.Close(False)  
        Return strSessionID  
  
    Finally  
        objConnection = Nothing  
    End Try  
End Function  
```  
  
```csharp  
static string CreateSession(string connectionString)  
{  
    string strSessionID = "";  
    AdomdConnection objConnection = new AdomdConnection();  
    try  
    {  
        /*First, try to connect to the specified data source.  
          If the connection string is not valid, or if the specified  
          provider does not support sessions, an exception is thrown. */  
        objConnection.ConnectionString = connectionString;  
        objConnection.Open();  
  
        // Now that the connection is open, retrieve the new  
        // active session ID.  
        strSessionID = objConnection.SessionID;  
        // Close the connection, but leave the session open.  
        objConnection.Close(false);  
        return strSessionID;  
    }  
    finally  
    {  
        objConnection = null;  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Établissement de connexions dans ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
  
