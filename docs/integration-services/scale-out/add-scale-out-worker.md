---
title: Ajouter un SSIS Scale Out Worker avec Scale Out Manager | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef11448d03bd188aaea425225312af9f681f530c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Ajouter un Scale Out Worker avec Scale Out Manager

Integration Services Scale Out Manager simplifie considérablement l’ajout de Scale Out Worker à votre environnement Scale Out existant. 

Les étapes ci-dessous indiquent comment ajouter un Scale Out Worker à votre topologie Scale Out :

## <a name="1-install-scale-out-worker"></a>1. Installer Scale Out Worker
Dans l’Assistant Installation de SQL Server, sélectionnez Integration Services et Scale Out Worker dans la page **Sélection de fonctionnalités**. 
![Sélection de la fonctionnalité Worker](media/feature-select-worker.PNG)

Dans la page **Configuration d’Integration Services Scale Out - Nœud worker**, vous pouvez simplement cliquer sur « Suivant » pour ignorer la configuration à ce stade et utiliser **Scale Out Manager** pour effectuer la configuration après l’installation.

Terminez l’Assistant Installation.

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2. Ouvrir le pare-feu sur l’ordinateur Scale Out Master
Ouvrez le port spécifié pendant l’installation de Scale Out Master (8391, par défaut) et le port de SQL Server (1433, par défaut) à l’aide du Pare-feu Windows sur l’ordinateur Scale Out Master.

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3. Ajouter Scale Out Worker avec Scale Out Manager
Exécutez SQL Server Management Studio en tant qu’administrateur et connectez-vous à l’instance SQL Server de Scale Out Master.

Cliquez avec le bouton droit sur **SSISDB** dans l’Explorateur d’objets et sélectionnez **Gérer Scale Out**. 

![Gérer Scale Out](media/manage-scale-out.PNG)

Dans la fenêtre **Scale Out Manager** qui apparaît, basculez vers **Gestionnaire de workers**. Cliquez sur le bouton « + » et suivez les instructions de la boîte de dialogue de connexion à Worker. Pour plus d’informations, consultez [Scale Out Manager](integration-services-ssis-scale-out-manager.md).
