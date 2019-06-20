---
title: Réservations d’URL pour les instances multiples signalent les déploiements de serveur (Gestionnaire de Configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL reservations
ms.assetid: f67c83c0-1f74-42bb-bfc1-e50c38152d3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f49a13fa50254e4c485a228d506b49e14d190959
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108618"
---
# <a name="url-reservations-for-multi-instance-report-server-deployments--ssrs-configuration-manager"></a>Réservations d’URL pour les déploiements de serveur de rapports multi-instance (Gestionnaire de configuration de SSRS)
  Si vous installez plusieurs instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur le même ordinateur, vous devez considérer comment vous définirez les réservations d'URL pour chaque instance. Dans chaque instance, le service Web Report Server et le Gestionnaire de rapports doivent avoir au moins une réservation d'URL chacun. L'ensemble entier de réservations doit être unique dans HTTP.SYS.  
  
 Les URL en double sont détectées pendant l'inscription d'URL, qui se produit lorsque le service démarre. Si vous créez des réservations d'URL qui ne sont pas uniques, le conflit de nom peut ne pas être détecté avant le démarrage du service. Pour cette raison, assurez-vous de suivre les conventions ou les règles d'affectation de noms afin de vous assurer que toutes les valeurs sont uniques.  
  
## <a name="default-naming-conventions"></a>Conventions d'affectation de noms par défaut  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peut être installé dans une instance nommée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Lorsque vous installez ou configurez un serveur de rapports dans une instance nommée, le nom de l'instance est inclus automatiquement dans le répertoire virtuel dans la réservation d'URL par défaut que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit. Le tableau suivant indique les réservations d'URL pour une instance par défaut et une instance nommée.  
  
|Instance SQL Server|Réservation d'URL par défaut|  
|-------------------------|-----------------------------|  
|Par défaut (MSSQLSERVER)|http://+:80/reportserver|  
|Nommée (MynamedInstance)|http://+:80/reportserver_MyNamedInstance|  
  
 Pour l'instance nommée, le répertoire virtuel inclut le nom de l'instance. L'instance par défaut et l'instance nommée écoutent sur le même port, mais les noms de répertoires virtuels uniques déterminent quel serveur de rapports obtient la demande.  
  
 Il est recommandé d'utiliser le nom de répertoire virtuel afin de distinguer parmi l'instance de serveur de rapports. Il fournit une correspondance claire entre une URL et l'instance cible et garantit que les noms d'applications sont uniques dans tout le système.  
  
## <a name="custom-naming-conventions"></a>Conventions d'affectation de noms personnalisées  
 Bien que l'utilisation du nom de l'instance soit recommandée, vous pouvez utiliser la syntaxe d'URL et vos propres conventions d'affectation de noms afin de satisfaire les contraintes de nom uniques pour les réservations d'URL. Les exemples suivants illustrent différentes approches permettant de créer des URL uniques pour chaque instance.  
  
|Instance par défaut du serveur de rapports (MSSQLSERVER)|ReportServer_MyNamedInstance|Unicité|  
|----------------------------------------------------|-----------------------------------|----------------|  
|http://+:80/reportserver|http://+:8888/reportserver|Chaque instance écoute sur un port différent.|  
|http://www.contoso.com/reportserver|http://SRVR-46/reportserver|Chaque instance répond à différents noms de serveurs (nom de domaine complet et nom d'ordinateur).|  
  
## <a name="uniqueness-requirements"></a>Spécifications relatives à l'unicité  
 Les technologies sous-jacentes utilisées par [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] imposent des spécifications relatives aux noms uniques. HTTP.SYS requiert que toutes les URL dans sa base de données de référentiel soient uniques. Vous pouvez varier le port, le nom d'hôte ou le nom de répertoire virtuel pour créer une URL unique. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] requiert que les identités d’application soient uniques dans le même processus. Cette spécification affecte les noms de répertoires virtuels. Elle spécifie que vous ne pouvez pas dupliquer de nom de répertoire virtuel dans la même instance de serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](configure-a-url-ssrs-configuration-manager.md)  
  
  
