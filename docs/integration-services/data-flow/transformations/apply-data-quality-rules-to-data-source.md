---
title: Appliquer des règles de qualité des données à la source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bb34223b2bfcb896c2f5b6fa6ec01e7e3487a072
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68112855"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Appliquer des règles de qualité des données à la source de données

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Vous pouvez utiliser Data Quality (DQS) Services pour corriger les données dans le flux de données du package en connectant la transformation de nettoyage DQS à la source de données. Pour plus d’informations sur DQS, consultez [Concepts Data Quality Services](../../../data-quality-services/data-quality-services-concepts.md). Pour plus d’informations sur la transformation, consultez [Transformation de nettoyage DQS](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Lorsque vous traitez des données avec la transformation de nettoyage DQS, un projet de qualité des données est créé sur le serveur de qualité des données. Vous utilisez le client de qualité des données pour gérer le projet. Pour plus d’informations, consultez [Ouvrir, déverrouiller, renommer et supprimer un projet de qualité des données](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Pour corriger les données dans le flux de données  
  
1.  Créer un package.  
  
2.  Ajoutez et configurez la transformation de nettoyage DQS. Pour plus d’informations, consultez [Éditeur de transformation de nettoyage DQS (boîte de dialogue)](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Connectez la transformation de nettoyage DQS à une source de données.  
  
  
