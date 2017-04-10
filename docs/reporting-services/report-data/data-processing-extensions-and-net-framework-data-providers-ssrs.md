---
title: "Extensions pour le traitement des donn&#233;es et fournisseurs de donn&#233;es&#160;.NET Framework (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rapports [Reporting Services], données"
  - "extensions pour le traitement des données [Reporting Services]"
  - "fournisseurs de données [Reporting Services]"
  - "récupération de données [Reporting Services]"
  - "Reporting Services, sources de données"
  - "données de rapport [Générateur de rapports], accès"
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Extensions pour le traitement des donn&#233;es et fournisseurs de donn&#233;es&#160;.NET Framework (SSRS)
  Une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est un composant installé avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et chargé de récupérer des données à partir d’un type spécifique de source de données, et de fournir des fonctionnalités supplémentaires de prise en charge de la conception et du traitement des rapports. Un fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] est un composant disponible dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou des sources tierces qui prend en charge des interfaces <xref:System.Data> qui vous permettent de récupérer et de modifier des données à partir d’un type spécifique de source de données.  
  
## Présentation d'une extension pour le traitement des données  
 Une extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prend en charge un sous-ensemble des interfaces <xref:System.Data>. Les extensions pour le traitement des données requièrent l'accès en lecture seule à une source de données ; de ce fait, les interfaces pour l'écriture et la mise à jour ne sont pas implémentées. Chaque extension pour le traitement des données peut fournir des fonctionnalités personnalisées pour prendre en charge le traitement des rapports. Par exemple, une extension pour le traitement des données peut prendre en charge les types de fonctionnalités suivants :  
  
-   Gestion des informations d'identification indépendamment de la chaîne de connexion  
  
-   Prise en charge des paramètres à valeurs multiples  
  
-   Récupération des agrégats de serveur, calculés sur la source de données  
  
-   Récupération des propriétés de données ainsi que des valeurs de données dans la source de données  
  
## Présentation d'un fournisseur de données  
 Un fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (parfois connu sous le nom de pilote) prend en charge un jeu standard d’interfaces <xref:System.Data> pour lire, écrire et mettre à jour des données sur une source de données. Vous pouvez utiliser un fournisseur de données en l'absence d'extension pour le traitement des données pour un type spécifique de source de données. De nombreux fournisseurs de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] standard tiers sont disponibles.  
  
 Comme [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] possède une architecture de fournisseur de données extensible, vous pouvez créer une extension pour le traitement des données personnalisée pour inclure les fonctionnalités supplémentaires fournies par les extensions pour le traitement de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour plus d'informations, consultez [Implémentation d’une extension pour le traitement des données](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md). Pour les extensions pour le traitement des données tierces, consultez la documentation associée.  
  
> [!NOTE]  
>  Vous devez installer et inscrire un fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ou une extension pour le traitement des données personnalisée avant de pouvoir les utiliser pour accéder à des données à partir d'une source de données. L'extension pour le traitement des données doit être installée et inscrite à la fois sur le client de création de rapports pour créer le rapport et sur le serveur de rapports pour afficher le rapport publié. Tous les fournisseurs de données ne sont pas conçus pour fonctionner dans un environnement serveur. Pour plus d’informations, consultez [Inscrire un fournisseur de données .NET Framework standard &#40;SSRS&#41;](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md) et [Déploiement d’une extension pour le traitement des données](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md).  
  
## Voir aussi  
 [Vue d'ensemble des extensions pour le traitement des données](../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  