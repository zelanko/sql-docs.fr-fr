---
title: Informations de référence sur les fichiers d’entrée XML (Assistant Paramétrage du moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7dd0170481a3894334dc01b2974a27ace6b736b4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041508"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Référence des fichiers d'entrée XML (Assistant Paramétrage du moteur de base de données)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] L’Assistant Paramétrage peut utiliser un fichier d’entrée XML pour paramétrer une base de données. Ce fichier XML désigne les bases de données, les tables, les fichiers ou tables de charge de travail et les options de paramétrage à utiliser pendant la session de paramétrage. Vous pouvez également utiliser ce fichier pour indiquer une configuration spécifiée par l'utilisateur afin d'effectuer une évaluation de simulation.  
  
 Un fichier d’entrée XML de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] contient une hiérarchie d’éléments XML, chaque élément XML comprenant le texte ou d’autres éléments qui spécifient les paramètres de la session de paramétrage. Le fichier d’entrée XML de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit être conforme aux normes pour le XML correctement formé. Tous les éléments respectent la casse. Les éléments sont spécifiés à l'aide de la casse Pascal, ce qui signifie que le premier caractère est en majuscules, tout comme la première lettre des mots concaténés suivants.  
  
 Toutes les valeurs d'éléments doivent respecter les conventions d'affectation de noms XML. Pour plus d’informations sur ces conventions, consultez [XML Textual Content](http://go.microsoft.com/fwlink/?LinkId=7614) (Contenu textuel XML) dans la bibliothèque MSDN.  
  
 Notez que ce Guide de référence n'est pas complet. Pour plus d'informations sur tous les éléments que vous pouvez utiliser pour définir une entrée XML, reportez-vous au schéma DTASchema.xsd de l'Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="xml-declaration"></a>Déclaration XML  
  
-   [Données XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Élément racine DTAXML  
  
-   [DTAXML, élément &#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Éléments DTAInput  
  
-   [DTAInput, élément &#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Élément serveur &#40;DTA&#41;](server-element-dta.md)  
  
-   [Élément de la charge de travail &#40;DTA&#41;](workload-element-dta.md)  
  
-   [Tuningoptions, élément &#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [Élément de configuration &#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Éléments de serveur  
  
-   [Nom d’élément pour le serveur &#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Élément de base de données pour le serveur &#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Éléments de charge de travail  
  
-   [Élément de fichier &#40;DTA&#41;](file-element-dta.md)  
  
-   [Élément de base de données pour les charges de travail &#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [Élément EventString &#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Éléments d'options de paramétrage  
  
-   [Tuningtimeinmin, élément &#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [Storageboundinmb, élément &#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [TESTSERVER, élément &#40;DTA&#41;](testserver-element-dta.md)  
  
-   [Featureset, élément &#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Partitioning, élément &#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [DropOnlyMode (élément) &#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [Keepexisting, élément &#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [Onlineindexoperation, élément &#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [Databasetoconnect, élément &#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Éléments de configuration  
  
-   [Élément de serveur de Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Élément de base de données de Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Recommendation, élément &#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [Créer l’élément &#40;DTA&#41;](create-element-dta.md)  
  
-   [Élément d’index &#40;DTA&#41;](index-element-dta.md)  
  
-   [Nom d’élément pour l’Index &#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Élément de colonne pour les Index &#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [Nom d’élément de colonne &#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Élément de groupe de fichiers pour les Index &#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Éléments de base de données  
  
-   [Nom d’élément de base de données &#40;DTA&#41;](name-element-for-database-dta.md)  
  
-   [Élément de schéma pour la base de données &#40;DTA&#41;](schema-element-for-database-dta.md)  
  
-   [Nom d’élément de schéma &#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [Élément de table de schéma &#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [Nom d’élément pour la Table &#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  