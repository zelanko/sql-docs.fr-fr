---
title: Créer un InfoSource | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7db233b-5464-43de-9d26-6dd24c7ac1b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a81bf2cef2329853df05eda97e2ce53501369c8
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923540"
---
# <a name="create-infosource"></a>Créer un InfoSource

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Utilisez la boîte de dialogue **Créer un InfoSource** pour créer un InfoSource. Pour créer l’InfoSource, utilisez la boîte de dialogue **Créer un InfoSource pour les données de transaction** ou **Créer un InfoSource pour les données maîtres** .  
  
 Vous pouvez ouvrir la boîte de dialogue **Créer un InfoSource** à partir de la page **Gestionnaire de connexions** de l’ **Éditeur de destination SAP BW**. Pour en savoir plus sur la destination SAP BW, consultez [Destination SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Créer un InfoSource**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la destination SAP BW.  
  
3.  Dans l' **Éditeur de destination SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la page **Gestionnaire de connexions** , dans la zone de groupe **Créer des objets SAP BW** , sélectionnez **InfoSource**, puis cliquez sur **Créer**.  
  
## <a name="options"></a>Options  
 **Données de transaction**  
 Créez un InfoSource pour les données de transaction.  
  
 Si vous sélectionnez cette option, la boîte de dialogue **Créer un InfoSource pour les données de transaction** s’affiche. Utilisez la boîte de dialogue **Créer un InfoSource pour les données de transaction** pour créer l’InfoSource. Pour plus d’informations sur cette boîte de dialogue, consultez [Créer un InfoSource pour les données de transaction](../../integration-services/data-flow/create-infosource-for-transaction-data.md).  
  
 **Données maîtres**  
 Créez un InfoSource pour les données maîtres.  
  
 Si vous sélectionnez cette option, la boîte de dialogue **Créer un InfoSource pour les données maîtres** s’affiche. Utilisez la boîte de dialogue **Créer un InfoSource pour les données maîtres** pour créer l’InfoSource. Pour plus d’informations sur cette boîte de dialogue, consultez [Créer un Infosource pour les données maîtres](../../integration-services/data-flow/create-infosource-for-master-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) sur Microsoft Connector pour SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
