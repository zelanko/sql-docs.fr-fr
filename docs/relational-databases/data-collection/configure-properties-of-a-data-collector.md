---
title: "Configurer les propriétés d’un collecteur de données | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.dc.datacollectionprop.general.f1
- sql13.swb.dc.datacollectionprop.advanced.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2a0aad98c302e55b3edc76b01fc0c5eae4e249ac
ms.lasthandoff: 04/11/2017

---
# <a name="configure-properties-of-a-data-collector"></a>Configurer les propriétés d'un collecteur de données
  Cette rubrique explique comment configurer les propriétés d'un collecteur de données.  
  
## <a name="data-collection-properties-general-tab"></a>Propriétés de la collecte de données (onglet Général)  
 Utilisez cette page pour configurer les paramètres relatifs à l'entrepôt de données de gestion et spécifier l'emplacement où les données collectées doivent être stockées avant d'être téléchargées dans l'entrepôt de données.  
  
 **Activer la collecte de données**  
 Sélectionnez cette option pour activer la collecte de données. Cela équivaut à exécuter la procédure stockée sp_syscollector_enable_collector. La désactivation de cette case à cocher désactive la collecte de données et équivaut à exécuter la procédure stockée p_syscollector_disable_collector.  
  
 **Server**  
 Affiche le nom du serveur qui hébergera l'entrepôt de données de gestion  
  
 **Nom de la base de données**  
 Affiche le nom de la base de données relationnelle utilisée pour l'entrepôt de données de gestion.  
  
 **Tester la connexion**  
 Testez la connexion au **Serveur** spécifié à l’aide des informations fournies quand la collecte de données est configurée.  
  
 **Répertoire du cache**  
 Spécifie le répertoire où les données collectées sont stockées sur le système collectant les données avant d'être téléchargées dans l'entrepôt de données de gestion. Si le **Répertoire du cache** n'est pas spécifié, le collecteur de données tente de localiser les variables d'environnement %TEMP% et %TMP% et utilise l'un de ces emplacements comme emplacement par défaut pour le stockage temporaire. Si ces variables d'environnement ne sont pas configurées, une erreur se produit et vous êtes invité à créer un répertoire de cache.  
  
## <a name="data-collection-properties-advanced-tab"></a>Propriétés de la collecte de données (onglet Avancé)  
 Utilisez cette page pour configurer les paramètres du délai entre reprises pour la connexion à l'entrepôt de données de gestion.  
  
 **Nombre de tentatives en cas d'échec du téléchargement**  
 Spécifie le nombre de tentatives de téléchargement dans l'entrepôt de données de gestion en cas d'échec du téléchargement. La valeur par défaut est 1.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la collecte de données](../../relational-databases/data-collection/manage-data-collection.md)   
 [Configurer l’entrepôt de données de gestion &#40;SQL Server Management Studio&#41;](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
