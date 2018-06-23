---
title: Configurer les propriétés d’un collecteur de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.dc.datacollectionprop.advanced.f1
- sql12.swb.dc.datacollectionprop.general.f1
ms.assetid: cf98f57d-5a6d-4bc3-bf10-783e460fc63d
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a65a92528715220e2ef4762e16a1dceb941c6bad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153952"
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
 [Gérer la collecte de données](data-collection.md)   
 [Configurer l’entrepôt de données de gestion &#40;SQL Server Management Studio&#41;](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  