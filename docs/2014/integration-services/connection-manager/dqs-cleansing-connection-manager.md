---
title: Gestionnaire de connexions de nettoyage DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: faa1eedd-db14-41e5-8e58-8f0f6f561e42
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2aa3e59db56a39ceb96c49f25ab3c0d836c0f4f7
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434206"
---
# <a name="dqs-cleansing-connection-manager"></a>Gestionnaire de connexions de nettoyage DQS
  Un gestionnaire de connexions de nettoyage DQS permet à un package de se connecter à un serveur [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] . La transformation de nettoyage DQS utilise le gestionnaire de connexions de nettoyage DQS.  
  
 Pour plus d’informations sur Data Quality Services, consultez [Concepts Data Quality Services](../../data-quality-services/data-quality-services-concepts.md).  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions de nettoyage DQS prend en charge uniquement l'authentification Windows.  
  
## <a name="related-tasks"></a>Tâches associées  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation. Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur de transformation de nettoyage DQS](../dqs-cleansing-transformation-editor-dialog-box.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez la documentation de la classe <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> dans le Guide du développeur.  
  
  
