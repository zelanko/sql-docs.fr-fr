---
title: 'Tâche 16 : Vérification avec Master Data Manager | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7d0c5b2f72a04b1c1f99829e61ca2dca3fedc39a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304649"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Tâche 16 : Vérification à l'aide de Master Data Manage
  Dans cette tâche, vous allez vérifier l'état du programme de traitement par lots soumis par le package SSIS et vérifiez que les données ont été téléchargées sur le serveur MDS à l'aide de Master Data Manager.  
  
1.  Lancez **Master Data Manager** ([http://localhost/MDS](http://localhost/MDS)). Si elle est déjà ouverte, cliquez sur **Microsoft SQL Server Master Data Services** en haut pour basculer vers le **page d’accueil**.  
  
2.  Cliquez sur **gestion de l’intégration**.  
  
3.  Notez qu’il existe un lot nommé **EIMBatch** que vous avez envoyée dans la liste. Cliquez sur **importer des données** sur la barre de menus si vous ne voyez pas l’écran suivant.  
  
     ![Lot EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "lot EIM")  
  
4.  Basculer vers la page d’accueil en un clic **SQL Server 2012 Master Data Services** en haut.  
  
5.  Assurez-vous que l’option **fournisseurs** modèle est sélectionné pour **modèle** et **VERSION_1** est sélectionné pour **Version**, puis cliquez sur  **Explorer**.  
  
6.  Vous pouvez voir le package de données SSIS importé dans MDS. Les données doivent être nettoyées et n’avoir aucune **Code** valeurs (Remarque : **SupplierID** colonne dans Excel correspond à **Code** attribut de l’entité fournisseur dans MDS).  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 17 : Examen du projet de nettoyage DQS créé par le package SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
