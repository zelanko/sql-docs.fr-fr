---
title: Configurer SQL Server pour recevoir des copies de tables distantes
description: Décrit comment configurer une instance de SQL Server SMP externe pour recevoir des copies de tables distantes à partir de Data Warehouse parallèles.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 3e5475e86582ede2e6fa7ca5a302bba7ee74faa3
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401323"
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies---parallel-data-warehouse"></a>Configurer un SQL Server SMP externe pour recevoir des copies de tables distantes-Parallel Data Warehouse
Décrit comment configurer une instance de SQL Server externe pour recevoir des copies de tables distantes à partir de Data Warehouse parallèles.  

Cette rubrique décrit l’une des étapes de configuration de la configuration de la copie des tables distantes. Pour obtenir la liste de toutes les étapes de configuration, consultez [copie de table distante](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
Avant de pouvoir configurer l’SQL Server externe, vous devez :  
  
-   Utilisez un système Windows avec SQL Server 2008 Enterprise Edition ou une version ultérieure prête à être installée ou déjà installée. Le système Windows doit déjà être configuré conformément aux instructions fournies dans [configurer un système Windows externe pour recevoir des copies de tables distantes à l’aide de InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md).  
  
-   Un compte d’administrateur Windows avec la possibilité de configurer l’instance de SQL Server et le système Windows.  
  
-   Un compte de connexion SQL Server (si SQL Server est déjà installé) avec la possibilité de créer des connexions et d’accorder des autorisations sur la ou les bases de données de destination.  
  
## <a name="HowToSQLServer"></a>Configurer un SQL Server SMP externe pour recevoir des copies de tables distantes  
La fonctionnalité de copie de table distante copie les tables de l’appliance SQL Server PDW vers une base de données SMP SQL Server externe qui s’exécute sur un système Windows. Après avoir configuré le système Windows externe pour recevoir des copies de tables distantes, l’étape suivante consiste à installer et à configurer SQL Server sur le système Windows.  
  
Pour configurer SQL Server, procédez comme suit :  
  
1.  Installez SQL Server édition Enterprise 2008 ou version ultérieure sur le système Windows. C’est ce que l’on appelle le SQL Server SMP.  
  
2.  Configurez SQL Server pour accepter les connexions TCP/IP sur un port TCP fixe. Cette configuration est désactivée par défaut et doit être activée pour permettre à SQL Server PDW de se connecter au SQL Server SMP.  
  
3.  Désactivez le pare-feu Windows ou configurez le port SMP SQL Server TCP afin qu’il fonctionne avec le pare-feu Windows activé.  
  
4.  Configurez SQL Server pour autoriser le mode d’authentification SQL Server. L’exportation de données parallèles utilise toujours les comptes SQL Server pour l’authentification.  
  
5.  Déterminez un compte SQL Server sur le SQL Server SMP qui sera utilisé pour l’authentification. Accordez à ce compte le privilège de créer, de supprimer et d’insérer des données dans les tables de la base de données de destination pour l’opération d’exportation de données en parallèle.  
  
## <a name="BPSQLConfig"></a>Meilleures pratiques pour la configuration SMP SQL Server pour la copie de tables distantes  
Quand vous configurez le SMP SQL Server pour recevoir des copies de tables distantes, utilisez les meilleures pratiques suivantes pour améliorer les performances.  
  
1.  Suivez les meilleures pratiques décrites dans SQL Server Documentation du produit. Par exemple, activez le chiffrement des données. Pour plus d’informations sur la sécurisation des SQL Server, consultez [sécurisation des SQL Server](../relational-databases/security/securing-sql-server.md) sur MSDN.  
  
2.  Utilisez le mode de récupération journalisé en bloc ou simple.  
  
    Lors des opérations d’exportation de données parallèles, les données sont insérées en bloc dans la table de destination nouvellement créée. Pour des performances maximales lors de l’insertion en bloc, définissez la base de données de destination pour qu’elle utilise le mode de récupération journalisé en bloc ou simple.  
  
3.  Utilisez l’option batch_size pour récupérer l’espace du journal.  
  
    Bien que les modes de récupération journalisés en bloc utilisent une journalisation minimale pour les données insérées en bloc, la journalisation continue à se produire. Pour éviter que les fichiers journaux ne deviennent trop volumineux, utilisez l’option SQL Server batch_size pour récupérer périodiquement l’espace du journal.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
