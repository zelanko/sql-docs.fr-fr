---
title: Enterprise Information Management à l’aide de SSIS, MDS et DQS conjointement [didacticiel] | Microsoft Docs
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
ms.topic: conceptual
ms.assetid: ba09b504-3007-4cb7-8ef8-f01adbf51646
caps.latest.revision: 11
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf4106c531dbb1f386f8c1b6745f773bbe3c0f4b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189656"
---
# <a name="enterprise-information-management-using-ssis-mds-and-dqs-together-tutorial"></a>Gestion des informations d'entreprise en associant SSIS, MDS et DQS [Didacticiel]
  La gestion des informations dans une entreprise implique généralement l'intégration des données au sein de l'entreprise et avec l'extérieur, le nettoyage des données, leur correspondance pour supprimer tous les doublons, leur normalisation, leur enrichissement, rendre les données conformes aux exigences juridiques et de conformité, et enfin, le stockage des données dans un emplacement centralisé avec tous les paramètres de sécurité nécessaires.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] fournit tous les composants nécessaires pour une solution de gestion des informations d'entreprise (EIM) efficace dans un seul produit. Les composants clés qui vous aident à générer une solution EIM sont les suivants :  
  
-   SQL Server Integration Services  
  
-   SQL Server Data Quality Services  
  
-   SQL Server Master Data Services  
  
 SQL Server Integration Services (SSIS) fournit une plateforme puissante et souple pour intégrer les données provenant de différentes sources dans une solution d'extraction, de transformation et de chargement (ETL) complète qui prend en charge les flux de travail d'entreprise, un entrepôt de données, ou la gestion des données de référence. Consultez [présentation d’Integration Services](http://msdn.microsoft.com/library/ms141263\(SQL.105\).aspx) rubrique pour une présentation rapide et classique utilise de SSIS.  
  
 SQL Server Data Quality Services (DQS) permet de nettoyer, faire correspondre, normaliser et enrichir les données, afin de disposer d'informations approuvées pour le décisionnel, d'un entrepôt de données et de charges de traitement transactionnel. Consultez [présentation de Data Quality Services](http://msdn.microsoft.com/library/ff877917.aspx) rubrique pour les besoins de l’entreprise pour DQS et la manière dont DQS répond à la nécessité.  
  
 SQL Server Master Data Services (MDS) est un concentrateur de données central qui garantit l'intégrité des informations et la cohérence des données entre différentes applications. Consultez [Master Data Services Overview](http://msdn.microsoft.com/library/ff487003.aspx) rubrique pour une brève description des fonctionnalités importantes de MDS.  
  
 Consultez [nettoyage et la mise en correspondance des données de référence en utilisant les Technologies EIM](http://msdn.microsoft.com/library/hh403491.aspx) livres blancs pour obtenir une aide complète sur l’implémentation d’une solution EIM à l’aide de ces technologies Microsoft EIM ensemble et un espion [Enterprise Information Management (EIM) : Associer SSIS, DQS et MDS](http://go.microsoft.com/fwlink/?LinkId=258672) vidéo pour un exemple d’un scénario EIM.  
  
 Dans ce didacticiel, vous allez apprendre à utiliser SSIS, MDS et DQS conjointement pour implémenter un exemple de solution de gestion des informations d'entreprise (EIM). Vous utiliserez d'abord DQS pour créer une base de connaissances contenant les connaissances relatives aux données (métadonnées), puis vous allez nettoyer les données dans un fichier Excel à l'aide de la base de connaissances, et enfin, vous allez faire correspondre les données pour identifier et supprimer les doublons. Ensuite, vous utiliserez le complément MDS pour Excel pour télécharger les données nettoyées et mises en correspondance dans MDS. Enfin, vous automatiserez l'ensemble du processus en utilisant une solution SSIS. La solution SSIS décrite dans ce didacticiel lit les données d'entrée à partir d'un fichier Excel, mais vous pouvez l'étendre pour lire d'autres sources telles que Oracle, Teradata, DB2 et Microsoft Azure SQL Database.  
  
## <a name="prerequisites"></a>Prérequis  
  
1.  Microsoft SQL Server 2012 avec les composants suivants.  
  
    1.  Integration Services (SSIS)  
  
    2.  Master Data Services (MDS)  
  
    3.  Data Quality Services (DQS)  
  
    4.  SQL Server Data Tools  
  
         Consultez [Guide d’Installation de SQL Server 2012](http://msdn.microsoft.com/library/bb500469.aspx) pour plus d’informations sur l’installation du produit.  
  
2.  [Configurer MDS à l’aide du Gestionnaire de Configuration de Master Data Services](http://msdn.microsoft.com/library/ee633884.aspx)  
  
     Utilisez le Gestionnaire de configuration pour créer et configurer une base de données Master Data Services. Après avoir créé la base de données MDS, créez une application web pour MDS dans un site web (par exemple : [ http://localhost/MDS ](http://localhost/MDS)) et associer la base de données MDS à l’application web MDS. Notez que, pour créer une application Web MDS, vous devez installer IIS sur votre ordinateur. Consultez [configuration requise pour Application Web (Master Data Services)](http://msdn.microsoft.com/library/ee633744.aspx) et [configuration requise (Master Data Services) de la base de données](http://msdn.microsoft.com/library/ee633767.aspx) pour plus d’informations sur la configuration requise pour la configuration d’application de base de données et web MDS.  
  
3.  [Installer et configurer DQS à l’aide de Data Quality Server Installer](http://msdn.microsoft.com/library/hh231682.aspx). Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2014**, cliquez sur **Data Quality Services**, puis cliquez sur **Data Quality Server Installer**.  
  
4.  Microsoft Excel 2010 (32 bits) est préférable.  
  
5.  Installer **complément Master Data Services pour Excel** (32 bits ou 64 bits basé sur la version d’Excel que vous avez sur votre ordinateur) à partir de [ici](http://www.microsoft.com/download/details.aspx?id=29064). Pour rechercher la version d’Excel installée sur votre ordinateur, exécutez **Excel**, cliquez sur **fichier** sur la barre de menus, cliquez sur **aide** pour afficher la version dans le volet droit. Notez que vous devez installer Visual Studio 2010 Tools pour Office Runtime avant d’installer la macro complémentaire Excel.  
  
6.  (Facultatif) Créez un compte avec [Windows Azure Marketplace](https://datamarket.azure.com/). Une des tâches dans le didacticiel, vous devez avoir un **place de marché Azure** (à l’origine nommé **Data Market**) compte. Vous pouvez ignorer cette tâche, si vous préférez, et passer à la tâche suivante.  
  
7.  Téléchargez le fichier Suppliers.xls à partir de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=271504).  
  
8.  DQS ne vous permet pas exporter le nettoyage ou la mise en correspondance les résultats vers un fichier Excel si vous utilisez **version 64 bits d’Excel**. Il s'agit d'un problème connu. Pour le contourner, procédez comme suit :  
  
    1.  Exécutez **DQLInstaller.exe – mise à niveau**. Si vous avez installé l'instance par défaut de SQL Server, le fichier DQSInstaller.exe est copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn. Double-cliquez sur le fichier DQSInstaller.exe.  
  
    2.  Dans **Gestionnaire de Configuration de Master Data Services**, cliquez sur **sélectionner la base de données**, sélectionnez existant **MDS** de base de données, puis cliquez sur **mise à niveau**.  
  
## <a name="lessons"></a>Leçons  
  
|Leçon|Brève description|Durée estimée (en minutes).|  
|------------|-----------------------|------------------------------------------------|  
|[Leçon 1 : Création d’une base de connaissances DQS nommée Fournisseurs](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md)|Dans cette leçon, vous créez une base de connaissances DQS nommée **fournisseurs**.|60|  
|[Leçon 2 : Nettoyage des données des fournisseurs avec la base de connaissances Fournisseurs](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)|Dans cette leçon, vous créez et exécutez un projet DQS pour nettoyer les données des fournisseurs dans un fichier Excel à l’aide de la **fournisseurs** vous avez créé dans la première leçon de Base de connaissances.|45|  
|[Leçon 3 : Faire correspondre les données pour supprimer les doublons de la liste des fournisseurs](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)|Dans cette leçon, vous allez créer un projet DQS pour effectuer une activité de correspondance et identifier et supprimer les doublons de la liste des fournisseurs nettoyée.|45|  
|[Leçon 4 : Stockage des données sur les fournisseurs dans MDS](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)|Dans cette leçon, vous chargez les données des fournisseurs nettoyées et mises en correspondance à Master Data Services (MDS) à l’aide de la **complément MDS pour Excel**.|45|  
|[Leçon 5 : Automatisation du nettoyage et de la mise en correspondance avec SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)|Dans cette leçon, vous allez créer une solution SSIS qui nettoie les données d'entrée à l'aide de DQS, fait correspondre les données nettoyées pour supprimer les doublons, et stocke dans MDS les données nettoyées et mises en correspondance de manière automatisée.|75|  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour démarrer le didacticiel, passez à la première leçon : [leçon 1 : création de la Base de connaissances DQS nommée fournisseurs](../../2014/tutorials/lesson-1-creating-the-suppliers-dqs-knowledge-base.md).  
  
  
