---
title: "Types de données SQL Server et SSIS pris en charge pour les domaines DQS | Microsoft Docs"
ms.custom: 
ms.date: 11/08/2011
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ec7d426fd60890eb6b61da4441e9f497e4d58162
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="supported-sql-server-and-ssis-data-types-for-dqs-domains"></a>Types de données SQL Server et SSIS pris en charge pour les domaines DQS
  Il existe de nombreux types de données dans SQL Server et SQL Server Integration Services (SSIS), mais seulement quatre types de données pour les domaines DQS : Date, Décimal, Entier et Chaîne. Les types de données SQL Server et SSIS ne sont pas tous pris en charge dans DQS. Vous ne pouvez mapper vos données source à un domaine DQS en vue d'y effectuer des activités portant sur la qualité des données que si le type de données source est pris en charge dans DQS et qu'il correspond au type de données du domaine DQS. Cette rubrique fournit des informations relatives aux types de données SQL Server et SSIS qui sont pris en charge et disponibles en vue d'un mappage à chacun des quatre types de données de domaine dans DQS.  
  
> [!NOTE]  
>  Dans les fichiers .xlsx et .xls, le type de données de la colonne source est déterminé par le type de données prédominant des huit premières lignes. Si une cellule n'est pas conforme à ce type de données, elle recevra une valeur NULL. De la même manière, dans les fichiers .csv, le type de données de la colonne source est déterminé par le type de données prédominant des huit premières lignes.  
  
##  <a name="SQLServer"></a> Types de données SQL Server pris en charge  
 Le tableau suivant fournit des informations sur les types de données SQL Server pris en charge pour chaque type de données de domaine DQS :  
  
|Type de données de domaine DQS|Type de données SQL Server pris en charge|  
|--------------------------|------------------------------------|  
|Date|Date|  
|Décimal|Décimal<br /><br /> float<br /><br /> money<br /><br /> numeric<br /><br /> real<br /><br /> smallmoney|  
|Entier|bigint<br /><br /> int<br /><br /> smallint<br /><br /> tinyint|  
|Chaîne|char<br /><br /> nchar<br /><br /> nvarchar<br /><br /> varchar|  
  
 Les autres types de données SQL Server ne sont pas pris en charge dans DQS. Pour plus d’informations sur les types de données SQL Server, consultez [Types de données &#40;Transact-SQL&#41;](../t-sql/data-types/data-types-transact-sql.md).  
  
##  <a name="SSIS"></a> Types de données SSIS pris en charge  
 Le tableau suivant fournit des informations sur les types de données SSIS pris en charge pour chaque type de données de domaine DQS :  
  
|Type de données de domaine DQS|Type de données SSIS pris en charge|  
|--------------------------|------------------------------|  
|Date|DT_DATE|  
|Décimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|Entier|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|Chaîne|DT_STR<br /><br /> DT_WSTR|  
  
 Les autres types de données SSIS ne sont pas pris en charge dans DQS Pour plus d'informations sur tous les types de données SSIS, consultez [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion d’un domaine](../data-quality-services/managing-a-domain.md)  
  
  
