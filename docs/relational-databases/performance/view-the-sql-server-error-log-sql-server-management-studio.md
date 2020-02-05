---
title: Voir le journal des erreurs SQL Server (SSMS)
description: Visualisez le journal des erreurs SQL Server dans SSMS (SQL Server Management Studio).
ms.custom: seo-dt-2019
ms.date: 09/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: f6410575af0d05b8d407ba9f52cc116fbe2ac733
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74165475"
---
# <a name="view-the-sql-server-error-log-in-sql-server-management-studio-ssms"></a>Voir le journal des erreurs SQL Server dans SSMS (SQL Server Management Studio)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient des événements définis par l’utilisateur et certains événements système utiles pour la résolution des problèmes. 

## <a name="view-the-logs"></a>Afficher les journaux

1. Dans SQL Server Management Studio, sélectionnez **Explorateur d’objets**. Pour ouvrir **l’Explorateur d’objets**, sélectionnez F8. Vous pouvez aussi cliquer dans le menu du haut, sélectionner **Affichage**, puis **Explorateur d’objets** :
    
    ![Object_Explorer](../../relational-databases/performance/media/object-explorer.png) 

2. Dans **l’Explorateur d’objets**, connectez-vous à une instance de SQL Server et développez-la.
  
3. Recherchez et développez la section **Gestion** (en supposant que vous disposiez des autorisations nécessaires pour la voir).

4. Cliquez avec le bouton droit sur **Journaux SQL Server**, sélectionnez **Affichage**, puis choisissez **Journal SQL Server**.

    ![Affichage du journal SQL Server dans SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5. La **visionneuse du fichier journal** s’affiche (l’opération peut prendre un certain temps) avec une liste des journaux consultables.

  ## <a name="see-also"></a>Voir aussi
  Pour plus d’informations, consultez le post très intéressant [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/) sur [MSSQLTips.com](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/).

