---
title: Aperçu | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 551494c4-9e27-4592-9200-c6bf19e80c9a
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fa7f94ad690362189b29c7e86e34519d1a937bc1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281595"
---
# <a name="preview"></a>Aperçu
  Utilisez la boîte de dialogue **Aperçu** pour afficher un aperçu des données que la source SAP BW devra extraire.  
  
> [!IMPORTANT]  
>  L'option **Aperçu** , qui est disponible sur la page **Gestionnaire de connexions** de l' **Éditeur de source SAP BW**, extrait réellement des données. Si vous avez configuré le système SAP Netweaver BW pour extraire uniquement les données qui ont été modifiées depuis l'extraction précédente, la sélection d' **Aperçu** exclura les données de l'aperçu de l'extraction suivante.  
  
 Pour en savoir plus sur le composant source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Source SAP BW](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
 **Pour ouvrir la boîte de dialogue Aperçu**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source SAP BW.  
  
3.  Dans l' **Éditeur de source SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Configurez la source SAP BW.  
  
5.  Après avoir configuré la source SAP BW, sur la page **Gestionnaire de connexions** , cliquez sur **Aperçu** pour afficher un aperçu des données dans la boîte de dialogue **Aperçu** .  
  
    > [!NOTE]  
    >  Cliquer sur **Aperçu** ouvre également la boîte de dialogue **Journal des requêtes** . Pour plus d'informations sur cette boîte de dialogue, consultez [Request Log](request-log.md).  
  
## <a name="options"></a>Options  
 La boîte de dialogue **Aperçu** affiche les lignes qui sont demandées par le système SAP Netweaver BW. Les colonnes qui sont affichées sont les colonnes qui sont définies dans les données sources.  
  
 Il n'existe aucune autre option dans cette boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source SAP BW &#40;Page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
