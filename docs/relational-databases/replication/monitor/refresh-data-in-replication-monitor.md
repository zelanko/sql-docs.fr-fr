---
title: Actualiser des données dans le moniteur de réplication | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- refreshing data
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: be4dde11a67c0391f753c29b411baf9ccb25d804
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770522"
---
# <a name="refresh-data-in-replication-monitor"></a>Actualiser des données dans le Moniteur de réplication
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Dans le moniteur de réplication, la fenêtre principale et les fenêtres de détails (ces fenêtres lancées à partir de la fenêtre principale) peuvent être actualisées automatiquement ou manuellement. Pour actualiser une fenêtre manuellement, appuyez sur la touche F5. Par défaut, la fenêtre principale est actualisée automatiquement toutes les cinq secondes ; la fréquence peut être personnalisée pour chaque serveur de publication.  
  
 Les données affichées dans le moniteur de réplication sont recherchées dans une mémoire cache. Pour plus d’informations sur les relations entre la mémoire cache et l’actualisation du moniteur de réplication, consultez [Mise en cache, actualisation et performances du moniteur de réplication](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md). Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-set-refresh-options-for-replication-monitor"></a>Pour définir les options d'actualisation pour le moniteur de réplication
  
1.  Cliquez avec le bouton droit dans le volet gauche du moniteur de réplication, puis cliquez sur **Paramètres du serveur de publication**.  
  
2.  Dans la boîte de dialogue **Paramètres du serveur de publication** , définissez les options **Actualisation automatique** et **Fréquence d'actualisation** . Le paramètre **Actualisation automatique** affecte la fenêtre principale du moniteur de réplication. Le paramètre **Fréquence d'actualisation** affecte également toutes les fenêtres de détails qui sont paramétrées pour s'actualiser automatiquement (les modifications du paramètre affectent seulement les fenêtres de détails ouvertes après la modification).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

### <a name="to-specify-that-a-detail-window-should-automatically-refresh"></a>Pour spécifier qu'une fenêtre de détails doit s'actualiser automatiquement  
  
1.  Ouvrez une fenêtre de détails dans le moniteur de réplication. Par exemple :  
  
    1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
    2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
    3.  Cliquez avec le bouton droit sur un abonnement, puis cliquez sur **Afficher les détails**.  
  
2.  Dans la fenêtre de détails **Abonnement \<Nom_Abonnement>** , cliquez sur **Action**, puis sur **Actualisation automatique**. La fréquence d'actualisation est déterminée par le paramètre **Fréquence d'actualisation** dans la boîte de dialogue **Paramètres du serveur de publication** .  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
