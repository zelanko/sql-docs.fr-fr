---
title: 'Tâche 14 : Ajout de tâche d’exécution SQL au flux de contrôle pour exécuter la procédure stockée pour MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: cf0a02e973d046f3dff2b2df95327cf38e88443c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027970"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a>Tâche 14 : Ajout d'une tâche d'exécution SQL au flux de contrôle pour exécuter la procédure stockée pour MDS
  Après le chargement des données dans les tables intermédiaires de MDS, vous allez exécuter une procédure stockée associée à ces tables pour charger les données des tables intermédiaires vers les tables appropriées dans la base de données MDS. Cette procédure stockée nécessite deux paramètres requis : LogFlag et VersionName. LogFlag spécifie si les transactions sont journalisées pendant le processus intermédiaire et VersionName représente la version du modèle. Consultez [procédure stockée intermédiaire](https://msdn.microsoft.com/library/hh231028.aspx) rubrique pour plus d’informations.  
  
 Dans cette tâche, vous allez ajouter la tâche d'exécution SQL au flux de contrôle pour appeler la procédure stockée et charger les données intermédiaires dans les tables MDS appropriées.  
  
1.  Maintenant, basculez vers le **flux de contrôle** onglet.  
  
2.  Glisser-déplacer **tâche d’exécution SQL** à partir de la **boîte à outils SSIS** à la **flux de contrôle** onglet.  
  
3.  Avec le bouton droit **tâche d’exécution SQL** dans le **flux de contrôle** onglet, puis cliquez sur **renommer**. Type **déclencher la procédure stockée pour charger des données dans MDS** et appuyez sur **entrée**.  
  
4.  Se connecter **recevoir, nettoyer, correspondance et maintenir les données des fournisseurs** à **déclencher la procédure stockée pour charger des données** à l’aide du connecteur vert.  
  
     ![Se connecter à la tâche d’exécution SQL](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "se connecter à la tâche d’exécution SQL")  
  
5.  À l’aide de la **Variables** fenêtre, ajoutez deux nouvelles variables avec les paramètres suivants. Si vous ne voyez pas le **Variables** fenêtre, cliquez sur **SSIS** sur la barre de menus et cliquez sur **Variables**.  
  
    |Créer une vue d’abonnement|Type de données|Value|  
    |----------|---------------|-----------|  
    |LogFlag|Int32|1|  
    |VersionName|String|VERSION_1|  
  
     ![Fenêtre Variables SSIS](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "fenêtre Variables SSIS.")  
  
6.  Double-cliquez sur **déclencher la procédure stockée pour charger des données dans MDS**.  
  
7.  Dans le **Execute SQL Task Editor** boîte de dialogue, sélectionnez **(local). MDS** (ou **localhost. MDS**) pour **connexion**.  
  
8.  Type **EXEC [stg]. [ udp_Supplier_Leaf] ?, ?, ?** pour **instruction SQL**. Vérifiez le nom à l'aide de SQL Server Management Studio.  
  
     ![Exécuter des paramètres généraux de boîte de dialogue Éditeur SQL -](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "exécuter boîte de dialogue Éditeur SQL - paramètres généraux")  
  
9. Cliquez sur **mappage de paramètre** dans le menu de gauche.  
  
10. Dans le **mappage de paramètre** , cliquez sur **ajouter** pour ajouter un mappage. Agrandissez la fenêtre et redimensionnez les colonnes afin de voir correctement les valeurs dans les listes déroulantes.  
  
11. Sélectionnez **User::VersionName** dans la liste déroulante pour le **nom de la Variable**.  
  
12. Sélectionnez **NVARCHAR** pour **Type de données**.  
  
13. Type **0** (zéro) pour **nom du paramètre**.  
  
14. Répétez les quatre étapes précédentes pour ajouter deux variables supplémentaires.  
  
    |Nom de la variable|Type de données (important)|Nom du paramètre|  
    |-------------------|-----------------------------|--------------------|  
    |User::LogFlag|LONG|1|  
    |User::BatchTag|NVARCHAR|2|  
  
     ![Exécuter l’éditeur de tâche SQL - mappage de paramètre](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "exécuter l’éditeur de tâche SQL - mappage de paramètre")  
  
15. Cliquez sur **OK** pour fermer la **Éditeur d’exécution SQL** boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 15 : Générer et exécuter le projet SSIS](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)  
  
  
