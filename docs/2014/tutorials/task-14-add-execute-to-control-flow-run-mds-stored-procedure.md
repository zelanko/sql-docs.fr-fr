---
title: 'Tâche 14 : ajout d’une tâche d’exécution SQL à un workflow de contrôle pour exécuter la procédure stockée pour MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9a5d1b52-d505-4e6f-8a89-569329c094e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 151db2640e9038ad574775fa5374bddb9ed4aad0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061116"
---
# <a name="task-14-adding-execute-sql-task-to-control-flow-to-run-the-stored-procedure-for-mds"></a>Tâche 14 : Ajout d’une tâche d’exécution SQL au flux de contrôle pour exécuter la procédure stockée pour MDS
  Après le chargement des données dans les tables intermédiaires de MDS, vous allez exécuter une procédure stockée associée à ces tables pour charger les données des tables intermédiaires vers les tables appropriées dans la base de données MDS. Cette procédure stockée nécessite deux paramètres : LogFlag et VersionName. LogFlag spécifie si les transactions sont journalisées pendant le processus intermédiaire et VersionName représente la version du modèle. Pour plus d’informations, consultez la rubrique [procédure stockée intermédiaire](https://msdn.microsoft.com/library/hh231028.aspx) .

 Dans cette tâche, vous allez ajouter la tâche d'exécution SQL au flux de contrôle pour appeler la procédure stockée et charger les données intermédiaires dans les tables MDS appropriées.

1.  Maintenant, basculez vers l’onglet **Flow Control** .

2.  Glissez-déplacez la **tâche d’exécution SQL** de la **boîte à outils SSIS** vers l’onglet **Flow Control** .

3.  Cliquez avec le bouton droit sur **tâche d’exécution SQL** dans l’onglet **contrôle** de la gestion, puis cliquez sur **Renommer**. Tapez **déclencher la procédure stockée pour charger des données dans MDS** et appuyez sur **entrée**.

4.  Connectez **recevoir, nettoyer, faire correspondre et organiser les données des fournisseurs** pour **déclencher la procédure stockée et charger les données** à l’aide du connecteur vert.

     ![Connecter à la tâche d'exécution SQL](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-01.jpg "Connecter à la tâche d'exécution SQL")

5.  À l’aide de la fenêtre **variables** , ajoutez deux nouvelles variables avec les paramètres suivants. Si vous ne voyez pas la fenêtre **variables** , cliquez sur **SSIS** dans la barre de menus, puis cliquez sur **variables**.

    |Nom|Type de données|Valeur|
    |----------|---------------|-----------|
    |LogFlag|Int32|1|
    |VersionName|String|VERSION_1|

     ![Fenêtre Variables SSIS.](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-02.jpg "Fenêtre Variables SSIS.")

6.  Double-cliquez sur **déclencher une procédure stockée pour charger des données dans MDS**.

7.  Dans la boîte de dialogue **éditeur de tâche d’exécution de SQL** , sélectionnez **(local). MDS** (ou **localhost. MDS**) pour la **connexion**.

8.  Tapez **exec [STG]. [ udp_Supplier_Leaf] ?, ?, ?** pour l' **instruction SQL**. Vérifiez le nom à l'aide de SQL Server Management Studio.

     ![Boîte de dialogue Éditeur de tâche d'exécution SQL - Paramètres généraux](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-03.jpg "Boîte de dialogue Éditeur de tâche d'exécution SQL - Paramètres généraux")

9. Cliquez sur **mappage des paramètres** dans le menu de gauche.

10. Dans la page **mappage de paramètre** , cliquez sur **Ajouter** pour ajouter un mappage. Agrandissez la fenêtre et redimensionnez les colonnes afin de voir correctement les valeurs dans les listes déroulantes.

11. Sélectionnez **User :: VersionName** dans la liste déroulante correspondant au **nom**de la variable.

12. Sélectionnez **nvarchar** pour **type de données**.

13. Tapez **0** (zéro) comme **nom de paramètre**.

14. Répétez les quatre étapes précédentes pour ajouter deux variables supplémentaires.

    |Nom de la variable|Type de données (important)|Nom du paramètre|
    |-------------------|-----------------------------|--------------------|
    |User::LogFlag|LONG|1|
    |User::BatchTag|NVARCHAR|2|

     ![Éditeur de tâche d'exécution de SQL - Mappage de paramètre](../../2014/tutorials/media/et-addingesqltasktocftorunthespformds-04.jpg "Éditeur de tâche d'exécution de SQL - Mappage de paramètre")

15. Cliquez sur **OK** pour fermer la boîte de dialogue **éditeur SQL d’exécution** .

## <a name="next-step"></a>étape suivante
 [Tâche 15 : Génération et exécution du projet SSIS](../../2014/tutorials/task-15-building-and-running-the-ssis-project.md)


