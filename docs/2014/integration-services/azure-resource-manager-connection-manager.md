---
title: Gestionnaire de connexions Azure Resource Manager | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2db468ae6a9bc90c492a9c4557d248f7f7ef81d1
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925226"
---
# <a name="azure-resource-manager-connection-manager"></a>Gestionnaire de connexions Azure Resource Manager
Le **gestionnaire de connexions Azure Resource Manager** permet à un package SSIS de gérer les ressources Azure à l’aide d’un [principal du service](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

Pour créer et configurer un **gestionnaire de connexions Azure Resource Manager**, effectuez les étapes suivantes :

1. Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **AzureResourceManager**, puis cliquez sur **Ajouter**.
2. Dans l’**Éditeur du gestionnaire de connexions Azure Resource Manager**, spécifiez l’**ID d’application**, la **clé de l’application** et l’**ID de locataire** du principal du service. Pour plus d’informations sur ces propriétés, consultez [cet](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) article.
3. Cliquez sur **OK** pour fermer la boîte de dialogue.
4. Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .
