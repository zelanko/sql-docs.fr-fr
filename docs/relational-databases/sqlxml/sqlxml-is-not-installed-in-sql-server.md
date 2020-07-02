---
title: SQLXML n'est pas installé dans SQL Server
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3412b02a7164a5cb57421c52b3662e226bf7e537
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85665917"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML n'est pas installé dans SQL Server
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Avant [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 était fourni avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et faisait partie de l'installation par défaut de toutes les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l'exception de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. À partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la dernière version de SQLXML (SQLXML 4.0 SP1) n'est plus incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour installer SQLXML 4,0 SP1, téléchargez-le à partir de l' [emplacement d’installation de sqlxml 4,0 SP1](https://www.microsoft.com/download/details.aspx?id=30403).  
  
 Si une application s’exécute sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et requiert sqlxml 4,0, vous devez télécharger et installer sqlxml 4,0 SP1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Comportement de SQLXML 4.0 SP1 avec les nouveaux types de données utilisant SQLOLEDB et le fournisseur OLE DB SQL Server Native Client  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]a introduit les types de données suivants, que les développeurs qui utilisent SQLXML peuvent souhaiter utiliser :  
  
-   **Date**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 Lorsque vous utilisez SQLXML 4,0 SP1 avec SQLOLEDB ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , ces types apparaissent en tant que chaînes pour un développeur. SQLXML 4,0 SP1 activera ces quatre nouveaux types de données comme types scalaires intégrés lorsqu’ils sont utilisés avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur 11,0 ou version ultérieure. Tant que vous n'aurez pas téléchargé SQLXML 4.0 SP1, le mappage de ces types en types autres que chaîne risque de provoquer la troncation de certaines données. Par exemple, si vous mappez **datetime2** à **xsd : date** , les données seront tronquées à la [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] précision **DateTime** de 3,33 millisecondes.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de la programmation SQLXML 4.0](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
