---
title: Afficher le journal des erreurs SQL Server (SQL Server Management Studio) | Microsoft Docs
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 7de82937a4bb622190da96b5668318304f641895
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>Afficher le journal des erreurs SQL Server (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient des événements définis par l’utilisateur et certains événements système utiles pour la résolution des problèmes. 

## <a name="view-the-logs"></a>Afficher les journaux

1. Dans SQL Server Management Studio, sélectionnez **Explorateur d’objets**. Pour ouvrir **l’Explorateur d’objets**, sélectionnez F8. Vous pouvez aussi cliquer dans le menu du haut, sélectionner **Affichage**, puis **Explorateur d’objets** :
    
    ![Object_Explorer](../../relational-databases/performance/media/object-explorer.png) 

2. Dans **l’Explorateur d’objets**, connectez-vous à une instance de SQL Server et développez-la.
  
3. Recherchez et développez la section **Gestion** (en supposant que vous disposiez des autorisations nécessaires pour la voir).

4. Cliquez avec le bouton droit sur **Journaux SQL Server**, sélectionnez **Affichage**, puis choisissez **Journal SQL Server**.

    ![Affichage du journal SQL Server dans SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5. La **visionneuse du fichier journal** s’affiche (l’opération peut prendre un certain temps) avec une liste des journaux consultables.
  
  ## <a name="see-also"></a>Voir aussi
  Pour plus d’informations, consultez le post très intéressant [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/) sur [MSSQLTips.com](https://www.mssqltips.com/).

