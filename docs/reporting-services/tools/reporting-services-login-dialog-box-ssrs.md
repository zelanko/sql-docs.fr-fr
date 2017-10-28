---
title: "Boîte de dialogue de connexion de Services (SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sql13.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
caps.latest.revision: 31
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3f9da76454e0b1fe52499471cbb3a04ada2d896e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Ouverture de session Reporting Services, boîte de dialogue (SSRS)
  Utilisez la boîte de dialogue **Ouverture de session Reporting Services** pour fournir les informations d'identification nécessaires à la publication de rapports sur le serveur de rapports.  
  
-   **Remarque** S’il s’agit de la première fois que vous publiez un rapport sur un serveur de rapports depuis que vous avez défini la propriété de déploiement **TargetServerURL** pour un projet, vérifiez que le nom du serveur comprend le mot **server** et non **reports**. Par exemple, `http://localhost/reportserver`, et non à `http://localhost/reports`. La spécification du répertoire `reports` sur le serveur local au lieu du répertoire `reportserver` provoque indirectement l'ouverture de cette boîte de dialogue. Pour plus d’informations sur la configuration de **TargetServerURL**, consultez [Définir des propriétés de déploiement &#40;Reporting Services&#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Options  
 **Server**  
 Affiche le nom du serveur de rapports. Par exemple, `http://localhost/reportserver`. Pour les serveurs de rapports qui utilisent un autre port que le port par défaut 80, incluez le numéro de port. Par exemple, `http://localhost:81/reportserver`.  
  
 **Nom d'utilisateur**  
 Tapez le nom d'utilisateur pour la connexion au service Web.  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion au service Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, sources de données et chaînes de connexion &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Spécifiez les informations d’identification et les informations de connexion pour les Sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Aide F1 sur le Concepteur de rapports](../../reporting-services/tools/report-designer-f1-help.md)  
  
  

