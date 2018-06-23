---
title: Vue d’ensemble de la sécurité (réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
caps.latest.revision: 44
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a3ca129d5dd03d788f639a51322ceb999a25e76a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041082"
---
# <a name="security-overview-replication"></a>Vue d'ensemble de la sécurité (réplication)
  Pour l'essentiel, sécuriser l'environnement de réplication revient à comprendre les différentes options d'authentification et d'autorisation, à utiliser de façon appropriée les fonctionnalités de filtrage de la réplication et à se familiariser avec les diverses mesures de sécurisation possibles des différentes parties d'un environnement de réplication. L'environnement de réplication inclut le serveur de distribution, le serveur de publication, les abonnés et le dossier d'instantanés. Ce chapitre traite de la sécurité de réplication, mais la sécurité de réplication repose sur la sécurité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et la sécurité Windows. Par conséquent, vous devez comprendre les fondements et les caractéristiques de la sécurité de réplication. Pour plus d’informations sur la sécurité, consultez [Considérations de sécurité pour une installation SQL Server](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md). Pour plus d'informations sur les questions de sécurité à prendre en compte pour la publication dans Oracle, consultez la section « Modèle de sécurité de réplication » dans la rubrique [Design Considerations and Limitations for Oracle Publishers](../non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Limitation des menaces et des risques de vulnérabilité &#40;réplication&#41;](threat-and-vulnerability-mitigation-replication.md)  
 Discute des menaces potentielles auxquelles est exposée la topologie de réplication et décrit des solutions réduire ces menaces.  
  
 [Identité et contrôle d’accès &#40;réplication&#41;](identity-and-access-control-replication.md)  
 Décrit comment utiliser l'authentification, l'autorisation et le filtrage pour aider à sécuriser une topologie de réplication.  
  
 [Développement sécurisé &#40;réplication&#41;](secure-development-replication.md)  
 Décrit le comportement de la sécurité de réplication, les méthodes recommandées e les autorisations minimales pour la réplication.  
  
 [Déploiement sécurisé &#40;réplication&#41;](secure-deployment-replication.md)  
 Décrit comment sécuriser au mieux tous les composants d'une topologie de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et protection &#40;réplication&#41;](security-and-protection-replication.md)  
  
  