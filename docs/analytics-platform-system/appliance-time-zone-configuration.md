---
title: Configurer le fuseau horaire - Analytique Platform System | Microsoft Docs
description: La page de fuseau horaire vous permet de définir le fuseau horaire pour tous les nœuds sur votre appliance Analytique Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f9997ed26cea5c63d69a7be84b25c247add9b692
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961443"
---
# <a name="appliance-time-zone-configuration---analytics-platform-system"></a>Configuration du fuseau horaire matériel - Analytique Platform System
Le **fuseau horaire** page vous permet de définir le fuseau horaire pour tous les nœuds sur votre appliance Analytique Platform System (APS).  
  
## <a name="to-set-the-time-zone"></a>Pour définir le fuseau horaire  
  
1.  Lancez le Gestionnaire de Configuration. Pour plus d’informations, consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Arrêter les services de l’appliance à l’aide de la **l’état des Services** page dans le Gestionnaire de Configuration. Consultez [l’état des Services PDW &#40;Analytique Platform System&#41; ](pdw-services-status.md) pour obtenir des instructions.  
  
3.  Dans le volet gauche du Gestionnaire de Configuration, cliquez sur **fuseau horaire**. Sélectionnez le fuseau horaire souhaité à partir de la **fuseau horaire** menu déroulant. Selon votre emplacement, vous pouvez également choisir d’activer la case à côté **ajuster l’horloge pour l’heure d’été**.  
  
4.  Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
5.  Redémarrez les services de l’appliance à l’aide de la **l’état des Services** page dans le Gestionnaire de Configuration. Si vous comptez également modifier les privilèges, vous pouvez le faire avant le redémarrage de l’appliance.  
  
![Temps des appliances DWConfig](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md)  
  
