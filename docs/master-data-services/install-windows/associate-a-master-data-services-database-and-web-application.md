---
title: Associer la base de données et l’application Web
ms.custom: seo-lt-2019
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d82bee5e275365b72adb3700cae8c11e6e67c9e7
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75253085"
---
# <a name="associate-a-master-data-services-database-and-web-application"></a>Associer une base de données Master Data Services et une application Web

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Associez votre application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour spécifier la base de données à utiliser pour les opérations web.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   
  [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] doit être installé sur l’ordinateur local. Pour plus d’informations, consultez [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md).  
  
-   Une application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] locale doit exister. Pour plus d’informations, consultez [Créer une application web Master Data Manager &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
-   Une base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] locale ou distante doit exister. Pour plus d’informations, consultez [Créer une base de données Master Data Services](../../master-data-services/install-windows/create-a-master-data-services-database.md).  
  
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
  
-   Lorsque l'application Web est créée, l'accès par programme au service Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] est automatiquement activé. Pour permettre aux développeurs d'accéder aux métadonnées de service afin de créer facilement des classes proxy pour l'accès par programme, activez la publication de métadonnées. Pour plus d’informations, consultez [Créer des classes proxy de service Web Master Data Manager](../../master-data-services/develop/create-master-data-manager-web-service-proxy-classes.md).  
  
-   Ajoutez des utilisateurs et des groupes à [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Si aucun utilisateur ou groupe n’a accès à [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], vous devez ouvrir [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] à l’aide des informations d’identification de l’administrateur système [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md) et [Utilisateurs et groupes &#40;Master Data Services&#41;](../../master-data-services/users-and-groups-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
 [Page de configuration Web &#40;Gestionnaire de configuration Master Data Services&#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  
