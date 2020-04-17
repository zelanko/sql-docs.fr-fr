---
title: 'Tâche 16 : Vérification avec Master Data Manager (en anglais seulement) Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d9828c02625ae2bc5a85859577a237b4c4fa99c5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484679"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Tâche 16 : Vérification à l’aide de Master Data Manager
  Dans cette tâche, vous allez vérifier l'état du programme de traitement par lots soumis par le package SSIS et vérifiez que les données ont été téléchargées sur le serveur MDS à l'aide de Master Data Manager.  
  
1.  Lancement Master Data`http://localhost/MDS` **Manager** ( ). S’il est déjà ouvert, cliquez sur **Microsoft SQL Server Master Data Services** en haut pour passer à la page **d’accueil**.  
  
2.  Cliquez sur **La gestion de l’intégration**.  
  
3.  Notez qu’il y a un lot avec **EIMBatch** nommé que vous avez soumis dans la liste. Cliquez sur **Les données d’importation** sur la barre du menu si vous ne voyez pas l’écran suivant.  
  
     ![Lot EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "Lot EIM")  
  
4.  Retournez à la page d’accueil en cliquant sur **SQL Server 2012 Master Data Services** en haut.  
  
5.  Assurez-vous que le modèle **Fournisseurs** est sélectionné pour **le modèle** et **VERSION_1** est sélectionné pour **la version**, et cliquez sur **Explorer**.  
  
6.  Vous pouvez voir le package de données SSIS importé dans MDS. Les données doivent être nettoyées et n’ont pas de doublons **valeurs de code** (Note: Colonne **SupplierID** dans Excel correspond à **l’attribut** de code de l’entité fournisseur dans MDS).  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 17 : Examen du projet de nettoyage DQS créé par le package SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
