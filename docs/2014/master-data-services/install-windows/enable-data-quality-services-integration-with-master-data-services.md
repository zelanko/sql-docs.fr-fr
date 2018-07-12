---
title: Activer l’intégration de Data Quality Services à Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 276b17d6e62f9ba45a02d1e3e325a457ff6ee77c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164821"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a>Activer l'intégration de Data Quality Services avec Master Data Services
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], la fonctionnalité de mise en correspondance est assurée par Data Quality Services (DQS). Cette fonctionnalité doit être activée pour pouvoir être utilisée.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Une application Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et une base de données doivent exister.  
  
-   La fonctionnalité Data Quality Services et le Data Quality Client doivent être installés sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données MDS. Pour plus d’informations, consultez [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
### <a name="to-enable-data-quality-services-integration"></a>Pour activer l'intégration de Data Quality Services  
  
1.  Ouvrez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Dans le volet gauche, cliquez sur **Configuration Web**.  
  
3.  Dans la page **Configuration web** , sélectionnez le site web et l’application web.  
  
4.  Dans la section **Activer l’intégration DQS** , cliquez sur **Activer l’intégration avec Data Quality Services**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Qualité des données correspondantes dans le complément MDS pour Excel](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Complément Master Data Services pour Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)   
 [Installer Master Data Services](install-master-data-services.md)  
  
  
