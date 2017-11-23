---
title: "Sauvegarde et le chargement de la vue d’ensemble du matériel pour APS PDW"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Pour déployer votre solution sur le système de plateforme Analytique (APS) d’entreposage avec SQL Server Parallel Data Warehouse (PDW) de données de bout en bout, vous devez créer un plan de sauvegarde de l’entrepôt de données et de chargement des données."
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 3a2ae046-f8d8-4a5c-b3c1-6ecee005df6c
caps.latest.revision: "9"
ms.openlocfilehash: 0bdf529aacf1644f55cd44da3d0a7590e509a323
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="backup-and-loading-hardware-overview"></a>Sauvegarde et chargement de vue d’ensemble du matériel
Pour déployer votre solution sur le système de plateforme Analytique (APS) d’entreposage avec SQL Server Parallel Data Warehouse (PDW) de données de bout en bout, vous devez créer un plan de sauvegarde de l’entrepôt de données et de chargement des données. Utilisez ce guide pour obtenir et configurer les serveurs de sauvegarde et de chargement qui répond aux besoins de votre entreprise.  
  
## <a name="acquire-and-configure-backup-servers"></a>Obtenir et configurer les serveurs de sauvegarde  
![Processus de sauvegarde](media/backup-process.png "processus de sauvegarde")  
  
Pour sauvegarder une base de données PDW, vous avez besoin d’un ou plusieurs serveurs de sauvegarde. Vous pouvez utiliser votre propre matériel existant ou acheter du nouveau matériel. Pour plus d’informations, consultez [acquérir et de configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md). Ces instructions incluent un [feuille de planification de capacité de serveur de sauvegarde](backup-capacity-planning-worksheet.md) pour vous aider à planifier la solution appropriée pour la sauvegarde.  
  
## <a name="acquire-and-configure-loading-servers"></a>Acquérir et de configurer des serveurs de chargement  
![Processus de chargement](media/loading-process.png "processus de chargement")  
  
Pour charger des données, vous avez besoin d’un ou plusieurs serveurs de chargement. Vous pouvez utiliser votre propre ETL existant ou autres serveurs, ou vous pouvez acheter de nouveaux serveurs. Pour plus d’informations, consultez [Acquire et configurer un serveur de chargement](acquire-and-configure-loading-server.md). Ces instructions incluent un [le chargement de feuille de calcul de planification de capacité serveur](loading-server-capacity-planning-worksheet.md) pour vous aider à planifier la solution appropriée pour le chargement.  
  
## <a name="see-also"></a>Voir aussi  
[Vue d’ensemble de sauvegarde et de restauration](backup-and-restore-overview.md)  
[Vue d’ensemble de la charge](load-overview.md)  
  
