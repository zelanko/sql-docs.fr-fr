---
title: Limiter l’historique de rapport - Reporting Services | Microsoft Docs
description: Découvrez comment configurer un historique de rapport pour un serveur de rapports. Découvrez également comment configurer un historique pour un rapport.
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
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
ms.openlocfilehash: 634a033c06b2ed6815e32cf97829118dafa13b5f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510120"
---
# <a name="limit-report-history---reporting-services"></a>Limiter l’historique de rapport - Reporting Services
  L'historique de rapport est un ensemble d'instantanés de rapport que vous créez au fil du temps. Vous pouvez soit créer l'historique de rapport à la demande, soit planifier la fréquence à laquelle un instantané est créée et ajoutée à l'historique de rapport.  
  
 L'historique de rapport est stocké dans la base de données du serveur de rapports. Si les instantanés de rapport contiennent une grande quantité de données, pensez à limiter l’historique de rapport afin de réduire l’impact de la conservation des instantanés sur la taille de la base de données.  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
## <a name="to-configure-report-history-for-a-report-server"></a>Pour configurer un historique de rapport destiné à un serveur de rapports  
  
1.  Dans le Gestionnaire de rapports, dans la barre d’outils globale, cliquez sur **Paramètres du site** .  
  
2.  Sélectionnez l’option **Conserver un nombre illimité d’instantanés dans l’historique de rapport** pour conserver tous les historiques de rapport sur une durée indéterminée. Sinon, choisissez **Limiter les copies de l’historique de rapport** pour spécifier le nombre maximal d’instantanés à conserver pour un rapport donné.  
  
3.  Cliquez sur **Appliquer**.  
  
## <a name="to-configure-report-history-for-a-specific-report"></a>Pour configurer un historique de rapport destiné à un rapport spécifique  
  
1.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'au rapport pour lequel configurer l'historique, puis cliquez sur cet élément pour l'ouvrir.  
  
2.  Cliquez sur l’onglet **Propriétés**.  
  
3.  Cliquez sur l’onglet **Historique** .  
  
4.  Sélectionnez les options pour votre rapport, puis cliquez sur **Appliquer**. Pour plus d’informations sur chaque option, consultez [Page de propriétés Options d’instantanés &#40;Gestionnaire de rapports&#41;](https://msdn.microsoft.com/library/f6641f59-5267-4f57-8957-63b93d1a9679).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’un instantané à un historique de rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)  

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="to-configure-report-history-for-a-report-server"></a>Pour configurer un historique de rapport destiné à un serveur de rapports  
  
1.  Dans le portail web, cliquez sur **Paramètres du site** dans la barre d’outils générale.  
  
2.  Sélectionnez l’option **Conserver un nombre illimité d’instantanés dans l’historique de rapport** pour conserver tous les historiques de rapport sur une durée indéterminée. Sinon, choisissez **Limiter les copies de l’historique de rapport** pour spécifier le nombre maximal d’instantanés à conserver pour un rapport donné.  
  
3.  Cliquez sur **Appliquer**.  
  
## <a name="to-configure-report-history-for-a-specific-report"></a>Pour configurer un historique de rapport destiné à un rapport spécifique  
  
1.  Dans le portail web, parcourez l’arborescence jusqu’au rapport pour lequel configurer l’historique, puis cliquez sur cet élément pour l’ouvrir.  
  
2.  Cliquez sur l’onglet **Propriétés**.  
  
3.  Cliquez sur l’onglet **Historique** .  
  
4.  Sélectionnez les options pour votre rapport, puis cliquez sur **Appliquer**. Pour plus d’informations sur chaque option, consultez [Page de propriétés Options d’instantanés](https://msdn.microsoft.com/library/f6641f59-5267-4f57-8957-63b93d1a9679).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter un instantané à un historique de rapports](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   

::: moniker-end
  
