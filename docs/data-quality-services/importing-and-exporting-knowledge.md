---
description: Importation et exportation de connaissances
title: Importation et exportation de connaissances
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 639e248fd938f3d2429b3d33729414224db1dc8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462121"
---
# <a name="importing-and-exporting-knowledge"></a>Importation et exportation de connaissances

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Vous pouvez créer des bases de connaissances et les domaines directement dans l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ou vous pouvez importer ou exporter les connaissances vers ou depuis une base de connaissances. Dans l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , vous pouvez utiliser un fichier de données pour les opérations d'importation et d'exportation, ou un fichier Excel pour les opérations d'importation. Le fichier de données utilisé est un fichier chiffré qui est créé par [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) avec l'extension .dqs. Les fichiers créés par Microsoft Excel peuvent avoir une extension .xlsx, .xls ou .csv. Ces opérations offrent plus de souplesse dans la génération et le partage des connaissances que vous utilisez pour effectuer le nettoyage et la correspondance des données.  
  
> [!IMPORTANT]  
>  Vous pouvez exporter *toutes* les bases de connaissances de votre [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] vers un fichier de sauvegarde DQS (.dqsb) en exécutant le fichier DQSInstaller.exe à partir de l'invite de commandes. De même, vous pouvez importer *toutes* les bases de connaissances à partir d'un fichier de sauvegarde DQS (.dqsb) vers votre [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] en exécutant le fichier DQSInstaller.exe à partir de l'invite de commandes. Pour plus d’informations, consultez [Export et Import DQS Knowledge Bases Using DQSInstaller.exe](../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) dans le guide d’installation DQS.  
  
## <a name="in-this-section"></a>Dans cette section  
 Vous pouvez exécuter les opérations d'importation et d'exportation suivantes :  
  
|Description de l’opération|Rubrique|  
|-|-|  
|Exporter un domaine d'une base de connaissances vers un fichier de données .dqs|[Exporter un domaine vers un fichier .dqs](../data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|Importer un domaine à partir d'un fichier de données .dqs vers une base de connaissances existante|[Importer un domaine à partir d'un fichier .dqs](../data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|Exporter une base de connaissances entière vers un fichier de données .dqs|[Exporter une base de connaissances dans un fichier .dqs](../data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|Importer une base de connaissances entière vers un fichier de données .dqs|[Importer une base de connaissances à partir d'un fichier .dqs](../data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|Importer les valeurs d'un fichier Excel dans un domaine|[Importer les valeurs d'un fichier Excel dans un domaine](../data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|Importer les domaines d'un fichier Excel vers une base de connaissances|[Importer les domaines d'un fichier Excel dans la découverte des connaissances](../data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|Importer les connaissance recueillies pendant le nettoyage vers une base de connaissances|[Importer des valeurs de projet de nettoyage dans un domaine](../data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Construction d'une base de connaissances par la découverte de la connaissance et la gestion interactive de la connaissance|[Construction d'une base de connaissances](../data-quality-services/building-a-knowledge-base.md)|  
|Création d'un seul domaine et ajout de connaissances au domaine.|[Gestion d'un domaine](../data-quality-services/managing-a-domain.md)|  
|Création d'un domaine composite et ajout de connaissances au domaine.|[Gestion d'un domaine composite](../data-quality-services/managing-a-composite-domain.md)|  
  
  
