---
title: Ouverture de session Reporting Services, boîte de dialogue (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 232ee51614a668b07263c3e3a4182f23652135bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099870"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Ouverture de session Reporting Services, boîte de dialogue (SSRS)
  Utilisez la boîte de dialogue **Ouverture de session Reporting Services** pour fournir les informations d'identification nécessaires à la publication de rapports sur le serveur de rapports.  
  
-   **Remarque** S’il s’agit de la première fois que vous publiez un rapport sur un serveur de rapports depuis que vous avez défini la propriété de déploiement **TargetServerURL** pour un projet, vérifiez que le nom `http://localhost/reportserver`du serveur que `http://localhost/reports`vous avez spécifié est semblable à, et non. La spécification du répertoire `reports` sur le serveur local au lieu du répertoire `reportserver` provoque indirectement l'ouverture de cette boîte de dialogue. Pour plus d’informations sur la configuration de **TargetServerURL**, consultez [Définir des propriétés de déploiement &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Options  
 **Serveur**  
 Affiche le nom du serveur de rapports. Par exemple : `http://localhost/reportserver`. Pour les serveurs de rapports qui utilisent un autre port que le port par défaut 80, incluez le numéro de port. Par exemple : `http://localhost:81/reportserver`.  
  
 **Nom d'utilisateur**  
 Tapez le nom d'utilisateur pour la connexion au service Web.  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion au service Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Spécifier les informations d’identification et de connexion pour les sources de données de rapport](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Concepteur de rapports aide F1](report-designer-f1-help.md)  
  
  
