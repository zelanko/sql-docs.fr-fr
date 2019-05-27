---
title: Importer à partir d’une Source de données relationnelles (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 61fb30ea21ea810eab8d30a3a040fac4a1bd2128
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080530"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a>Importer à partir d'une source de données relationnelles (SSAS Tabulaire)
  Vous pouvez importer des données provenant de diverses bases de données relationnelles à l’aide de l’Assistant Importation de table. L’assistant est disponible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le menu **Modèle** . Pour vous connecter à une source de données, vous devez disposer du fournisseur approprié, installé sur votre ordinateur. Pour plus d’informations sur les fournisseurs et les sources de données pris en charge, consultez [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
 L'Assistant Importation de table prend en charge l'importation des données à partir des sources de données suivantes :  
  
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
  
 L’Assistant Importation de table ne prend pas en charge l’importation des données d’un classeur [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] comme source de données.  
  
### <a name="to-import-data-from-a-database"></a>Pour importer des données à partir d'une base de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
2.  Dans la page **Connexion à une source de données** , sélectionnez le type de base de données à laquelle établir une connexion, puis cliquez sur **Suivant**.  
  
3.  Suivez les étapes de l'Assistant Importation de table. Dans les pages suivantes, vous pouvez sélectionner des vues et des tables spécifiques ou appliquer des filtres à l’aide de la page **Sélectionner des tables et des vues** ou en créant une requête SQL dans la page **Spécifier une requête SQL** .  
  
## <a name="see-also"></a>Voir aussi  
 [Importer des données &#40;SSAS Tabulaire&#41;](import-data-ssas-tabular.md)   
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
