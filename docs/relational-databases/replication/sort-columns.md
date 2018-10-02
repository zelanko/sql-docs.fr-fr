---
title: Trier des colonnes | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.sortcolumns.f1
ms.assetid: 66b44b6c-10a5-4e3f-a97b-7568609c88ac
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ce595fc0032ef8c1f498993f0953aa90117d73ce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737377"
---
# <a name="sort-columns"></a>Trier les colonnes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La boîte de dialogue **Trier les colonnes** vous permet de trier des grilles dans le Moniteur de réplication selon une ou plusieurs colonnes (vous pouvez également effectuer un tri sur une colonne unique en cliquant sur l'en-tête de colonne dans la grille du Moniteur de réplication). Par exemple, pour trier des abonnements sous l'onglet **Tous les abonnements** selon l'état, puis selon le type de connexion, procédez comme suit :  
  
1.  Dans la première ligne de la grille, sélectionnez **État** dans la colonne **Nom de la colonne** et une valeur dans la colonne **Ordre de tri** .  
  
2.  Dans la deuxième ligne de la grille, sélectionnez **Type de connexion** dans la colonne **Nom de la colonne** et une valeur dans la colonne **Ordre de tri** .  
  
## <a name="options"></a>Options  
 **Nom de la colonne**  
 Nom de la colonne sur laquelle vous souhaitez effectuer le tri. Vous pouvez effectuer le tri sur une ou plusieurs colonnes. Vous ne pouvez pas trier sur les colonnes **Performance moyenne actuelle** ou **Pire performance actuelle** sous l'onglet **Publications** en raison de la façon dont ces valeurs de colonne sont calculées.  
  
 **Ordre de tri**  
 Spécifiez **Croissant** ou **Décroissant**.  
  
 **Effacer tout**  
 Supprime toutes les lignes de la grille de tri. Pour supprimer une ligne unique, sélectionnez la ligne et appuyez sur la touche Suppr.  
  
## <a name="see-also"></a> Voir aussi  
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
