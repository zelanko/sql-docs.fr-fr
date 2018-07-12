---
title: Gestionnaire de connexions Azure Resource Manager | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
caps.latest.revision: 2
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ddde8d5e677dd2cf480ca523c97cfd8e04bf67ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169270"
---
# <a name="azure-resource-manager-connection-manager"></a>Gestionnaire de connexions Azure Resource Manager
Le **gestionnaire de connexions Azure Resource Manager** permet à un package SSIS de gérer les ressources Azure à l’aide d’un [principal du service](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).

Pour créer et configurer un **gestionnaire de connexions Azure Resource Manager**, effectuez les étapes suivantes :

1. Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS**, sélectionnez **AzureResourceManager**, puis cliquez sur **Ajouter**.
2. Dans l’**Éditeur du gestionnaire de connexions Azure Resource Manager**, spécifiez l’**ID d’application**, la **clé de l’application** et l’**ID de locataire** du principal du service. Pour plus d’informations sur ces propriétés, consultez [cet](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) article.
3. Cliquez sur **OK** pour fermer la boîte de dialogue.
4. Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .
