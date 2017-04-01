---
title: "Mise &#224; niveau du moteur de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f08087e-e532-416c-8caa-e0ec88c57596
caps.latest.revision: 10
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 10
---
# Mise &#224; niveau du moteur de base de donn&#233;es
  Après une mise à niveau vers SQL Server 2016, vous devrez probablement exécuter quelques tâches supplémentaires. Ces options en question sont les suivantes :  
  
 Après la mise à niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)], effectuez les tâches suivantes :  
  
-   **Sauvegarder vos bases de données :** effectuez une sauvegarde complète de chaque base de données mise à niveau.  
  
-   **Activer les nouvelles fonctionnalités : **Dans SQL Server 2016, certaines modifications sont activées uniquement une fois que le niveau DATABASE_COMPATIBILITY d’une base de données a été modifié pour passer à 130.  Pour obtenir plus d’informations et accéder au flux de travail recommandé, consultez [Modifier le mode de compatibilité de base de données et utiliser le magasin des requêtes](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
-   **Integration Services :**  
  
     Migrez les packages Integration Services vers le format [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Pour plus d’informations, voir [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
-   **Reporting Services :** pour la mise à niveau d’une nouvelle installation, restaurez les clés de chiffrement de Reporting Services. Pour plus d’informations, consultez [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md).  
  
-   **Master Data Services :**  mettez à niveau le schéma de la base de données MDS et créez l’application web de SQL Server 2016. Pour plus d’informations, consultez [Upgrade Master Data Services](../../database-engine/install-windows/upgrade-master-data-services.md).  
  
-   **Data Quality Services :** mettez à niveau le schéma de bases de données DQS et vérifiez la mise à niveau du schéma de bases de données DQS. Pour plus d’informations, consultez [Upgrade Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
  
-   **Recherche en texte intégral :** Alimentez à nouveau les catalogues de texte intégral pour garantir la cohérence sémantique dans les résultats de la requête. Pour plus d’informations, consultez [Alimenter des index de recherche en texte intégral](../../relational-databases/search/populate-full-text-indexes.md).  
  
## Cet article vous a-t-il été utile ? Nous sommes à votre écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous tenons compte de vos commentaires pour améliorer le contenu de nos articles. Veuillez envoyer vos commentaires à l’adresse suivante : [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Complete%20the%20Database%20Engine%20Upgrade%20page)  
  
  