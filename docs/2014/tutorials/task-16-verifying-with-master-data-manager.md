---
title: 'Tâche 16 : vérification à l’aide de la Data Manager maître | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d1649582f97e9e08691726745e4ba14b2f8226bd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061078"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Tâche 16 : Vérification à l’aide de Master Data Manager
  Dans cette tâche, vous allez vérifier l'état du programme de traitement par lots soumis par le package SSIS et vérifiez que les données ont été téléchargées sur le serveur MDS à l'aide de Master Data Manager.  
  
1.  Lancez le **Data Manager maître** ( `http://localhost/MDS` ). S’il est déjà ouvert, cliquez sur **Microsoft SQL Server Master Data Services** en haut pour basculer vers la **page d’hébergement**.  
  
2.  Cliquez sur gestion de l' **intégration**.  
  
3.  Notez qu’il existe un lot avec nommé **EIMBatch** que vous avez envoyé dans la liste. Si vous ne voyez pas l’écran suivant, cliquez sur **importer des données** dans la barre de menus.  
  
     ![Lot EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "Lot EIM")  
  
4.  Revenez à la page d’hébergement en cliquant sur **SQL Server 2012 Master Data Services** en haut.  
  
5.  Assurez-vous que le modèle **fournisseurs** est sélectionné pour **modèle** et que **Version_1** est sélectionné pour **version**, puis cliquez sur **Explorateur**.  
  
6.  Vous pouvez voir le package de données SSIS importé dans MDS. Les données doivent être nettoyées et ne pas avoir de valeurs de **code** en double (Remarque : la colonne **RéfFournisseur** dans Excel correspond à l’attribut **code** de l’entité fournisseur dans MDS).  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 17 : Examen du projet de nettoyage DQS créé par le package SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
