---
title: "L’authentification du Service de Web | Documents Microsoft"
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
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 95f694a89450016929fa5129aa823c7242ef0056
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="web-service-authentication"></a>Authentification du Service Web
  Vous pouvez utiliser l'authentification Windows ou l'authentification de base pour authentifier les appels effectués auprès du service Web Report Server. Tout client qui effectue des demandes SOAP au serveur de rapports doit implémenter la partie cliente de l'un des protocoles d'authentification pris en charge. Si vous utilisez la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vous pouvez utiliser les classes HTTP du code managé pour implémenter l’authentification. L'utilisation de ces API simplifie l'envoi des informations d'authentification et des demandes SOAP.  
  
 Si vous n'avez pas les informations d'identification appropriées avant d'effectuer un appel auprès du service Web Report Server, l'appel échoue. Au moment de l’exécution, vous pouvez passer des informations d’identification au service Web en définissant le **informations d’identification** propriété de l’objet côté client qui représente le service Web avant d’appeler ses méthodes.  
  
 Les sections suivantes contiennent un exemple de code qui envoie des informations d'identification à l'aide de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="windows-authentication"></a>Authentification Windows  
 Le code suivant passe des informations d'identification Windows au service Web.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a>Authentification de base  
 Le code suivant passe des informations d'identification de base au service Web.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 Les informations d'identification doivent être définies avant d'appeler chacune des méthodes du service Web Report Server. Si vous ne définissez pas ces informations, vous recevez le code d'erreur HTTP 401 : Accès refusé. Vous devez vous authentifier le service avant que vous l’utilisez, mais après avoir défini les informations d’identification, vous n’avez pas besoin de les définir à nouveau tant que vous continuez à utiliser la même variable de service (tel que *rs*).  
  
## <a name="custom-authentication"></a>Authentification personnalisée  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclut une API de programmation qui permet aux développeurs de concevoir et de développer des extensions d'authentification personnalisées appelées extensions de sécurité. Pour plus d’informations, consultez [Implémentation d’une extension de sécurité](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service Web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
