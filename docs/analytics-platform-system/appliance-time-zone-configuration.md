---
title: Configurer le fuseau horaire
description: La page fuseau horaire vous permet de définir le fuseau horaire de tous les nœuds de votre appliance Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1da16790d011a628bc2536de051eb1181f06b8cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401397"
---
# <a name="appliance-time-zone-configuration---analytics-platform-system"></a>Configuration du fuseau horaire de l’appliance-système de plateforme d’analyse
La page **fuseau** horaire vous permet de définir le fuseau horaire de tous les nœuds de votre appliance Analytics Platform System (APS).  
  
## <a name="to-set-the-time-zone"></a>Pour définir le fuseau horaire  
  
1.  Lancez le Configuration Manager. Pour plus d’informations, consultez [la page lancement du&#41;Configuration Manager &#40;Analytics Platform System ](launch-the-configuration-manager.md).  
  
2.  Arrêtez les services de l’appliance à l’aide de la page **État des services** de la Configuration Manager. Pour obtenir des instructions, consultez l' [État des services PDW &#40;Analytics Platform System&#41;](pdw-services-status.md) .  
  
3.  Dans le volet gauche de la Configuration Manager, cliquez sur **fuseau horaire**. Sélectionnez le fuseau horaire souhaité dans le menu déroulant **fuseau horaire** . En fonction de votre emplacement, vous pouvez également choisir d’activer la case à cocher en regard de l’option **Ajuster automatiquement l’horloge pour l’heure d’été**.  
  
4.  Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
5.  Redémarrez les services de l’appliance à l’aide de la page **État des services** de la Configuration Manager. Si vous envisagez également de modifier les privilèges, vous pouvez le faire avant de redémarrer l’appliance.  
  
![Temps des appliances DWConfig](./media/appliance-time-zone-configuration/SQL_Server_PDW_DWConfig_ApplTopTime.png "SQL_Server_PDW_DWConfig_ApplTopTime")  
  
## <a name="see-also"></a>Voir aussi  
[Lancez le système de plateforme Configuration Manager &#40;Analytics&#41;](launch-the-configuration-manager.md)  
  
