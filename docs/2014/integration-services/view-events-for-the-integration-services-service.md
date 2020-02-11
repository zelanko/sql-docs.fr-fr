---
title: Afficher les événements du service Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- events [Integration Services]
- service [Integration Services], events
- Integration Services service, events
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4be91309e4feb34bd8dfd85aee8e3e0cd1f82ffd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66054673"
---
# <a name="view-events-for-the-integration-services-service"></a>afficher les événements du service Integration Services
  Il existe deux outils dans lesquels vous pouvez afficher les événements du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] :  
  
-   La boîte de dialogue **Visionneuse du fichier journal** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. La boîte de dialogue **Visionneuse du fichier Journal** comprend des options permettant d’exporter et de filtrer le journal et d’effectuer des recherches. Pour plus d’informations sur les options de la **Visionneuse du fichier Journal**, consultez [Visionneuse du fichier journal - Aide (F1)](../relational-databases/logs/log-file-viewer-f1-help.md).  
  
-   L'Observateur d'événements Windows.  
  
 Pour obtenir une description des événements consignés par le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , consultez [Événements consignés par le service Integration Services](service/events-logged-by-the-integration-services-service.md).  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a>Pour afficher les événements du service Integration Services dans SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Dans le menu **Fichier** , cliquez sur **Connecter l’Explorateur d’objets**.  
  
3.  Dans la boîte de dialogue **Se connecter au serveur** , sélectionnez le type de serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , sélectionnez ou recherchez le serveur auquel la connexion doit être établie, puis cliquez sur **Se connecter**.  
  
4.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , puis sélectionnez **Afficher les journaux**.  
  
5.  Pour afficher les événements [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , sélectionnez **SQL Server Integration Services**. L’option **Événements NT** est automatiquement sélectionnée et effacée avec l’option **SQL Server Integration Services** .  
  
### <a name="to-view-service-events-for-integration-services-in-windows-event-viewer"></a>Pour afficher les événements du service Integration Services dans l'Observateur d'événements Windows  
  
1.  Dans le **Panneau de configuration**, si vous utilisez l’affichage classique, cliquez sur **Outils d’administration**. Si vous utilisez l’affichage des catégories, cliquez sur **Performance et maintenance** puis sur **Outils d’administration**.  
  
2.  Cliquez sur **Observateur d’événements**.  
  
3.  Dans la boîte de dialogue **Observateur d’événements** , cliquez sur **Application**.  
  
4.  Dans le composant logiciel enfichable **Application** , recherchez dans la colonne **Source** l’entrée dont la valeur est **SQLISService**, cliquez sur cette entrée avec le bouton droit, puis cliquez sur **Propriétés**.  
  
5.  Si vous le souhaitez, cliquez sur la flèche vers le haut ou le bas pour afficher l'événement précédent ou suivant.  
  
6.  Vous pouvez également cliquez sur l'icône Copier dans le Presse-papiers pour copier les informations sur l'événement.  
  
7.  Choisissez d'afficher les données d'événements sous forme d'octets ou de mots.  
  
8.  Cliquez sur **OK**.  
  
9. Dans le menu **Fichier** , cliquez sur **Quitter** pour fermer la boîte de dialogue **Observateur d’événements** .  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer le service de Integration Services](../../2014/integration-services/manage-the-integration-services-service.md)   
 [Ajouter un journal pour les compteurs de performances de flux de données](performance/performance-counters.md)  
  
  
