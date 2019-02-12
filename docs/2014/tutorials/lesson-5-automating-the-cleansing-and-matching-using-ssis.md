---
title: 'Leçon 5 : Automatisation du nettoyage et la mise en correspondance avec SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 92261bc69590bcc338bf18aa9d406964bfe42fcd
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56026631"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a>Leçon 5 : Automatisation du nettoyage et de la mise en correspondance avec SSIS
  Dans la leçon 1, vous créé la base de connaissances fournisseurs et il permet de nettoyer les données dans la leçon 2 et de faire correspondre les données dans la leçon 3 à l’aide de l’outil **Client DQS**. Dans un scénario réel, vous devrez peut-être extraire des données à partir d’une source que DQS ne prend pas en charge ou que vous souhaitez automatiser le nettoyage et le processus de correspondance sans avoir à utiliser le **Client DQS** outil. SQL Server Integration Services (SSIS) a des composants que vous pouvez utiliser pour intégrer des données provenant de sources hétérogènes et un **[transformation de nettoyage DQS](https://msdn.microsoft.com/library/ee677619.aspx)** composant à appeler les opérations de nettoyage fonctionnalités exposées par DQS. Actuellement, DQS n’expose pas de fonctionnalité de correspondance pour SSIS à utiliser, mais vous pouvez utiliser la **[transformation de regroupement probable](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)** pour identifier des doublons dans les données.  
  
 Vous pouvez charger des données dans MDS à l’aide de la **fonctionnalité de mise en lots basée sur l’entité**. Lorsque vous créez une entité dans MDS, les tables intermédiaires et les procédures stockées correspondantes sont automatiquement créées. Par exemple, lorsque vous avez créé l’entité fournisseur, le **stg.supplier_Leaf** table et le **stg.udp_Supplier_Leaf** procédure stockée ont été créées automatiquement. Vous utilisez les tables intermédiaires et les procédures pour créer, mettre à jour et supprimer des membres d'entité. Dans cette leçon, vous allez créer de nouveaux membres d'entité pour l'entité Fournisseur. Pour charger des données dans le serveur MDS, le package SSIS charge d'abord les données dans la table intermédiaire stg.supplier_Leaf puis exécute la procédure stockée associée stg.udp_Supplier_Leaf. Consultez [l’importation de données](../master-data-services/overview-importing-data-from-tables-master-data-services.md) pour plus d’informations.  
  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
1.  Supprimer les données des fournisseurs dans MDS (si vous avez suivi les quatre leçons précédentes). Le package SSIS que vous allez créer dans cette leçon va télécharger automatiquement les données dans MDS. Précédemment, vous avez téléchargé manuellement sur le serveur MDS les données des fournisseurs nettoyées et mises en correspondance à l'aide du client DQS.  
  
2.  Créer une vue d'abonnement sur l'entité Fournisseur pour exposer les données de l'entité dans d'autres applications. Cette action crée une vue SQL que vous allez vérifier l'aide de SQL Server Management Studio. Vous n'utiliserez pas cette vue dans cette version du didacticiel.  
  
3.  Créer et exécuter un projet SSIS à l’aide de **SQL Server Data Tools**. Le projet utilise **nettoyage des données** transformation pour soumettre une demande de nettoyage au serveur DQS. DQS n’expose pas encore, la fonctionnalité de correspondance donc vous utiliserez **regroupement probable** transformation pour identifier des doublons.  
  
4.  Vérifier que les données sont créées dans MDS à l'aide de Master Data Manager.  
  
5.  Examiner les résultats du projet de nettoyage DQS créé par le package SSIS et, éventuellement, effectuer un nettoyage interactif pour créer la base de connaissances par la suite.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 1 &#40;prérequis&#41;: Supprimer les données des fournisseurs dans MDS](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  
