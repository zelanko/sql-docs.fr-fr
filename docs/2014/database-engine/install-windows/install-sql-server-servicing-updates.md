---
title: Installer les mises à jour de maintenance de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07f438f86a22b866351a0b83ee7634338f3ad2cd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62775342"
---
# <a name="install-sql-server-2014-servicing-updates"></a>Installer des mises à jour de maintenance de SQL Server 2014
  Cette rubrique fournit des informations sur l'installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Cette section aborde les sujets suivants :  
  
-   Installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pendant une nouvelle installation  
  
-   Installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] après qu'il a déjà été installé.  
  
 Il est recommandé que les clients évaluent et installent les dernières mises à jour de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en temps voulu pour s'assurer que les systèmes sont à jour avec des mises à jour de sécurité les plus récentes.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-during-a-new-installation"></a>Installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pendant une nouvelle installation  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intègre les dernières mises à jour du produit avec l'installation principale, de sorte que le produit principal et les mises à jour applicables sont installés en même temps. La mise à jour du produit peut rechercher les mises à jour applicables à partir de :  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Windows Server Update Services (WSUS)  
  
-   Un dossier local  
  
-   Un partage de réseau  
  
 Une fois que le programme d'installation a détecté les versions les plus récentes des mises à jour applicables, il les télécharge et les intègre dans le processus d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours. La fonctionnalité de mise à jour du produit peut inclure une mise à jour, un Service Pack, ou un Service Pack et la mise à jour cumulative. La fonctionnalité de mise à jour du produit est une extension de la [fonctionnalité Slipstream](https://go.microsoft.com/fwlink/?LinkId=219945) qui était disponible dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>Installation des mises à jour de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] après qu'il a déjà été installé  
 Sur une instance installée de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nous vous recommandons d’appliquer toutes les mises à jour disponibles : Versions générales de Distribution (GDR - mises à jour critiques ou de sécurité), Service Packs (SP), ainsi que la dernière version disponible Cumulative mise à jour (CU).  
  
 Selon le type de version de maintenance, les mises à jour de SQL Server sont disponibles via Microsoft Update (MU), du Microsoft Download Center et/ou le correctif logiciel de Support technique serveur. Mises à jour de sécurité et critique pour SQL Server sont automatiquement fournies par Microsoft Update (pour être en mesure de voir ces mises à jour que vous avez besoin pour participer à Microsoft Update via Windows Update dans le panneau de configuration). Service Packs sont disponibles sur Microsoft Update sous forme de téléchargements de facultatif/Important, ainsi que le centre de téléchargement. Mises à jour cumulatives sont disponibles sur le serveur de téléchargement de correctif logiciel de Microsoft fourni dans les articles de la Base de connaissances CU.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2014 à partir de l’Assistant Installation &#40;le programme d’installation&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [Installation des mises à jour à partir de l’invite de commandes](installing-updates-from-the-command-prompt.md) [ajouter des fonctionnalités à une Instance de SQL Server 2014 &#40;le programme d’installation&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [Ignorer une installation de SQL Server 2014](repair-a-failed-sql-server-installation.md)  
  
  
