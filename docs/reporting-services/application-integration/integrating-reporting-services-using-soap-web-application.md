---
title: "À l’aide de l’API SOAP dans une Application Web | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 15901a45f5342fa5c7d26a9b95230eabb67e20af
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="integrating-reporting-services-using-soap---web-application"></a>Intégration de Reporting Services à l’aide de SOAP - Application Web
  Vous pouvez accéder aux fonctionnalités complètes du serveur de rapports via l'API SOAP de Reporting Services. Étant donné qu'il s'agit d'un service Web, l'API SOAP est facilement accessible afin de fournir des fonctionnalités de création de rapports d'entreprise à vos applications de gestion personnalisées. Vous accédez au service Web Report Server à partir d'une application Web à peu près de la même manière que vous accédez à l'API SOAP à partir d'une application [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. À l’aide de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez générer une classe proxy qui expose les propriétés et méthodes du Web Report Server service et vous permet d’utiliser des outils et une infrastructure familier pour générer des applications d’entreprise [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] technologie.  
  
 Les fonctionnalités de gestion de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont tout aussi faciles d'accès à partir d'une application Web qu'à partir d'une application Windows. À partir d'une application Web, vous pouvez ajouter et supprimer des éléments dans la base de données du serveur de rapports, définir la sécurité des éléments, modifier les éléments de la base de données du serveur de rapports, gérer la planification et la remise, etc.  
  
## <a name="enabling-impersonation"></a>Activation de l'emprunt d'identité  
 La première étape de la configuration de votre application Web consiste à activer l'emprunt d'identité à partir du client de service Web. Avec l'emprunt d'identité, les applications [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] peuvent s'exécuter avec l'identité du client au nom duquel elles s'exécutent. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] compte sur les services Internet (IIS) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour authentifier l'utilisateur et passer soit un jeton authentifié à l'application [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)], soit un jeton non authentifié en cas d'incapacité à authentifier l'utilisateur. Dans les deux cas, l'application [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] emprunte l'identité de n'importe quel jeton reçu si l'emprunt d'identité est activé. Vous pouvez activer l'emprunt d'identité sur le client, en modifiant le fichier Web.config de l'application cliente comme suit :  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  L'emprunt d'identité est désactivé par défaut.  
  
 Pour plus d’informations sur [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] l’emprunt d’identité, consultez la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation du Kit de développement logiciel.  
  
## <a name="managing-the-report-server-using-soap-api"></a>Gestion du serveur de rapports à l'aide de l'API SOAP  
 Vous pouvez également utiliser votre application Web pour gérer un serveur de rapports et son contenu. Le Gestionnaire de rapports, inclus dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], est un exemple d'application Web complètement créée à l'aide de [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] et de l'API SOAP de Reporting Services. Vous pouvez ajouter les fonctionnalités de gestion de rapports du Gestionnaire de rapports à vos applications Web personnalisées. Par exemple, vous pouvez souhaiter renvoyer une liste des rapports disponibles dans la base de données du serveur de rapports et les afficher dans un [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] **Listbox** contrôle pour vos utilisateurs à sélectionner. Le code suivant permet de se connecter à la base de données du serveur de rapports et de retourner la liste des éléments contenus dans la base de données du serveur de rapports. Les rapports disponibles sont alors ajoutés à un contrôle ListBox, lequel affiche le chemin d'accès de chaque rapport.  
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Intégration de Reporting Services dans des Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [À l’aide de l’API SOAP dans une Application Windows](../../reporting-services/application-integration/integrating-reporting-services-using-soap-windows-application.md)  
  
  
