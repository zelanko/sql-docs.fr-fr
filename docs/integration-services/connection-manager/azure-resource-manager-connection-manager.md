---
title: Gestionnaire de connexions Azure Resource Manager | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dd1dbf668bf3ac24d9d6598b0ff9e2256d897c42
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="azure-resource-manager-connection-manager"></a>Gestionnaire de connexions Azure Resource Manager
Le **Gestionnaire de connexions Azure Resource Manager** permet à un package SSIS gérer les ressources Azure à l’aide un [principal du service](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).

Le **Gestionnaire de connexions Azure Resource Manager** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Pour créer et configurer un **Gestionnaire de connexions Azure Resource Manager**, procédez comme suit :

1. Dans le **ajouter un gestionnaire de connexions SSIS** boîte de dialogue, sélectionnez **AzureResourceManager**, puis cliquez sur **ajouter**.
2. Dans le **Éditeur du Gestionnaire de connexions du Gestionnaire de ressources Azure** boîte de dialogue, spécifiez la **ID d’Application**, **clé d’Application**, et **ID client** pour le principal du service. Pour plus d’informations sur ces propriétés, reportez-vous à [cela](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) l’article.
3. Cliquez sur **OK** pour fermer la boîte de dialogue.
4. Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .

