---
title: Types de données d’instance Oracle CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5dc1ae24d927247a1af61ff974a535b6bdb48502
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71298670"
---
# <a name="oracle-cdc-instance-data-types"></a>Types de données d'instance Oracle CDC

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  L'instance Oracle CDC prend en charge la plupart des types de données Oracle. Les sections suivantes décrivent les types de données pris en charge et les types de données non pris en charge.  
  
## <a name="supported-data-types"></a>Types de données pris en charge  
 Le tableau suivant décrit les types de données Oracle qui peuvent être capturés et leur mappage par défaut aux types de données SQL Server dans les tables de modifications. Lorsque vous ajoutez une instance de capture pour une table Oracle source, vous pouvez remplacer certains de ces mappages.  
  
|Type de données de base de données Oracle|Type de données de SQL Server|  
|-------------------------------|--------------------------|  
|BINARY_FLOAT|real|  
|BINARY_DOUBLE|FLOAT|  
|CHAR|NVARCHAR|  
|DATE|DATETIME|  
|FLOAT|FLOAT|  
|INT|NUMERIC (38)|  
|INTERVAL|DATETIME|  
|NCHAR|NVARCHAR|  
|NUMBER|FLOAT|  
|NAVARCHAR2|NVARCHAR|  
|RAW|VARBINARY|  
|real|FLOAT|  
|timestamp|DATETIME2|  
|TIMESTAMP WITH TIME ZONE|VARCHAR (37)|  
|TIMESTAMP WITH LOCAL TIME ZONE|VARCHAR (37)|  
|VARCHAR2|VARCHAR|  
|XMLTYPE|NVARCHAR (MAX)|  
  
## <a name="non-supported-data-types"></a>Types de données non pris en charge  
 Les tables Oracle sources avec des colonnes de types de données Oracle suivants ne peuvent pas être capturées. Les colonnes capturées avec ces types de données s'affichent en tant que colonnes NULL ; toutefois, une modification de leur valeur est indiquée dans le masque de modification des tables capturées.  
  
-   LONG  
  
-   XMLTYPE  
  
-   BLOB  
  
-   CLOB  
  
 Les tables Oracle sources avec des colonnes de types de données Oracle suivants ne peuvent pas être capturées.  
  
-   BFILE  
  
-   ROWID  
  
-   REF  
  
-   UROWID  
  
-   Table imbriquée  
  
 Si les types de données suivants sont présents dans une table, ils empêchent le LogMinder d'obtenir les données de colonne de la table :  
  
-   Types de données définis par l'utilisateur  
  
-   VARRAY  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de capture de données modifiées pour Oracle par Attunity](../../integration-services/change-data-capture/change-data-capture-designer-for-oracle-by-attunity.md)   
 [Instance CDC Oracle](../../integration-services/change-data-capture/the-oracle-cdc-instance.md)  
  
  
