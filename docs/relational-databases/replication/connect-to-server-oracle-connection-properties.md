---
description: Se connecter au serveur (Oracle), Propriétés de connexion
title: Se connecter au serveur (Oracle), Propriétés de connexion | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d6a5c942305252f8e694042633651baf981032c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455614"
---
# <a name="connect-to-server-oracle-connection-properties"></a>Se connecter au serveur (Oracle), Propriétés de connexion
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  L'onglet **Propriétés de connexion** de la boîte de dialogue **Se connecter au serveur** permet de spécifier une option de publication **Passerelle** ou **Complet**. Une fois qu'un serveur de publication est identifié, vous ne pouvez pas modifier cette option sans supprimer et reconfigurer ce serveur. Pour plus d’informations, consultez [Configurer un serveur de publication Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Options  
 **Type d’éditeur**  
 Sélectionnez **Passerelle** ou **Complet**. L'option **Complet** a pour but de fournir un instantané et des publications transactionnelles avec le jeu complet de fonctionnalités prises en charge pour le serveur de publication Oracle. L'option **Passerelle** permet l'optimisation de la conception en améliorant les performances pour les cas où la réplication sert de passerelle entre les systèmes. Vous ne pouvez pas utiliser l'option **Passerelle** si vous envisagez de publier la même table dans plusieurs publications transactionnelles. Une table peut apparaître au maximum dans une publication transactionnelle et dans une ou plusieurs publications d'instantané si vous sélectionnez **Passerelle**.  
  
 **Délais d'attente**  
 Indiquez la durée pendant laquelle le serveur de distribution [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit essayer de se connecter au serveur de publication Oracle avant qu’une erreur d’expiration de délai ne se produise.  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des termes de la publication Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Réglage des performances pour les serveurs de publication Oracle](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
