---
title: 'Leçon 5 : Automatisation du nettoyage et la mise en correspondance avec SSIS | Documents Microsoft'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 00dff9ac204e5e1b86feafc51da643222bce1758
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040092"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a>Leçon 5 : Automatisation du nettoyage et de la mise en correspondance avec SSIS
  Dans la leçon 1, vous avez créé la base de connaissances fournisseurs et utilisée pour nettoyer les données dans la leçon 2 et la faire correspondre les données dans la leçon 3, à l’aide de l’outil **Client DQS**. Dans un scénario réel, vous devrez peut-être extraire des données à partir d’une source qui DQS ne prend pas en charge ou pour automatiser les opérations de nettoyage et le processus de correspondance sans avoir à utiliser le **Client DQS** outil. SQL Server Integration Services (SSIS) a des composants que vous pouvez utiliser pour intégrer des données provenant de sources hétérogènes et un **[lien hypertexte «http://msdn.microsoft.com/library/ee677619.aspx"\t « _blank » transformation de nettoyage DQS](http://msdn.microsoft.com/library/ee677619.aspx)** composant pour appeler la fonctionnalité de nettoyage exposée par DQS. Actuellement, DQS n’expose pas de fonctionnalité de correspondance pour SSIS à utiliser, mais vous pouvez utiliser la **[transformation de regroupement probable](http://msdn.microsoft.com/library/ms141764.aspx)** pour identifier des doublons dans les données.  
  
 Vous pouvez télécharger des données dans MDS à l’aide de la **fonctionnalité de mise en lots basée sur l’entité**. Lorsque vous créez une entité dans MDS, les tables intermédiaires et les procédures stockées correspondantes sont automatiquement créées. Par exemple, lorsque vous avez créé l’entité fournisseur, le **stg.supplier_Leaf** table et la **stg.udp_Supplier_Leaf** procédure stockée ont été créées automatiquement. Vous utilisez les tables intermédiaires et les procédures pour créer, mettre à jour et supprimer des membres d'entité. Dans cette leçon, vous allez créer de nouveaux membres d'entité pour l'entité Fournisseur. Pour charger des données dans le serveur MDS, le package SSIS charge d'abord les données dans la table intermédiaire stg.supplier_Leaf puis exécute la procédure stockée associée stg.udp_Supplier_Leaf. Consultez [l’importation de données](http://msdn.microsoft.com/library/ee633726.aspx) pour plus d’informations.  
  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
1.  Supprimer les données des fournisseurs dans MDS (si vous avez suivi les quatre leçons précédentes). Le package SSIS que vous allez créer dans cette leçon va télécharger automatiquement les données dans MDS. Précédemment, vous avez téléchargé manuellement sur le serveur MDS les données des fournisseurs nettoyées et mises en correspondance à l'aide du client DQS.  
  
2.  Créer une vue d'abonnement sur l'entité Fournisseur pour exposer les données de l'entité dans d'autres applications. Cette action crée une vue SQL que vous allez vérifier l'aide de SQL Server Management Studio. Vous n'utiliserez pas cette vue dans cette version du didacticiel.  
  
3.  Créer et exécuter un projet SSIS à l’aide de **SQL Server Data Tools**. Le projet utilise **le nettoyage des données** transformation pour soumettre une demande de nettoyage pour le serveur DQS. DQS n’expose pas encore, la fonctionnalité de correspondance donc vous utiliserez **regroupement probable** transformation pour identifier des doublons.  
  
4.  Vérifier que les données sont créées dans MDS à l'aide de Master Data Manager.  
  
5.  Examiner les résultats du projet de nettoyage DQS créé par le package SSIS et, éventuellement, effectuer un nettoyage interactif pour créer la base de connaissances par la suite.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 1 &#40;requis&#41;: supprimer les données des fournisseurs dans MDS](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  