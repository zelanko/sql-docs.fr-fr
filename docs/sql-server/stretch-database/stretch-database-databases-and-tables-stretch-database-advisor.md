---
title: "Bases de données et tables pour Stretch Database - Stretch Database Advisor | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/14/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, identifying databases
- Stretch Database, identifying tables
- identifying databases for Stretch Database
- identifying tables for Stretch Database
ms.assetid: 81bd93d8-eef8-4572-88d7-5c37ab5ac2bf
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 59608301d353d99eb710a956389fd9f8d8948dfe
ms.contentlocale: fr-fr
ms.lasthandoff: 07/29/2017

---
# <a name="stretch-database-databases-and-tables---stretch-database-advisor"></a>Bases de données et tables pour Stretch Database - Stretch Database Advisor
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Pour identifier les bases de données et tables candidates pour Stretch Database, téléchargez Stretch Database Advisor 2016 et exécutez Stretch Database Advisor. Stretch Database Advisor identifie également les blocages.  
  
## <a name="download-and-install-upgrade-advisor"></a>Télécharger et installer le Conseiller de mise à niveau  
 Pour télécharger et installer le Conseiller de mise à niveau, cliquez [ici](https://www.microsoft.com/en-us/download/details.aspx?id=53595). Cet outil n’est pas inclus dans le support d’installation de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .  
  
## <a name="run-the-stretch-database-advisor"></a>Exécuter Stretch Database Advisor  
  
1.  Exécutez le Conseiller de mise à niveau.  
  
2.  Sélectionnez **Scénarios**, puis **EXÉCUTER STRETCH DATABASE ADVISOR**.  
  
3.  Dans le panneau **Exécuter Stretch Database Advisor** , cliquez sur **SÉLECTIONNER LES BASES DE DONNÉES À ANALYSER**.  
  
4.  Dans le panneau **Sélectionner des bases de données** , entrez ou sélectionnez le nom du serveur et les informations d’authentification. Cliquez sur **Se connecter**.

5.  La liste des bases de données disponibles sur le serveur sélectionné s’affiche. Sélectionnez les bases de données que vous voulez analyser. Cliquez sur **Sélectionner**.  
  
6.  Dans le panneau **Exécuter Stretch Database Advisor** , cliquez sur **Exécuter**.  L’analyse se lance.  
  
## <a name="review-the-results"></a>Examiner les résultats  
  
1.  Une fois l’analyse terminée, dans le panneau **Bases de données analysées** , sélectionnez une des bases de données analysées pour afficher le panneau **Résultats de l’analyse** .  
  
     Le panneau **Résultats de l’analyse** répertorie les tables de la base de données, qui correspondent aux critères de recommandation par défaut. 
  
2.  Dans la liste des tables du panneau **Résultats de l’analyse** , sélectionnez l’une des tables recommandées pour afficher le panneau **Résultats de la table** .  
  
     En cas de blocage, vous pouvez consulter le panneau **Résultats de la table** qui répertorie les blocages de la table sélectionnée. Pour plus d’informations sur les blocages détectés par Stretch Database Advisor, consultez [Limitations concernant Stretch Database](../../sql-server/stretch-database/limitations-for-stretch-database.md).  
  
3.  Dans la liste des problèmes de blocage du panneau **Résultats de la table** , sélectionnez l’un des problèmes pour afficher des informations détaillées et les mesures d’atténuation proposées. Mettez en œuvre les mesures d’atténuation suggérées si vous souhaitez configurer la table sélectionnée pour Stretch Database.  
  
## <a name="next-step"></a>Étape suivante  
 Activez Stretch Database.  
  
-   Pour activer Stretch Database sur une **base de données**, consultez [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
-   Pour activer Stretch Database sur une autre **table**, alors que Stretch est déjà activé sur la base de données, consultez [Enable Stretch Database for a table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md). 
  
## <a name="see-also"></a>Voir aussi  
 [Limitations concernant Stretch Database](../../sql-server/stretch-database/limitations-for-stretch-database.md)   
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Activer Stretch Database pour une table](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  

