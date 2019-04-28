---
title: Limiter l’historique de rapport (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe038f264a1bf748414715b0f51a32c5f14531bf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63012246"
---
# <a name="limit-report-history-report-manager"></a>Limiter l'historique de rapport (Gestionnaire de rapports)
  L'historique de rapport est un ensemble d'instantanés de rapport que vous créez au fil du temps. Vous pouvez soit créer l'historique de rapport à la demande, soit planifier la fréquence à laquelle un instantané est créée et ajoutée à l'historique de rapport.  
  
 L'historique de rapport est stocké dans la base de données du serveur de rapports. Si les instantanés de rapport contiennent une grande quantité de données, songez à limiter l'historique de rapport afin de réduire l'impact de la rétention des instantanés sur la taille de la base de données.  
  
### <a name="to-configure-report-history-for-a-report-server"></a>Pour configurer un historique de rapport destiné à un serveur de rapports  
  
1.  Dans le Gestionnaire de rapports, dans la barre d’outils globale, cliquez sur **Paramètres du site** .  
  
2.  Sélectionnez l’option **Conserver un nombre illimité d’instantanés dans l’historique de rapport** pour conserver tous les historiques de rapport sur une durée indéterminée. Sinon, choisissez **Limiter les copies de l’historique de rapport** pour spécifier le nombre maximal d’instantanés à conserver pour un rapport donné.  
  
3.  Cliquez sur **Appliquer**.  
  
### <a name="to-configure-report-history-for-a-specific-report"></a>Pour configurer un historique de rapport destiné à un rapport spécifique  
  
1.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'au rapport pour lequel configurer l'historique, puis cliquez sur cet élément pour l'ouvrir.  
  
2.  Cliquez sur l’onglet **Propriétés** .  
  
3.  Cliquez sur l’onglet **Historique** .  
  
4.  Sélectionnez les options pour votre rapport, puis cliquez sur **Appliquer**. Pour plus d’informations sur chaque option, consultez [Page de propriétés Options d’instantanés &#40;Gestionnaire de rapports&#41;](../snapshot-options-properties-page-report-manager.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’un instantané à un historique de rapport &#40;Gestionnaire de rapports&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md)  
  
  
