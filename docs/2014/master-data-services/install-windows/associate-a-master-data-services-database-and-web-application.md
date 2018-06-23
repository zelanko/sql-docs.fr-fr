---
title: Associer une base de données Master Data Services et une application web | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 08be865103fd45fc3bd8e33520df735ceabec202
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153743"
---
# <a name="associate-a-master-data-services-database-and-web-application"></a>Associer une base de données Master Data Services et une application Web
  Associez votre application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour spécifier la base de données à utiliser pour les opérations web.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] doit être installé sur l’ordinateur local. Pour plus d’informations, consultez [Installer Master Data Services](install-master-data-services.md).  
  
-   Une application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] locale doit exister. Pour plus d’informations, consultez [Créer une application web Master Data Manager &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).  
  
-   Une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] locale ou distante doit exister. Pour plus d’informations, consultez [Créer une base de données Master Data Services](create-a-master-data-services-database.md).  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a>Pour associer une base de données Master Data Services et une application Web  
  
1.  Ouvrez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Dans le volet gauche, cliquez sur **Configuration Web**.  
  
3.  Dans la page **Configuration Web** , sous **Application Web**, dans la liste **Site Web** , sélectionnez le site web qui contient votre application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
4.  Dans la zone **Application web** , sélectionnez l’application web qui héberge [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
5.  Sous **Associer l’application à une base de données**, cliquez sur **Sélectionner**. La boîte de dialogue **Connexion à une base de données** s’ouvre.  
  
6.  Spécifiez les informations de connexion pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et cliquez sur **Se connecter**.  
  
7.  Dans la liste **Base de données Master Data Services** , sélectionnez la base de données que vous souhaitez associer à l’application web et cliquez sur **OK**.  
  
8.  Sous **Associer l’application à une base de données**, vérifiez que l’instance et les informations de la base de données sont correctes, puis cliquez sur **Appliquer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Lorsque l'application Web est créée, l'accès par programme au service Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] est automatiquement activé. Pour permettre aux développeurs d'accéder aux métadonnées de service afin de créer facilement des classes proxy pour l'accès par programme, activez la publication de métadonnées. Pour plus d’informations, consultez [Créer des classes proxy de service Web Master Data Manager](../develop/create-master-data-manager-web-service-proxy-classes.md).  
  
-   Ajoutez des utilisateurs et des groupes à [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Si aucun utilisateur ou groupe n’a accès à [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], vous devez ouvrir [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à l’aide des informations d’identification de l’administrateur système [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../administrators-master-data-services.md) et [Utilisateurs et groupes &#40;Master Data Services&#41;](../users-and-groups-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Master Data Services](install-master-data-services.md)   
 [Page Configuration web &#40;Gestionnaire de configuration Master Data Services&#41;](../web-configuration-page-master-data-services-configuration-manager.md)  
  
  