---
title: "Création du Proxy de Service Web | Documents Microsoft"
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
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
caps.latest.revision: 44
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: 1c39d81ec9a1d2cd24f01b9dccfed13e8560a770
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="creating-the-web-service-proxy"></a>Création du proxy de service Web
  Un client et un service Web peuvent communiquer à l'aide de messages SOAP qui encapsulent les paramètres d'entrée et de sortie au format XML. Une classe proxy mappe des paramètres aux éléments XML puis envoie les messages SOAP sur un réseau. De cette manière, la classe proxy vous évite de devoir communiquer avec le service Web au niveau SOAP et vous permet d'appeler des méthodes de service Web dans tout environnement de développement qui prend en charge les proxies de service Web et SOAP.  
  
 Il existe deux façons d’ajouter une classe proxy dans votre projet de développement en utilisant le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: avec l’outil WSDL dans la [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]et en ajoutant une référence Web dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Les sections suivantes approfondissent ce sujet.  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a>Ajout du proxy à l'aide de l'outil WSDL  
 Le Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] inclut l'outil Web Services Description Language (Wsdl.exe) qui vous permet de générer un proxy de service Web pour une utilisation dans l'environnement de développement [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. La méthode la plus courante pour créer un proxy client dans les langages qui prennent en charge des services Web (actuellement c# et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) consiste à utiliser l’outil WSDL.  
  
 **Pour ajouter une classe proxy à votre projet à l’aide de Wsdl.exe**  
  
1.  À partir d'une invite de commandes, utilisez Wsdl.exe pour créer une classe proxy en spécifiant (au minimum) l'URL du service Web Report Server.  
  
     Par exemple, l'instruction d'invite de commandes suivante spécifie une URL pour le point de terminaison de gestion du service Web Report Server :  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     L'outil WSDL accepte plusieurs arguments d'invite de commandes pour générer un proxy. L'exemple précédent spécifie le langage C#, un espace de noms suggéré à utiliser dans le proxy (évite la collision de nom en présence de plusieurs points de terminaison de service Web), et génère un fichier C# appelé ReportingService2010.cs. Si l'exemple avait spécifié [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], l'exemple aurait généré un fichier proxy avec le nom ReportingService2010.vb. Ce fichier est créé dans le répertoire à partir duquel vous exécutez la commande.  
  
2.  Compilez la classe proxy dans un fichier d'assembly (avec l'extension .dll) et référencez-la dans votre projet ou ajoutez la classe comme un élément de projet.  
  
    > [!NOTE]  
    >  Lorsque vous ajoutez manuellement une classe proxy à votre projet, vous devez ajouter une référence à System.Web.Services.dll. Si vous ajoutez le proxy à l'aide d'une référence Web dans Visual Studio .NET, la référence est créée automatiquement. Pour plus d'informations, consultez « Ajout du proxy à l'aide d'une référence Web dans Visual Studio » plus loin dans cette rubrique.  
  
     Après avoir ajouté la classe proxy comme un élément à votre projet, le fichier associé s'affiche dans l'Explorateur de solutions.  
  
3.  Pour appeler le service par programme, créez une instance de la classe proxy.  
  
     L'exemple de code suivant affiche la syntaxe permettant de créer une instance de la classe proxy <xref:ReportService2010.ReportingService2010> dans un projet :  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 Pour plus d'informations sur l'outil Wsdl.exe, y compris sa syntaxe complète, consultez la rubrique « Web Services Description Language Tool » dans la documentation du Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Pour une explication complète des proxies de service Web, consultez « Création d'un proxy de service Web XML » dans la documentation du Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a>Ajout du proxy à l'aide d'une référence Web dans Visual Studio  
 Une référence Web permet à un projet de faire appel à un ou plusieurs services Web [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] permet aux utilisateurs d'ajouter des références de service Web aux projets en suivant quelques étapes simples.  
  
 **Pour ajouter une référence Web à un projet**  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le projet qui utilisera le service Web.  
  
2.  Sur le **projet** menu, cliquez sur **ajouter une référence Web**.  
  
     Le **ajouter une référence Web** boîte de dialogue s’ouvre.  
  
3.  Dans le **URL** , entrez le chemin d’accès complet au service Web Report Server.  
  
     Voici une URL simplifiée pour le point de terminaison d'exécution du rapport du service Web Report Server :  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     L'URL contient le domaine de déploiement du service Web Report Server, le nom du dossier qui contient le service, et le nom du fichier de découverte pour le service. Pour obtenir une description complète des différents éléments d’URL, consultez [l’accès à l’API SOAP](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md).  
  
     Une description des méthodes et propriétés fournies par le service Web apparaît dans le volet Navigateur sur la gauche.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur les éléments associés au service Web Report Server, consultez [méthodes de Service Web Report Server](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md).  
  
4.  Vérifiez que votre projet peut utiliser le service Web Report Server, et que vous avez l'autorisation appropriée d'accéder au serveur de rapports.  
  
5.  Dans le **nom de référence Web** , entrez un nom que vous utiliserez dans votre code pour accéder par programme au service Web Report Server.  
  
6.  Sélectionnez le **ajouter une référence** bouton permettant de créer une référence dans votre application au service Web.  
  
     La nouvelle référence s’affiche dans **l’Explorateur de solutions** sous le nœud Références Web pour le projet actif, nommé comme spécifié dans le **nom de référence Web** champ.  
  
7.  Dans **l’Explorateur de solutions**, développez le dossier références Web pour noter l’espace de noms pour les classes de référence Web qui sont disponibles pour les éléments dans votre projet.  
  
     Après avoir ajouté une référence Web à votre projet, les fichiers associés sont affichés dans un dossier dans le dossier des références Web **l’Explorateur de solutions**.  
  
 Après avoir ajouté la référence Web, utilisez la syntaxe suivante pour créer une instance de la classe proxy :  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 Vous pouvez également ajouter un **à l’aide de** (**importation** dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) directive pour la référence de service Web Report Server. Si vous utilisez cette directive, il n'est pas nécessaire de qualifier complètement les types dans l'espace de noms. Pour cela, ajoutez le code suivant à votre fichier :  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Service Web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Informations techniques de référence &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
