---
title: Comptes de service (Assistant Configuration de la sécurité de la mise en miroir de bases de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fdca44263bfa60ebf7a2a2a3d66d0c827c3d0868
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152189"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Comptes de service (Assistant Configuration de la sécurité de la mise en miroir de bases de données)
  Lors de l'utilisation de l'authentification Windows, si les instances de serveur utilisent des comptes différents, spécifiez les comptes de service pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces comptes de service doivent tous être des comptes de domaine (dans les mêmes domaines ou des domaines approuvés).  
  
 Si toutes les instances de serveur utilisent le même compte de domaine ou une authentification basée sur les certificats, laissez les champs vides. Cliquez simplement sur **Terminer**; l'Assistant configure alors automatiquement les comptes en fonction du compte de l'Assistant actuel.  
  
> [!IMPORTANT]  
>  Si les points de terminaison de mise en miroir de base de données des instances de serveur sont configurés pour utiliser des certificats, vous devez laisser les champs de compte de service vides.  
  
 **Pour configurer la mise en miroir de bases de données à l'aide de SQL Server Management Studio**  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Options  
 **Principal**  
 Permet de spécifier le compte de service de l'instance de serveur principal. Entrez le nom du domaine en majuscules :  
  
 *NOM_DOMAINE*\\*nom_utilisateur*  
  
 **Miroir**  
 Permet de spécifier le compte de service de l'instance de serveur miroir. Entrez le nom du domaine en majuscules :  
  
 *NOM_DOMAINE*\\*nom_utilisateur*  
  
 **Témoin**  
 Permet de spécifier le compte de service de l'instance de serveur témoin. Entrez le nom du domaine en majuscules :  
  
 *NOM_DOMAINE*\\*nom_utilisateur*  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la base de données &#40;page Mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Démarrer le moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Configurer les comptes de connexion pour la mise en miroir de base de données ou les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  