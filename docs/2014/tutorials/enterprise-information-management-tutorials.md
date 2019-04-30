---
title: Didacticiels de gestion des informations Enterprise | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8745dc80-193d-4de0-9f17-ba648ab1e81c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ee7cc12f4fde3a2e5116458034ae3d4a8cc1c13a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313851"
---
# <a name="enterprise-information-management-tutorials"></a>Didacticiels sur la Gestion des informations d'entreprise
  Cette section contient des didacticiels pour gérer les informations de l'entreprise à l'aide des technologies de gestion des informations d'entreprise (EIM) incluses dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. La gestion des informations d'entreprise (EIM) fournit un éventail de solutions qui permettent aux organisations d'évaluer la crédibilité et la cohérence de leurs données afin de prendre des décisions commerciales critiques. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] contient les technologies suivantes, qui vous aident à mettre en œuvre les solutions EIM dans votre entreprise.  
  
-   SQL Server Integration Services (SSIS). SSIS fournit une plateforme puissante et souple pour intégrer les données provenant de différentes sources dans une solution d'extraction, de transformation et de chargement (ETL) complète qui prend en charge les flux de travail d'entreprise, un entrepôt de données, ou la gestion des données de référence.  
  
-   SQL Server Data Quality Services (DQS). DQS permet de nettoyer, faire correspondre, normaliser et enrichir les données, afin de disposer d'informations approuvées pour le décisionnel, d'un entrepôt de données et de charges de traitement pour les transactions.  
  
-   SQL Server Master Data Services (MDS). MDS est un concentrateur de données central qui garantit l'intégrité des informations et la cohérence des données entre différentes applications.  
  
 [Enterprise Information Management à l’aide de SSIS, MDS et DQS conjointement &#91;didacticiel&#93;](../../2014/tutorials/enterprise-information-management-using-ssis-mds-and-dqs-together-[tutorial].md)  
 Dans ce didacticiel, vous allez apprendre à utiliser SSIS, MDS et DQS conjointement pour implémenter un exemple de solution de gestion des informations d'entreprise (EIM). Vous utiliserez d'abord DQS pour créer une base de connaissances contenant les connaissances relatives aux données des fournisseurs (métadonnées), puis vous allez nettoyer les données dans un fichier Excel en fonction de la base de connaissances, et enfin, vous allez faire correspondre les données pour identifier et supprimer les doublons. Ensuite, vous utiliserez le complément MDS pour Excel pour télécharger les données nettoyées et mises en correspondance dans MDS. Enfin, vous automatiserez l'ensemble du processus en utilisant une solution SSIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Enterprise Information Management - Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=270871)  
  
  
