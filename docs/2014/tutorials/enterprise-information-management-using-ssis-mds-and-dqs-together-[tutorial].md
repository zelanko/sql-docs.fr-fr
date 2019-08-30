---
title: Gestion des informations d’entreprise à l’aide de SSIS, MDS et DQS [Tutoriel] | Microsoft Docs
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
ms.openlocfilehash: 47bb74bf5fd35696481a88c4ccc30a8733f257a2
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153562"
---
# <a name="enterprise-information-management-using-ssis-mds-and-dqs-together-tutorial"></a>Gestion des informations d'entreprise en associant SSIS, MDS et DQS [Didacticiel]
  La gestion des informations dans une entreprise implique généralement l'intégration des données au sein de l'entreprise et avec l'extérieur, le nettoyage des données, leur correspondance pour supprimer tous les doublons, leur normalisation, leur enrichissement, rendre les données conformes aux exigences juridiques et de conformité, et enfin, le stockage des données dans un emplacement centralisé avec tous les paramètres de sécurité nécessaires.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] fournit tous les composants nécessaires pour une solution de gestion des informations d'entreprise (EIM) efficace dans un seul produit. Les composants clés qui vous aident à générer une solution EIM sont les suivants :  
  
-   SQL Server Integration Services  
  
-   SQL Server Data Quality Services  
  
-   SQL Server Master Data Services  
  
 SQL Server Integration Services (SSIS) fournit une plateforme puissante et souple pour intégrer les données provenant de différentes sources dans une solution d'extraction, de transformation et de chargement (ETL) complète qui prend en charge les flux de travail d'entreprise, un entrepôt de données, ou la gestion des données de référence. Consultez [Integration Services rubrique vue d’ensemble](https://msdn.microsoft.com/library/ms141263\(SQL.105\).aspx) pour obtenir une vue d’ensemble rapide et des utilisations courantes de SSIS.  
  
 SQL Server Data Quality Services (DQS) permet de nettoyer, faire correspondre, normaliser et enrichir les données, afin de disposer d'informations approuvées pour le décisionnel, d'un entrepôt de données et de charges de traitement transactionnel. Consultez Présentation de la rubrique [Data Quality Services](https://msdn.microsoft.com/library/ff877917.aspx) pour connaître les besoins de l’entreprise pour DQS et comment DQS répond à ce besoin.  
  
 SQL Server Master Data Services (MDS) est un concentrateur de données central qui garantit l'intégrité des informations et la cohérence des données entre différentes applications. Consultez [Master Data Services rubrique vue d’ensemble](../master-data-services/master-data-services-overview-mds.md) pour obtenir une brève description des fonctionnalités importantes de MDS.  
  
 Pour obtenir une aide complète sur l’implémentation d’une solution EIM à l’aide de ces technologies Microsoft EIM et regarder [la gestion des informations d’entreprise (EIM), consultez nettoyage et mise en correspondance des [données de référence à l’aide](https://msdn.microsoft.com/library/hh403491.aspx) de la technologie EIM. : Regroupez SSIS, DQS et MDS](https://go.microsoft.com/fwlink/?LinkId=258672) Video pour une démonstration pratique d’un scénario EIM.  
  
 Dans ce didacticiel, vous allez apprendre à utiliser SSIS, MDS et DQS conjointement pour implémenter un exemple de solution de gestion des informations d'entreprise (EIM). Vous utiliserez d'abord DQS pour créer une base de connaissances contenant les connaissances relatives aux données (métadonnées), puis vous allez nettoyer les données dans un fichier Excel à l'aide de la base de connaissances, et enfin, vous allez faire correspondre les données pour identifier et supprimer les doublons. Ensuite, vous utiliserez le complément MDS pour Excel pour télécharger les données nettoyées et mises en correspondance dans MDS. Enfin, vous automatiserez l'ensemble du processus en utilisant une solution SSIS. La solution SSIS dans ce didacticiel lit les données d’entrée à partir d’un fichier Excel, mais vous pouvez l’étendre pour lire à partir de diverses sources telles que Oracle, Teradata, DB2 et Azure SQL Database.  
  
## <a name="prerequisites"></a>Prérequis  
  
1.  Microsoft SQL Server 2012 avec les composants suivants.  
  
    1.  Integration Services (SSIS)  
  
    2.  Master Data Services (MDS)  
  
    3.  Data Quality Services (DQS)  
  
    4.  SQL Server Data Tools  
  
         Pour plus d’informations sur l’installation du produit, consultez le [Guide d’installation de SQL Server 2012](../database-engine/install-windows/installation-for-sql-server.md) .  
  
2.  [Configurer MDS à l’aide de Gestionnaire de configuration Master Data Services](https://msdn.microsoft.com/library/ee633884.aspx)  
  
     Utilisez le Gestionnaire de configuration pour créer et configurer une base de données Master Data Services. Après avoir créé la base de données MDS, créez une application Web pour MDS dans un site Web (par [http://localhost/MDS](http://localhost/MDS)exemple:) et associez la base de données MDS à l’application Web MDS. Notez que, pour créer une application Web MDS, vous devez installer IIS sur votre ordinateur. Pour plus d’informations sur les conditions préalables à la configuration de la base de données MDS et de l’application Web, consultez Configuration requise pour l' [application Web (Master Data Services)](https://msdn.microsoft.com/library/ee633744.aspx) et [base de données (Master Data Services)](https://msdn.microsoft.com/library/ee633767.aspx) .  
  
3.  [Installez et configurez DQS à l’aide du programme d’installation de Data Quality Server](https://msdn.microsoft.com/library/hh231682.aspx). Cliquez **sur Démarrer**, **sur tous les programmes**, sur **Microsoft SQL Server 2014**, sur **Data Quality Services**, puis sur **Data Quality Server installer**.  
  
4.  Microsoft Excel 2010 (32 bits) est préférable.  
  
5.  Installez **complément Master Data Services pour Excel** (32 bits ou 64 bits en fonction de la version d’Excel que vous avez sur votre ordinateur) [ici](https://www.microsoft.com/download/details.aspx?id=29064). Pour trouver la version d’Excel installée sur votre ordinateur, exécutez **Excel**, cliquez sur **fichier** dans la barre de menus et cliquez sur **aide** pour afficher la version dans le volet droit. Notez que vous devez installer Visual Studio 2010 Tools pour Office Runtime avant d’installer le complément Excel.  
  
6.  Facultatif Créez un compte avec la place de [marché Azure](https://azuremarketplace.microsoft.com/marketplace/). L’une des tâches du didacticiel nécessite que vous disposiez d’un compte **Azure Marketplace** (nommé à l’origine **Data Market**). Vous pouvez ignorer cette tâche, si vous préférez, et passer à la tâche suivante.  
  
7.  Téléchargez le fichier Suppliers. xls à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=50426).  
  
8.  DQS ne vous permet pas d’exporter les résultats de nettoyage ou de correspondance dans un fichier Excel si vous utilisez la **version 64 bits d’Excel**. Il s'agit d'un problème connu. Pour le contourner, procédez comme suit :  
  
    1.  Exécutez **DQLInstaller. exe-Upgrade**. Si vous avez installé l'instance par défaut de SQL Server, le fichier DQSInstaller.exe est copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn. Double-cliquez sur le fichier DQSInstaller.exe.  
  
    2.  Dans **Gestionnaire de configuration Master Data Services**, cliquez sur **Sélectionner une base de**données, sélectionnez base de données **MDS** existante, puis cliquez sur **mettre à niveau**.  
  
## <a name="lessons"></a>Leçons  
  
|Leçon|Brève description|Durée estimée (en minutes).|  
|------------|-----------------------|------------------------------------------------|  
|[Leçon 1 : Création de la base de connaissances DQS des fournisseurs](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)|Dans cette leçon, vous allez créer une base de connaissancesDQS nommée Suppliers.|60|  
|[Leçon 2 : Nettoyage des données des fournisseurs à l’aide de la base de connaissances fournisseurs](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)|Dans cette leçon, vous allez créer et exécuter un projet DQS pour nettoyer les données des fournisseurs dans un fichier Excel à l’aide de la base de connaissances **fournisseurs** que vous avez créée dans la première leçon.|45|  
|[Leçon 3 : Données correspondantes pour supprimer les doublons de la liste des fournisseurs](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)|Dans cette leçon, vous allez créer un projet DQS pour effectuer une activité de correspondance et identifier et supprimer les doublons de la liste des fournisseurs nettoyée.|45|  
|[Leçon 4 : Stockage des données des fournisseurs dans MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)|Dans cette leçon, vous chargez les données des fournisseurs nettoyés et mis en correspondance dans Master Data Services (MDS) à l’aide de la **complément MDS pour Excel**.|45|  
|[Leçon 5 : Automatisation du nettoyage et de la correspondance à l’aide de SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)|Dans cette leçon, vous allez créer une solution SSIS qui nettoie les données d'entrée à l'aide de DQS, fait correspondre les données nettoyées pour supprimer les doublons, et stocke dans MDS les données nettoyées et mises en correspondance de manière automatisée.|75|  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour commencer le didacticiel, passez à la première leçon: [Leçon 1 : Création de la base](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)de connaissances DQS des fournisseurs.  
  
  
