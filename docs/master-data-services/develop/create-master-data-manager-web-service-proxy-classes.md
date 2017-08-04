---
title: "Créer des Classes de Proxy de Service Web Master Data Manager | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a45cd15ced90aef95feb03f8fbaafd5aa70cb746
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-master-data-manager-web-service-proxy-classes"></a>Créer des classes proxy de service Web Master Data Manager
  Le service Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] vous permet de programmer les fonctionnalités de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] à partir de n'importe quel ordinateur pouvant accéder à votre site Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Avant de commencer à écrire du code pour accéder au service Web, vous devez générer des classes proxy. La classe proxy principale que vous utilisez pour effectuer des opérations de service Web est la classe <xref:Microsoft.MasterDataServices.ServiceClient>, qui implémente l'interface <xref:Microsoft.MasterDataServices.IService>.  
  
## <a name="enable-web-service-metadata-publishing"></a>Activer la publication de métadonnées de service Web  
 Avant de pouvoir générer des classes proxy, vous devez activer la publication de métadonnées de service Web. Suivez ces étapes pour ce faire :  
  
1.  Ouvrez le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] fichier Web.config dans un éditeur de texte. Ce fichier se trouve dans le dossier WebApplication du chemin d'installation de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Rechercher les **mdsWsHttpBehavior** sous  **\<serviceBehaviors >**. Pour le  **\<serviceMetadata >** élément, la valeur **httpGetEnabled** à **true**.  
  
    > [!NOTE]  
    >  Si vous souhaitez activer les services Web via SSL Secure Sockets Layer (), la valeur **httpsGetEnabled** à **true** dans les **mdsWsHttpBehavior** section du fichier web.config. Vous devez également modifier **mdsWsHTTPBinding** afin qu’il est configuré pour SSL, également et commentez la section non-SSL.  
  
3.  Enregistrez les modifications apportées au fichier.  
  
4.  Publication de métadonnées de test en accédant à l’URL du service, par exemple : `http://yourserver/MDS/service/service.svc`. Si la publication de métadonnées est activée, une page s'affiche, commençant par :   
    « Vous avez créé un service. »  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a>Création de classes proxy à l'aide de Visual Studio  
 Si vous avez installé Visual Studio 2010, le plus simple pour générer des classes proxy consiste à ajouter un **une référence de Service** à votre projet. L'adresse de la référence de service est l'URL de l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], suivie de /service/service.svc. Par exemple : `http://yourserver/MDS/service/service.svc`. Pour plus d’informations, consultez [Comment : ajouter, mettre à jour ou supprimer une référence de Service](http://go.microsoft.com/fwlink/?LinkId=221167).  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a>Création de classes proxy à l'aide de Svcutil.exe  
 Vous devez avoir [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou le [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK est installé pour avoir Svcutil.exe sur votre ordinateur. Si vous utilisez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vous devez utiliser l'invite de commandes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pour exécuter la commande. Pour plus d’informations, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](http://go.microsoft.com/fwlink/?LinkId=165027) et [génération d’un Client WCF à partir des métadonnées de Service](http://go.microsoft.com/fwlink/?LinkId=164821).  
  
 Pour créer un jeu de classes proxy C# à l'aide de Svcutil.exe, utilisez une commande telle que :  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 Où :  
  
-   *nom_serveur*:*port* sont le nom d’ordinateur et le numéro de port de l’ordinateur qui héberge [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
-   *CheminVirtuel* est le chemin d’accès virtuel de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] dans Internet Information Services (IIS).  
  
-   *proxy_name* est le nom du fichier proxy généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de Service Web par catégorie &#40; Master Data Services &#41;](../../master-data-services/develop/categorized-web-service-operations-master-data-services.md)  
  
  
