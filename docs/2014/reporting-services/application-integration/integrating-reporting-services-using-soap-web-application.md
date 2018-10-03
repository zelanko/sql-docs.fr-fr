---
title: Utilisation de l’API SOAP dans une application web | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3853fd48c75cfeb6ec786b0d7d7518112fe07f61
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056320"
---
# <a name="using-the-soap-api-in-a-web-application"></a>Utilisation de l'API SOAP dans une application Web
  Vous pouvez accéder aux fonctionnalités complètes du serveur de rapports via l'API SOAP de Reporting Services. Étant donné qu'il s'agit d'un service Web, l'API SOAP est facilement accessible afin de fournir des fonctionnalités de création de rapports d'entreprise à vos applications de gestion personnalisées. Vous accédez au service Web Report Server à partir d'une application Web à peu près de la même manière que vous accédez à l'API SOAP à partir d'une application [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. À l’aide du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez générer une classe proxy qui expose les propriétés et méthodes du service web Report Server et vous permet d’utiliser une infrastructure et des outils familiers pour générer des applications de gestion basées sur la technologie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Les fonctionnalités de gestion de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont tout aussi faciles d'accès à partir d'une application Web qu'à partir d'une application Windows. À partir d'une application Web, vous pouvez ajouter et supprimer des éléments dans la base de données du serveur de rapports, définir la sécurité des éléments, modifier les éléments de la base de données du serveur de rapports, gérer la planification et la remise, etc.  
  
## <a name="enabling-impersonation"></a>Activation de l'emprunt d'identité  
 La première étape de la configuration de votre application Web consiste à activer l'emprunt d'identité à partir du client de service Web. Avec l'emprunt d'identité, les applications [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] peuvent s'exécuter avec l'identité du client au nom duquel elles s'exécutent. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] compte sur les services Internet (IIS) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour authentifier l'utilisateur et passer soit un jeton authentifié à l'application [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)], soit un jeton non authentifié en cas d'incapacité à authentifier l'utilisateur. Dans les deux cas, l'application [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] emprunte l'identité de n'importe quel jeton reçu si l'emprunt d'identité est activé. Vous pouvez activer l'emprunt d'identité sur le client, en modifiant le fichier Web.config de l'application cliente comme suit :  
  
```  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  L'emprunt d'identité est désactivé par défaut.  
  
 Pour plus d’informations sur l’emprunt d’identité [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)], consultez la documentation du SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="managing-the-report-server-using-soap-api"></a>Gestion du serveur de rapports à l'aide de l'API SOAP  
 Vous pouvez également utiliser votre application Web pour gérer un serveur de rapports et son contenu. Le Gestionnaire de rapports, inclus dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], est un exemple d'application Web complètement créée à l'aide de [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] et de l'API SOAP de Reporting Services. Vous pouvez ajouter les fonctionnalités de gestion de rapports du Gestionnaire de rapports à vos applications Web personnalisées. Par exemple, vous souhaiterez peut-être retourner une liste des rapports disponibles dans la base de données de serveur de rapports et les afficher dans un [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] `Listbox` contrôle pour vos utilisateurs de choisir à partir de. Le code suivant permet de se connecter à la base de données du serveur de rapports et de retourner la liste des éléments contenus dans la base de données du serveur de rapports. Les rapports disponibles sont alors ajoutés à un contrôle ListBox, lequel affiche le chemin d'accès de chaque rapport.  
  
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
 [Création d’applications à l’aide du service web et du .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Intégration de Reporting Services dans des applications](../application-integration/integrating-reporting-services-into-applications.md)   
 [Le Gestionnaire de rapports &#40;SSRS en Mode natif&#41;](../report-manager-ssrs-native-mode.md)   
 [Utilisation de l’API SOAP dans une application Windows](integrating-reporting-services-using-soap-windows-application.md)  
  
  
