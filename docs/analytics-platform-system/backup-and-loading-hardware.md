---
title: Sauvegarde et chargement de matériel - Parallel Data Warehouse
description: Pour déployer votre solution Analytique Platform System (APS) d’entreposage avec Parallel Data Warehouse (PDW) de données de bout en bout, vous devez créer un plan de sauvegarde de l’entrepôt de données et le chargement des données. Utilisez ce guide pour obtenir et configurer des serveurs de sauvegarde et de charger répondant aux besoins de votre entreprise.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4d7f7b6b4edea9dacab7287a7936b7fd87fd7973
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63065124"
---
# <a name="backup-and-loading-hardware-overview---parallel-data-warehouse"></a>Sauvegarde et chargement de vue d’ensemble de matériel - Parallel Data Warehouse
Pour déployer votre solution Analytique Platform System (APS) d’entreposage avec Parallel Data Warehouse (PDW) de données de bout en bout, vous devez créer un plan de sauvegarde de l’entrepôt de données et le chargement des données. Utilisez ce guide pour obtenir et configurer des serveurs de sauvegarde et de charger répondant aux besoins de votre entreprise.  
  
## <a name="acquire-and-configure-backup-servers"></a>Obtenir et configurer des serveurs de sauvegarde  
![Processus de sauvegarde](media/backup-process.png "processus de sauvegarde")  
  
Pour sauvegarder une base de données PDW, vous avez besoin d’un ou plusieurs serveurs de sauvegarde. Vous pouvez utiliser votre propre matériel existant ou acheter du nouveau matériel. Pour plus d’informations, consultez [obtenir et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md). Ces instructions incluent un [feuille de planification de capacité de serveur de sauvegarde](backup-capacity-planning-worksheet.md) pour vous aider à planifier la solution adaptée pour la sauvegarde.  
  
## <a name="acquire-and-configure-loading-servers"></a>Obtenir et configurer des serveurs de chargement  
![Processus de chargement](media/loading-process.png "processus de chargement")  
  
Pour charger des données, vous avez besoin d’un ou plusieurs serveurs de chargement. Vous pouvez utiliser votre propre ETL existant ou autres serveurs, ou vous pouvez acheter de nouveaux serveurs. Pour plus d’informations, consultez [Acquire et configurer un serveur de chargement](acquire-and-configure-loading-server.md). Ces instructions incluent un [le chargement de feuille de planification de capacité serveur](loading-server-capacity-planning-worksheet.md) pour vous aider à planifier la solution adaptée pour le chargement.  
  
## <a name="see-also"></a>Voir aussi  
[Vue d’ensemble de sauvegarde et de restauration](backup-and-restore-overview.md)  
[Vue d’ensemble de la charge](load-overview.md)  
  
