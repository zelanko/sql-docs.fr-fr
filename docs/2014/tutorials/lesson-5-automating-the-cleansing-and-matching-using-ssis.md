---
title: 'Leçon 5 : automatisation du nettoyage et de la correspondance à l’aide de SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ec6f347cdbc6d14e8f621466a1708b8ee9fe7d36
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489751"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a>Leçon 5 : Automatisation du nettoyage et de la mise en correspondance avec SSIS
  Dans la leçon 1, vous avez créé la base de connaissances fournisseurs et vous l’avez utilisée pour nettoyer les données de la leçon 2 et faire correspondre les données de la leçon 3 à l’aide de l’outil **DQS client**. Dans un scénario réel, vous devrez peut-être extraire des données d’une source que DQS ne prend pas en charge ou vous souhaitez automatiser le processus de nettoyage et de correspondance sans avoir à utiliser l’outil **client DQS** . SQL Server Integration Services (SSIS) comporte des composants que vous pouvez utiliser pour intégrer des données provenant de différentes sources hétérogènes et un composant de **[transformation de nettoyage DQS](https://msdn.microsoft.com/library/ee677619.aspx)** pour appeler les fonctionnalités de nettoyage exposées par DQS. Actuellement, DQS n’expose pas les fonctionnalités de correspondance pour SSIS à utiliser, mais vous pouvez utiliser la **[transformation de regroupement probable](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)** pour identifier les doublons dans les données.  
  
 Vous pouvez charger des données dans MDS à l’aide de la **fonctionnalité de mise en lots basée sur les entités**. Lorsque vous créez une entité dans MDS, les tables intermédiaires et les procédures stockées correspondantes sont automatiquement créées. Par exemple, lorsque vous avez créé l’entité supplier, la table **STG. supplier_Leaf** et la procédure stockée **STG. udp_Supplier_Leaf** ont été créées automatiquement. Vous utilisez les tables intermédiaires et les procédures pour créer, mettre à jour et supprimer des membres d'entité. Dans cette leçon, vous allez créer de nouveaux membres d'entité pour l'entité Fournisseur. Pour charger des données dans le serveur MDS, le package SSIS charge d'abord les données dans la table intermédiaire stg.supplier_Leaf puis exécute la procédure stockée associée stg.udp_Supplier_Leaf. Pour plus d’informations, consultez [importation de données](../master-data-services/overview-importing-data-from-tables-master-data-services.md) .  
  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
1.  Supprimer les données des fournisseurs dans MDS (si vous avez suivi les quatre leçons précédentes). Le package SSIS que vous allez créer dans cette leçon va télécharger automatiquement les données dans MDS. Précédemment, vous avez téléchargé manuellement sur le serveur MDS les données des fournisseurs nettoyées et mises en correspondance à l'aide du client DQS.  
  
2.  Créer une vue d'abonnement sur l'entité Fournisseur pour exposer les données de l'entité dans d'autres applications. Cette action crée une vue SQL que vous allez vérifier l'aide de SQL Server Management Studio. Vous n'utiliserez pas cette vue dans cette version du didacticiel.  
  
3.  Créez et exécutez un projet SSIS à l’aide de **SQL Server Data Tools**. Le projet utilise la transformation de **nettoyage de données** pour envoyer une demande de nettoyage au serveur DQS. DQS n’expose pas encore la fonctionnalité de correspondance, vous allez donc utiliser la transformation de **regroupement approximatif** pour identifier les doublons.  
  
4.  Vérifier que les données sont créées dans MDS à l'aide de Master Data Manager.  
  
5.  Examiner les résultats du projet de nettoyage DQS créé par le package SSIS et, éventuellement, effectuer un nettoyage interactif pour créer la base de connaissances par la suite.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 1 &#40;&#41; requis : suppression des données des fournisseurs dans MDS](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  
