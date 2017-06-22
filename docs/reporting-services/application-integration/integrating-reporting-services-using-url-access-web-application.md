---
title: "À l’aide de l’accès URL dans une Application Web | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
caps.latest.revision: 33
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f931c5bd79835f8cf2ce9ceb88078e9408ace71a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="integrating-reporting-services-using-url-access---web-application"></a>Intégration de Reporting Services à l’aide de l’accès URL - Application Web
  L'accès URL dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est conçu spécifiquement pour permettre l'accès à des rapports individuels sur un réseau. Ce type d'accès convient pour intégrer l'affichage des rapports et la navigation au sein de ces derniers dans une application Web personnalisée. Pour utiliser l'accès URL dans des applications Web, vous pouvez :  
  
-   définir une URL vers un serveur de rapports spécifique à partir d'un site ou d'un portail Web ;  
  
-   utiliser une méthode POST de formulaire et passer des paramètres de chaîne de requête à une URL du serveur de rapports à l'aide de champs de formulaire.  
  
## <a name="url-access-through-direct-addressing"></a>Accès URL via l'adressage direct  
 Pour accéder à un serveur de rapports ou un élément de base de données de serveur de rapports à l’aide d’une URL, il suffit de fournir l’adresse URL dans un navigateur Web ou une application. Vous pouvez également fournir des paramètres à l'URL qui peuvent affecter l'apparence du rapport ou de la ressource en cours d'accès. Une URL peut cibler un serveur de rapports via la barre d’adresses d’un navigateur Web, ou une URL peut être la source d’un **IFrame** qui fait partie d’une application Web plus importante ou le portail. Vous pouvez ajouter des liens hypertexte à des rapports sur différentes pages Web de votre portail, et cibler un frame spécifique pour le rapport ou ouvrir une nouvelle fenêtre de navigateur dans le processus.  
  
 Dans l'exemple suivant, le lien hypertexte cible un frame nommé « main » qui peut être différent de celui qui inclut le lien hypertexte. Le lien hypertexte peut faire partie d'un portail Web.  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 Dans l’exemple précédent, les paramètre d’informations de périphérique **LinkTarget** est passé avec la valeur « main » dans la chaîne de requête de l’URL. De cette manière, tous les liens hypertexte d'extraction dans le rapport ciblent également le frame nommé « main ».  
  
 Pour plus d’informations sur les paramètres d’informations de périphérique, consultez [en passant des paramètres d’informations de périphérique aux Extensions de rendu](../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
 Notez que de nombreux serveurs et navigateurs limitent le nombre de caractères autorisés dans une URL. Dans certains cas, une limite de 256 caractères est imposée. Pour contourner cette limitation, vous pouvez utiliser des requêtes POST à l'aide de l'envoi de formulaire.  
  
> [!NOTE]  
>  Internet Explorer impose une longueur maximale de 2 083 caractères dans les URL. Cette limite s'applique aux URL de requêtes POST et GET. Toutefois, POST n'est pas limité par la taille de l'URL pour l'envoi de paires nom/valeur dans le cadre d'un formulaire, celles-ci étant transférées dans l'en-tête et non dans l'URL.  
  
## <a name="url-access-through-a-form-post-method"></a>Accès URL via une méthode POST de formulaire  
 Lorsqu'un utilisateur demande des données à partir d'un serveur de rapports à l'aide de l'accès URL, la requête HTTP utilise la méthode GET. Ceci équivaut à un envoi de formulaire où METHOD="GET". Les demandes d'URL ou les envois de formulaire qui utilisent METHOD="GET" sont limités par le nombre maximal de caractères qu'un serveur ou navigateur Web peut traiter.  
  
 Avec les requêtes POST (METHOD="POST" et champs d'entrée), les paires nom/valeur sont transférées dans l'en-tête et non dans l'URL. Par conséquent, les paires nom/valeur de la chaîne de requête ne font pas partie de l'URL, ce qui vous permet de fournir des listes de paramètres plus longues et plus complexes.  
  
 À l'aide de l'accès direct, un utilisateur peut afficher l'URL pour le serveur de rapports et éventuellement modifier la chaîne de requête ou noter les paramètres particuliers de la demande d'URL et du serveur de rapports pour une utilisation ultérieure.  
  
 L'exemple de code HTML suivant montre l'utilisation d'un formulaire que vous pouvez utiliser pour cibler un serveur de rapports avec une URL spécifique et passer des paramètres de chaîne de requête dans le cadre des champs d'entrée du formulaire.  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 Dans l'exemple précédent, si un utilisateur clique sur le bouton du formulaire, le serveur de rapports retourne un rapport rendu en HTML ciblant le frame actuel. Une chaîne d'accès URL comparable peut se présenter comme suit :  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration de Reporting Services dans des Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Intégration de Reporting Services à l’aide de l’accès URL](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [À l’aide de l’accès URL dans une Application Windows](../../reporting-services/application-integration/integrating-reporting-services-using-url-access-windows-application.md)   
 [Accès URL &#40; SSRS &#41;](../../reporting-services/url-access-ssrs.md)  
  
  
