---
title: Planification d’une installation de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing SQL Server, planning
ms.assetid: b1d56f2f-603f-48f2-b902-c715f14a6db9
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 30acad1bce8a94a1cb3eedd5867977ebddc6d015
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045501"
---
# <a name="planning-a-sql-server-installation"></a>Planification d’une installation de SQL Server
  Pour installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], suivez ces étapes :  
  
-   Prenez connaissance des conditions requises pour l'installation, des options d'installation, des contrôles de configuration du système et des considérations sur la sécurité pour une installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer une installation ou une mise à niveau vers une version ultérieure.  
  
-   Configurez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide des utilitaires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Indépendamment de la méthode d'installation, vous êtes invité à confirmer l'acceptation des termes de la licence de logiciel en tant que personne physique ou pour le compte d'une entité, sauf si votre utilisation du logiciel est régie par un accord distinct, tel qu'un accord de concession de licence en volume de [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou un accord tiers avec un éditeur de logiciels ou un fabricant OEM.  
  
 Les termes du contrat de licence sont affichés afin que vous puissiez les consulter et les accepter dans l'interface utilisateur du programme d'installation. Les installations sans assistance (à l'aide du paramètre /Q ou /QS) doivent inclure le paramètre /IAcceptSQLServerLicenseTerms. Vous pouvez passer en revue les termes du contrat de licence séparément à la page [Termes du contrat de licence logiciel Microsoft](http://go.microsoft.com/fwlink/?LinkID=148209).  
  
> [!NOTE]  
>  Selon la façon dont vous avez reçu le logiciel (par exemple, via le programme de licence en volume [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), votre utilisation du logiciel peut être soumise à des termes et conditions supplémentaires.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Nouveautés liées à l'installation de SQL Server](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md)  
 Cette rubrique décrit les détails des fonctionnalités nouvelles ou améliorées de l'installation de cette version de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
 Cette rubrique répertorie les configurations matérielle et logicielle minimales requises pour installer et exécuter une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Considérations sur la sécurité pour une installation SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
 Cette rubrique traite des recommandations qu'il est conseillé de prendre en considération en matière de sécurité avant d'installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et après l'avoir installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
 Cette rubrique décrit la configuration par défaut des services inclus dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi que les options de configuration des services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] susceptibles d'être définies durant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et par la suite.  
  
 [Protocoles réseau et bibliothèques réseau](../../../2014/sql-server/install/network-protocols-and-network-libraries.md)  
 Cette rubrique décrit la configuration par défaut des protocoles réseau dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et les options de configuration disponibles.  
  
 [Utiliser plusieurs versions et instances de SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)  
 Cette rubrique décrit les considérations pour l'installation de plusieurs versions et instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Versions linguistiques locales dans SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
 Cette rubrique décrit les versions localisées de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="related-sections"></a>Sections connexes  
 [Installer SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)  
 Cette section fournit une vue d'ensemble des différentes options d'installation disponibles pour installer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Installer les fonctionnalités BI de SQL Server 2014](install-sql-server-business-intelligence-features.md)  
 Cette section de la documentation d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] explique comment installer les fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui font partie de la plateforme Microsoft BI.  
  
 [Mise à niveau vers SQL Server 2014](../../database-engine/install-windows/upgrade-sql-server.md)  
 La section fournit une vue d'ensemble des instances de mise à niveau des versions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] précédentes vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 [Désinstaller SQL Server 2014](uninstall-sql-server.md)  
 Reportez-vous à cette section pour désinstaller complètement une instance existante de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et préparer le système afin de pouvoir réinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Installation d'un cluster de basculement SQL Server](../failover-clusters/install/sql-server-failover-cluster-installation.md)  
 Cette section de la documentation d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] décrit comment installer et configurer un cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de SQL Server 2014 de démarrage rapide](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)   
 [Installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Solutions haute disponibilité &#40;SQL Server&#41;](../failover-clusters/high-availability-solutions-sql-server.md)   
 [Avant l'installation du clustering de basculement](../failover-clusters/install/before-installing-failover-clustering.md)   
 [Mise à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation &#40;le programme d’installation&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  