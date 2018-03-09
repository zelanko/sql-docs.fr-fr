---
title: "Configuration du fuseau horaire de matériel (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cea9eeb9-fe05-4e65-b229-539de02ab20a
caps.latest.revision: "18"
ms.openlocfilehash: 0dc20594fa45375fe07b4ec374da9c752d3cc8b0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="appliance-time-zone-configuration"></a>Configuration du fuseau horaire matériel
Le **fuseau horaire** page vous permet de définir le fuseau horaire pour tous les nœuds sur votre appliance SQL Server PDW.  
  
## <a name="to-set-the-time-zone"></a>Pour définir le fuseau horaire  
  
1.  Lancez le Gestionnaire de Configuration. Pour plus d’informations, consultez [lance le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41; ](launch-the-configuration-manager.md).  
  
2.  Arrêter les services d’application à l’aide de la **l’état des Services** page dans le Gestionnaire de Configuration. Consultez [PDW Services état &#40; Système de plateforme Analytique &#41; ](pdw-services-status.md) pour obtenir des instructions.  
  
3.  Dans le volet gauche du Gestionnaire de Configuration, cliquez sur **fuseau horaire**. Sélectionnez le fuseau horaire de votre choix à partir de la **fuseau horaire** menu déroulant. En fonction de votre emplacement, vous pouvez également choisir d’activer la case à côté **ajuster l’horloge pour l’heure d’été**.  
  
4.  Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
5.  Redémarrez les services d’application à l’aide de la **l’état des Services** page dans le Gestionnaire de Configuration. Si vous souhaitez également modifier les privilèges, vous pouvez le faire avant de redémarrer l’application.  
  
![Temps des appliances DWConfig](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le Gestionnaire de Configuration &#40; Système de plateforme Analytique &#41;](launch-the-configuration-manager.md)  
  
