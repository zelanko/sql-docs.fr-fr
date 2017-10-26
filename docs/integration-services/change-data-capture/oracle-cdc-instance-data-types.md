---
title: "Types de données d’Instance Oracle CDC | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ce8e5f7622c520f819b65000729b7d3c750764fc
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="oracle-cdc-instance-data-types"></a>Types de données d'instance Oracle CDC
  L'instance Oracle CDC prend en charge la plupart des types de données Oracle. Les sections suivantes décrivent les types de données pris en charge et les types de données non pris en charge.  
  
## <a name="supported-data-types"></a>Types de données pris en charge  
 Le tableau suivant décrit les types de données Oracle qui peuvent être capturés et leur mappage par défaut aux types de données SQL Server dans les tables de modifications. Lorsque vous ajoutez une instance de capture pour une table Oracle source, vous pouvez remplacer certains de ces mappages.  
  
|Type de données de base de données Oracle|Type de données de SQL Server|  
|-------------------------------|--------------------------|  
|BINARY_FLOAT|REAL|  
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
|REAL|FLOAT|  
|TIMESTAMP|DATETIME2|  
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
 [Concepteur de Capture de données modifiées pour Oracle par Attunity](../../integration-services/change-data-capture/change-data-capture-designer-for-oracle-by-attunity.md)   
 [L’Instance Oracle CDC](../../integration-services/change-data-capture/the-oracle-cdc-instance.md)  
  
  

