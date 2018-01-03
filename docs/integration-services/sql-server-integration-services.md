---
title: SQL Server Integration Services | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
keywords: SSIS
helpviewer_keywords:
- SSIS
- DTS [Integration Services]
- SQL Server Integration Services
- Integration Services
- DTS [Integration Services], about Integration Services
- data integration [Integration Services]
- Data Transformation Services
ms.assetid: c4398655-5657-4ae4-a690-a380790fe84f
caps.latest.revision: "51"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 2f1580e8d59c391b5721fc89ea2b58712ec34364
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sql-server-integration-services"></a>SQL Server Integration Services

 > Pour accéder au contenu relatif aux versions précédentes de SQL Server, consultez [SQL Server Integration Services](https://msdn.microsoft.com/library/ms141026(SQL.120).aspx).

[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est une plateforme qui permet de créer des solutions de transformation de données et d’intégration de données au niveau de l’entreprise. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vous permet de résoudre des problèmes professionnels complexes en copiant ou en téléchargeant des fichiers, en envoyant des messages électroniques en réponse à des événements, en mettant à jour des entrepôts de données, en nettoyant et en explorant des données et en gérant des données et des objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Les packages peuvent fonctionner en mode autonome ou de concert avec d'autres packages en réponse à des besoins professionnels complexes. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] peut extraire et transformer des données provenant d’une grande variété de sources, par exemple des fichiers de données XML, des fichiers plats et des sources de données relationnelles, puis charger les données dans une ou plusieurs destinations.<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut un ensemble étendu de tâches et de transformations intégrées, des outils pour construire des packages, et le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] permettant d’exécuter et de gérer des packages. Vous pouvez utiliser les outils graphiques de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour créer des solutions sans écrire une seule ligne de code. Vous pouvez également programmer le modèle objet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] étendu pour créer des packages par programmation, et coder des tâches personnalisées et d’autres objets de package.

## <a name="try-sql-server-and-sql-server-integration-services"></a>Essayer SQL Server et SQL Server Integration Services
- [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [Télécharger SQL Server 2017 ou 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server)
- [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [Télécharger SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)

##  <a name="infotipsql-servermediainfo-tippng-get-help"></a>![info_tip](../sql-server/media/info-tip.png) Obtenir de l’aide
 
- [Forum MSDN pour SSIS - poser des questions](https://social.msdn.microsoft.com/Forums/home?forum=sqlintegrationservices)
- [Forum MSDN SSDT et SSMS - poser des questions](https://social.msdn.microsoft.com/Forums/home?forum=sqltool)
- [Dépassement de la capacité de la pile (balise *ssis*) - poser des questions](http://stackoverflow.com/questions/tagged/ssis)
- [Microsoft Connect : signaler des bogues et demander des fonctionnalités](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit : discussion générale sur SSIS](https://www.reddit.com/r/SQLServer/search?q=ssis&restrict_sr=on)
- [Options de support Microsoft pour les utilisateurs professionnels](https://support.microsoft.com/gp/support-options-for-business)
- [Options de contact Microsoft pour les utilisateurs professionnels](https://support.microsoft.com/gp/contactus81?Audience=Commercial)
