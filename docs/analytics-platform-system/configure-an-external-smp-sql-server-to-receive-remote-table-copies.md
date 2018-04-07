---
title: Configurer le serveur SQL SMP externes pour recevoir des Copies de la Table distante (PDW)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bbd2ed6-064e-4b45-b67b-608dc0f2b2bc
caps.latest.revision: 13
ms.openlocfilehash: 94b62dbae331c19fa97c1625a53804f4cd96bfa5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies"></a>Configurer un serveur SQL SMP externes pour recevoir une copie de la Table distante
Décrit comment configurer une instance de SQL Server externe pour recevoir des copies de la table distante de SQL Server PDW.  
  
Cette rubrique décrit l’une des étapes de configuration pour la configuration de copie de la table distante. Pour obtenir la liste de toutes les étapes de configuration, consultez [copie distante de la Table](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
Avant de pouvoir configurer le serveur SQL Server externe, vous devez :  
  
-   Disposer d’un système Windows avec SQL Server 2008 Enterprise Edition ou une version ultérieure prête à être installés ou déjà installée. Le système Windows doit être déjà configuré en suivant les instructions de [configurer un externe Windows System pour recevoir à distance Table Copies à l’aide de InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md).  
  
-   Un compte d’administrateur Windows avec la possibilité de configurer l’instance de SQL Server et le système Windows.  
  
-   Un compte de connexion SQL Server (si SQL Server est déjà installé) avec la possibilité de créer des connexions et accorder des autorisations sur les bases de données de destination.  
  
## <a name="HowToSQLServer"></a>Configurer un serveur SQL SMP externes pour recevoir une copie de la Table distante  
La fonctionnalité de copie de table distante copie des tables à partir de l’appliance SQL Server PDW pour une base de données externe SMP SQL Server qui s’exécute sur un système Windows. Après avoir configuré le système Windows externe pour recevoir une copie de la table distante, l’étape suivante consiste à installer et configurer SQL Server sur le système Windows.  
  
Pour configurer SQL Server, procédez comme suit :  
  
1.  Installer SQL Server 2008 Enterprise Edition ou une version ultérieure sur le système Windows. Cette opération est dénommée SMP SQL Server.  
  
2.  Configurez SQL Server pour accepter les connexions TCP/IP sur un port TCP fixe. Cette configuration est désactivée par défaut et doit être activée pour permettre à SQL Server PDW pour se connecter au serveur SQL SMP.  
  
3.  Désactiver le pare-feu Windows soit configurer le port TCP SMP SQL Server afin qu’il fonctionne avec le pare-feu Windows est activé.  
  
4.  Configurer SQL Server pour autoriser le mode d’authentification SQL Server. Exportation de données parallèles toujours utilise des comptes SQL Server pour l’authentification.  
  
5.  Déterminer un compte SQL Server sur le serveur SQL SMP qui sera utilisé pour l’authentification. Accordez à ce compte le privilège pour créer, supprimer et insérer des données dans des tables dans la base de données de destination pour l’opération d’exportation de données en parallèle.  
  
## <a name="BPSQLConfig"></a>Meilleures pratiques pour la Configuration du serveur SQL de SMP pour la copie de la Table distante  
Lorsque vous configurez le serveur SQL de SMP pour recevoir une copie de la table distante, utilisez les meilleures pratiques suivantes pour améliorer les performances.  
  
1.  Suivez les meilleures pratiques décrites dans la documentation du produit SQL Server. Par exemple, activer le chiffrement de données. Pour plus d’informations sur la sécurisation de SQL Server, consultez [sécurisation de SQL Server](../relational-databases/security/securing-sql-server.md) sur MSDN.  
  
2.  Utilisez le mode de récupération journalisé en bloc ou simple.  
  
    Pendant les données en parallèle des opérations d’exportation, les données est insérée dans la table de destination qui vient d’être créée. Pour optimiser les performances lors de l’insertion en bloc, définissez la base de données de destination à utiliser les journaux de transactions ou le mode de récupération simple.  
  
3.  Utilisez l’option batch_size pour récupérer de l’espace du journal.  
  
    Bien que la récupération journalisé en bloc ou simple modélise utilisation minimale de journalisation pour les données insérées en masse, certains journalisation se produit toujours. Pour empêcher les fichiers journaux ne devienne trop importante, utilisez l’option de batch_size de SQL Server pour récupérer de l’espace du journal régulièrement.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
