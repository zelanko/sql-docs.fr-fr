---
title: Ouverture de session Reporting Services, boîte de dialogue (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6bc56775aa932f26caeaa1eab9e67a0845f19b27
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077869"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Ouverture de session Reporting Services, boîte de dialogue (SSRS)
  Utilisez la boîte de dialogue **Ouverture de session Reporting Services** pour fournir les informations d'identification nécessaires à la publication de rapports sur le serveur de rapports.  
  
-   **Remarque** S'il s'agit de la première fois que vous avez publié un rapport sur un serveur de rapports depuis que vous avez défini la propriété de déploiement **TargetServerURL** pour un projet, vérifiez que le nom du serveur que vous avez spécifié est semblable à `http://localhost/reportserver`, et non à `http://localhost/reports`. La spécification du répertoire `reports` sur le serveur local au lieu du répertoire `reportserver` provoque indirectement l'ouverture de cette boîte de dialogue. Pour plus d’informations sur la configuration de **TargetServerURL**, consultez [Définir des propriétés de déploiement &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Options  
 **Server**  
 Affiche le nom du serveur de rapports. Par exemple, `http://localhost/reportserver`. Pour les serveurs de rapports qui utilisent un autre port que le port par défaut 80, incluez le numéro de port. Par exemple, `http://localhost:81/reportserver`.  
  
 **Nom d'utilisateur**  
 Tapez le nom d'utilisateur pour la connexion au service Web.  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion au service Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Spécifiez les informations d’identification et les informations de connexion pour les Sources de données de rapport](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [aide F1 de Concepteur de rapports](report-designer-f1-help.md)  
  
  
