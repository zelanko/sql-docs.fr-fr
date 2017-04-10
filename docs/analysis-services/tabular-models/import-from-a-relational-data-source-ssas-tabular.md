---
title: "Importer &#224; partir d&#39;une source de donn&#233;es relationnelles (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Importer &#224; partir d&#39;une source de donn&#233;es relationnelles (SSAS Tabulaire)
  Vous pouvez importer des données provenant de diverses bases de données relationnelles à l’aide de l’Assistant Importation de table. L’assistant est disponible dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans le menu **Modèle**. Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur. Pour plus d’informations sur les fournisseurs et les sources de données pris en charge, consultez [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md).  
  
 L'Assistant Importation de table prend en charge l'importation des données à partir des sources de données suivantes :  
  
 **Bases de données relationnelles**  
  
-   Base de données Microsoft SQL Server  
  
-   Microsoft SQL Azure  
  
-   Base de données Microsoft Access  
  
-   Microsoft SQL Server Parallel Data Warehouse  
  
-   Oracle  
  
-   Teradata  
  
-   Sybase  
  
-   Informix  
  
-   IBM DB2  
  
-   OLE DB/ODBC  
  
 **Sources multidimensionnelles**  
  
-   Cube Microsoft SQL Server Analysis Services  
  
 L’Assistant Importation de table ne prend pas en charge l’importation des données d’un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] comme source de données.  
  
### Pour importer des données à partir d'une base de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
2.  Dans la page **Connexion à une source de données**, sélectionnez le type de base de données à laquelle établir une connexion, puis cliquez sur **Suivant**.  
  
3.  Suivez les étapes de l'Assistant Importation de table. Dans les pages suivantes, vous pouvez sélectionner des vues et des tables spécifiques ou appliquer des filtres à l’aide de la page **Sélectionner des tables et des vues** ou en créant une requête SQL dans la page **Spécifier une requête SQL**.  
  
## Voir aussi  
 [Importer des données &#40;SSAS Tabulaire&#41;](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)   
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  