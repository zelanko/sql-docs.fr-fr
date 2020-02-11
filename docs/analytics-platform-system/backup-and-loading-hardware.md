---
title: Sauvegarde & le chargement du matériel
description: Pour déployer votre solution d’entreposage de données de bout en bout sur Analytics Platform System (APS) avec des Data Warehouse parallèles, vous devez créer un plan pour la sauvegarde de l’entrepôt de données et le chargement des données. Utilisez ces conseils pour acquérir et configurer des serveurs de sauvegarde et de chargement qui répondent aux besoins de votre entreprise.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4dd4fba91b1507f711a66a88f40b2fa2ea35e1ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401359"
---
# <a name="backup-and-loading-hardware-overview---parallel-data-warehouse"></a>Vue d’ensemble du matériel de sauvegarde et de chargement-Data Warehouse parallèle
Pour déployer votre solution d’entreposage de données de bout en bout sur Analytics Platform System (APS) avec des Data Warehouse parallèles, vous devez créer un plan pour la sauvegarde de l’entrepôt de données et le chargement des données. Utilisez ces conseils pour acquérir et configurer des serveurs de sauvegarde et de chargement qui répondent aux besoins de votre entreprise.  
  
## <a name="acquire-and-configure-backup-servers"></a>Acquérir et configurer des serveurs de sauvegarde  
![Processus de sauvegarde](media/backup-process.png "Processus de sauvegarde")  
  
Pour sauvegarder une base de données PDW, vous avez besoin d’un ou de plusieurs serveurs de sauvegarde. Vous pouvez utiliser votre propre matériel existant ou acheter un nouveau matériel. Pour plus d’informations, consultez [acquérir et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md). Ces instructions incluent une [feuille de planification](backup-capacity-planning-worksheet.md) de la capacité du serveur de sauvegarde pour vous aider à planifier la bonne solution pour la sauvegarde.  
  
## <a name="acquire-and-configure-loading-servers"></a>Acquérir et configurer le chargement des serveurs  
![Chargement du processus](media/loading-process.png "Chargement du processus")  
  
Pour charger des données, vous avez besoin d’un ou de plusieurs serveurs de chargement. Vous pouvez utiliser vos propres serveurs ETL existants ou d’autres serveurs, ou vous pouvez acheter de nouveaux serveurs. Pour plus d’informations, consultez [acquérir et configurer un serveur de chargement](acquire-and-configure-loading-server.md). Ces instructions incluent une [feuille de calcul de planification de la capacité du serveur de chargement](loading-server-capacity-planning-worksheet.md) pour vous aider à planifier la bonne solution pour le chargement.  
  
## <a name="see-also"></a>Voir aussi  
[Vue d’ensemble de la sauvegarde et de la restauration](backup-and-restore-overview.md)  
[Vue d’ensemble du chargement](load-overview.md)  
  
