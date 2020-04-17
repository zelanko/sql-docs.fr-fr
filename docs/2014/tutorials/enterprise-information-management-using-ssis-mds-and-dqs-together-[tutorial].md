---
title: Gestion de l’information d’entreprise à l’aide de SSIS, MDS et DQS Together [Tutorial] Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ba09b504-3007-4cb7-8ef8-f01adbf51646
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 29ed5816a3a5fc0af6c5a4ac144557933e3e1a5f
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487718"
---
# <a name="enterprise-information-management-using-ssis-mds-and-dqs-together-tutorial"></a>Gestion des informations d'entreprise en associant SSIS, MDS et DQS [Didacticiel]
  La gestion des informations dans une entreprise implique généralement l'intégration des données au sein de l'entreprise et avec l'extérieur, le nettoyage des données, leur correspondance pour supprimer tous les doublons, leur normalisation, leur enrichissement, rendre les données conformes aux exigences juridiques et de conformité, et enfin, le stockage des données dans un emplacement centralisé avec tous les paramètres de sécurité nécessaires.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] fournit tous les composants nécessaires pour une solution de gestion des informations d'entreprise (EIM) efficace dans un seul produit. Les composants clés qui vous aident à générer une solution EIM sont les suivants :  
  
-   SQL Server Integration Services  
  
-   SQL Server Data Quality Services  
  
-   SQL Server Master Data Services  
  
 SQL Server Integration Services (SSIS) fournit une plateforme puissante et souple pour intégrer les données provenant de différentes sources dans une solution d'extraction, de transformation et de chargement (ETL) complète qui prend en charge les flux de travail d'entreprise, un entrepôt de données, ou la gestion des données de référence. Voir le sujet [d’aperçu des services d’intégration](https://msdn.microsoft.com/library/ms141263\(SQL.105\).aspx) pour une vue d’ensemble rapide et les utilisations typiques du SSIS.  
  
 SQL Server Data Quality Services (DQS) permet de nettoyer, faire correspondre, normaliser et enrichir les données, afin de disposer d'informations approuvées pour le décisionnel, d'un entrepôt de données et de charges de traitement transactionnel. Voir [l’introduction du](https://msdn.microsoft.com/library/ff877917.aspx) sujet des services de qualité des données pour le besoin d’affaires pour DQS et comment DQS répond au besoin.  
  
 SQL Server Master Data Services (MDS) est un concentrateur de données central qui garantit l'intégrité des informations et la cohérence des données entre différentes applications. Consultez le sujet [d’aperçu des services de données master](../master-data-services/master-data-services-overview-mds.md) pour de brèves descriptions des caractéristiques importantes de MDS.  
  
 Voir Cleansing and Matching Master Data à l’aide de whitepapers [d’EIM Technologies](https://msdn.microsoft.com/library/hh403491.aspx) pour obtenir des conseils complets sur la mise en œuvre d’une solution EIM utilisant ensemble ces technologies DE l’EIM Microsoft et regarder la gestion de [l’information d’entreprise (EIM) : réunir la vidéo SSIS, DQS et MDS](https://go.microsoft.com/fwlink/?LinkId=258672) pour une démonstration cool d’un scénario EIM.  
  
 Dans ce didacticiel, vous allez apprendre à utiliser SSIS, MDS et DQS conjointement pour implémenter un exemple de solution de gestion des informations d'entreprise (EIM). Vous utiliserez d'abord DQS pour créer une base de connaissances contenant les connaissances relatives aux données (métadonnées), puis vous allez nettoyer les données dans un fichier Excel à l'aide de la base de connaissances, et enfin, vous allez faire correspondre les données pour identifier et supprimer les doublons. Ensuite, vous utiliserez le complément MDS pour Excel pour télécharger les données nettoyées et mises en correspondance dans MDS. Enfin, vous automatiserez l'ensemble du processus en utilisant une solution SSIS. La solution SSIS dans ce tutoriel lit les données d’entrée d’un fichier Excel, mais vous pouvez l’étendre à lire à partir de diverses sources telles que Oracle, Teradata, DB2, et Azure SQL Database.  
  
## <a name="prerequisites"></a>Prérequis  
  
1.  Microsoft SQL Server 2012 avec les composants suivants.  
  
    1.  Integration Services (SSIS)  
  
    2.  Master Data Services (MDS)  
  
    3.  Data Quality Services (DQS)  
  
    4.  SQL Server Data Tools  
  
         Consultez [le guide d’installation SQL Server 2012](../database-engine/install-windows/installation-for-sql-server.md) pour plus de détails sur l’installation du produit.  
  
2.  [Configurer MDS à l'aide du Gestionnaire de configuration Master Data Services](https://msdn.microsoft.com/library/ee633884.aspx)  
  
     Utilisez le Gestionnaire de configuration pour créer et configurer une base de données Master Data Services. Après avoir créé la base de données MDS, créez une application `http://localhost/MDS`Web pour MDS dans un site Web (par exemple : ) et associez la base de données MDS à l’application Web MDS. Notez que, pour créer une application Web MDS, vous devez installer IIS sur votre ordinateur. Consultez [les exigences en matière d’applications Web (Services de données master)](https://msdn.microsoft.com/library/ee633744.aspx) et les exigences en matière de bases de données [(Services de données master)](https://msdn.microsoft.com/library/ee633767.aspx) pour plus de détails sur les conditions préalables à la configuration de la base de données MDS et de l’application Web.  
  
3.  [Installer et configurer DQS à l’aide de Data Quality Server Install](https://msdn.microsoft.com/library/hh231682.aspx). Cliquez sur **Démarrer**, cliquez sur **Tous les programmes**, cliquez sur Microsoft **SQL Server 2014**, cliquez sur **Data Quality Services**, puis cliquez sur Data Quality Server Install **.**  
  
4.  Microsoft Excel 2010 (32 bits) est préférable.  
  
5.  Installez **Master Data Services Add-in pour Excel** (32 bits ou 64 bits en fonction de la version d’Excel que vous avez sur votre ordinateur) à partir [d’ici](https://www.microsoft.com/download/details.aspx?id=29064). Pour trouver la version d’Excel installée sur votre ordinateur, exécutez **Excel**, cliquez sur **Fichier** sur la barre du menu et cliquez sur **Aide** pour voir la version dans le bon volet. Notez que vous devez installer Visual Studio 2010 Tools pour Office Runtime avant d'installer le complément Excel.  
  
6.  (Facultatif) Créez un compte avec [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/). L'une des tâches du didacticiel nécessite que vous ayez un compte sur la **Place de marché Azure** (anciennement **Data Market**). Vous pouvez ignorer cette tâche, si vous préférez, et passer à la tâche suivante.  
  
7.  Téléchargez le fichier Suppliers.xls à partir de [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=50426).  
  
8.  DQS ne vous permet pas d’exporter les résultats de nettoyage ou de correspondance vers un fichier Excel si vous utilisez **la version 64 bits d’Excel**. Il s'agit d'un problème connu. Pour le contourner, procédez comme suit :  
  
    1.  Exécuter **DQLInstaller.exe -upgrade**. Si vous avez installé l'instance par défaut de SQL Server, le fichier DQSInstaller.exe est copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn. Double-cliquez sur le fichier DQSInstaller.exe.  
  
    2.  Dans **Master Data Services Configuration Manager**, cliquez sur Select **Database**, sélectionnez la base de données **MDS** existante, puis cliquez **sur Mise à niveau**.  
  
## <a name="lessons"></a>Leçons  
  
|Leçon|Brève description|Durée estimée (en minutes).|  
|------------|-----------------------|------------------------------------------------|  
|[Leçon 1 : Création d’une base de connaissances DQS nommée Fournisseurs](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)|Dans cette leçon, vous créez une base de connaissances DQS nommée **Fournisseurs**.|60|  
|[Leçon 2 : Nettoyage des données des fournisseurs avec la base de connaissances Fournisseurs](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)|Dans cette leçon, vous créez et exécutez un projet DQS pour nettoyer les données des fournisseurs dans un fichier Excel en utilisant la base de connaissances **fournisseurs** que vous avez créée dans la première leçon.|45|  
|[Leçon 3 : Faire correspondre les données pour supprimer les doublons de la liste des fournisseurs](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)|Dans cette leçon, vous allez créer un projet DQS pour effectuer une activité de correspondance et identifier et supprimer les doublons de la liste des fournisseurs nettoyée.|45|  
|[Leçon 4 : Stockage des données sur les fournisseurs dans MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)|Dans cette leçon, vous téléchargez les données des fournisseurs nettoyés et appariés à Master Data Services (MDS) en utilisant **l’add-in MDS pour Excel**.|45|  
|[Leçon 5 : Automatisation du nettoyage et de la mise en correspondance avec SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)|Dans cette leçon, vous allez créer une solution SSIS qui nettoie les données d'entrée à l'aide de DQS, fait correspondre les données nettoyées pour supprimer les doublons, et stocke dans MDS les données nettoyées et mises en correspondance de manière automatisée.|75|  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour commencer le tutoriel, continuez à la première leçon: [Leçon 1: Création des fournisseurs DQS Knowledge Base](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md).  
  
  
