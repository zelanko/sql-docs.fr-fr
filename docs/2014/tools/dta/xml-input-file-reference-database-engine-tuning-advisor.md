---
title: Informations de référence sur les fichiers d’entrée XML (Assistant Paramétrage du moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b560b36eb98ec73723a4ce25cb3c647f4962b634
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62509981"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Référence des fichiers d'entrée XML (Assistant Paramétrage du moteur de base de données)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)]L’Assistant Paramétrage du peut utiliser un fichier d’entrée XML pour paramétrer une base de données. Ce fichier XML désigne les bases de données, les tables, les fichiers ou tables de charge de travail et les options de paramétrage à utiliser pendant la session de paramétrage. Vous pouvez également utiliser ce fichier pour indiquer une configuration spécifiée par l'utilisateur afin d'effectuer une évaluation de simulation.  
  
 Un fichier d’entrée XML de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] contient une hiérarchie d’éléments XML, chaque élément XML comprenant le texte ou d’autres éléments qui spécifient les paramètres de la session de paramétrage. Le fichier d’entrée XML de l’Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit être conforme aux normes pour le XML correctement formé. Tous les éléments respectent la casse. Les éléments sont spécifiés à l'aide de la casse Pascal, ce qui signifie que le premier caractère est en majuscules, tout comme la première lettre des mots concaténés suivants.  
  
 Toutes les valeurs d'éléments doivent respecter les conventions d'affectation de noms XML. Pour plus d’informations sur ces conventions, consultez [XML Textual Content](https://go.microsoft.com/fwlink/?LinkId=7614) (Contenu textuel XML) dans la bibliothèque MSDN.  
  
 Notez que ce Guide de référence n'est pas complet. Pour plus d'informations sur tous les éléments que vous pouvez utiliser pour définir une entrée XML, reportez-vous au schéma DTASchema.xsd de l'Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="xml-declaration"></a>Déclaration XML  
  
-   [Données XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Élément racine DTAXML  
  
-   [Élément DTAXML &#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Éléments DTAInput  
  
-   [Élément DTAInput &#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Server, élément &#40;Assistant Paramétrage de base de données&#41;](server-element-dta.md)  
  
-   [Élément de charge de travail &#40;&#41;DTA](workload-element-dta.md)  
  
-   [Élément TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [Élément de configuration &#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Éléments de serveur  
  
-   [Élément Name pour le serveur &#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Élément Database pour le serveur &#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Éléments de charge de travail  
  
-   [Élément file &#40;DTA&#41;](file-element-dta.md)  
  
-   [Database, élément de la charge de travail &#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [Élément EventString &#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Éléments d'options de paramétrage  
  
-   [Élément TuningTimeInMin, &#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [Élément StorageBoundInMB, &#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [Élément TestServer &#40;DTA&#41;](testserver-element-dta.md)  
  
-   [Élément FeatureSet, &#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Élément de partitionnement &#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [Élément DropOnlyMode, &#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [Élément KeepExisting, &#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [Élément OnlineIndexOperation, &#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [Élément DatabaseToConnect, &#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Éléments de configuration  
  
-   [Élément Server pour la configuration &#40;DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Élément Database pour la configuration &#40;DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Élément Recommendation &#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [Créer un élément &#40;DTA&#41;](create-element-dta.md)  
  
-   [Élément index &#40;DTA&#41;](index-element-dta.md)  
  
-   [Élément Name pour l’index &#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Élément Column pour l’index &#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [Élément Name pour la colonne &#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Élément FileGroup pour l’index &#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Éléments de base de données  
  
-   [Name, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](name-element-for-database-dta.md)  
  
-   [Schema, élément pour les bases de données &#40;Assistant Paramétrage de base de données&#41;](schema-element-for-database-dta.md)  
  
-   [Élément Name pour le schéma &#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [Élément table pour le schéma &#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [Élément Name pour la table &#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
