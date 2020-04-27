---
title: 'Tâche 15 : génération et exécution du projet SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 50b313f63ae434a96d6c0e38f3c8b600914c806d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66822994"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Tâche 15 : Génération et exécution du projet SSIS

  Dans cette tâche, vous allez générer et exécuter le projet SSIS. Si la version 64 bits d’Excel 2010 est installée sur votre ordinateur, vous devez définir la valeur de **Run64BitRuntime** sur **false** pour que la source Excel fonctionne.  
  
1.  Dans la fenêtre **Explorateur de solutions** , cliquez sur **projet** dans le menu, puis sur **Propriétés de CleanseAndCurateSuppliers**.  
  
2.  Dans la boîte de dialogue **Propriétés** , développez **Propriétés de configuration** sur la gauche, puis cliquez sur **débogage**.  
  
3.  Affectez à **Run64BitRuntime** la **valeur false**.  
  
     ![Propriétés du projet CleanseAndCurateSuppliers](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "Propriétés du projet CleanseAndCurateSuppliers")  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés**.  
  
5.  Dans la barre de menus, cliquez sur **générer** , puis sur **générer CleanseAndCurateSuppliers**. Vérifiez l'absence d'erreurs de génération.  
  
6.  Dans la barre de menus, cliquez sur **Déboguer** , puis sur **Démarrer le débogage**.  
  
7.  Passez en revue les messages dans la fenêtre de **progression** et vérifiez que le package est exécuté et qu’il s’est terminé avec succès.  
  
     ![Résultats de la fenêtre En cours](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Résultats de la fenêtre En cours")  
  
     ![État final de la fenêtre En cours](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "État final de la fenêtre En cours")  
  
8.  Cliquez sur **Déboguer** dans la barre de menus et cliquez sur **arrêter le débogage** pour arrêter la session de débogage. Si le package échoue, vous devez activer les visionneuses de données pour voir comment les données circulent entre les composants.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 16 : Vérification à l’aide de Master Data Manager](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
