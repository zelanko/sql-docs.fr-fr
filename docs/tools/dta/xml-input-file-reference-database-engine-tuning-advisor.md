---
title: "Référence (Assistant Paramétrage du moteur de base de données) du fichier d’entrée XML | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d98a6bfc0fc61d76c434f20609205c52c202a257
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Référence des fichiers d'entrée XML (Assistant Paramétrage du moteur de base de données)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)]L’Assistant paramétrage peut utiliser un fichier d’entrée XML pour paramétrer une base de données. Ce fichier XML désigne les bases de données, les tables, les fichiers ou tables de charge de travail et les options de paramétrage à utiliser pendant la session de paramétrage. Vous pouvez également utiliser ce fichier pour indiquer une configuration spécifiée par l'utilisateur afin d'effectuer une évaluation de simulation.  
  
 Un fichier d’entrée XML de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] contient une hiérarchie d’éléments XML, chaque élément XML comprenant le texte ou d’autres éléments qui spécifient les paramètres de la session de paramétrage. Le fichier d’entrée XML de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit être conforme aux normes pour le XML correctement formé. Tous les éléments respectent la casse. Les éléments sont spécifiés à l'aide de la casse Pascal, ce qui signifie que le premier caractère est en majuscules, tout comme la première lettre des mots concaténés suivants.  
  
 Toutes les valeurs d'éléments doivent respecter les conventions d'affectation de noms XML. Pour plus d’informations sur ces conventions, consultez [XML Textual Content](http://go.microsoft.com/fwlink/?LinkId=7614) (Contenu textuel XML) dans la bibliothèque MSDN.  
  
 Notez que ce Guide de référence n'est pas complet. Pour plus d'informations sur tous les éléments que vous pouvez utiliser pour définir une entrée XML, reportez-vous au schéma DTASchema.xsd de l'Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="xml-declaration"></a>Déclaration XML  
  
-   [Données XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Élément racine DTAXML  
  
-   [DTAXML, élément &#40; DTA &#41;](../../tools/dta/dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Éléments DTAInput  
  
-   [DTAInput, élément &#40; DTA &#41;](../../tools/dta/dtainput-element-dta.md)  
  
-   [Élément de serveur &#40; DTA &#41;](../../tools/dta/server-element-dta.md)  
  
-   [Workload, élément &#40; DTA &#41;](../../tools/dta/workload-element-dta.md)  
  
-   [Tuningoptions, élément &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)  
  
-   [Élément de configuration &#40; DTA &#41;](../../tools/dta/configuration-element-dta.md)  
  
## <a name="server-elements"></a>Éléments de serveur  
  
-   [Name, élément pour les serveurs &#40; DTA &#41;](../../tools/dta/name-element-for-server-dta.md)  
  
-   [Élément de base de données de serveur &#40; DTA &#41;](../../tools/dta/database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Éléments de charge de travail  
  
-   [Élément de fichier &#40; DTA &#41;](../../tools/dta/file-element-dta.md)  
  
-   [Élément de base de données pour la charge de travail &#40; DTA &#41;](../../tools/dta/database-element-for-workload-dta.md)  
  
-   [Eventstring, élément &#40; DTA &#41;](../../tools/dta/eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Éléments d'options de paramétrage  
  
-   [Tuningtimeinmin, élément &#40; DTA &#41;](../../tools/dta/tuningtimeinmin-element-dta.md)  
  
-   [Storageboundinmb, élément &#40; DTA &#41;](../../tools/dta/storageboundinmb-element-dta.md)  
  
-   [TESTSERVER, élément &#40; DTA &#41;](../../tools/dta/testserver-element-dta.md)  
  
-   [Featureset, élément &#40; DTA &#41;](../../tools/dta/featureset-element-dta.md)  
  
-   [Partitioning, élément &#40; DTA &#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   [Droponlymode, élément &#40; DTA &#41;](../../tools/dta/droponlymode-element-dta.md)  
  
-   [Keepexisting, élément &#40; DTA &#41;](../../tools/dta/keepexisting-element-dta.md)  
  
-   [Onlineindexoperation, élément &#40; DTA &#41;](../../tools/dta/onlineindexoperation-element-dta.md)  
  
-   [Databasetoconnect, élément &#40; DTA &#41;](../../tools/dta/databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Éléments de configuration  
  
-   [Élément Server Configuration &#40; DTA &#41;](../../tools/dta/server-element-for-configuration-dta.md)  
  
-   [Élément de base de données Configuration &#40; DTA &#41;](../../tools/dta/database-element-for-configuration-dta.md)  
  
-   [Recommendation, élément &#40; DTA &#41;](../../tools/dta/recommendation-element-dta.md)  
  
-   [Créer, élément &#40; DTA &#41;](../../tools/dta/create-element-dta.md)  
  
-   [Index, élément &#40; DTA &#41;](../../tools/dta/index-element-dta.md)  
  
-   [Name, élément pour les Index &#40; DTA &#41;](../../tools/dta/name-element-for-index-dta.md)  
  
-   [Column, élément pour les Index &#40; DTA &#41;](../../tools/dta/column-element-for-index-dta.md)  
  
-   [Name, élément pour la colonne &#40; DTA &#41;](../../tools/dta/name-element-for-column-dta.md)  
  
-   [Élément de groupe de fichiers pour les Index &#40; DTA &#41;](../../tools/dta/filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Éléments de base de données  
  
-   [Name, élément pour la base de données &#40; DTA &#41;](../../tools/dta/name-element-for-database-dta.md)  
  
-   [Élément de schéma pour la base de données &#40; DTA &#41;](../../tools/dta/schema-element-for-database-dta.md)  
  
-   [Name, élément pour les schémas &#40; DTA &#41;](../../tools/dta/name-element-for-schema-dta.md)  
  
-   [Table, élément pour les schémas &#40; DTA &#41;](../../tools/dta/table-element-for-schema-dta.md)  
  
-   [Name, élément pour la Table &#40; DTA &#41;](../../tools/dta/name-element-for-table-dta.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
