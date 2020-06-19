---
title: Rechercher la destination RFC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: db9404d8-4c42-45e5-a100-c7a84b056109
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ae4c22636095f211eef836b709beac269938c730
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84915249"
---
# <a name="look-up-rfc-destination"></a>Rechercher la destination RFC
  Utilisez la boîte de dialogue **Rechercher la destination RFC** pour rechercher une destination RFC qui est définie dans le système SAP Netweaver BW. Lorsque la liste de destinations RFC disponibles apparaît, sélectionnez la destination de votre choix. Le composant remplira les options associées à l'aide des valeurs requises.  
  
 La source SAP BW et la destination SAP BW utilisent toutes les deux la boîte de dialogue **Rechercher la destination RFC** . Pour plus d’informations sur ces composants de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Source SAP BW](sap-bw-source.md) et [Destination SAP BW](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Rechercher la destination RFC**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source ou la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source ou la destination SAP BW.  
  
3.  Dans l' **Éditeur de source SAP BW** ou dans l' **Éditeur de destination SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Sur la page **Gestionnaire de connexions** , dans la zone de groupe **Destination RFC** , cliquez sur **Rechercher** pour afficher la boîte de dialogue **Rechercher la destination RFC** .  
  
     Dans **l’Éditeur de source SAP BW**, la zone de groupe **Destination RFC** s’affiche uniquement si l’option **Mode d’exécution** a la valeur **P - Déclencher une chaîne de processus** ou **A - Attendre la notification**.  
  
## <a name="options"></a>Options  
 **Destination**  
 Affichez le nom de la destination RFC qui est définie dans le système SAP Netweaver BW.  
  
 **Hôte de passerelle**  
 Affichez le nom du serveur ou l'adresse IP de l'hôte de passerelle. Généralement, le nom ou l'adresse IP est identique au serveur d'applications SAP.  
  
 **Service de passerelle**  
 Entrez le nom du service de passerelle, au format `sapgwNN`, où `NN` représente le numéro du système.  
  
 **ID de programme**  
 Affichez l'ID de programme associé à la destination RFC.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Éditeur de destination SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
