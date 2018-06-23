---
title: Propriétés de la base de données (page Suivi des modifications) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6643218cd4671c86c8e44b751c5163171fc2b236
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143492"
---
# <a name="database-properties-changetracking-page"></a>Propriétés de la base de données (page Suivi des modifications)
  Utilisez cette page pour consulter ou modifier les paramètres de suivi des modifications pour la base de données sélectionnée. Pour plus d’informations sur les options disponibles sur cette page, consultez [Activer et désactiver le suivi des modifications &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).  
  
## <a name="options"></a>Options  
 **Suivi des modifications**  
 Utilisez cette option pour activer ou désactiver le suivi des modifications pour la base de données.  
  
 Pour activer le suivi des modifications, vous devez posséder l'autorisation de modifier la base de données.  
  
 L’affectation de la valeur **True** définit une option de base de données qui permet d’activer le suivi des modifications sur des tables individuelles.  
  
 Vous pouvez également configurer le suivi des modifications en utilisant [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).  
  
 **Période de rétention**  
 Spécifie la période minimale de conservation des informations de suivi des modifications dans la base de données. Les données sont supprimées uniquement si la valeur **Nettoyage automatique**a la valeur **True**.  
  
 La valeur par défaut est 2.  
  
 **Unités de la période de rétention**  
 Spécifie les unités de la valeur Période de rétention. Vous avez le choix entre les unités suivantes : **Jours**, **Heures**ou **Minutes**. La valeur par défaut est **Jours**.  
  
 La période de rétention minimale est 1 minute. Il n'existe pas de période de rétention maximale.  
  
 **Nettoyage automatique**  
 Indique si les informations de suivi des modifications sont supprimées automatiquement à l'issue de la période de rétention spécifiée.  
  
 L’activation de l’option **Nettoyage automatique** remplace toute période de rétention personnalisée précédente par la période de rétention par défaut de 2 jours.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
