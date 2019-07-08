---
title: Afficher le journal des erreurs SQL Server (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: 38d99822b2d77e25259c793d350e4d329d4c0af7
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582217"
---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>Afficher le journal des erreurs SQL Server (SQL Server Management Studio)
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

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

  ## <a name="see-also"></a>Voir aussi
  Pour plus d’informations, consultez le post très intéressant [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/) sur [MSSQLTips.com](https://www.mssqltips.com/).

