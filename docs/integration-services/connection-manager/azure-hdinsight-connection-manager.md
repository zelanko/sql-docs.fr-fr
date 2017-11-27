---
title: Gestionnaire de connexions Azure HDInsight | Documents Microsoft
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPHDICM.F1
- SQL14.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 29d01bd9-8b38-43b1-b937-67f8aea57c0f
caps.latest.revision: 4
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 080cd1184d3c29673ac476d6fe6087b697160544
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="azure-hdinsight-connection-manager"></a>Gestionnaire de connexions Azure HDInsight
Le **Gestionnaire de connexions Azure HDInsight** permet à un package SSIS pour vous connecter à un cluster Azure HDInsight.

Le **Gestionnaire de connexions Azure HDInsight** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Pour créer et configurer un **Gestionnaire de connexions Azure HDInsight**, procédez comme suit :

1. Dans le **ajouter un gestionnaire de connexions SSIS** boîte de dialogue, sélectionnez **AzureHDInsight**, puis cliquez sur **ajouter**.
2. Dans le **Éditeur du Gestionnaire de connexions HDInsight Azure** boîte de dialogue, spécifiez la **nom DNS de Cluster** (sans le préfixe de protocole), **nom d’utilisateur**, et **mot de passe** pour le cluster HDInsight pour se connecter à.
3. Cliquez sur **OK** pour fermer la boîte de dialogue.
4. Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .

