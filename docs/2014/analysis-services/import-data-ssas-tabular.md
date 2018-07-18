---
title: Importer des données (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6617b2a2-9f69-433e-89e0-4c5dc92982cf
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 35312647eeb1b452c155c05d7f4392fa540aa156
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253561"
---
# <a name="import-data-ssas-tabular"></a>Importer des données (SSAS Tabulaire)
  Vous pouvez importer des données dans un modèle tabulaire à partir d'une grande diversité de sources. Les rubriques de cette section décrivent l'utilisation de l'Assistant Importation de données pour vous connecter à des données et les sélectionner afin de les importer dans un projet de modèle.  
  
> [!IMPORTANT]  
>  Si l'une des tables de votre modèle contient un grand nombre de lignes, envisagez d'importer uniquement un sous-ensemble des données lors de la création du modèle. En important un sous-ensemble des données, vous pouvez réduire le temps de traitement et la consommation des ressources du serveur de base de données de l'espace de travail.  
  
 Grâce à l'Assistant Importation de table, vous pouvez importer des données à partir des sources de données suivantes :  
  
|**Source de données**|**Description**|  
|---------------------|---------------------|  
|**Bases de données relationnelles**|Les sources de données relationnelles incluent :<br /><br /> Microsoft SQL Server<br /><br /> Microsoft SQL Azure<br /><br /> Microsoft SQL Server Parallel Data Warehouse<br /><br /> Microsoft Access<br /><br /> Oracle<br /><br /> Teradata<br /><br /> Sybase<br /><br /> Informix<br /><br /> IBM DB2<br /><br /> OLEDB/ODBC|  
|**Sources multidimensionnelles**|Cube Microsoft SQL Server Analysis Services|  
|**Flux de données**|Les flux de données incluent :<br /><br /> Rapport Microsoft Reporting Services<br /><br /> Dataset Azure DataMarket<br /><br /> Flux Atom d'un fournisseur public ou d'entreprise|  
|**Fichiers texte**|Les fichiers texte incluent :<br /><br /> Fichiers Excel (.xlsx)<br /><br /> Fichier texte (.txt)|  
  
 Outre l'importation de données à l'aide de l'Assistant Importation de table, vous pouvez coller des données copiées (depuis le Presse-papiers) dans une table. Les données collées se comportent différemment des données qui ont été importées à partir d'autres sources de données. Les données collées dans les tables n'ont aucune propriété de nom de connexion ou de données sources. Les données collées sont persistantes dans le fichier model.bim. Lorsque le projet ou le fichier model.bim est enregistré, les données collées le sont également.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Importer à partir d’une Source de données relationnelles &#40;SSAS tabulaire&#41;](import-from-a-relational-data-source-ssas-tabular.md)|Décrit comment importer des données depuis des sources de données relationnelles, telles qu'une base de données Microsoft SQL Server, Oracle ou Teradata.|  
|[Importer à partir d’une Source de données multidimensionnelle &#40;SSAS tabulaire&#41;](import-from-a-multidimensional-data-source-ssas-tabular.md)|Décrit comment importer les données d'un cube multidimensionnel SQL Server Analysis Services.|  
|[Importer à partir d’un flux de données &#40;SSAS tabulaire&#41;](import-from-a-data-feed-ssas-tabular.md)|Décrit comment importer des données depuis un flux de données tel qu'un rapport Microsoft Reporting Services ou un dataset Azure Data Market.|  
|[Importer à partir d’un fichier texte &#40;SSAS tabulaire&#41;](import-from-a-text-file-ssas-tabular.md)|Décrit comment importer des données à partir d'un classeur Microsoft Excel ou d'un fichier texte.|  
|[Copier et coller des données &#40;SSAS tabulaire&#41;](copy-and-paste-data-ssas-tabular.md)|Décrit comment ajouter des données à une table existante dans le générateur de modèles à l'aide des commandes Coller et Coller par ajout.|  
  
  
